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

**Proposed tech (Dec 2025):** React Native (TypeScript), iOS + Android.

**Client preference (May 2026):** Flutter. Joseph Osei Owusu specified Flutter in the May 2026 LinkedIn exchange. This supersedes the React Native recommendation in the December 2025 proposal but has not yet been validated with VL internally.

**Resourcing note:** VL has limited Flutter developer capacity. This is a resourcing consideration to resolve before committing to a Flutter engagement — not a technical blocker.

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

## Layer 3 — RemitONE White-label Backend

Third-party managed (black box). Provides the core remittance domain: remitter registry, beneficiaries, FX rates, transaction lifecycle, wallet ledger, wallet load flows, compliance/business rules via UISettings.

API: REST-style POST endpoints, XML responses. Version 3.3 (March 2020). See [`integrations/remitone.md`](./integrations/remitone.md).

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
