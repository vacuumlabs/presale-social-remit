---
type: concept
title: Client Overview — SocialRemit
tags: [client, remittance, product, overview]
sources:
  - ../team-inputs/2025-12-08-call-transcript.md
  - ../team-inputs/2025-12-17-fe-build-proposal.md
  - ../client-inputs/Socialremit_Customer_Flow_Nov2025.md
last_updated: 2026-05-18
status: active
---

# Client Overview — SocialRemit

SocialRemit is a UK-based startup building a consumer remittance mobile application. The company is building on top of the RemitONE white-label platform as its initial infrastructure layer, while simultaneously planning a proprietary Flutter-based frontend for the longer term.

## What they are building

A full-featured remittance app targeting migrants sending money internationally. The product covers: user onboarding with progressive KYC, multi-currency wallet, send money (bank deposit and mobile money delivery rails), wallet top-ups via card and open banking, beneficiary management, transaction history, scheduled payments, and a basic help/support section. The full screen specification was shared in November 2025 (see [`client-inputs/Socialremit_Customer_Flow_Nov2025.md`](../client-inputs/Socialremit_Customer_Flow_Nov2025.md)).

## Stage as of May 2026

Joseph Osei Owusu describes the project as having "progressed quite a lot" since December 2025. SocialRemit is now:

- **Planning to go live "within the next couple of months"** using RemitONE white-label infrastructure.
- **Simultaneously building** a proprietary Flutter frontend and longer-term platform architecture.

This is a classic "borrow before buy" pattern: use the RemitONE white-label to go live quickly, then replace it with a custom stack over time.

## Target market (inferred)

VL's discovery questions (December 2025) asked whether SocialRemit targets migrants in the UK from eastern/western Africa. No answer was captured in available sources. The RemitONE API spec and the emphasis on mobile money delivery rails is consistent with UK→Sub-Saharan Africa corridors, but this remains unconfirmed.

## Regulatory status (unknown)

VL's discovery questions included the licensing question (MSB / EMI licence status). No answer is recorded. Going live in months implies either a licence is in place or SocialRemit is operating under a third-party's regulatory umbrella (e.g., RemitONE or a sponsor bank). **This must be clarified on the May 2026 call.**

## Key unknowns

- Exact corridors and currencies in scope for MVP.
- Regulatory / licensing status.
- Whether Paul (co-founder) is still involved and in what capacity.
- Why the deal did not proceed to contract after December 2025.
- Whether other vendors have been engaged in the interim.
- What "longer-term platform architecture" means and what the exit plan from RemitONE looks like.
