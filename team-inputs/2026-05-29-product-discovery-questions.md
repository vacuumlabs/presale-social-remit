---
type: concept
title: Product Discovery Questions — strategy, personas, differentiation, GTM
tags: [discovery, product-strategy, personas, gtm, differentiation, P3]
source_type: internal-authored
author: Rudolf Vido
role: Product Owner / incoming PM
informed_by:
  - ../client-inputs/2026-05-19-call-transcript.md
  - ../client-inputs/2026-05-28-joseph-qa-response.md
sources:
  - ../product-management/product-vision.md
  - ../product-management/domain-research.md
  - ../deal-context/group-structure.md
last_updated: 2026-05-29
status: draft
---

# Product Discovery Questions

Drafted 2026-05-29 to close the strategic gaps surfaced during PM onboarding. These go
beyond the December 2025 discovery questions ([T2-discovery-qa.md](./T2-discovery-qa.md))
and the resolved Joseph Q&A ([2026-05-28](../client-inputs/2026-05-28-joseph-qa-response.md)) —
those covered *what to build*. These cover *for whom, why us, and how it grows*.

The brief that motivates each cluster is in the body. Questions are deliberately open —
they are interview prompts, not a form.

---

## A. Targets, traction & the 3-year picture

The 1,000–3,000 transactions/day figure implies ~20k–90k active monthly senders
(see math in the onboarding note). That is inconsistent with a "first 10k customers"
framing and a 4–5 person pre-seed team. We need to know which horizon each number describes.

1. Is the 1,000–3,000 transactions/day figure a **launch target, a 6-month target, or a steady-state ambition**? Over what timeframe?
2. How many **active senders** and how many **registered users** does that assume? What send-frequency are you modelling per user?
3. What is the **single metric** that proves traction to your seed investors — transaction count, total volume (£), active senders, or retention?
4. What does **success at 3 years** look like in numbers — users, volume, corridors, valuation band?
5. What is the **minimum traction** that unlocks the seed raise, and by when?

## B. Personas & segmentation — who exactly?

We have a segment label ("UK-based migrants and low-income workers, Ghana + Nigeria corridors")
but no personas, no education/income texture, and no behavioural detail. Joseph's own profile
(FCCA, founder) sits far from the stated target user — the "for migrants" claim needs
validation *from users*, not only the founder.

6. Who is the **primary sender persona** for the Ghana and Nigeria corridors — age, occupation, income band, digital literacy, English fluency?
7. Are these **first-generation arrivals, settled migrants, students, or seasonal workers**? Do they differ by corridor?
8. What device and app behaviour is typical — smartphone tier, data constraints, app-store habits, comfort with biometric/2FA?
9. Who is the **receiver** at the destination, and how do they take delivery (bank, mobile money, cash pickup)? Does the receiver influence which app the sender chooses?
10. Has **any of this been validated with real target users**, or is it founder intuition so far? Can we talk to 5–10 actual senders?

## C. Differentiation & identity — make "built by migrants" concrete

Right now "built by migrants, for migrants" is a founder story, not a product feature, and
"make your money work the way life actually works" has no product referent. We need the
features that make the claim falsifiable — otherwise it is positioning a competitor can copy
or out-spend.

11. Name **three things in the MVP** that exist *because* the team is migrant-built and that a generic fintech team would not have thought to do.
12. What does **"the way life actually works"** translate to in concrete user moments? Walk us through one.
13. The **6-year innovation pipeline** is the stated moat. Can you share even the next 2–3 features (under NDA)? Without them we cannot assess defensibility.
14. **Why wouldn't a target customer just use Wise** (cheaper/transparent), **Western Union/WorldRemit** (faster/established), or **crypto/USDT** (corridor-popular, low fee)? What is the switching trigger?
15. Is the edge **lower fees, less friction, trust, or emotional connection** — and how is each measurably better than the incumbent on that corridor *today*?

## D. Brand & naming risk

"E-money" is an FCA term of art for *electronic money*. For an EMI licence-holder to trade as
"E-money = Emotional Money" risks regulatory and customer confusion. Worth surfacing now,
cheaply, before marketing spend.

16. Has the **"E-money" naming** been checked against the FCA's use of "electronic money" / "e-money" and for trademark conflicts? Is there appetite to revisit?
17. Which name leads in market — **Social Remit, E-money, or E-money Pay** — and is that consistent across app store, marketing, and regulatory disclosures?

## E. Go-to-market — the first 10k customers

There is currently **nothing documented** on acquisition, channels, or community strategy —
yet the whole seed timeline depends on traction. This is client-owned, but it directly
determines whether 6-months-to-seed is realistic and what the app must support (referral,
deep-linking, attribution).

18. How do you reach the **first 10,000 customers** — paid, community, diaspora networks, agents, referral, partnerships (churches, associations, money shops)?
19. **Where do these communities gather online** (WhatsApp groups, Facebook groups, TikTok, Telegram, community radio) and who influences them?
20. What is your assumed **CAC and the budget** behind launch? Is there a marketing team or partner?
21. How central is **referral / word-of-mouth** to the model — and what referral mechanics must the MVP support at launch (codes, rewards, deep links, attribution)?
22. Are there **anchor partnerships or communities** already lined up for one corridor we can launch into first?

## F. Product scope beyond remittance

The group roadmap (E-money Score, Finance, Transpara) implies the app is a wedge for credit,
savings, and EWA. We need to know what, if anything, must be *visible or instrumented* in the
MVP to enable that later.

23. Beyond send-money, what must the MVP **do or capture** to seed the later products (e.g. behavioural data for E-money Score, savings hooks)?
24. Are **rewards / loyalty / referral** a launch feature or Phase 2? How sophisticated at go-live?
25. Is there any **non-remittance feature** (bill pay, airtime top-up, savings pot) that target users expect from day one on these corridors?

## G. Channel — digital-only vs physical

MVP is fully digital with cash-pickup *delivery* at destination. Many migrant remittance
flows still involve physical/agent touchpoints (cash-in, trust-building). We should confirm
the intended channel model.

26. Is the sender experience **fully digital**, or do you anticipate any **physical/agent presence** (cash-in points, community agents, branded kiosks) now or later?
27. How do customers **fund the wallet** in practice — and is card/open-banking enough for a cash-heavy migrant segment, or is cash-in a gap?
28. What is the **trust-building mechanism** for a first-time user sending money through a brand-new app with no high-street presence?

---

## How to use this set

Recommended sequencing:
- **Cluster A, C, E** are for **Joseph directly** (founder-level strategy) — fits the next
  call after the 2026-06-01 internal alignment.
- **Cluster B, G** are best answered by **primary research with real corridor users**
  (5–10 interviews) — Joseph's intuition is a hypothesis, not the answer.
- **Cluster D, F** can be raised async / in the proposal discovery thread.

Feeds `/p3` problem framing once answers land.
