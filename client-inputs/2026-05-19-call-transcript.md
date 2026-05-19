---
type: concept
title: SocialRemit — Teams Call Transcript, 19 May 2026
tags: [transcript, call, discovery, architecture, commercial]
sources:
  - ../../../Flutter - SocialRemit Transcript.txt
last_updated: 2026-05-19
status: active
---

# SocialRemit — Teams Call Transcript, 19 May 2026

Companion summary for `../../../Flutter - SocialRemit Transcript.txt` (immutable). ~57-minute Teams call between Boris Vida (VL SA), Joseph Owusu (SocialRemit), and at least one unidentified SocialRemit colleague.

## Key outcomes

### Why the deal stalled since December 2025
Joseph apologised for the delay. Reasons: internal team restructuring (people joining from other jobs), chasing funding, ensuring regulatory/liquidity/operational readiness. The team is now in place and they want to move immediately.

### Regulatory and financial status — confirmed
- **EMI registered** (happened last year). FCA regulated. Anti-money laundering board in place.
- **$900M liquidity** committed across two countries — not yet deployed, reserved for transaction float.
- Self-funded by Joseph for two years. Soft/bridge investor commitments secured but not activated. Investors want traction before committing.
- **Grantify** has qualified SocialRemit for £2M Innovate UK loans (not yet drawn).
- AWS account exists with potentially $300k–$1M in credits (to be confirmed with team).

### White-label provider changed: RemitONE → Fincode
After the December 2025 discussions, "Penny" (SocialRemit colleague) reviewed RemitONE and recommended switching. **Fincode** is the new provider — more expensive than RemitONE but described as significantly more collaborative and engaging. Joseph is currently reviewing the Fincode contract.

### Architecture confirmed
Flutter frontend → proprietary middleware/BFF → Fincode white-label. Explicit plan to use Fincode for **12 months only**, then replace with SocialRemit's own backend. The BFF/middleware layer is specifically designed to avoid lock-in. Joseph confirmed: "we don't want to connect the front end directly to the white label."

### Flutter vs React Native — open
Boris raised that React Native is architecturally equivalent, easier to hire for (JavaScript vs Dart), and that VL has more experience there. Joseph acknowledged this and opened the decision: "if in the end it costs less and gives the customer the same experience, it makes sense." Boris to consult VL mobile experts and include a recommendation in the proposal. Joseph's current prototype is built in React.

### KYC provider: Sumsub
Contract signed. Integration via SDK (popup flow). No custom KYC build needed.

### Authentication: VL pre-built library
No authentication solution in place on SocialRemit's side. Boris offered VL's pre-built authentication library (mobile + backend + user definitions). Joseph accepted.

### Product vision — "Built by migrants, for migrants"
Joseph came from UnityLink (scaled it from 50k to 1.5M transactions/day as CEO/CFO/treasury). Brand: "Social Remit", trading as e-money (emotional money). Tagline: "Money is emotional — make your money work the way life actually works." Coral brand colour. Differentiation: designed by migrants for migrants; emotional intelligence in product design.

### Team
- **Paul Duncan** (Technical Director) — left Unitalink to join SocialRemit. Currently in Singapore, back 25 May. Paul needs to approve commercial terms before the board signs off.
- **Joseph Owusu** — product owner ("it's all in my head"), CFO/treasury, primary contact.
- A second (operational) CTO is being brought on board — not yet named.
- **Julio** — tech person who set up SocialRemit's AWS/GitHub. Contract to be finalised; Joseph plans to bring him back.

### Group structure (Affecta Technology)
See [`deal-context/group-structure.md`](../deal-context/group-structure.md).

### Commercial
Joseph asked for a **deferred payment model**: minimum upfront, remainder on go-live. Equity/options also offered to partners who come on board. He referenced freelancer quotes (£5k–£10k) for context but acknowledged VL brings payments domain expertise and a long-term partnership. Boris confirmed commercial structure decisions sit with VL's CRO, not with him.

### Next steps agreed
- Boris sends clarification questions by **Friday 22 May**.
- Boris delivers first proposal version **early week of 25 May**.
- Joseph to send: Fincode API docs, Figma prototype link, call notes.
- NDA status to be confirmed (may already be in place from December 2025).
- Boris to discuss deferred payment / equity model internally.
- Boris to consult VL mobile experts on Flutter vs React Native.
