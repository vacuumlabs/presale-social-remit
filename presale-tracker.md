---
type: status
title: Presale Tracker (HTML dashboard) — companion summary
tags: [tracker, status, dashboard, project-management]
sources:
  - ./presale-tracker.html
last_updated: 2026-05-29
status: active
---

# Presale Tracker — companion summary

Companion to [`presale-tracker.html`](./presale-tracker.html), a self-contained HTML
dashboard for the SocialRemit presale. Open the HTML file in a browser.

## What it shows

- **Pipeline** across the V2 presale SDLC (P1 → P9 with gates G1–G4). Status as of 2026-05-29: P1 and P2 **done**; P3 (Problem Framing) and P4 (Technical Architecture) **in progress** in parallel; everything from P5 onward **not started**. G1 passed; G2–G4 pending.
- **Blocker banner** — the deferred-payment + equity commercial model (owner: Andy Birch / CRO), the single red flag gating the proposal.
- **Task cards** distinguishing **Agreed** steps (solid hot-pink border) from **Suggested** steps (dashed border — the incoming PM's proposal, not yet team-confirmed), each with a best-guess owner, stage, and status. A filter toggles All / Agreed / Suggested.

## Maintenance

The dashboard is data-driven: edit the `STAGES` and `TASKS` arrays near the bottom of
the HTML file to update status, owners, or steps. Owners are best-guess pending
confirmation; the agreed/suggested split should be revisited after the 2026-06-01
internal alignment meeting.

Branding uses VL hot pink (`#FF1F8E`).
