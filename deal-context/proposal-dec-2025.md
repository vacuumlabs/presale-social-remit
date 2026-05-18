---
type: status
title: December 2025 Proposal — Status & Summary
tags: [proposal, commercial, scope, status]
sources:
  - ../team-inputs/2025-12-17-fe-build-proposal.md
  - ../team-inputs/2025-12-08-call-transcript.md
last_updated: 2026-05-18
status: active
---

# December 2025 Proposal — Status & Summary

VL sent a formal proposal to SocialRemit on 17 December 2025. The proposal offered two options and described a 3-layer architecture. Full text is in [`team-inputs/2025-12-17-fe-build-proposal.md`](../team-inputs/2025-12-17-fe-build-proposal.md).

## Commercial options

| Option | Scope | MDs | Estimated fee |
|--------|-------|-----|---------------|
| Option 1 | Mobile app (React Native) + BFF layer | 175 MD | £118,125 |
| Option 2 | Option 1 + parallel Discovery track | 250 MD | £168,750 |

Both options on a Time & Material basis (±30% range stated). No fixed-price offer was made at this stage.

## Architecture proposed

Three layers:
1. **Mobile app** — React Native (TypeScript), iOS + Android.
2. **BFF (Backend-for-Frontend)** — NestJS on AWS ECS Fargate, Redis caching, XML→JSON translation of RemitONE API.
3. **RemitONE white-label backend** — third-party managed.

## Deal outcome

The deal **did not proceed to contract** after the December 2025 proposal. Marcus Davey had proposed a February 2026 start date on the 8 December call, but no engagement began. As of May 2026 — five months later — Joseph Osei Owusu has re-engaged Boris Vida directly via LinkedIn, signalling renewed interest.

## What has changed since the proposal

Per Joseph's May 2026 LinkedIn message:
- Customer journeys and product direction are now "mapped out in much more detail."
- SocialRemit now specifies **Flutter** as the mobile technology (the proposal used React Native).
- They are planning to go live "within the next couple of months" on RemitONE white-label.
- They are simultaneously building a "proprietary frontend and longer-term platform architecture."

The React Native → Flutter shift requires re-evaluation. VL has limited Flutter developer capacity, which is a **resourcing consideration** (not a blocker) for any new engagement.
