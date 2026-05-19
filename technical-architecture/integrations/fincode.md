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

## Open items

- API documentation not yet received (Joseph to send post-call).
- Protocol details (REST/SOAP, response format, auth mechanism) unknown until docs arrive.
- Exact feature coverage vs RemitONE unknown — needs mapping against SocialRemit's MVP scope once docs are received.
- Contract not yet signed by SocialRemit as of 19 May 2026.
