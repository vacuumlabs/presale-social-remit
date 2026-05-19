---
type: system
title: System Architecture Overview
tags: [architecture, system, bff, remitone, flutter, react-native, aws]
sources:
  - ../team-inputs/2025-12-17-fe-build-proposal.md
last_updated: 2026-05-18
status: active
---

# System Architecture Overview

Three-layer architecture proposed in December 2025. The mobile technology choice is under re-evaluation for the May 2026 re-engagement (see note below).

## Layer 1 — Mobile App

**Open decision — Flutter vs React Native.** See `decisions.md` entry dated 2026-05-19.

Joseph's initial preference was Flutter. On the 19 May call Boris explained that React Native and Flutter are architecturally equivalent for this use case; React Native has a larger hiring pool (JavaScript vs Dart) and VL has more experience with it. Joseph opened up to React Native: "if it costs less and gives the customer the same experience, it makes sense." Boris to consult VL mobile experts and include a recommendation in the proposal. VL internal lean: React Native.

The current Figma prototype has a React implementation behind it (built separately by SocialRemit's team).

The app holds no RemitONE credentials. All communication goes through the BFF. Session token from the BFF is stored in secure device storage with optional biometric unlock.

## Layer 2 — BFF (Backend-for-Frontend)

Built by VL. Single JSON/REST API surface for the mobile app.

**Tech stack (Dec 2025 proposal):**
- Runtime: Node.js + NestJS
- Caching: Redis (ElastiCache)
- Deployment: Docker on AWS ECS Fargate, behind ALB or API Gateway
- Security: AWS WAF, Secrets Manager for RemitONE keys
- Observability: CloudWatch Logs + Metrics

**BFF responsibilities:**
- XML↔JSON translation (RemitONE API returns XML over POST)
- RSA encryption of `encrypted_data` fields required by RemitONE
- Session/token lifecycle management
- UISettings caching (RemitONE uses dynamic form configuration)
- Error normalisation and retry/timeout handling
- Optional: PDF statement generation, analytics event forwarding, notification orchestration

The BFF insulates the app from RemitONE's API design and is the correct place to implement any future-proofing if SocialRemit later migrates away from RemitONE.

## Layer 3 — Fincode White-label Backend

Third-party managed. Replaces RemitONE (selected after the December 2025 proposal; see [`integrations/remitone.md`](./integrations/remitone.md) for the superseded provider). SocialRemit plans to use Fincode for **12 months only**, then replace with their own proprietary backend. The BFF is the abstraction layer that makes this swap possible.

API details: not yet received. Joseph to send Fincode API documentation post-19 May 2026 call. See [`integrations/fincode.md`](./integrations/fincode.md).

## Layer 4 — Administration Portal

Provided by RemitONE (TBC). Covers: customer lookup, transaction search and status timeline, beneficiary lookup, wallet balances, support triage, manual compliance notes, CSV/PDF export.

## Architecture diagram

A high-level architecture diagram exists at `../../hla.png` (GDrive: `1Aqd0_Z91hjxnCWg2qjN4u9I_8H8MFSsO`). It shows a longer-term target state with additional services (auth & user management, beneficiary service, wallets & ledger, KYC/AML, FX & fees engine, fraud & risk, payments orchestrator, mobile money aggregator, open banking, card processor, notifications, CRM, DMS, analytics, reporting) — this appears to represent the Phase 2+ proprietary architecture, not the MVP.

## Send money — API call chain

The BFF orchestrates the following RemitONE calls for the send money flow:

1. `getTransactionUISettings` + `getBeneficiaryUISettings` + `getDestinationCountries` — initialise screen
2. `listBeneficiaries` — recipient selection
3. `createBeneficiary` / `updateBeneficiary` — add or edit recipient
4. `getCharges` — quote (fees + FX)
5. `createTransaction` — pre-commit
6. `getTransactionPaymentInstructions` — payment details for card/wallet/open banking
7. `confirmTransaction` (with OTP) — finalise
8. Optional: `requestTransactionConfirmationCode` — resend OTP
