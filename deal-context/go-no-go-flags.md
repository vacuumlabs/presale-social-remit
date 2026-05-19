---
type: concept
title: Go/no-go flags — SocialRemit
tags: [intake, go-no-go, G1]
sources:
  - ../team-inputs/T1-sales-deal-brief.md
last_updated: 2026-05-19
status: draft
---

# Go/no-go flags — SocialRemit

**Note — V2 gates are soft checkpoints, not hard stops.** These flags surface signals for an informed team conversation at G1. They are not mechanical blockers.

---

## Green — conditions that support proceeding

- **Budget signal provided.** It is Soft with significant caveats, but a signal exists and the December 2025 T&M range (£118–169k) is on record. We are not going in blind.
- **VL has directly relevant prior work.** Boris Vida led the December 2025 SocialRemit architecture — React Native + NestJS BFF + white-label integration. The domain, stack, and client are already known. No ramp-up needed.
- **Named technical stakeholder.** Paul Duncan (Technical Director) is confirmed, available from 25 May, and must approve commercial terms. The engagement has a real technical counterpart, not just a business contact.
- **Deal tier T2 is appropriate.** A mobile app + BFF + third-party integrations in the £100–150k range fits T2 comfortably. Not under- or over-sized for the process.
- **Regulatory and operational readiness confirmed.** EMI registration (FCA), $900M liquidity for two corridors, Sumsub contracted, Figma prototype complete. This is not vaporware — the client has done their groundwork.
- **Warm relationship.** Joseph reached out directly to Boris (bypassing sales), indicating trust in VL's technical credibility specifically. This is a relationship to build on, not a cold RFP.

---

## Amber — conditions that need attention before or during Discovery

- **Deferred payment model awaiting VL leadership decision.** Joseph's ask (minimum upfront, rest on go-live, plus equity/options) is non-standard. Tomas Masek (CEO) and Marek Tomasik (CDO) have been alerted and must resolve this before the proposal is finalised. Presale effort should not be overcommitted until their answer is known.
- **Timeline is extremely aggressive relative to scope.** A 6–8 week go-live for a full MVP (KYC onboarding, multi-currency wallet, two payment rails, card + open banking top-up) is tight even with an experienced team. The PM must pressure-test this in Discovery and the proposal must set realistic expectations.
- **No hard budget figure.** The Soft signal and deferred model mean we do not know Joseph's mental model of total cost. The freelancer reference quotes (£5k–£10k) suggest a possible 10–20x expectation gap. This must be addressed before scope and commercial terms are finalised.
- **Flutter vs React Native is unresolved.** VL leans React Native (more experience, larger hiring pool), but the recommendation needs mobile expert input. If Flutter is ultimately chosen, resourcing and timeline assumptions in the proposal may shift.
- **Fincode API docs not yet received.** Integration effort cannot be confirmed until VL has reviewed the Fincode API. If the protocol is significantly different from RemitONE (XML, RSA encryption, UISettings-driven forms), BFF complexity could increase.
- **Presales ownership transition not yet formalised.** Marcus Davey (BD) is not looped in per CTO Michal Cernak's direction. If the transition to delivery-led presales is not documented before the proposal goes out, there is a risk of internal confusion over commercial ownership.

---

## Red — conditions that should prompt an explicit team discussion before committing presale effort

- **Deferred payment + equity is a structural commercial risk.** This is the single red flag for this deal. Joseph has explicitly asked for a model VL has not accepted before. If VL leadership declines, the deal cannot proceed on the client's stated terms. A clear answer from Tomas Masek / Marek Tomasik must come before the proposal is assembled. Until then, limit presale effort to work that has value regardless of commercial outcome (architecture, scope clarification, estimation update).

---

## Summary

| Category | Count | Key item |
|----------|-------|----------|
| Green | 6 | Strong technical fit, warm relationship, confirmed client readiness |
| Amber | 6 | Commercial model pending, aggressive timeline, budget gap risk |
| Red | 1 | Deferred payment + equity model — awaiting VL CEO/CDO decision |

**Recommended action before G1:** Obtain Tomas Masek / Marek Tomasik decision on deferred model. If green-lit (even conditionally), proceed to proposal. If declined, return to Joseph with VL's standard terms and assess whether the deal continues.
