---
type: concept
title: Domain research — SocialRemit
tags: [domain, research, P2]
sources:
  - ../team-inputs/T1-sales-deal-brief.md
last_updated: 2026-05-19
status: draft
---

# Domain research — SocialRemit

## 1. Client profile

**Company overview**
SocialRemit (trading as E-money Financial Services) is a UK-based consumer remittance startup. It operates under the umbrella of Affecta Technology, an IP holding group also encompassing Transpara (B2B white-label remittance infrastructure), E-money Score (credit engine), and E-money Finance (embedded finance/EWA). The immediate product is a mobile remittance app targeting UK-based migrants sending money internationally.

**Regulatory standing** _(confirmed from wiki — T1 brief and client call)_
SocialRemit holds an Electronic Money Institution (EMI) licence from the FCA. An AML board is in place. This is a meaningful milestone for a pre-revenue company — EMI registration takes 12–18 months and requires demonstrable safeguarding and compliance infrastructure. This is confirmed, not inferred.

**Stage and size** _(confirmed)_
Pre-revenue, pre-seed. Self-funded. Estimated 4–5 named team members. $900M in liquidity committed for two corridors — held in reserve as transaction float, not invested capital. Grantify has qualified the company for up to £2M Innovate UK loans (not yet drawn). AWS credits of $300k–$1M reportedly available.

**Key people** _(confirmed)_
- Joseph Owusu FCCA — founder, product owner, CFO-equivalent. Former CEO/CFO/treasury at UnityLink, where he scaled from 50k to 1.5M transactions/day. Deep domain expertise in remittance operations, treasury, and migrant finance.
- Paul Duncan — Technical Director, recently joined from Unitalink. Controls technical and commercial sign-off before board approval.

**Products and services** _(confirmed)_
MVP scope: consumer mobile remittance app (iOS + Android) with progressive KYC (Sumsub), multi-currency wallet, send money via bank deposit and mobile money, wallet top-up (card + open banking), beneficiary management, and transaction history. White-label backend via Fincode for 12 months, then replaced by Transpara.

**Recent strategic moves** _(confirmed from May 2026 call)_
Since the stalled December 2025 VL proposal: completed EMI registration, selected Fincode as white-label provider (replacing RemitONE), contracted Sumsub for KYC, completed a full Figma prototype, and recruited Paul Duncan. The company is now operationally ready to build.

**Visible pain points** _(inferred from T1 brief and call context)_
- No technology team — entirely dependent on external development partner.
- Aggressive go-live pressure (6–8 weeks) driven by fundraising timeline, not operational readiness.
- Commercial model not aligned with standard VL T&M terms; seeking deferred payment.
- Fincode API capabilities not yet reviewed — BFF integration scope is unconfirmed.

---

## 2. Domain context

**How cross-border remittance works in the UK** _(inferred from industry knowledge, corroborated by Joseph's background)_
The UK is one of the world's largest remittance-sending markets. The Office for National Statistics estimates approximately 14% of the UK population was born abroad. Key outbound corridors include Africa (Nigeria, Ghana, Kenya), South Asia (Pakistan, Bangladesh, India), and the Caribbean. The market is served by incumbents (Western Union, MoneyGram), digital challengers (Wise, Worldremit, Remitly, TapTap Send), and informal value transfer networks.

**Business model and revenue drivers** _(inferred from industry norms; SocialRemit's specific model not disclosed)_
Consumer remittance revenue comes from two sources: (1) spread on the FX rate (the gap between mid-market and the rate offered to customers) and (2) transaction fees, either flat or percentage-based. High-frequency, low-value transfers (e.g., £50–£200) are typical for migrant workers. Volume — not margin per transaction — is the primary driver; hence SocialRemit's stated target of 1,000–3,000 transactions/day pre-seed.

**Typical costs and liquidity mechanics** _(inferred)_
White-label providers (Fincode, RemitONE) handle the payout network — they maintain relationships with correspondent banks and mobile money operators in destination countries. The remittance operator (SocialRemit) holds prefunded positions in-country or pays the provider to manage liquidity. The $900M liquidity figure Joseph cites is either the aggregate capacity of Fincode's network for SocialRemit's corridors, or prefunded float — this needs clarification.

**Market dynamics** _(inferred from industry knowledge)_
The UK consumer remittance market is crowded but not commoditised at the experience layer. Wise and Remitly have competed primarily on price transparency; challengers are now competing on user experience, trust, and corridor depth. The migrant-first, emotionally-intelligent brand positioning Joseph describes (see `product-vision.md`) is a real differentiation vector — no leading player was founded by people with lived migrant experience.

**Where technology is a constraint or enabler** _(confirmed + inferred)_
The key constraint is integration complexity: connecting consumer-facing apps to payout networks (bank APIs, mobile money operators like M-Pesa) via a white-label backend involves compliance-gated API access, variable settlement times, and corridor-specific edge cases. The BFF abstraction layer VL proposes is specifically designed to insulate the app from this complexity and to enable the planned Fincode → Transpara migration. Technology is an enabler here, not a constraint, if the integration layer is designed well.

---

## 3. Likely priorities

Based on public domain knowledge of companies at this stage and vertical, combined with what Joseph has disclosed:

1. **Speed to market above all else.** The go-live date drives the seed raise timeline. Every week of delay is a week of burn without evidence of traction. Joseph will trade scope reduction and risk acceptance for speed.

2. **De-risking the KYC/AML compliance layer.** FCA-regulated EMI operators have onboarding obligations that affect every user. Any go-live delay caused by KYC failures (Sumsub integration, progressive disclosure logic) would be commercially and reputationally catastrophic. Joseph is likely treating Sumsub SDK integration as a hard dependency, not a nice-to-have.

3. **Demonstrating the Fincode exit path to investors.** The 12-month Fincode → Transpara migration plan is a strategic narrative for investors: SocialRemit is not permanently dependent on a third-party backend. The BFF abstraction layer is not just a technical choice — it is a fundraising story. Joseph will want this explicitly articulated in architecture documentation.
