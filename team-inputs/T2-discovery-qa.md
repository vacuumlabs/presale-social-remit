---
type: other
title: T2 — Discovery Q&A — SocialRemit
source_type: internal-authored
author: Boris Vida
status: active
last_updated: 2026-05-29
---

# T2 — Discovery Q&A Document

**Client:** SocialRemit (Emoni Financial Services / Affecta Technology)
**Date started:** 2025-12-08 (first discovery call)
**Last updated:** 2026-05-20

_Pre-filled from: Dec 2025 call transcript, 19 May 2026 call transcript, meeting minutes, and governance notes. Section 7 open questions to be sent to Joseph on Friday 23 May 2026._

---

## Section 1 — Business Context

**1. What is the primary business objective behind this initiative? What changes in your business when this project succeeds?**

Go live with a consumer remittance mobile app (iOS + Android) within 6–8 weeks of agreement. Reach 1,000–3,000 transactions/day. Use that traction to raise a seed round approximately 6 months post-launch. The app is the first product of the Affecta Technology group — the seed raise funds the broader platform vision (Transpara B2B infrastructure, Emoni Score credit engine, Emoni Finance embedded finance).

_Source: T1-sales-deal-brief.md, 2026-05-19-call-transcript.md_

**2. What is driving the timing — why now?**

Five-month delay since the December 2025 VL proposal, caused by team restructuring, funding discussions, and regulatory setup. All blockers now resolved: EMI registration complete (FCA regulated), $900M liquidity committed for two corridors, Paul Duncan joined as Technical Director (previously at Unitalink), Sumsub contracted, Fincode selected (replacing RemitONE), Figma prototype complete. Investors exist but are waiting for traction before committing — Joseph wants to move before activating larger funding rounds from a position of leverage.

_Source: T1-sales-deal-brief.md, 2026-05-19-call-transcript.md, 2026-05-19-meeting-minutes.md_

**3. Who are the key decision-makers for this project? Who signs off on the contract?**

- **Joseph Owusu FCCA** — founder, product owner, CFO-equivalent. Primary contact. Reached out directly to Boris in May 2026.
- **Paul Duncan** — Technical Director (joined from Unitalink). Must approve commercial terms before board sign-off. Back from Singapore 25 May 2026.
- **Board** — includes an individual named "Isaac" (role/influence not confirmed).

_Source: deal-context/stakeholder-map.md_

**4. What does the board / executive team care about most in this engagement?**

Speed to go-live (seed raise depends on it). Architecture that preserves independence from Fincode (12-month exit to Transpara). Long-term technology partnership for the full Affecta group, not just the MVP.

_Source: 2026-05-19-call-transcript.md, 2026-05-19-governance-notes-v1.md_

**5. Have you run a project of this scope before? What happened?**

Joseph was CEO/CFO/treasury at UnityLink, scaling it from 50,000 to 1.5 million transactions/day manually. That operational experience directly informs the governance framework he's written — particularly the emphasis on observability, operational visibility, and avoiding "operational blindness." VL produced a formal proposal for SocialRemit in December 2025 (£118–169k T&M); the deal stalled client-side before contracts were signed.

_Source: 2026-05-19-call-transcript.md, 2026-05-19-governance-notes-v1.md_

---

## Section 2 — Current State

**6. Walk us through your current system landscape: what platforms are you running, how old are they, and what are their main limitations?**

Greenfield — no live system. Existing assets: Figma prototype (full customer journey), AWS account (possibly with $300k–$1M in credits), GitHub setup (likely available). Fincode contract under review; Sumsub contracted. No production infrastructure yet.

_Source: 2026-05-19-call-transcript.md, 2026-05-19-meeting-minutes.md_

**7. Which of your current systems are in scope for this project?**

All new build. The only external integrations in scope for MVP are Fincode (remittance backend) and Sumsub (KYC). Card payment gateway and open banking provider not yet selected.

_Source: deal-context/client-overview.md_

**8. What do your operations and back-office teams currently spend the most time on manually?**

Not discussed. SocialRemit has no live operations yet. However, Joseph's governance framework (§26) places strong emphasis on proactive monitoring and early issue detection — informed explicitly by his UnityLink experience of managing high-volume remittance operations manually.

_Status: not answered — low priority for Friday send._

**9. What reporting and data access do you currently have? What would you like to have?**

Not discussed. Governance notes (§17) specify analytics requirements post-launch: onboarding funnel, reward engagement, referral analytics, customer retention, transaction funnel visibility. Tools mentioned: Mixpanel, PostHog, Firebase Analytics, Amplitude.

_Status: not answered — feeds Phase 2 scope._

---

## Section 3 — Products and Users

**10. List the products / services you currently offer. For each: who uses it, how it works, and the main friction point.**

No live products. MVP is the Social Remit consumer remittance app. Future group products: Transpara (B2B remittance infrastructure), Emoni Score (credit/behavioural scoring), Emoni Finance (embedded finance/EWA), Emoni ESG (trust/impact layer). See deal-context/group-structure.md.

_Source: deal-context/group-structure.md_

**11. Are there products or services you want to launch as part of this initiative that you don't currently offer?**

MVP is consumer remittance only. The Affecta group roadmap is a 6-year innovation pipeline but none of it is in scope for this engagement.

_Source: 2026-05-19-call-transcript.md_

**12. Who are your end users? Rough volumes: DAU/MAU, transaction volumes, etc.**

UK-based migrants and low-income workers sending money internationally. Two corridors (specific countries not confirmed). Consumer-only for MVP. Target: 1,000–3,000 transactions/day at launch. No existing user base — all net new.

_Source: deal-context/client-overview.md_

---

## Section 4 — Technical Landscape

**13. What is your current core banking / remittance system?**

No current system. Fincode is the selected white-label backend for MVP (12 months only). Plan: replace Fincode with Transpara (SocialRemit's own proprietary backend) after approximately 12 months. The BFF/middleware is explicitly designed to make this swap transparent to the frontend.

_Source: technical-architecture/system-overview.md_

**14. What third-party systems must this project integrate with?**

Confirmed in scope for MVP:
- **Fincode** — white-label remittance backend (contract under review). Sandbox: `remitjunction.fincode.software`.
- **Sumsub** — KYC / identity verification (contracted).
- **Card payment gateway** — TBC. Fincode supports `processpaymentwithpaymenttoken` with SECURE_TRADING (TrustPayments), Stripe, Flutterwave, and others. Possibly Fincode's own native widget.
- **AWS** — infrastructure (existing account).

Optional / not yet decided:
- Open banking provider (GoCardless, TrueLayer, Yapily) — moved to optional scope.
- Push notification service (FCM/APNs) — likely MVP.
- Analytics (Mixpanel / PostHog / Firebase) — likely Phase 2.

_Source: technical-architecture/fincode-gap-analysis.md_

**15. Do you have existing API documentation or a system architecture diagram you can share?**

- Fincode public API docs: https://docs.fincode.technology/remittance/overview
- Fincode sandbox: `https://remitjunction.fincode.software/api/v6/services/`
- Figma prototype: shared verbally — link not yet received.
- Architecture governance framework: shared by Joseph 19 May 2026 (ingested as `client-inputs/2026-05-19-governance-notes-v1.md`).
- Phase 2+ architecture diagram referenced (`hla.png`, GDrive `1Aqd0_Z91hjxnCWg2qjN4u9I_8H8MFSsO`) — not yet reviewed.

_Status: Fincode docs received. Figma link and sandbox credentials outstanding._

**16. What are your non-functional requirements? (uptime, throughput, data residency, DR)**

Throughput target: 1,000–3,000 transactions/day at launch. FCA/EMI regulated — UK data residency implications (UK GDPR; Fincode hosting location not confirmed). Uptime SLA and disaster recovery not discussed. Governance framework requires fintech-grade security, 3-environment CI/CD with rollback, and proactive monitoring.

_Source: technical-architecture/governance-principles.md, product-management/regulatory-brief.md_

**17. What is your tech team structure? Will VL be working alongside an internal team, or owning the full build?**

VL would own the full build. Joseph has a finance/operations background (not technical). Paul Duncan (Technical Director) provides technical direction and sign-off but is not a hands-on developer. No internal development team. Additional directors expected to join — roles and technical involvement not confirmed.

_Source: deal-context/stakeholder-map.md, 2026-05-19-meeting-minutes.md_

---

## Section 5 — Constraints

**18. What budget has been approved for this initiative?**

No hard figure given. Joseph referenced freelancer quotes of £5k–£10k as context (not comparable scope). December 2025 VL proposal was £118–169k T&M. Joseph has requested a deferred payment model (minimum upfront, remainder on go-live) plus equity/options. This is under review by VL CEO Tomas Masek and CDO Marek Tomasik — **VL's position must be resolved before the proposal can be sent.**

_Source: T1-sales-deal-brief.md_

**19. Are there regulatory or compliance requirements that directly constrain architecture or timeline?**

Yes — three primary constraints:
1. **Progressive KYC thresholds** — FCA-mandated business logic in the BFF; must escalate CDD based on transaction volume.
2. **Sanctions + PEP screening + ongoing monitoring** — required at transaction time and ongoing; whether Fincode covers natively needs confirmation.
3. **UK GDPR / data residency** — Fincode hosting location not confirmed; affects what PII can be passed to Fincode.

_Source: product-management/regulatory-brief.md_

**20. Are there any technology or vendor constraints?**

- Fincode is selected (non-negotiable for MVP).
- Sumsub is contracted (non-negotiable for KYC).
- Joseph's preference is Flutter; VL's recommendation is React Native — decision pending Paul Duncan's input.
- AWS is the preferred cloud provider.
- Governance framework (§35) mandates provider abstraction, no frontend coupling to provider logic, fintech-grade security, and CI/CD with 3 environments.

_Source: technical-architecture/governance-principles.md, decisions.md_

**21. What is the latest acceptable go-live date? What is the target?**

Target: 6–8 weeks from agreement (early–mid July 2026). Hard constraint: go-live before the seed fundraise, which Joseph wants to run approximately 6 months post-launch. No explicit "latest acceptable" date stated, but every week of delay is a week of burn without investor evidence.

_Source: T1-sales-deal-brief.md_

---

## Section 6 — Operating Model & Success

_Feeds P3e (Business Architecture). T2 engagement — fill in what is known._

**22. Which internal teams will be most affected? What does their day look like today vs after?**

Post-launch: Joseph's team will need to monitor transactions, handle customer queries, manage compliance flags, and oversee payout operations. Joseph's governance framework (§26) places high emphasis on internal operational visibility — informed by his UnityLink experience. Current state: no ops team or tooling. Future state: needs customer/transaction management capability from day one.

_Source: 2026-05-19-governance-notes-v1.md_

**23. Are there roles or capabilities SocialRemit will need to build internally?**

Yes — a customer operations function to handle KYC flags, failed transactions, and compliance reviews. No detail on headcount or timeline. This is relevant to the admin/back-office portal scope decision.

_Status: partially answered — detail needed._

**24. What would "a year after go-live" look like if this project succeeded?**

Seed round raised. 1,000–3,000 transactions/day established and growing. Fincode to Transpara migration underway or complete. Potentially one or two additional Affecta group products in development with VL as technology partner.

_Source: T1-sales-deal-brief.md, deal-context/group-structure.md_

**25. What metrics or KPIs would judge success?**

Transaction volume (1,000–3,000/day). Seed raise completion (~6 months post-launch). No formal KPI framework discussed.

_Source: 2026-05-19-call-transcript.md_

---

## Section 7 — Open Questions

_7 questions sent to Joseph on 22 May 2026. All answered by Joseph on 28 May 2026._

| # | Question | Asked by | Date asked | Answer | Status |
|---|----------|----------|-----------|--------|--------|
| 1 | **Fincode progressive KYC** — To keep the MVP scope lean, we'd like to use Fincode's built-in KYC and compliance engine rather than a separate Sumsub integration. Before we confirm that, can you tell us: does Fincode support a gradual KYC approach — i.e. minimal information collected at registration, with verification escalating automatically based on transaction thresholds or risk? | Boris Vida | 2026-05-22 | VL builds the Flutter KYC capture flow and passes customer data to the KYC provider (likely Sumsub) via SDK/API. Sumsub handles all verification logic (document validation, liveness, PEP/sanctions screening, risk scoring, progressive escalation) either directly or through Fincode's integration layer. Middleware must be provider-agnostic — architecture must support switching KYC provider without rebuilding the Flutter front-end. | Answered 2026-05-28 |
| 2 | **Card payment** — We'd use Fincode's `processpaymentwithpaymenttoken` endpoint for card top-up, which keeps card data off our servers entirely. Does Fincode provide its own native card capture widget on your tenant, or should we plan to integrate a specific third-party gateway (e.g. TrustPayments)? | Boris Vida | 2026-05-22 | **Trust Payments** (SECURE_TRADING) is confirmed as the card gateway — already integrated in Fincode and to be enabled on the SR tenant. VL integrates Trust Payments SDK in the mobile app for card tokenisation and wires the token through BFF to Fincode. Open Banking uses **Volume**, also already in Fincode. Elavon may be considered post-MVP. | Answered 2026-05-28 |
| 3 | **Push notifications** — For transaction updates (send confirmed, send failed) — do you need push notifications at go-live, or would email confirmation plus in-app status be sufficient for the first weeks of operation? | Boris Vida | 2026-05-22 | Desired at go-live for key events (send confirmed, send failed, status updates) — important for customer trust and engagement. **Not a hard blocker**: email + in-app status tracking is acceptable if timelines are tight. Architecture must support push from day one even if some types are phased in post-launch. | Answered 2026-05-28 |
| 4 | **Operational visibility** — For your ops team post-launch: do you need a customer/transaction management interface on day one, or can that be phased in shortly after go-live? | Boris Vida | 2026-05-22 | Fincode + Sumsub dashboards cover most ops needs at go-live. No full custom dashboard expected from VL before go-live unless critical gaps emerge. Lightweight internal tooling may be needed (customer lookup, transaction/KYC status). Joseph wants a Fincode technical walkthrough session with VL to assess what tooling already exists and what gaps remain. | Answered 2026-05-28 |
| 5 | **Revenue model** — What is the fee structure for transactions (FX spread, flat fee, percentage, or blended)? | Boris Vida | 2026-05-22 | Blend of FX spread + transaction fees + corridor/method-specific pricing rules. Exact structure varies by corridor, payout method, payment method, promotional campaigns, and customer tier. **Must be configurable** — not hardcoded. Pricing logic originates from Fincode backend but middleware and front-end must be flexible for future pricing and loyalty strategies. | Answered 2026-05-28 |
| 6 | **Wallet funding at launch** — Would manual bank transfer alone be sufficient for initial launch, deferring card and open banking to a later phase? | Boris Vida | 2026-05-22 | **No** — all three methods at MVP: card (Trust Payments), open banking (Volume), and manual bank transfer. Manual-only is insufficient for the remittance market. Both Trust Payments and Volume are already in Fincode and only need to be enabled/configured for the SR tenant — not built from scratch. | Answered 2026-05-28 |
| 7 | **Timeline** — What is driving the 6–8 week window? Is there a specific investor conversation, regulatory deadline, or other event we should be aware of? | Boris Vida | 2026-05-22 | Driven by: (1) signed liquidity arrangements for **Ghana and Nigeria** already in place; (2) regulatory permissions already received and consultants advising timely launch; (3) substantial prior work complete — Figma UX/UI done, provider infrastructure in place (Fincode, Trust Payments, Volume). VL's role is Flutter UX implementation, middleware/orchestration, and provider integration — not building financial infrastructure from scratch. Open to phasing discussion if timelines are at risk. | Answered 2026-05-28 |
