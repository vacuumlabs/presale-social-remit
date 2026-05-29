---
type: concept
title: Client Overview — SocialRemit
tags: [client, remittance, product, overview]
sources:
  - ../team-inputs/2025-12-08-call-transcript.md
  - ../team-inputs/2025-12-17-fe-build-proposal.md
  - ../client-inputs/Socialremit_Customer_Flow_Nov2025.md
  - ../client-inputs/2026-05-19-meeting-minutes.md
  - ../client-inputs/2026-05-28-joseph-qa-response.md
last_updated: 2026-05-29
status: active
---

# Client Overview — SocialRemit

SocialRemit is a UK-based startup building a consumer remittance mobile application. The company is building on Fincode's white-label platform as its initial infrastructure layer (RemitONE was the original choice, replaced in early 2026), while planning to migrate to a proprietary backend (Transpara) within 12 months.

## What they are building

A full-featured remittance app targeting migrants sending money internationally. The product covers: user onboarding with progressive KYC, multi-currency wallet, send money (bank deposit and mobile money delivery rails), wallet top-ups via card and open banking, beneficiary management, transaction history, scheduled payments, and a basic help/support section. The full screen specification was shared in November 2025 (see [`client-inputs/Socialremit_Customer_Flow_Nov2025.md`](../client-inputs/Socialremit_Customer_Flow_Nov2025.md)).

## Stage as of May 2026 (updated post 19 May call)

SocialRemit is now ready to move. Key milestones since December 2025:

- **EMI registered** (last year). FCA regulated. Anti-money laundering board in place.
- **$900M liquidity** committed for two countries — not yet deployed, reserved for transaction float.
- **Paul Duncan** (Technical Director) has officially left Unitalink and joined full-time.
- **Fincode** selected as white-label provider (replacing RemitONE after Penny's review).
- **Sumsub** contracted for KYC (SDK integration).
- **Figma prototype** completed for the full customer journey.
- Grantify has qualified SocialRemit for **£2M Innovate UK loans** (not yet drawn).
- AWS account exists, potentially with **$300k–$1M in credits**.
- **Go-live target: 6–8 weeks.** Then 6 months of live transactions → seed raise.

The delay since December 2025 was caused by team restructuring, funding discussions, and ensuring regulatory/liquidity/operational readiness — all now resolved.

## White-label strategy

SocialRemit plans to use Fincode for **12 months only**, then replace it with their own proprietary backend. The BFF/middleware layer is explicitly designed to make this swap transparent to the frontend.

## Target market

UK-based migrants and low-income workers. **Corridors confirmed: Ghana and Nigeria** — signed liquidity arrangements already in place. Consumer-only for MVP. Joseph has deep domain expertise — he scaled UnityLink from 50k to 1.5M transactions/day as CEO/CFO/treasury. See [`product-management/product-vision.md`](../product-management/product-vision.md) for brand and differentiation.

## Group structure

SocialRemit is one product in the Affecta Technology group. See [`deal-context/group-structure.md`](./group-structure.md) for the full picture including Transpara (B2B white-label), E-money Score (credit engine), and E-money Finance.

## Funding & investor situation

The business has been self-funded for two years. Joseph confirmed on 19 May 2026 that investors already exist but want to see traction before committing — Joseph wants stronger bargaining power before activating larger funding rounds. This nuances the "pre-seed, self-funded" framing: it is not that there are no investors, but that they are contingent on live transaction volume. The seed raise is planned approximately 6 months post go-live.

## Key remaining unknowns

- **Commercial model** — deferred payment / equity structure is the single open risk. Andy Birch (CRO) responsible for VL's position. See [`deal-context/go-no-go-flags.md`](./go-no-go-flags.md).
- **Flutter vs React Native** — VL leans React Native; recommendation pending mobile expert input.
- **NDA status** — may already be in force from December 2025; to be confirmed.
- **Fincode sandbox credentials** — field-level API verification still pending. See [`technical-architecture/fincode-gap-analysis.md`](../technical-architecture/fincode-gap-analysis.md).
