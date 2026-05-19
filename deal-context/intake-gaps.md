---
type: concept
title: Intake gap analysis — SocialRemit
tags: [intake, gaps, T1]
sources:
  - ../team-inputs/T1-sales-deal-brief.md
last_updated: 2026-05-19
status: draft
---

# Intake gap analysis — SocialRemit

## What we know

**The ask.** SocialRemit wants VL to build a Flutter or React Native mobile app (iOS + Android) plus a BFF/middleware layer that connects to Fincode's white-label remittance backend. Core scope: progressive KYC onboarding (Sumsub SDK), multi-currency wallet, send-money flow (bank deposit + mobile money), wallet top-up (card + open banking), beneficiary management, and transaction history. VL's pre-built auth library is proposed for authentication. The architecture must abstract Fincode so it can be replaced by SocialRemit's own backend (Transpara) within 12 months without the customer noticing.

**Business context.** SocialRemit is a UK startup, EMI registered and FCA regulated. They had a 5-month delay since the December 2025 VL proposal caused by team restructuring, funding work, and regulatory setup — all now resolved. Paul Duncan (Technical Director, formerly Unitalink) has joined full-time. Sumsub KYC is contracted. Fincode white-label is under contract review. $900M liquidity is committed for two corridors. A Figma prototype covers the full customer journey. The go-live target is 6–8 weeks (early to mid July 2026), after which a seed fundraise is planned approximately 6 months post-launch.

**Budget signal.** Soft, with significant commercial risk. No hard figure provided. Joseph referenced freelancer quotes of £5k–£10k as context (not comparable). The December 2025 VL proposal was £118–169k T&M. Joseph has explicitly asked for a deferred payment model (minimum upfront, remainder on go-live) plus equity/options as additional compensation. This is being escalated to VL CEO Tomas Masek and CDO Marek Tomasik — their answer shapes the proposal entirely.

**Timeline.** Urgent. Joseph wants a proposal by early w/c 25 May 2026. Paul Duncan is back from Singapore on 25 May and must approve commercial terms before board sign-off. Delivery start is expected immediately after agreement.

**VL's angle.** We completed a formal proposal in December 2025 (£118–169k, led by Boris Vida). That deal stalled client-side. The re-engagement is warm, direct (Joseph bypassed sales to contact Boris), and technically credible. VL's differentiators are payments domain expertise, pre-built auth and KYC patterns, BFF abstraction experience, and long-term partnership capability. SocialRemit sees VL as a potential long-term technology partner for the broader Affecta Technology group.

---

## What we don't know

### Business & Commercial

| Question | Why it matters |
|----------|---------------|
| Will VL accept a deferred payment model? | This is the commercial gate — if VL declines, the deal likely cannot proceed or must be fundamentally restructured. Tomas Masek / Marek Tomasik resolution pending. |
| What is the minimum upfront VL requires if a hybrid model is accepted? | Drives the specific commercial structure of the proposal. |
| What are the specific MVP corridors and currencies? | Determines which Fincode API flows are in scope and which payout rails need integration (bank deposit vs mobile money varies significantly by corridor). |
| What is the business revenue model? | Affects how Joseph frames the ROI on VL's cost. Margin-per-transfer, subscription, or blended? |
| Is the December 2025 NDA still in force? | Governs what information can be shared pre-contract. |
| Has Joseph had substantive conversations with other agencies (beyond freelancers)? | If a full-service agency is also in the running, the competitive dynamic changes. |

### Technical

| Question | Why it matters |
|----------|---------------|
| What are the Fincode API capabilities and protocol? | Required to confirm BFF scope, estimate integration effort, and validate what's available natively vs custom-built. Docs to be sent by Joseph post-call. |
| Flutter or React Native? | Affects staffing, timeline, and potentially cost. VL leans React Native (more experience, larger hiring pool). Needs mobile expert consultation. |
| What open banking provider will be used for top-up? | Additional integration scope if not bundled with Fincode. |
| What card payment processor is planned (top-up)? | Same — if this is a separate integration, it is additional estimate scope. |
| Is an admin/back-office tool in scope? | Not discussed on 19 May call. Could add significant scope. |
| Are Fincode sandbox/test credentials available? | Required to de-risk the BFF integration before go-live; affects timeline confidence. |

### Stakeholder & Process

| Question | Why it matters |
|----------|---------------|
| What specifically does Paul Duncan need to approve before board sign-off? | Determines whether Paul must be on the proposal call or can review async. |
| Who is "Isaac" on the board? | Named in passing during the May 19 call; role and influence not confirmed. |
| Is there a named product contact for Figma access? | Figma prototype link not yet received; UX sign-off process unknown. |
| Who at Fincode is the technical contact for API access? | VL will need a direct Fincode contact for integration questions. |

---

## What to watch for

1. **Deferred payment model is the deal-breaker.** If VL leadership declines to accept any deferred structure, the proposal cannot be built on Joseph's terms. Do not invest further presale effort until Tomas Masek / Marek Tomasik respond. This is the single most important signal to resolve before the proposal is sent.

2. **6–8 week go-live is extremely aggressive for the stated scope.** Full onboarding, KYC integration, multi-currency wallet, two payment rails, open banking top-up, and card top-up in under two months requires either scope reduction or a very large, experienced team running in parallel. This needs to be pressure-tested with the PM and named in the proposal.

3. **Freelancer reference quotes signal a budget expectation problem.** £5k–£10k quotes (for comparable scope) vs VL's £118–169k creates a 10–20x gap. Even with a deferred structure, Joseph's mental model of total cost may not match VL's minimum. This risk should be surfaced early and directly, not buried in the proposal.

4. **Pre-revenue client accepting equity as VL compensation.** Equity/options in a pre-seed, pre-revenue company with no external investors is speculative. If VL accepts equity as partial compensation, this should be treated as a high-risk receivable, not a commercial offset.

5. **No BD involvement creates account management risk.** Marcus Davey is not looped in. If CTO Michal Cernak's presales ownership transition is not fully formalised before the proposal is sent, there is a risk of internal VL confusion over who owns commercial terms.
