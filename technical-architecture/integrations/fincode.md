---
type: integration
title: Fincode — Integration Reference
tags: [fincode, integration, white-label, remittance]
sources:
  - ../../client-inputs/2026-05-19-call-transcript.md
last_updated: 2026-05-19
status: active
---

# Fincode — Integration Reference

Fincode is SocialRemit's chosen white-label remittance backend as of May 2026, replacing RemitONE. See [`remitone.md`](./remitone.md) for the superseded provider.

## Why Fincode over RemitONE

Per the 19 May 2026 call, "Penny" (SocialRemit colleague) reviewed RemitONE post-December 2025 and recommended switching. Fincode is described as more expensive than RemitONE but significantly more collaborative and engaging — they work with clients rather than just providing a service. SocialRemit is currently reviewing the Fincode contract (as of 19 May 2026).

## Known facts

- More expensive than RemitONE.
- API documentation to be provided by Joseph after the call.
- SocialRemit plans to use Fincode for **12 months only**, then replace with their own proprietary backend.
- The BFF/middleware layer is specifically designed to make this swap possible without the frontend noticing.

## Integration approach

Same BFF pattern as planned for RemitONE: Flutter/React Native app → VL-built BFF → Fincode. The BFF abstracts Fincode's API, handles authentication/session management, and translates responses to JSON for the app. When SocialRemit's own backend is ready, only the BFF's downstream integration changes — the app is unaffected.

## API documentation

Public docs: https://docs.fincode.technology/remittance/overview (full index at https://docs.fincode.technology/llms.txt)

**Sandbox:** `https://remitjunction.fincode.software/api/v6/services/` — SocialRemit's tenant is `remitjunction`. Test credentials match Fincode's own documentation (`hello@remitjunction.co.uk`). Sandbox appears to be provisioned and accessible.

Full field-level review pending sandbox access confirmation with Joseph.

## Open items

- Full API review: protocol, auth mechanism, response formats — docs URL now available (see above).
- Feature coverage vs SocialRemit MVP scope: needs mapping once docs are reviewed.
- Whether Fincode handles sanctions screening, PEP screening, and ongoing monitoring natively (required per governance non-negotiables).
- Whether Fincode provides an operational admin portal equivalent to RemitONE's.
- Sandbox/test credentials for integration testing.
- Contract not yet signed by SocialRemit as of 19 May 2026.
