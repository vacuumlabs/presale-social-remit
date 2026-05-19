# T1 — Sales Deal Brief

_Complete this before the intake call. This is the minimum information needed to start a presale. If you cannot complete a field, write "Unknown" — do not leave it blank._

---

## Client

| Field | Value |
| --- | --- |
| Client name | SocialRemit (trading as E-money Financial Services) |
| Country / Market | UK (outbound international remittance) |
| Vertical | Payments — cross-border remittance / migrant fintech |
| Company size | Startup — pre-revenue, self-funded, pre-seed. EMI registered. ~4–5 named team members including board. |
| Stage | Startup |
| Key contact — relationship owner | Marcus Davey (VL BD) — original intro. Presales ownership shifting to delivery per CTO Michal Cernak directive. Boris Vida (SA) is now primary contact. |
| Key contact — decision maker | Joseph Owusu FCCA (CFO-equivalent, product owner). Paul Duncan (Technical Director) must approve commercial terms before board sign-off. |
| Key contact — technical | Paul Duncan (Technical Director, formerly of Unitalink) |

---

## The Opportunity

**What does the client want?**
SocialRemit wants VL to build a Flutter or React Native mobile app (iOS + Android) and a BFF/middleware layer that connects to Fincode's white-label remittance backend. Core app features: onboarding with progressive KYC (Sumsub SDK), multi-currency wallet, send money flow (bank deposit + mobile money), wallet top-up (card + open banking), beneficiary management, and transaction history. VL's pre-built authentication library is proposed for the auth layer. The architecture must explicitly abstract the Fincode backend so it can be replaced with SocialRemit's own proprietary backend after approximately 12 months, without the customer noticing any change.

**What is the trigger for this engagement now?**
SocialRemit is now ready to move after a 5-month delay caused by internal team restructuring, funding discussions, and regulatory setup. They are now EMI registered (FCA), have $900M liquidity committed for two corridors, have Paul Duncan joining as Technical Director from Unitalink, have a completed Figma prototype, and have Sumsub (KYC) and Fincode (white-label) contracts in progress. They want to go live in 6–8 weeks to reach 1,000–3,000 transactions/day before raising a seed round.

**What does success look like for the client?**
The app goes live within 6–8 weeks, reaches meaningful transaction volume (1,000–3,000/day), and enables a seed fundraise approximately 6 months post-launch. The architecture leaves SocialRemit free to migrate away from Fincode to their own proprietary backend (Transpara) within 12 months. The longer-term vision is a multi-product fintech group (Affecta Technology) including B2B remittance infrastructure (Transpara), credit scoring (E-money Score), and embedded finance — with VL as a long-term technology partner.

---

## Budget Signal

| Field | Value |
| --- | --- |
| Budget signal type | Soft — with significant commercial risk |
| Amount | No hard figure given. Joseph referenced freelancer quotes of £5k–£10k (for context, not comparable scope). Dec 2025 VL proposal was £118–169k T&M. |
| Budget source | Joseph on 19 May 2026 call |
| Notes | Joseph explicitly requested a **deferred payment model**: minimum upfront, remainder paid on go-live. He also offered equity / options as additional compensation. This is non-standard for VL and is being escalated to CEO Tomas Masek and CDO Marek Tomasik for commercial qualification. This is the single biggest risk to the deal proceeding. |

_Plan to obtain a hard signal: commercial qualification from Tomas Masek / Marek Tomasik must resolve whether VL will accept any deferred model, and if so, the minimum upfront floor. That answer shapes the proposal entirely._

---

## Commercial

| Field | Value |
| --- | --- |
| Expected contract model | T&M historically (Dec 2025 proposal). Client wants deferred / success-fee model — under internal VL review. |
| Is this competitive? | Yes — Joseph has been speaking to freelancers and other agencies. Freelancers quoted £5k–£10k. VL's differentiator is payments domain expertise, pre-built auth + KYC patterns, and long-term partnership capability. |
| Other vendors known to be in the running | Freelancers (unnamed). Possibly agencies — Joseph said "I've been speaking to so many different people giving me proposals." |
| Decision timeline | Urgent. Joseph wants proposal early w/c 25 May 2026. Paul Duncan back from Singapore 25 May and must approve. |
| Delivery start expected | ASAP — go-live target 6–8 weeks from now (early–mid July 2026). |

---

## Context

**What do we already know about this client?**
VL completed a formal proposal for SocialRemit in December 2025 (£118–169k, T&M). Boris Vida led the architecture — React Native app + NestJS BFF + RemitONE. The deal stalled due to client-side restructuring and funding work. Since then: provider changed (RemitONE → Fincode), Paul Duncan joined as Technical Director, EMI registration completed, Figma prototype completed, Sumsub contracted. Joseph has described a 6-year innovation pipeline and a group structure (Affecta Technology) with significant long-term product ambitions.

**What is our current relationship with this client?**
Warm re-engagement. Boris Vida has a trusted technical relationship with Joseph, who reached out directly (bypassing sales). Marcus Davey led the December 2025 commercial discussions. Presales ownership has shifted to delivery per CTO directive.

**Anything unusual about this deal?**
Three notable things: (1) **Non-standard commercial ask** — deferred payment + equity, currently under VL CEO/CDO review. (2) **Pre-revenue client with regulatory standing** — EMI registered and FCA regulated, which is real, but no revenue or traction yet. (3) **Presales ownership transition** — deal is being run by SA (Boris) and delivery leadership, not sales. Marcus Davey is not being looped in at this stage per CTO Michal Cernak's direction.

---

## Proposed Engagement Tier (Sales view)

Sales recommendation: **T2**
Rationale: Discovery has been conducted (19 May call), the technical approach is defined, and a formal proposal is needed. The scope is meaningful (mobile app + BFF + integration, ~£100–150k range) and the client relationship requires careful commercial management. Not T3 — the engagement is not large or complex enough to warrant full T3 presale overhead.

---

_Completed by:_ Boris Vida (reconstructed from wiki context)
_Date:_ 2026-05-19
