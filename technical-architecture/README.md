# technical-architecture/

System design, architecture diagrams, tech-stack decisions, ADRs, ARB records, integration specs.

## Typical wiki pages

- `tech-stack.md` — summary of what we're using and why
- `systems/<name>.md` — one page per system or subsystem in scope
- `integrations/<name>.md` — one page per external integration
- `adrs/ADR-NNNN-<slug>.md` — one Architecture Decision Record per material decision (use [`ADR format`](https://adr.github.io/madr/))
- `arb-records/YYYY-MM-DD-<topic>.md` — Architecture Review Board minutes
- `diagrams/<name>.md` — diagram pages (with source Mermaid / Excalidraw / drawio snapshots in the repo)

## Index

<!-- Claude maintains this list -->

- [`system-overview.md`](./system-overview.md) — 3-layer MVP architecture (Product/Control/Infrastructure); observability and CI/CD requirements; Flutter vs React Native open decision
- [`governance-principles.md`](./governance-principles.md) — client's non-negotiable architectural, operational, delivery and strategic principles; 3-layer model; vendor shortlist; scope signals for estimation
- [`fincode-gap-analysis.md`](./fincode-gap-analysis.md) — what Fincode covers natively vs what VL must build; Bucket 3 resolved (Sumsub confirmed MVP, Trust Payments + Volume confirmed, push notification architecture in scope from day one); remaining gaps: analytics, rewards, observability, internal DB, CI/CD
- [`integrations/fincode.md`](./integrations/fincode.md) — Fincode (current white-label provider); API docs URL now available
- [`integrations/remitone.md`](./integrations/remitone.md) — RemitONE (superseded); retained for reference
