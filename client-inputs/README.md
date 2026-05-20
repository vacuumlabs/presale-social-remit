# client-inputs/

Raw material **from the customer**: meeting transcripts, RFPs, emails, annexes, decks they sent, forms they filled in, screenshots they shared.

## Edit rule — immutable

Nobody edits files under `client-inputs/`. Not humans, not Claude. If the client sends an updated version, commit it as a *new* date-prefixed file — the old one stays as the historical record.

This is different from `team-inputs/`, where the author can iterate on their file. See the [root README](../README.md).

## Binary companion rule

Any non-markdown file (PDF, deck, spreadsheet, image) gets a matching `.md` next to it summarising its contents — e.g. `annex-3.xlsx` → `annex-3.md`. Without this, Claude can't answer questions about the binary.

## Index of client inputs

<!-- Claude maintains this on every /ingest and /lint pass -->

- [`Socialremit_Customer_Flow_Nov2025.md`](./Socialremit_Customer_Flow_Nov2025.md) — companion summary for `../../../Socialremit_Customer Flow Nov 2025.pdf`; full UX screen spec from client (Nov 2025)
- [`2026-05-19-call-transcript.md`](./2026-05-19-call-transcript.md) — transcript of 19 May 2026 Boris Vida + Joseph Owusu call (57 min)
- [`2026-05-19-governance-notes-v1.md`](./2026-05-19-governance-notes-v1.md) — SocialRemit MVP Technology Governance Notes v1; 38-section technical governance framework authored by Joseph; non-negotiable principles, 3-layer model, vendor shortlist
- [`2026-05-19-meeting-minutes.md`](./2026-05-19-meeting-minutes.md) — Joseph's written meeting minutes from the 19 May 2026 call; corroborates transcript with additional nuances (investor situation, self-funded 2 years, AI tooling)
