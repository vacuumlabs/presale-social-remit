---
type: contract
title: Engagement — SocialRemit
tags: [engagement, contract, commercial]
sources:
  - ../team-inputs/T1-sales-deal-brief.md
  - ../client-inputs/2026-05-19-call-transcript.md
  - ../team-inputs/T2-discovery-qa.md
last_updated: 2026-05-29
status: draft
---

# Engagement — SocialRemit

- **Client:** SocialRemit Technologies (socialremit.co.uk) — part of the Affecta Technology group
- **Project code:** TBD (not yet contracted)
- **Engagement status:** Pre-sales — proposal in preparation
- **Engagement type:** T&M (offered in Dec 2025; final commercial model pending Andy Birch / CRO decision on deferred payment + equity ask)
- **Start date:** Not yet contracted. Target: immediately after agreement (~early June 2026 if commercial model resolved by w/c 2026-06-01)
- **Target go-live:** 6–8 weeks from agreement (~early–mid July 2026)

## VL team

| Role | Person |
|------|--------|
| Solution Architect | Boris Vida |
| Project Manager | Jaroslav Novák |
| Product Owner | Rudolf Vido |
| CRO / commercial lead | Andy Birch |

## Client contacts

| Role | Person | Contact |
|------|--------|---------|
| Founder & CEO | Joseph Osei Owusu FCCA | joseph@socialremit.co.uk |
| Technical Director | Paul Duncan | paul@firmview.co.uk |

## Commercial status

Joseph has requested a deferred payment model (minimum upfront, remainder on go-live) plus equity/options. This is non-standard for VL. Andy Birch (CRO) is responsible for VL's position. Decision pending as of 2026-05-29. Marcus Davey (BD) is also engaged on the qualification. See [`deal-context/go-no-go-flags.md`](../deal-context/go-no-go-flags.md).

## Scope summary

Flutter or React Native mobile app (iOS + Android) + BFF/middleware layer connecting to Fincode white-label backend, with:
- Progressive KYC onboarding (Sumsub SDK integration)
- Multi-currency wallet (Ghana + Nigeria corridors)
- Send money — bank deposit + mobile money
- Wallet top-up — card (Trust Payments via Fincode), open banking (Volume via Fincode), manual bank transfer
- Push notifications (architecture from day one; phased delivery if timeline constrained)
- Fincode provider abstraction (exit ramp for 12-month Fincode → Transpara migration)

Full scope detail: [`technical-architecture/fincode-gap-analysis.md`](../technical-architecture/fincode-gap-analysis.md)

## NDA

Status: unconfirmed. May already be in force from December 2025 engagement. To be clarified before contract signature.
