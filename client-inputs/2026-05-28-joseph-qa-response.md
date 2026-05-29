---
type: client-email
title: Joseph Owusu — Responses to 7 Architecture & Scope Questions
tags: [qa, scope, kYc, payments, timeline, corridors, revenue]
sources:
  - email thread "RE: Social Remit – Architecture Direction & MVP Vision"
  - sent: boris.vida@vacuumlabs.com → joseph@socialremit.co.uk, 2026-05-22
  - received: joseph@socialremit.co.uk → boris.vida@vacuumlabs.com, 2026-05-28
last_updated: 2026-05-29
status: active
---

# Joseph Owusu — Responses to 7 Architecture & Scope Questions

**Email thread:** RE: Social Remit – Architecture Direction & MVP Vision
**Sent by:** joseph@socialremit.co.uk
**Date received:** 2026-05-28
**To:** boris.vida@vacuumlabs.com
**CC:** paul@firmview.co.uk

---

Thanks, Boris,

Please see our response in blue below…

---

## Q1 — Fincode progressive KYC

> To keep the MVP scope lean, we'd like to use Fincode's built-in KYC and compliance engine rather than a separate Sumsub integration. Before we confirm that, can you tell us: does Fincode support a gradual KYC approach — i.e. minimal information collected at registration, with verification escalating automatically based on transaction thresholds or risk signals?

**Our Response:**

For MVP, we are not asking Vacuum Labs to build a KYC engine.

The expectation is for Vacuum Labs to build the onboarding and KYC capture flow in Flutter, collect the required customer information, and pass that information to the relevant KYC provider via SDK or API integration.

The actual KYC verification process — including document validation, liveness checks, sanctions/PEP screening, risk scoring, and progressive KYC escalation — will be handled by the external KYC provider, likely Sumsub, either directly or through Fincode's integration layer.

From an architectural perspective, the app and middleware should support:

- secure customer data capture
- handoff of onboarding/KYC data to the provider
- receiving and storing KYC status updates
- management of verification states such as pending, approved, rejected, retry required, or enhanced due diligence required
- controlling customer access and transaction capabilities based on KYC status and configured transaction limits

The middleware should also avoid hardcoding KYC provider-specific logic. The architecture should remain flexible enough for Social Remit to:

- use Sumsub directly
- use Fincode's Sumsub integration if available
- or switch to another KYC provider in future without rebuilding the Flutter front-end

This approach keeps the MVP scope lean, avoids unnecessary overengineering, and provides Social Remit with long-term flexibility from both a regulatory and vendor-management perspective.

---

## Q2 — Card payment

> If card top-up is needed at launch: does Fincode provide its own native card capture widget on your tenant, or should we plan to integrate a specific third-party gateway (e.g. TrustPayments or Stripe)?

**Our Response:**

For MVP, card top-up will use Trust Payments, which is already integrated into Fincode's platform. We are not asking Vacuum Labs to build a new card gateway integration or integrate Stripe.

Fincode will switch on the existing Trust Payments capability for the Social Remit tenant. Vacuum Labs should therefore plan the Flutter/payment flow around triggering Fincode's existing card top-up journey/API, rather than building a separate card capture or payment-processing layer.

Open Banking payments will use Volume, which is also already integrated with Fincode and will be switched on for Social Remit.

Elavon may be considered later, but it is not required for MVP.

---

## Q3 — Push notifications

> For transaction updates (send confirmed, send failed) — do you need push notifications at go-live, or would email confirmation plus in-app status be sufficient for the first weeks of operation?

**Our Response:**

Ideally, we would like push notifications to be available at go-live for key transaction events such as send confirmed, send failed, and status updates, as they are important for customer trust, engagement, and future promotional campaigns.

However, push notifications are not considered a hard blocker for MVP launch.

If timelines become tight, email confirmations combined with clear in-app transaction status/history would be sufficient for the first weeks of operation, provided customers can reliably track the status of their transfers inside the app.

From an architecture perspective, the system should still be designed with push notification capability in mind from day one, even if some notification types are phased in shortly after launch.

---

## Q4 — Operational visibility

> For your ops team post-launch: do you need a customer and transaction management interface on day one, or can that be phased in shortly after go-live?

**Our Response:**

For MVP, both Fincode and Sumsub already provide operational and compliance dashboards which we expect to cover a significant portion of the initial operational requirements.

- Sumsub provides its own compliance/KYC dashboard for identity verification, document review, risk monitoring, and case management.
- Fincode already provides operational tooling and back-office functionality across payments, wallets, and transaction management as part of their existing platform.

Given this, we do not currently expect Vacuum Labs to build a full custom operational dashboard before go-live unless critical operational gaps are identified during discovery and integration.

At minimum, we may require lightweight internal operational visibility such as:

- basic customer lookup
- transaction status visibility
- KYC status visibility
- simple support/admin actions where not already covered by Fincode or Sumsub

Our preference would be for Vacuum Labs to have a technical and operational walkthrough session with Fincode so the team can properly assess:

- what operational tooling already exists
- which APIs/webhooks are available
- which workflows are already handled by Fincode
- and what additional internal tooling, if any, genuinely needs to be built for MVP

The goal is to keep the MVP architecture lean, avoid duplicating mature provider functionality, and focus development effort on the customer experience, middleware orchestration layer, and future scalability.

---

## Q5 — Revenue model

> What is the fee structure for transactions — FX spread, flat fee, percentage, or a blend?

**Our Response:**

For MVP, the revenue model will likely be a blend of:

- FX spread
- transaction fees
- and potentially corridor- or payment-method-specific pricing rules

The exact pricing structure may vary by:

- destination corridor
- payout method
- payment method
- promotional campaigns
- customer tier/reward status
- and future commercial partnerships

From a system architecture perspective, the pricing and fee engine should therefore remain configurable rather than hardcoded.

At minimum, the platform should support:

- fixed/flat fees
- percentage-based fees
- FX margin/spread
- blended fee structures
- promotional fee overrides or discounts
- corridor-specific pricing rules
- payment-method-specific pricing
- fee transparency before transaction confirmation

For MVP, we expect much of the core transaction pricing logic to originate from or interact with Fincode's backend capabilities, but the middleware and front-end should be designed with flexibility for future pricing and loyalty strategies.

---

## Q6 — Wallet funding at launch

> Fincode supports two native ways to fund a wallet: card top-up (requires a payment gateway integration) and manual bank transfer (customer transfers from their bank and taps to confirm — no integration beyond Fincode). Would manual bank transfer alone be sufficient for the initial launch? If yes, we can defer the card and open banking integrations to a later phase and keep the build scope tighter.

**Our Response:**

For MVP, we would prefer to launch with:

- card payments processed via Trust Payments
- open banking payments processed via Volume
- and manual bank transfer

While manual bank transfer alone is technically possible, we do not believe it would provide the desired customer experience or onboarding conversion for launch, particularly given the expectations within the remittance market.

Our understanding is that both Trust Payments and Volume are already integrated into Fincode's platform and simply need to be enabled/configured for the Social Remit tenant, rather than requiring Vacuum Labs to build entirely new payment gateway integrations from scratch.

From an architectural perspective, the expectation is therefore that:

- customers can choose their preferred funding method within the Flutter app
- the app and middleware orchestrate the payment flow
- and the actual payment processing is handled by the relevant provider through Fincode's existing infrastructure

Specifically:

- card payments would be processed by Trust Payments
- open banking payments would be processed by Volume
- and manual bank transfer flows would be handled through Fincode's native capabilities

Our preference is therefore to leverage Fincode's existing integrations and keep the implementation lightweight, rather than deferring core funding methods that materially impact customer adoption and transaction completion rates.

If Vacuum Labs believes there are timeline or complexity concerns even with the existing Fincode integrations, we would appreciate visibility on:

- what work remains on the Flutter side
- what middleware orchestration is required
- and which parts are dependent on Fincode versus Vacuum Labs

---

## Q7 — Timeline

> You mentioned 6–8 weeks from agreement as the target. To make sure we plan realistically together — what is driving that window? Is there a specific investor conversation, regulatory deadline, or other event we should be aware of? Understanding what's behind the timeline helps us advise on what scope is achievable and where there may be flexibility.

**Our Response:**

The 6–8-week target is driven primarily by a combination of commercial readiness, regulatory timing, and the fact that much of the foundational work has already been completed.

As mentioned on the call:

- we already have signed liquidity arrangements in place for Ghana and Nigeria
- the commercial infrastructure and provider relationships have been established for some time
- and we are now focused on moving from preparation into operational launch

From a regulatory perspective, Social Remit has already received the relevant permissions and we have been advised by our regulatory consultants that progressing to live operations within a reasonable timeframe is important from a regulatory and business credibility standpoint.

At the same time, we believe the timeline is achievable because:

- the customer journeys and product flows have already been mapped in detail
- substantial UX/UI work has already been completed in Figma
- we are not designing the product experience from scratch
- core provider infrastructure already exists through Fincode
- and several integrations (e.g. Trust Payments and Volume) are already available within the Fincode ecosystem

Our expectation is therefore not that Vacuum Labs builds an entirely new financial infrastructure stack, but rather that the team helps us:

- implement and refine the customer experience in Flutter
- build the middleware/orchestration layer
- integrate the relevant providers
- and prepare the platform for MVP launch in a scalable and maintainable way

That said, we absolutely want this to be a collaborative planning exercise. If, following technical discovery, Vacuum Labs believes certain items materially impact feasibility within the proposed timeline, we are open to discussing sensible phasing and prioritisation while still protecting the core MVP experience.
