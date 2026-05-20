---
type: other
title: Meeting Minutes — Social Remit & Vacuumlabs, 19 May 2026
source_type: client-authored
author: Social Remit Technologies
status: active
last_updated: 2026-05-19
gdrive_id: 1mkk659bVPT_X5Fgs5EC23AfNfDIvyKM6
---

# Meeting Minutes — Social Remit & Vacuumlabs Discussion

**Date:** Tuesday 19 May 2026
**Attendees:** Joseph Owusu (Social Remit Technologies), Boris Vida (Vacuumlabs), additional participants from both teams.
**Purpose:** Technical architecture, MVP build approach, white-label integration strategy, frontend/mobile development, middleware architecture, infrastructure planning, partnership discussion.

---

## Business Update (Joseph)

- Internal company structure now being finalised
- Several senior individuals transitioning to join Social Remit
- Paul Duncan has officially joined after leaving UnityLink
- Additional directors expected to join shortly
- Liquidity: ~$900M across two countries for operational settlement
- Social Remit is EMD registered and operationally progressing toward launch
- Figma UI/customer journey prototype largely complete

## White-Label Provider Decision

Previous provider: RemitOne. Updated decision: **FinCode**.

Reasons: better engagement/support, greater flexibility, stronger collaboration approach, more aligned with long-term vision.

White-label is intended as a temporary launch platform (~12 months). Goal: launch quickly, gain traction, raise seed investment, then replace with Social Remit's proprietary infrastructure.

## Architecture (Joseph's outline)

Proposed stack: Flutter mobile frontend (Android/iOS), Social Remit-owned API layer, middleware/orchestration layer, white-label provider abstraction layer, white-label backend.

Key objective: avoid vendor lock-in. Middleware allows easy future backend replacement and seamless migration to proprietary infrastructure.

Boris agreed with the middleware separation strategy; confirmed it is a sound long-term architectural decision.

## MVP & Go-Live Strategy

- Go live within 6–8 weeks
- Initial target: 1,000–3,000 transactions/day
- Funding strategy: launch first, demonstrate traction, raise seed funding afterwards
- **Investors already exist but want traction before investing.** Joseph wants stronger bargaining power before activating larger funding rounds.

## KYC & Compliance

- Sumsub contracted for KYC/identity verification
- Progressive KYC: minimal friction initially, enhanced verification based on transaction thresholds/risk
- Joseph stressed system must be built properly from the start; regulatory stability and customer safety are non-negotiable

## Product Philosophy & Brand Positioning

See `product-management/product-vision.md` for full detail. "Make your money work the way life actually works." — emotional finance, human-centred technology, designed by migrants for migrants.

## Frontend Technology

Joseph's current preference: Flutter. Boris's input: React Native may be easier to hire for, reduce future staffing costs, offer comparable customer experience. Action: VL to review and compare Flutter vs React Native (scalability, maintenance, cost efficiency).

## Infrastructure & Cloud

- AWS account likely already exists; possible unused AWS credits available
- Existing GitHub setup also likely available
- Joseph requested VL to manage: AWS infrastructure, security, access control, environment setup, governance

## Commercial Discussion

Joseph's position: business self-funded for two years. Open to deferred payments, flexible payment structures, potential equity/options for long-term contributors.

Boris's response: commercial structure discussions must involve VL revenue/commercial leadership. Suggested modular proposal approach: MVP essentials, optional add-ons, future roadmap components.

## AI-Assisted Development

Joseph highlighted desire to use AI-assisted tooling to accelerate development, reduce costs, scaffold code rapidly, improve launch speed. Boris confirmed AI tooling has improved significantly; could help reduce timeline, resource requirements, and overall development costs.

## Future Product Ecosystem

Broader plans: emotional finance ecosystem, credit/behavioural scoring, embedded finance, ESG/trust infrastructure, white-label payment infrastructure, reconciliation and treasury systems, financial inclusion products. All IP to sit within dedicated IP holding structure (Affecta Technology).

## Next Steps (as of 19 May 2026)

- Joseph to provide: meeting notes, FinCode API documentation, additional MVP framework details
- VL to: review architecture requirements, review FinCode API docs, assess middleware approach, prepare initial proposal, compare Flutter vs React Native, begin internal pricing discussions
- Questions likely to be sent Friday; initial proposal expected next week
