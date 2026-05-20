---
type: concept
title: Client Architecture & Governance Principles — SocialRemit
tags: [architecture, governance, non-negotiables, scope, client-requirements]
sources:
  - ../client-inputs/2026-05-19-governance-notes-v1.md
last_updated: 2026-05-20
status: active
---

# Client Architecture & Governance Principles — SocialRemit

Distilled from "Social Remit MVP Technology Governance Notes v1" (Joseph Owusu, May 2026). This document establishes what Social Remit considers non-negotiable from any technology delivery partner. VL's proposal and architecture decisions must be visibly aligned with these principles.

---

## Core architectural statement

> "We control the customer experience, orchestration layer, and internal data model, while leveraging external financial infrastructure providers (e.g. FinCode) to handle remittance rails, payment processing, and regulatory infrastructure during the initial phases."

This maps directly to VL's BFF abstraction approach. The governance framework formalises it as a three-layer model.

---

## Three-layer system model

| Layer | Owner | Examples |
|---|---|---|
| **Product Layer** | Social Remit | Mobile app, UX, onboarding, rewards, referrals, messaging, analytics events |
| **Control Layer** | Social Remit | Middleware/BFF, orchestration logic, internal transaction model, provider abstraction, business rules, routing, behavioural triggers, future migration bridge |
| **Infrastructure Layer** | External providers (initially) | Fincode (remittance rails), Sumsub (KYC), card processors, open banking, FX infrastructure |

The Control Layer is explicitly described as strategically important and expected to become "increasingly valuable" over time — this is the layer VL is building.

---

## Non-negotiable principles

### Architectural
- Frontend must not be tightly coupled to provider infrastructure
- Provider-specific logic must remain isolated in the Control Layer
- Architecture must preserve future migration flexibility (Fincode → Transpara exit)
- Hidden technical debt is strongly discouraged; significant compromises must be documented transparently

### Operational
- Critical failures must be detectable internally before customers report them
- Production systems must support monitoring, alerting, and operational visibility
- Critical workflows must support auditability and traceability
- Operational blind spots must be minimised

### Delivery
- Production deployments must support dev/staging/production environments with rollback capability
- Critical integrations must be documented
- Engineering decisions must prioritise maintainability
- Security-sensitive workflows must follow fintech-grade practices

### Strategic
- MVP must prioritise strong foundations over unnecessary complexity
- Architecture must support future infrastructure evolution
- Strategic operational and customer data must remain accessible and controllable by Social Remit
- System must remain extensible for future integrations, orchestration, and behavioural systems

---

## MVP priorities (client-stated order)

1. Operational stability
2. Security & compliance readiness
3. Scalability foundations
4. Maintainability
5. Customer trust
6. Clean architecture direction
7. Migration flexibility
8. Delivery quality
9. Operational visibility
10. Behavioural simplicity

---

## Scope signals for estimation

The governance doc explicitly names the following as required capabilities. Some are MVP baseline; some are phased. All must be accounted for in the new estimate.

| Capability | Gov doc section | MVP vs phased |
|---|---|---|
| Observability: monitoring, logging, alerting, dashboards, webhook monitoring, transaction lifecycle visibility | §25–26 | MVP — "operational blindness is a major business risk" |
| Multi-environment CI/CD (dev/staging/prod + rollback) | §29 | MVP |
| Progressive KYC + async verification states + webhook updates | §12 | MVP |
| Sanctions screening + PEP screening + ongoing monitoring | §12 | MVP |
| Rewards & referrals (as core behavioural infrastructure, not marketing feature) | §16 | MVP baseline |
| Event-driven orchestration (events → notifications, rewards, analytics) | §19 | MVP foundations |
| Analytics integration (Mixpanel/PostHog/Firebase/Amplitude) | §17 | Early post-MVP or MVP optional |
| CRM integration (Zendesk/Intercom) | §18 | Phase 2 |
| Gamification / SR Tribe | §16 | Future |

---

## Vendor shortlist (client-named, not yet contracted)

| Category | Mentioned vendors |
|---|---|
| KYC/identity | Sumsub _(contracted)_, Onfido, Sardine, LexisNexis |
| AML/sanctions | ComplyAdvantage, LexisNexis |
| Card/payment | Volume, Checkout.com, SagePay/Opayo |
| Open banking / direct debit | GoCardless |
| Wallets | Google Pay, Apple Pay |
| Analytics | Mixpanel, PostHog, Firebase Analytics, Amplitude |
| CRM/support | Zendesk, Intercom, HubSpot, Salesforce |

---

## AI-assisted development

Formally permitted for scaffolding, development, testing, prototyping, and documentation. All generated code must still meet production-grade standards, maintainability, security, and architectural consistency. Code quality remains the engineering team's responsibility.

---

## Collaboration expectations

Joseph explicitly states Social Remit values "collaborative engineering relationships rather than purely transactional development relationships." Technology partners are expected to communicate transparently, challenge weak assumptions, think structurally, and consider operational realities — not just execute a spec.
