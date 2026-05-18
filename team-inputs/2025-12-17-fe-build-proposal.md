---
type: other
title: SocialRemit — FE Build Proposal, Dec 2025
source_type: internal-authored
author: Boris Vida
role: architect
status: active
version: 1
informed_by:
  - ../client-inputs/Socialremit_Customer_Flow_Nov2025.md
last_updated: 2025-12-17
---

# SocialRemit — FE Build Proposal, Dec 2025

Proposal document sent to SocialRemit on 17 December 2025. Original GDrive doc: `1vbWLnsZ_GTBkVH0Xbcasam92xm3ugFXJ_WFeCMbXvsc`.

## Components

### 1.1 Mobile App (built by VL)
React Native (TypeScript), iOS + Android from one codebase. Distributed via App Store / Google Play.

Covers: onboarding + progressive KYC, login/2FA, profile, beneficiaries, FX calculator, send money (bank transfer / mobile money / cash pickup), top-up (card + bank transfer), wallet/balances, transaction history, support, settings.

Client-side validation only; no RemitONE keys stored in the app. Secure session storage, device binding, optional biometric unlock.

### 1.2 BFF Layer (built by VL)
NestJS (Node.js) + Redis. Deployed on AWS ECS Fargate behind ALB/API Gateway. ElastiCache for session and UISettings caching. AWS WAF + Secrets Manager. CloudWatch Logs + Metrics.

Responsibilities: RSA encryption for RemitONE `encrypted_data` fields, XML→JSON mapping, session/token management, retries/timeouts, error normalisation, UISettings caching. Optional: PDF statements, analytics forwarding, notification orchestration.

### 1.3 RemitONE White-label Backend (third party)
Black box — managed by RemitONE. Provides: remitters, beneficiaries, rates/charges, transaction lifecycle, wallet ledger, wallet load flows, compliance/business rules via UISettings.

### 1.4 Administration Portal (RemitONE-provided, TBC)
Customer lookup, transaction search + status timeline, beneficiary lookup, wallet balances, support triage, manual compliance notes, CSV/PDF export.

## MVP Omissions (Phase 2)
Request money, Direct Debit mandates, recurring/scheduled transfers, PDF statements, in-app notifications, cancel/reverse transfer, card issuance.

## Estimation

| Option | Description | MDs | Est. (£) |
|--------|-------------|-----|----------|
| Option 1 | FE + BFF only | 175 MD | £118,125 |
| Option 2 | FE + BFF + parallel Discovery track | 250 MD | £168,750 |

Discovery track (Option 2) delivers: post-MVP feature map, product docs (epics/stories), roadmap, vendor list, wireframes/prototype.

Contract type: Time & Material (±30% on estimates given unknowns at time of writing).

## Technical Flow Detail (Send Money)

Full BFF↔RemitONE API mapping documented for the send money flow: init → list beneficiaries → create/update beneficiary → getCharges → createTransaction → getTransactionPaymentInstructions → confirmTransaction (OTP) → success. Exception handling: quote drift (409 QUOTE_CHANGED), RemitONE validation errors mapped to screen sections, missing payment instructions → manual payment fallback.
