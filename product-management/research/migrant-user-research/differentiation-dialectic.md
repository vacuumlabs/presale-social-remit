---
type: research
title: Differentiation dialectic — built by migrants, for migrants
tags: [research, dialectic, personas, positioning, trust]
sources:
  - sender-behaviour.md
  - digital-ethnography.md
  - channel-map.md
  - ../migrant-user-research-brief.md
last_updated: 2026-05-29
status: draft
---

> Provenance: AI/agent-generated research artifact.
> Authority: raw material.
> Review status: unreviewed.

# Differentiation dialectic

## Question

Is "built by migrants, for migrants" a credible differentiator for SocialRemit, or is it
only founder narrative until translated into proof?

## Persona 1 — Ama, the established Ghanaian family supporter

Ama is 46, a Ghanaian-born care-home deputy manager living in South London. She came to
the UK in her twenties and now supports her mother in Kumasi, contributes to school fees
for two nieces, and occasionally sends money for church/community obligations. She uses
WhatsApp daily and is comfortable with banking apps, but she is not adventurous with money
apps. If a provider has worked ten times, she keeps using it.

Her pain is not learning an app. Her pain is being the person everyone asks when something
goes wrong. If her mother says the MoMo money did not arrive, Ama is on the phone between
work shifts, trying to understand whether the app, mobile wallet, network, or recipient
details caused the issue. She hates hidden rate differences, but she hates uncertainty
more.

Ama's view: "Built by migrants sounds nice, but I need to know my mum receives it. Show me
the exact amount, the MoMo route, and what happens if it gets stuck."

## Persona 2 — Tunde, the Nigerian rate optimizer

Tunde is 32, a British Nigerian software contractor in Manchester. He sends to siblings
and friends in Lagos, sometimes monthly and sometimes urgently. He compares rates, keeps
more than one app installed, and has used informal WhatsApp-brokered swaps when the rate
was better or formal routes were awkward. He is crypto-curious and understands USDT, but
does not want to make every family transfer a mini trading operation.

His pain is feeling that providers hide margin or fail precisely when urgency is highest.
He is not loyal to brands; he is loyal to whatever works today. He will test a new app if
it gives a better rate or a smoother Nigerian bank payout, but he will abandon it after
one unexplained failure.

Tunde's view: "Migrant-built is not a feature. Good rate, instant payout, no nonsense if
something fails. If you beat my backup options, I'll use you."

## Persona 3 — Esi, the receiver-side reality check

Esi is 58, Ama's mother in Ghana. She does not care which UK app Ama used. She cares
whether the money arrives in a form she can actually use. Sometimes mobile money is best;
sometimes cash or bank access matters. Her trust is practical: did the alert arrive, can
she withdraw, does the agent have float, are there fees or limits, and can her daughter
explain what happened?

Esi's pain is being invisible in sender-side product design. A beautiful app in the UK
does not help if the receiver experience is confusing, delayed, or costly.

Esi's view: "I don't use your app. I use the money. Make the last mile work."

## Persona 4 — Joseph, the founder-narrative holder

Joseph believes the market has been underserved by generic providers that do not
understand migrant life. He has domain history, finance experience, and a narrative rooted
in lived experience. He wants SocialRemit to feel emotionally closer to the community than
Wise, WorldRemit, Western Union, or anonymous fintech brands.

His risk is over-universalising from his own story. He may understand the migrant
experience deeply, but the target segment includes lower-income, lower-literacy, less
financially confident, and more receiver-dependent users than a founder can naturally
represent.

Joseph's view: "People will trust us because we are from the community and understand how
life works."

## Persona 5 — Marta, the skeptical VL product lead

Marta is responsible for protecting the proposal from wishful thinking. She does not
reject the migrant-built claim; she wants it operationalised. Her concern is that a
6-8-week app build could produce a generic remittance wrapper around Fincode while the
actual differentiation remains in slideware.

Her pain is scope ambiguity disguised as empathy. "Built by migrants" could mean better
copy, better support, corridor-specific payout UX, community launch, receiver
confirmation, lower fees, local partnerships, or an eventual financial-services roadmap.
Those are not the same product.

Marta's view: "If this is the differentiator, tell me what we build, what we measure, and
what we deliberately postpone."

## The debate

Ama and Tunde agree on one thing: they do not switch because a founder has a relatable
story. They switch when the new service reduces anxiety in a transfer that matters. Ama
wants reliability and receiver proof. Tunde wants rate, speed, and low-friction recovery.
Both punish uncertainty.

Esi forces the group to stop treating the UK sender as the only user. The receiver's
world decides whether a transfer is successful. A payout method that looks complete in an
API can still fail as a lived experience if the local bank, wallet, agent, or family
member creates friction.

Joseph gives the brand its emotional centre. Without his narrative, SocialRemit risks
being another low-cost transfer app in a crowded field. His lived story can create
permission to enter communities and ask better questions. But it becomes dangerous if the
team treats founder empathy as validated research.

Marta translates the debate into product discipline. "Built by migrants" becomes credible
only when it is attached to product and GTM choices:

- corridor-specific receiver methods and explanations;
- transparent total cost, including FX margin;
- transfer tracking that explains partner/local-bank states;
- visible escalation for stuck transfers;
- community/referral launch loops;
- user research with senders outside Joseph's immediate network.

## Verdict

"Built by migrants, for migrants" is a promising positioning platform but not yet a
validated differentiator. It should be treated as a hypothesis with three proof points:

1. **Trust proof** — users believe the service because community/reviews/support and
   regulated rails make it safer than a new anonymous app.
2. **Receiver proof** — the last mile works in Ghana and Nigeria, and senders can see why.
3. **Care proof** — the product reflects family obligation, urgency, and accountability,
   not just a generic fintech flow.

## Product decisions implied

For MVP, do not try to encode the whole migrant experience. Encode the parts that reduce
switching anxiety:

- corridor-specific rate and payout transparency;
- sender-visible receiver confirmation;
- plain-language transfer states;
- support escalation for exceptions;
- community/referral mechanics or at least launch instrumentation;
- post-transfer feedback that asks both sender and receiver what happened.

For proposal, VL should say the founder narrative is valuable but unvalidated. The
recommended approach is to launch with a lean product plus a structured learning loop, so
SocialRemit learns which migrant-specific trust signals actually drive adoption.
