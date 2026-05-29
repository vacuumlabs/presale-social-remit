---
type: status
title: Open Questions
tags: [open-questions, discovery, unknowns]
sources:
  - ../team-inputs/2025-12-15-discovery-questions.md
  - ../team-inputs/2025-12-08-call-transcript.md
last_updated: 2026-05-29
status: active
---

# Open Questions

Questions that remain unanswered from the December 2025 discovery phase, plus new questions arising from the May 2026 re-engagement. Answers should be pursued on the 19 May 2026 call with Joseph.

## Answered on 19 May 2026 call

| # | Question | Answer |
|---|----------|--------|
| 1 | Target user | UK-based migrants and low-income workers — confirmed |
| 2 | Product goals/origin | Joseph's own experience at UnityLink; scaling migrant remittance for a market he lived in |
| 3 | Primary use case + differentiator | International remittances. Differentiator: "Built by migrants, for migrants" — emotional intelligence in product design |
| 6 | Licensing status | **EMI registered** (last year). FCA regulated. Anti-money laundering board. |
| 8 | Third-party providers | KYC: **Sumsub** (signed, SDK). White-label: **Fincode** (contract under review). Open banking: TBC. |
| 9 | Consumer vs business | Consumer-only for MVP — confirmed |
| 10 | Design assets | Yes — full Figma prototype completed. Coral brand colour. Logo and brand defined. |
| 13 | Why the gap? | Team restructuring, funding work, regulatory/liquidity/operational readiness — all now resolved |
| 14 | Other vendors? | Yes — Joseph has been speaking to freelancers (quoted £5k–£10k). VL not the only party considered. |
| 15 | Paul's involvement | **Paul Duncan**, Technical Director, left Unitalink and joined SocialRemit full-time. Back from Singapore 25 May. |
| 16 | Go-live scope | Flutter frontend + BFF + Fincode — the full stack, not just a white-label web portal |
| 17 | Longer-term architecture | Confirmed: Fincode for 12 months, then replace with proprietary backend. BFF designed for this swap. |

## Answered via email 28 May 2026

| # | Question | Answer |
|---|----------|--------|
| 4 | Business model / revenue | Blend of FX spread + transaction fees + corridor/method-specific pricing. Must be configurable — not hardcoded. Pricing logic originates from Fincode but middleware and front-end must be flexible for future pricing and loyalty strategies. |
| 5 | MVP corridors | **Ghana and Nigeria** — signed liquidity arrangements already in place. |
| 7 | Admin/back-office tool | Fincode and Sumsub dashboards cover most ops needs. Lightweight internal tooling (customer lookup, transaction/KYC status) may also be needed. Joseph wants a Fincode technical walkthrough session with VL before finalising scope. No full custom dashboard expected before go-live. |
| — | Card payment processor | **Trust Payments** (SECURE_TRADING), already integrated in Fincode; to be enabled on the Social Remit tenant. No new gateway build required. |
| — | Open banking provider | **Volume**, already integrated in Fincode; to be enabled on the Social Remit tenant. No new gateway build required. |

## Still open

| # | Question | Notes |
|---|----------|-------|
| 11 | User validation / testing | Figma prototype shown; no mention of user testing |
| 12 | Flutter vs React Native | Open decision — Boris to recommend after consulting VL mobile experts |
| 18 | Budget / commercial model | **Critical open risk.** Joseph requesting deferred payment (minimum upfront, rest on go-live) + equity/options. Freelancer reference quotes (£5k–£10k) suggest budget pressure. Being escalated to VL CEO (Tomas Masek) and CDO (Marek Tomasik) for qualification. |
| — | Fincode API capabilities | Sandbox credentials still needed for field-level verification |
| — | NDA status | To be confirmed — may already exist from December 2025 |
