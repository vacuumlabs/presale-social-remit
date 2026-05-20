# Wiki index

Categorised catalogue of every wiki page. Claude reads this first when answering a question — it's the map.

Maintained by `/ingest` and `/lint`. Do not edit by hand except to resolve conflicts.

---

## Contract & engagement

- [`contract/engagement.md`](./contract/engagement.md) — canonical engagement metadata (fill at kickoff)

## Deal context

- [`deal-context/stakeholder-map.md`](./deal-context/stakeholder-map.md) — Joseph Owusu, Paul Duncan (Technical Director), Tomas Masek + Marek Tomasik (VL CEO/CDO), Boris Vida, Marcus Davey
- [`deal-context/client-overview.md`](./deal-context/client-overview.md) — SocialRemit: EMI registered, Fincode white-label, go-live 6–8 weeks, $900M liquidity
- [`deal-context/proposal-dec-2025.md`](./deal-context/proposal-dec-2025.md) — December 2025 VL proposal status: not contracted; re-engagement via Joseph May 2026
- [`deal-context/open-questions.md`](./deal-context/open-questions.md) — questions answered on 19 May call; critical open: commercial/payment model
- [`deal-context/group-structure.md`](./deal-context/group-structure.md) — Affecta Technology group: Social Remit, Transpara, E-money Score, E-money Finance
- [`deal-context/intake-gaps.md`](./deal-context/intake-gaps.md) — P1 gap analysis: know/don't-know, 5 risk signals
- [`deal-context/similar-deals.md`](./deal-context/similar-deals.md) — P1 similar deals: no past outcomes found; Dec 2025 SocialRemit proposal as baseline
- [`deal-context/go-no-go-flags.md`](./deal-context/go-no-go-flags.md) — P1 go/no-go flags: 6 green / 6 amber / 1 red
- [`deal-context/pre-meeting-brief.md`](./deal-context/pre-meeting-brief.md) — P1 pre-meeting brief for proposal delivery ~w/c 25 May

## Product management

- [`product-management/mvp-scope.md`](./product-management/mvp-scope.md) — MVP in/out of scope, what Fincode supports natively vs Phase 2
- [`product-management/product-vision.md`](./product-management/product-vision.md) — "Built by migrants for migrants"; emotional money brand; 6-year innovation pipeline
- [`product-management/domain-research.md`](./product-management/domain-research.md) — P2: client profile, UK remittance domain context, likely priorities
- [`product-management/regulatory-brief.md`](./product-management/regulatory-brief.md) — P2: FCA/EMI regulatory framework; top constraints: progressive KYC, sanctions screening, data residency
- [`product-management/competitive-positioning.md`](./product-management/competitive-positioning.md) — P2: freelancers vs agencies vs boutiques; VL differentiators; risks to VL's position

## Technical architecture

- [`technical-architecture/system-overview.md`](./technical-architecture/system-overview.md) — 3-layer architecture (Product/Control/Infrastructure); Fincode integration; observability + CI/CD requirements; Flutter vs RN open decision
- [`technical-architecture/governance-principles.md`](./technical-architecture/governance-principles.md) — client non-negotiables, 3-layer model, vendor shortlist, scope signals for estimation
- [`technical-architecture/fincode-gap-analysis.md`](./technical-architecture/fincode-gap-analysis.md) — Fincode coverage vs VL build scope; confirmed gaps (open banking, notifications, analytics, rewards, observability, DB, CI/CD); design risks (Sumsub/Fincode KYC overlap, PCI scope)
- [`technical-architecture/integrations/fincode.md`](./technical-architecture/integrations/fincode.md) — Fincode: white-label provider; API docs URL now available
- [`technical-architecture/integrations/remitone.md`](./technical-architecture/integrations/remitone.md) — RemitONE: superseded by Fincode; retained for reference

## Project management (incl. scope & estimates)

- [`project-management/estimation.md`](./project-management/estimation.md) — Dec 2025 estimates: Option 1 £118k (FE+BFF), Option 2 £169k (FE+BFF+Discovery)

## Cross-cutting

- [`decisions.md`](./decisions.md) — decision log across the engagement
- [`contradictions.md`](./contradictions.md) — conflicting claims across sources, pending resolution
- [`log.md`](./log.md) — append-only audit trail of ingest / query / lint actions

## Raw inputs

- [`client-inputs/`](./client-inputs/) — material from the customer (immutable)
- [`team-inputs/`](./team-inputs/) — material we authored ourselves
