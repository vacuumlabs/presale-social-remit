---
type: lint-report
title: Wiki Lint Report — 2026-05-29
tags: [lint, quality]
last_updated: 2026-05-29
status: active
---

# Wiki Lint Report — 2026-05-29

**Summary:** 0 contradictions unresolved · 3 stale by date (all Dec 2025 raw sources, expected) · 0 orphans · 1 missing wiki page candidate (Transpara) · 5 index/README drift items · 1 provenance hole · 4 pages with stale content despite fresh dates · 0 binary companion gaps · 0 open TODOs · 1 metadata-incomplete page.

---

## 1. Unresolved contradictions

None. [`contradictions.md`](../../contradictions.md) is empty.

---

## 2. Stale pages (last_updated > 14 days)

All wiki synthesis pages were updated between 2026-05-18 and 2026-05-29 — all within the 14-day window. The three pages below are raw source files dated from their creation; their dates are expected and do not represent maintenance failures.

- [`team-inputs/2025-12-08-call-transcript.md`](../../team-inputs/2025-12-08-call-transcript.md) — last_updated: 2025-12-08. Raw source (Dec discovery call). Expected.
- [`team-inputs/2025-12-15-discovery-questions.md`](../../team-inputs/2025-12-15-discovery-questions.md) — last_updated: 2025-12-15. Raw source (Dec discovery questions). Expected.
- [`team-inputs/2025-12-17-fe-build-proposal.md`](../../team-inputs/2025-12-17-fe-build-proposal.md) — last_updated: 2025-12-17. Raw source (Dec proposal, RemitONE scope). Expected.

### Content-stale pages (dates within 14 days, but content outdated by recent ingests)

These pages have not been updated to reflect the Joseph Q&A ingest (2026-05-28) or the go-no-go corrections (2026-05-29):

- [`deal-context/client-overview.md`](../../deal-context/client-overview.md) — "Two corridors confirmed (specific countries not named)" → Ghana and Nigeria are confirmed. "Card payment processor and open banking provider… none yet contracted" → Trust Payments + Volume confirmed. "Fincode API capabilities… full review pending" → full gap analysis done.
- [`deal-context/intake-gaps.md`](../../deal-context/intake-gaps.md) — "What we don't know" table still lists corridors, card processor, open banking provider, admin/back-office tool as unknowns — all now answered. Budget signal references the superseded £118–169k estimate. Watch-for item 5 ("No BD involvement") is partially resolved.
- [`technical-architecture/integrations/fincode.md`](../../technical-architecture/integrations/fincode.md) — Open items list: feature coverage mapping (done via gap analysis), sanctions screening coverage (confirmed), admin portal question (answered), card processor (Trust Payments confirmed). Contract status may still be open.
- [`contract/engagement.md`](../../contract/engagement.md) — "Paul (co-founder, surname unknown)" → Paul Duncan. Missing Jaro, Rudolf, Andy. "Engagement type: T&M" → still under discussion (deferred model). Severely stale.

---

## 3. Orphan pages

None. All wiki pages have at least 3 inbound links from other pages or the root index.

---

## 4. Missing wiki pages

Entities mentioned 3+ times without a dedicated wiki page:

- **Transpara** — 19 mentions across wiki. Described as SocialRemit's planned proprietary backend to replace Fincode after ~12 months, and a separate B2B product in the Affecta group. Currently only summarised in [`deal-context/group-structure.md`](../../deal-context/group-structure.md) and mentioned in passing throughout technical-architecture pages. Given its central role in the BFF exit-ramp design and estimation assumptions, a dedicated `technical-architecture/transpara-exit-plan.md` (or similar) would capture: what Transpara is, the 12-month horizon, what the BFF interface spec looks like, and what VL's role might be in the migration. **Strong candidate for promotion.**
- **NDA** — 4 mentions. Still unresolved open question. Not a full wiki page candidate, but should remain visible in [`deal-context/open-questions.md`](../../deal-context/open-questions.md). *(No action needed.)*
- **ComplyAdvantage** — 3 mentions as a potential AML vendor. Covered adequately as a passing mention in [`technical-architecture/governance-principles.md`](../../technical-architecture/governance-principles.md). *(No action needed.)*

---

## 5. Index drift

### Root `index.md`

No missing entries. All wiki pages are present.

### Folder READMEs — 4 stale entries

- [`deal-context/README.md`](../../deal-context/README.md) — go-no-go entry says "6 green, 6 amber, 1 red (deferred payment model)" → should be **6 green, 4 amber, 1 red**.
- [`deal-context/README.md`](../../deal-context/README.md) — stakeholder-map entry omits Jaro Novák, Rudolf Vido, Andy Birch.
- [`technical-architecture/README.md`](../../technical-architecture/README.md) — fincode-gap-analysis entry says "confirmed gaps (open banking, push notifications…)" → open banking (Volume) is now **confirmed MVP**, not a gap; push notifications architecture is **in MVP scope from day one**.
- [`project-management/README.md`](../../project-management/README.md) — estimation entry says "Dec 2025 T&M estimates: 175 MD / £118k…" → estimation.md is now marked **superseded**; entry should reflect that.
- [`team-inputs/README.md`](../../team-inputs/README.md) — T2-discovery-qa.md entry says "Section 7 open questions to send Joseph on 23 May 2026" → all 7 questions are now **answered**.

---

## 6. Provenance holes

- [`contract/engagement.md`](../../contract/engagement.md) — **missing `sources:` field entirely**. Also missing `type:` field. This is the only wiki page with both fields absent.

---

## 7. Binary companion gaps

None. No non-markdown files exist under `client-inputs/` or `team-inputs/` in the repo. The referenced PDF (`Socialremit_Customer Flow Nov 2025.pdf`) lives outside the repo; its companion `.md` ([`client-inputs/Socialremit_Customer_Flow_Nov2025.md`](../../client-inputs/Socialremit_Customer_Flow_Nov2025.md)) exists.

---

## 8. TODO audit

No open `- [ ]` checkboxes found across the wiki.

---

## 9. Metadata validity

- [`contract/engagement.md`](../../contract/engagement.md) — missing `type:` and `sources:` fields. All other pages pass.
