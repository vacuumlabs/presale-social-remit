---
type: concept
title: MVP Scope
tags: [mvp, scope, features, remittance]
sources:
  - ../client-inputs/Socialremit_Customer_Flow_Nov2025.md
  - ../team-inputs/2025-12-17-fe-build-proposal.md
  - ../client-inputs/2026-05-28-joseph-qa-response.md
last_updated: 2026-05-29
status: active
---

# MVP Scope

Defined in the December 2025 proposal ([`team-inputs/2025-12-17-fe-build-proposal.md`](../team-inputs/2025-12-17-fe-build-proposal.md)) based on analysis of what RemitONE supports out of the box versus what requires custom build.

## In scope for MVP

- iOS + Android app (single codebase)
- User onboarding with progressive KYC (quickregistered → updateProfile flow)
- Login, 2FA, PIN login, biometric unlock, password/PIN reset
- User profile management
- Beneficiary management (bank deposit + mobile money)
- FX calculator (rates, fees, exchange rate display)
- Send money flow — Bank Transfer, Mobile Money, Cash Pickup
- Wallet top-ups — Card Payment, Bank Transfer (open banking)
- Wallet balances and transaction history
- Support section and settings
- Standard UX polish (not pixel-perfect fintech; explicitly "not Revolut-level")
- One environment initially (prod-like)

## Explicitly out of scope for MVP (deferred to Phase 2)

These features are not natively supported by Fincode and would require custom BFF implementation if required earlier:

- Request money flow
- Direct Debit mandates
- Recurring transfers
- Scheduled transfers
- PDF statements / statement downloads
- Cancel / reverse transfer
- Card issuance / card management
- Full Admin Portal (Fincode + Sumsub dashboards cover ops needs at go-live; lightweight tooling TBC)
- Analytics

## Push notifications — desired at go-live, not a hard blocker

Joseph confirmed (28 May 2026): push notifications for key transaction events (send confirmed, send failed, status updates) are desired at go-live but are **not a hard blocker**. If timelines are tight, email confirmation + in-app status tracking is acceptable for the first weeks. **The architecture must support push notifications from day one**, even if some notification types are phased in shortly after launch. Source: [`client-inputs/2026-05-28-joseph-qa-response.md`](../client-inputs/2026-05-28-joseph-qa-response.md)

## Feature map (from client UX spec)

The November 2025 customer flow document ([`client-inputs/Socialremit_Customer_Flow_Nov2025.md`](../client-inputs/Socialremit_Customer_Flow_Nov2025.md)) additionally specifies the following Profile/Account features which overlap partially with Phase 2:

- Account statements (PDF, date-filtered) — Phase 2
- Wallets/Cards management (freeze card, Apple Wallet) — Phase 2 (card issuance excluded from MVP)
- Schedule transfers, direct debits, payment requests — Phase 2
- Notification preferences — Phase 2

## Open scope questions

Corridors (source/destination countries) and currencies in scope for MVP are not confirmed in any available source. See [`deal-context/open-questions.md`](../deal-context/open-questions.md) item 5.
