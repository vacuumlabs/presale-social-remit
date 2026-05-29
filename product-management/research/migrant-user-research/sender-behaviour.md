---
type: research
title: Sender behaviour and corridor reality — UK to Ghana/Nigeria
tags: [research, remittance, migrants, ghana, nigeria, sender-behaviour]
sources:
  - ../migrant-user-research-brief.md
  - https://www.cambridge.org/core/journals/journal-of-international-and-comparative-social-policy/article/abs/financialisation-of-transnational-family-care-a-study-of-ukbased-senders-of-remittances-to-ghana-and-nigeria/0891E8DF943D65BA6BAB1BEAB4157653
  - https://journals.sagepub.com/doi/10.1177/2158244015605353
  - https://discovery.ucl.ac.uk/id/eprint/10208232/
  - https://assets.publishing.service.gov.uk/media/5a78cf4ae5274a2acd189f5d/Constraints-UK-Ghana.pdf
  - https://remittanceprices.worldbank.org/corridor/United-Kingdom/Ghana
  - https://remittanceprices.worldbank.org/corridor/GB/NG
last_updated: 2026-05-29
status: draft
---

> Provenance: AI/agent-generated research artifact.
> Authority: raw material.
> Review status: unreviewed.

# Sender behaviour and corridor reality

## Executive read

UK-based Ghanaian and Nigerian senders should not be treated as a generic "migrant
remittance" audience. The common pattern is transnational family care: people in the UK
are expected to act as financial providers across distance, often under pressure and with
asymmetric visibility into how money is used. A Cambridge study of 20 UK-based Ghanaian
and Nigerian remittance senders frames this as family care becoming financialised, with
migrants positioned as "absent providers" in family networks.

The sender-side app is only half the product. The sender chooses the provider, but the
receiver's ability to get money reliably, quickly, locally, and without social friction can
decide whether the sender repeats use. For SocialRemit, receiver experience and payout
confidence should be treated as MVP trust features, not back-office plumbing.

## Corridor economics

World Bank Remittance Prices Worldwide data for Q3 2025 shows UK -> Nigeria as a highly
competitive low-cost corridor: the total average is listed at 1.26% for one transfer
profile and 1.96% for another view of the same corridor. Some digital players are listed
near zero visible fee plus very low exchange-rate margins, while legacy and mixed-channel
providers can be materially higher. UK -> Ghana is costlier: Q3 2025 averages are listed
around 3.79-4.24%, with some providers far above that because of exchange-rate margin.

Implication: SocialRemit cannot rely on "low cost" as a standalone differentiator,
especially for Nigeria. It needs a credible bundle: competitive FX, predictable delivery,
receiver convenience, transparency, and human recovery when something goes wrong.

## Sender jobs

The functional job is "send money home", but the lived jobs are more layered:

- **Care continuity** — keep family life functioning despite distance: food, school fees,
  medical costs, rent, emergencies, and seasonal obligations.
- **Reputation management** — maintain status as a responsible migrant while avoiding
  being seen as an endless cash source.
- **Control and accountability** — senders sometimes care whether the money is used for
  the stated purpose. Nigerian migrant research identifies conflicts around demands,
  expectations, unaccountability, household power, and rivalry.
- **Urgency handling** — many transfers are routine, but the painful ones are urgent:
  hospital, funeral, school deadline, travel, or a receiver suddenly short of cash.
- **Peace of mind** — sender needs proof that money arrived and confidence that support
  can resolve a stuck transfer.

## Ghana-specific signals

Older UK-Ghana corridor research found formal cash-to-cash transfer services heavily used
by Ghanaian diaspora respondents, even where the UK-side population was relatively banked.
The same report said users were generally satisfied with formal services and would be
unlikely to adopt new products unless the new offer improved cost, reliability, and
convenience.

Ghana's receiver side is strongly shaped by mobile money, especially MTN MoMo. Research on
digital remittances and mobile money in Ghana warns that digitisation is not neutral: it
can change how families manage money and how institutions gain control over household
financial flows. For SocialRemit, MoMo-style payout is likely table stakes for many Ghana
use cases, but the product should not assume every sender wants all money to become fully
visible and trackable to formal systems.

Likely Ghana sender segments:

- **Established family supporter** — 35-60, long-settled in the UK, sends routinely to
  parents, siblings, school fees, or property projects. Uses known brands, values
  reliability over novelty.
- **Younger digital sender** — 22-40, already compares Wise, Remitly, Sendwave, TapTap
  Send, and app-based providers. Sensitive to FX, speed, and app friction.
- **Purpose-bound sender** — sends for specific needs such as school, building, healthcare,
  or church/community obligations. Wants proof and sometimes control over destination.

## Nigeria-specific signals

Nigeria differs in the visibility of informal and network-based transfer alternatives.
UCL research on UK-Nigeria remittance entrepreneurship links informal money transfer
operators to ethnic networks and personal trust, created partly by regulatory burden and
niche community needs. Public diaspora discussions also describe WhatsApp-brokered swaps:
someone in Nigeria needs GBP, someone in the UK needs naira, and a trusted broker or group
matches the flows.

Crypto/stablecoin appears as a workaround in some public discussions, especially when
users want better rates or face restrictions on USD/naira flows. This is not enough to
make crypto mainstream for the MVP, but it is a competitive pressure among rate-aware,
financially confident users.

Likely Nigeria sender segments:

- **Bank-to-bank optimizer** — digitally confident, sends to Nigerian bank accounts, cares
  about rate and speed, may compare apps and informal WhatsApp brokers.
- **Emergency family responder** — sends when a parent, sibling, or friend has urgent
  need. Values same-day delivery, reliable recipient confirmation, and reachable support.
- **Trust-network user** — still relies on a person, WhatsApp group, broker, church member,
  or diaspora business because the social tie reduces uncertainty.
- **Crypto-curious rate seeker** — comfortable with USDT or wallet-based rails, likely
  narrower than the mainstream audience, but vocal and influential in online communities.

## Pain points that matter

The most dangerous pain point is not a high fee; it is a failed or frozen transfer when
the sender cannot get a human explanation. App-review evidence for major remittance
players shows praise for speed and convenience, but negative reviews cluster around money
on hold, delayed refunds, cancelled accounts, local-partner failures, and poor support.

Key pain clusters:

- **Hidden cost and FX opacity** — especially where "zero fee" masks exchange margin.
- **Delivery uncertainty** — transfer says sent, receiver has not received, sender cannot
  tell whether the issue is app, partner, bank, mobile wallet, or receiver details.
- **KYC/account shutdown** — sender is blocked mid-need without a clear path to recover.
- **Receiver friction** — wrong payout method, unavailable cash, weak agent coverage,
  receiver lacks the right wallet/account, or local partner delays.
- **Family pressure** — sender is expected to provide but may feel exploited, judged, or
  unable to refuse.

## Product implications

For MVP/proposal purposes, SocialRemit should treat these as trust-critical features:

- Clear total-cost display: fee, FX margin, receiver amount, and comparison to expected
  delivery.
- Payout confidence by corridor: bank/mobile money/cash pickup coverage and what happens
  when a receiver cannot collect.
- Transfer state clarity: "where the money is" in human language, not generic processing
  states.
- Recovery path: visible support escalation for stuck transfers, especially where local
  partners are involved.
- Recipient-side confirmation: sender needs proof, but the receiver experience must stay
  simple.
- Corridor-specific onboarding: Ghana and Nigeria should have tailored examples, payout
  methods, FAQs, and trust signals.

## Confidence map

High confidence: remittances are family-care work, not only financial transactions; price
alone is insufficient; receiver-side payout confidence matters; Nigeria has visible
informal/network alternatives; Ghana mobile money matters.

Medium confidence: exact segment sizes; relative importance of church/community vs online
ads; how much low-income senders use open banking vs debit card vs cash-in.

Low confidence: whether "built by migrants" resonates with target users before we hear
actual user language; whether crypto is material beyond a vocal minority.
