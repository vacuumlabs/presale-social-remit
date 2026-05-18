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
