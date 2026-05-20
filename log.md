# Log

Append-only audit trail of **material wiki-changing events**. Newest entries at the bottom.

**Format:** `## [YYYY-MM-DD HH:MM] <verb> | <title>` followed by one or two sentences describing what changed and which pages were touched.

**Verbs:** `ingest`, `lint`, `decision`, `contradiction`, `author`, `query`.

**When entries land here:**

- `ingest` — every `/ingest` run (always logged; summarises pages, decisions, contradictions touched).
- `lint` — every `/lint` run.
- `decision` / `contradiction` — when a query or ingest surfaces one and the user confirms saving it. The entry is in addition to the `/ingest` log entry only for queries; ingests fold these into their own entry.
- `author` — when a `team-inputs/` file is authored or materially revised.
- `query` — rare. Only when the user explicitly asks to record a query. Routine Q&A does **not** log.

---

<!-- Claude appends new entries here. Example shape:

## [2026-04-20 09:15] ingest | Annex 3 — Security/GDPR/AI/BCM requirements

Ingested `client-inputs/2026-04-17-Annex-3-Security-GDPR-AI-BCM-requirements.md`. Created stakeholder hubs (CISO, DPO, Cloud Architect), 8 ADR-seed pages under `technical-architecture/adrs/`, and `contract/clauses/audit-right.md`. Flagged 2 contradictions with the draft DPA template.

-->

## [2026-05-18 00:00] ingest | SocialRemit — initial wiki population from GDrive + local sources

Ingested 4 raw sources (client UX flow PDF, Dec 2025 call transcript, discovery questions doc, FE build proposal + estimation spreadsheet) from the parent folder and GDrive folder `1l4RkfBeIotiHJ5p5YEDTBAnyGeAObgdt`.

- Created: `client-inputs/Socialremit_Customer_Flow_Nov2025.md` — companion summary for Nov 2025 UX screen spec
- Created: `team-inputs/2025-12-08-call-transcript.md` — Dec 2025 discovery call (Marcus Davey, Paul, Joseph)
- Created: `team-inputs/2025-12-15-discovery-questions.md` — 12 VL discovery questions; answers not captured
- Created: `team-inputs/2025-12-17-fe-build-proposal.md` — Dec 2025 MVP proposal (React Native + NestJS BFF + RemitONE)
- Created: `deal-context/stakeholder-map.md` — Joseph Osei Owusu FCCA, Paul (surname unknown), Marcus Davey, Boris Vida
- Created: `deal-context/client-overview.md` — SocialRemit overview, current stage, key unknowns
- Created: `deal-context/proposal-dec-2025.md` — Dec 2025 proposal status (not contracted; re-engagement May 2026)
- Created: `deal-context/open-questions.md` — 18 open questions for 19 May 2026 call with Joseph
- Created: `product-management/mvp-scope.md` — MVP in/out-of-scope based on RemitONE capabilities
- Created: `technical-architecture/system-overview.md` — 3-layer architecture; Flutter vs React Native open question noted
- Created: `technical-architecture/integrations/remitone.md` — RemitONE API v3.3 reference and constraints
- Created: `project-management/estimation.md` — Dec 2025 T&M estimates: £118k (Option 1) / £169k (Option 2)
- Updated: `contract/engagement.md`, all folder READMEs, root `index.md`
- Decisions recorded: React Native selected (Dec 2025, under review); BFF pattern adopted (NestJS + Redis + ECS Fargate)
- Contradictions: none

## [2026-05-19 00:00] ingest | SocialRemit — Teams call transcript 19 May 2026

Ingested `Flutter - SocialRemit Transcript.txt` (57-min call, Boris Vida + Joseph Owusu). Major updates across the wiki: provider switched (RemitONE → Fincode), EMI registration confirmed, architecture and 12-month Fincode exit plan confirmed, Flutter/RN open decision noted. Paul's full name confirmed (Paul Duncan). Tomas Masek and Marek Tomasik added to stakeholder map. Commercial risk (deferred payment model) flagged. Created: `client-inputs/2026-05-19-call-transcript.md`, `technical-architecture/integrations/fincode.md`, `deal-context/group-structure.md`, `product-management/product-vision.md`. Updated: `client-overview.md`, `stakeholder-map.md`, `open-questions.md`, `system-overview.md`, `remitone.md` (superseded), `decisions.md`, all indexes.
- Decisions recorded: RemitONE → Fincode (client); Flutter vs RN (open, VL leans RN)
- Contradictions: none

## [2026-05-18 00:00] ingest | VL internal approach — SocialRemit re-engagement

Per CTO Michal Cernak: Boris Vida to continue the re-engagement independently; Martin Simonovic and Richard Peres to be informed only after the 19 May 2026 call. Marcus Davey not looped in before the call. Presales ownership shifting from sales to delivery. Updated `deal-context/stakeholder-map.md` with Michal Cernak, Martin Simonovic, Richard Peres. Saved to memory.

## [2026-05-19 00:00] ingest | P2 domain research — SocialRemit

P2 ran for SocialRemit. Three pages created in product-management/:
- Created: `domain-research.md` — client profile (EMI-registered startup, Joseph Owusu background, Affecta group), UK remittance domain context, likely priorities (speed to market, KYC compliance, Fincode exit narrative)
- Created: `regulatory-brief.md` — FCA/EMI regulatory framework, PSR 2017/EMR 2011, AML/CTF (MLR 2017), top 3 constraints: progressive KYC thresholds, sanctions screening, data residency/Fincode hosting location
- Created: `competitive-positioning.md` — freelancers (already quoting), nearshore agencies, UK boutiques; VL differentiators: relationship + pre-built patterns + BFF abstraction; key risk: cost gap vs. freelancers

## [2026-05-19 00:00] ingest | P1 deal intake — SocialRemit (T2)

P1 ran on T1 brief for SocialRemit (T2). T1 brief was reconstructed from wiki context (discovery call already complete). GDrive Deals folder searched for `_deal-outcome.md` files across 10+ domain-relevant subfolders — no files found. Four pages created in deal-context/:
- Created: `intake-gaps.md` — what we know / don't know / watch for; 5 risk signals flagged
- Created: `similar-deals.md` — no past deal outcomes found in GDrive; Dec 2025 SocialRemit proposal used as internal baseline
- Created: `go-no-go-flags.md` — 6 green / 6 amber / 1 red (deferred payment + equity model awaiting VL CEO/CDO decision)
- Created: `pre-meeting-brief.md` — one-pager framed for proposal delivery meeting ~w/c 25 May 2026

## [2026-05-20 00:00] ingest | Joseph's post-call documents — governance notes, meeting minutes, Fincode API

Ingested two client-authored documents shared by Joseph on 19 May 2026 email. Key output: formal client governance framework now captured in wiki; system-overview updated to adopt client's layer naming and add observability/CI/CD requirements.
- Created: `client-inputs/2026-05-19-governance-notes-v1.md` — full 38-section governance framework (raw source)
- Created: `client-inputs/2026-05-19-meeting-minutes.md` — Joseph's formatted meeting minutes from 19 May call (raw source)
- Created: `technical-architecture/governance-principles.md` — distilled wiki page: 3-layer model, non-negotiables, vendor shortlist, scope signals for estimation
- Updated: `technical-architecture/system-overview.md` — adopted Product/Control/Infrastructure layer naming; added observability requirements, CI/CD environments requirement, Control Layer scope; replaced RemitONE references with Fincode; referenced governance-principles.md
- Updated: `technical-architecture/integrations/fincode.md` — added API docs URL (https://docs.fincode.technology/api/transactions/call-quote); expanded open items to include sanctions/PEP screening coverage and admin portal question
- Updated: `deal-context/client-overview.md` — added investor nuance ("investors exist but want traction"), self-funded for two years, card/open banking provider open items
- Updated: `product-management/regulatory-brief.md` — expanded sanctions screening entry to include PEP screening and ongoing monitoring as client non-negotiables (governance doc §12)
- Contradictions: none

## [2026-05-20 00:00] author | Fincode gap analysis

Crawled Fincode public API documentation (overview, llms-full.txt, quote API, create-transaction API, webhooks API). Produced gap analysis mapping Fincode native coverage against SocialRemit MVP scope.
- Created: `technical-architecture/fincode-gap-analysis.md` — full coverage/gap matrix; confirmed gaps; design risks

Key findings: open banking top-up is a confirmed gap (no Fincode coverage); Sumsub/Fincode KYC overlap is an unresolved design risk; card payment PCI-DSS scope needs clarification; push notifications, analytics, rewards engine, internal DB, observability, and CI/CD are all VL-built with no Fincode coverage.

## [2026-05-20 00:00] author | T2 discovery Q&A created

Created `team-inputs/T2-discovery-qa.md`. Sections 1–6 pre-filled from existing wiki sources (call transcripts, governance notes, client overview). Section 7 contains 9 open questions for async send to Joseph on 23 May 2026. Answers to be ingested after Joseph responds to unblock `/p3`.
