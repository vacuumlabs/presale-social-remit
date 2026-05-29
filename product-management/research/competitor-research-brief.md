---
type: concept
title: Competitor Research Brief — remittance market
tags: [research, competitors, remittance, white-space, positioning, wise, western-union, P3]
sources:
  - ../../team-inputs/2026-05-29-product-discovery-questions.md
  - ../product-vision.md
  - ../domain-research.md
last_updated: 2026-05-29
status: planned
---

# Competitor Research Brief — remittance market

**Status: planned — not yet started.** Defines competitor research the team agreed is
needed during PM onboarding (2026-05-29). This is findings-to-come, not findings.

**Scope note — do not confuse with [competitive-positioning.md](../competitive-positioning.md).**
That page is about who *Vacuumlabs* competes against to win the build (freelancers, agencies).
**This brief is about who *SocialRemit* competes against in the remittance market** — the
incumbents and challengers a UK migrant could use instead of Social Remit.

## Why this research exists

SocialRemit's differentiation ("built by migrants", "the way life actually works") is
currently asserted against a positioning map Joseph sketched ([product-vision.md](../product-vision.md)),
not against evidence. We don't actually know, in detail, what the incumbents do well, where
they are weak, or where there is unserved **white space** on the Ghana and Nigeria corridors.
Without that, we cannot tell whether Social Remit's edge is real or whether it is competing
on an axis (emotion/brand) while losing on the axes users actually pick on (price, speed,
trust). This research grounds the positioning — and protects the proposal from building a
differentiated brand on top of an undifferentiated product.

## Research objectives

1. **Profile the relevant competitor set** for UK→Ghana and UK→Nigeria senders — what each does well, what they do poorly, and what genuinely holds up against them.
2. **Identify white space** — needs, segments, moments, or corridors that no incumbent serves well.
3. **Stress-test Social Remit's claimed differentiation** against what competitors already offer (don't let "built by migrants" paper over feature/price parity gaps).
4. **Benchmark the table stakes** — fees, FX spread, speed, delivery options, KYC friction — so the MVP and proposal are calibrated to what users compare against.

## Competitor set to cover

- **Price/transparency challengers:** Wise, Remitly.
- **Migrant-corridor specialists:** WorldRemit, TapTap Send, Lemonade Finance / others strong on Africa corridors, Sendwave.
- **Incumbents / cash networks:** Western Union, MoneyGram, Ria.
- **Mobile-money-native destinations:** how MTN MoMo (Ghana), OPay / PalmPay / Moniepoint (Nigeria) shape receiver expectations.
- **Crypto / stablecoin rails:** USDT/USDC P2P and apps used informally on these corridors — assess real usage, trust, and friction.
- **Informal channels:** hawala-style / community money agents — still material for migrant segments.

For each, capture: positioning, target user, fee + FX model, speed, delivery methods, KYC/onboarding friction, app experience quality, trust signals, and corridor strength (specifically Ghana & Nigeria).

## Key research questions

### What they do well / badly
- On UK→Ghana and UK→Nigeria specifically, who is cheapest, fastest, most trusted, easiest to onboard?
- What do users praise and complain about (app store reviews, community forums, Trustpilot)?
- Where do incumbents have structural advantages that genuinely hold against a newcomer (liquidity, payout network depth, brand trust, agent footprint, licensing)?

### White space
- Which user needs or moments are poorly served by everyone (e.g. first-time senders, cash-in for the unbanked, receiver experience, recurring obligations, transparency in local language, support when transfers fail)?
- Are there corridor-specific gaps (delivery method, speed, hours, mobile-money coverage) Social Remit could own?
- Is the "emotional / migrant-native" positioning actually unoccupied, or do challengers already claim it implicitly?

### Differentiation reality check
- On the axes users actually choose by (price, speed, trust), how close to parity must Social Remit be before "emotional connection" becomes a deciding factor?
- What can Social Remit credibly do *better*, not just *differently*?
- How fast could an incumbent copy each proposed differentiator? (Joseph assumes ~6 months — test that.)

## Suggested method

Lightweight, presale-appropriate, desk-research-led:

- **Desk research / teardown** of each competitor: pricing pages, app store listings, onboarding walk-throughs, fee + FX comparison for a representative transfer (e.g. £200 UK→Accra, £200 UK→Lagos). The `recon-research` or `deep-research` skill is well suited to fan this out and verify claims.
- **Review mining** — app store, Trustpilot, Reddit, and the same diaspora WhatsApp/Facebook/TikTok communities used in the [migrant user research](./migrant-user-research-brief.md) — for unprompted praise and complaints.
- **Live fee/FX snapshot** on a fixed date across providers, so the comparison is apples-to-apples (rates move).
- **Positioning map** placing each competitor on the axes that matter, with Social Remit's intended slot marked and defended (or challenged).

## Deliverables

- A **competitive-analysis** write-up in the parent folder ([competitive-analysis.md](../) per the README's typical pages), or one page per competitor under `competitors/<name>.md`.
- A **fee/FX/speed benchmark table** for both corridors as of a fixed date.
- A **positioning map** and an explicit **white-space verdict** — where the genuine opening is, if any.
- A **differentiation reality-check** feeding the proposal and discovery (cluster C of the [discovery questions](../../team-inputs/2026-05-29-product-discovery-questions.md)).

## Dependencies & caveats

- **Pairs with the [migrant user research](./migrant-user-research-brief.md):** competitor strengths only matter relative to what *these* users value — run them together or sequence user-first.
- **Rates are volatile:** any fee/FX comparison must be timestamped and corridor-specific.
- **Crypto data is noisy:** informal stablecoin usage is hard to size; treat as directional.
- **Owner unconfirmed:** provisionally PO/PM. Confirm at the 2026-06-01 internal alignment.

## Related

- Deal-side competition (not market): [competitive-positioning.md](../competitive-positioning.md)
- Companion user research: [migrant-user-research-brief.md](./migrant-user-research-brief.md)
- Differentiation claims under test: [product-vision.md](../product-vision.md)
- Discovery questions (cluster C — differentiation): [2026-05-29-product-discovery-questions.md](../../team-inputs/2026-05-29-product-discovery-questions.md)
