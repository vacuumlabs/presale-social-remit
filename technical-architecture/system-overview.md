---
type: system
title: System Architecture Overview
tags: [architecture, system, bff, fincode, flutter, react-native, aws]
sources:
  - ../team-inputs/2025-12-17-fe-build-proposal.md
  - ../client-inputs/2026-05-19-governance-notes-v1.md
  - ../client-inputs/2026-05-19-meeting-minutes.md
  - ../client-inputs/2026-05-28-joseph-qa-response.md
last_updated: 2026-05-29
status: active
---

# System Architecture Overview

Three-layer architecture — aligned with SocialRemit's formal governance model (see [`governance-principles.md`](./governance-principles.md)). The December 2025 proposal introduced this pattern; the May 2026 governance document formalises it using SocialRemit's own layer naming.

## Layer naming (client's formal model)

| Client term | VL equivalent | Owner |
|---|---|---|
| Product Layer | Mobile app | Social Remit / VL-built |
| Control Layer | BFF / middleware | VL-built, Social Remit-owned |
| Infrastructure Layer | Fincode + Sumsub + payment providers | Third-party |

---

## Layer 1 — Product Layer (Mobile App)

**Open decision — Flutter vs React Native.** See `decisions.md` entry dated 2026-05-19.

Joseph's preference is Flutter. On the 19 May call Boris explained that React Native and Flutter are architecturally equivalent; React Native has a larger hiring pool (JavaScript vs Dart) and VL has more experience with it. Joseph is open to React Native: "if it costs less and gives the customer the same experience, it makes sense." Boris to consult VL mobile experts and include a recommendation in the proposal. VL internal lean: React Native.

The current Figma prototype has a React implementation behind it (built separately by SocialRemit's team).

The app must remain fully decoupled from provider-specific logic — per governance non-negotiables. All communication goes through the BFF. Session token stored in secure device storage; optional biometric unlock.

---

## Layer 2 — Control Layer (BFF / Middleware)

Built by VL. Single JSON/REST API surface for the mobile app. This layer is described by SocialRemit as strategically important and expected to become "increasingly valuable over time" — it is the primary intellectual asset VL is creating.

**Tech stack (baseline from Dec 2025 proposal — to be confirmed in new estimate):**
- Runtime: Node.js + NestJS
- Caching: Redis (ElastiCache)
- Deployment: Docker on AWS ECS Fargate, behind ALB or API Gateway
- Security: AWS WAF, Secrets Manager for provider credentials
- Observability: CloudWatch Logs + Metrics (minimum; governance doc requires full operational visibility — see below)

**Control Layer responsibilities:**
- Fincode API integration (auth, session management, response mapping)
- Progressive KYC routing (Sumsub SDK orchestration, threshold logic for CDD escalation)
- Sanctions screening + PEP screening + ongoing monitoring (via Sumsub or ComplyAdvantage)
- Error normalisation and retry/timeout handling
- Provider abstraction — frontend must not depend on Fincode response formats or workflows
- Event-driven orchestration (KYC completion events, first transfer events, referral triggers, inactivity signals)
- Rewards and referral eligibility logic
- Analytics event forwarding (Mixpanel/PostHog/Firebase — phasing TBD)
- Notification orchestration (OTP, transactional, behavioural nudges)

**The BFF is also the Fincode exit ramp.** When SocialRemit's proprietary backend (Transpara) is ready (~12 months), only the BFF's downstream integration changes. The mobile app is unaffected. This is a governance non-negotiable and a key investment narrative for SocialRemit's seed raise.

---

## Layer 3 — Infrastructure Layer (Fincode + Third-party Providers)

Third-party managed. Fincode is the white-label remittance backend (replaces RemitONE — see [`integrations/remitone.md`](./integrations/remitone.md)). SocialRemit plans to use Fincode for **12 months only**.

API documentation shared by Joseph on 19 May 2026: https://docs.fincode.technology/api/transactions/call-quote. See [`integrations/fincode.md`](./integrations/fincode.md) for full integration notes.

Other Infrastructure Layer providers:
- **Sumsub** — KYC/identity verification (contracted). Confirmed in MVP scope — handles document validation, liveness checks, sanctions/PEP screening, risk scoring, and progressive KYC escalation. VL builds the Flutter capture flow and BFF handoff; Sumsub handles all verification logic.
- **Trust Payments** (SECURE_TRADING) — card top-up gateway, already integrated in Fincode; to be enabled on SR tenant. VL integrates Trust Payments SDK in the mobile app for card tokenisation; token is passed through BFF to Fincode. No raw card data touches VL servers.
- **Volume** — open banking payments, already integrated in Fincode; to be enabled on SR tenant. Covers account-to-account instant funding.
- **Sanctions/AML** — handled by Sumsub (PEP screening, ongoing monitoring). Fincode also performs sanctions screening natively in the transaction flow.

---

## Observability requirements (governance non-negotiable)

"Operational blindness is considered a major business risk." The platform must support:
- Transaction lifecycle visibility (end-to-end, not just app-side)
- API monitoring (Fincode response times, error rates)
- Webhook monitoring
- OTP delivery visibility
- Provider payout visibility
- Alerting before customers report failures

CloudWatch alone is insufficient. A structured observability approach (tooling TBD) is required and must be scoped in the new estimate.

---

## CI/CD and environments (governance non-negotiable)

Must include: development environment, staging environment, production environment, structured deployment pipeline, rollback capability, version control discipline. This is not optional — it is a delivery non-negotiable per the governance framework.

---

## Administration Portal

Status: TBD for new estimate. In Dec 2025 proposal this was provided by RemitONE. With Fincode, whether an equivalent operational portal is provided natively or needs to be built is an open item pending Fincode API review.

---

## Architecture diagram (Phase 2+ reference)

A high-level architecture diagram exists at `../../hla.png` (GDrive: `1Aqd0_Z91hjxnCWg2qjN4u9I_8H8MFSsO`). It shows a longer-term target state with additional services (auth & user management, beneficiary service, wallets & ledger, KYC/AML, FX & fees engine, fraud & risk, payments orchestrator, mobile money aggregator, open banking, card processor, notifications, CRM, DMS, analytics, reporting) — this represents the Phase 2+ proprietary architecture. The governance doc's §37 long-term direction aligns with this diagram.
