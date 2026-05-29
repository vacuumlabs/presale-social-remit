---
type: integration
title: Fincode — Integration Reference
tags: [fincode, integration, white-label, remittance]
sources:
  - ../../client-inputs/2026-05-19-call-transcript.md
  - ../../client-inputs/2026-05-28-joseph-qa-response.md
  - https://docs.fincode.technology/remittance/overview
  - https://docs.fincode.technology/llms-full.txt
last_updated: 2026-05-29
status: active
---

# Fincode — Integration Reference

Fincode is SocialRemit's chosen white-label remittance backend as of May 2026, replacing RemitONE. See [`remitone.md`](./remitone.md) for the superseded provider. Full capability mapping is in [`technical-architecture/fincode-gap-analysis.md`](../fincode-gap-analysis.md).

## Why Fincode over RemitONE

Per the 19 May 2026 call, "Penny" (SocialRemit colleague) reviewed RemitONE post-December 2025 and recommended switching. Fincode is more expensive than RemitONE but significantly more collaborative — they work with clients rather than just providing a service.

## Confirmed facts (as of 2026-05-29)

- SocialRemit plans to use Fincode for **12 months only**, then replace with their own proprietary backend (Transpara).
- The BFF/middleware layer is specifically designed to make this swap transparent to the frontend.
- **Card top-up gateway:** Trust Payments (`SECURE_TRADING`) — already integrated in Fincode; to be enabled on the SR tenant.
- **Open banking gateway:** Volume — already integrated in Fincode; to be enabled on the SR tenant.
- **Manual bank transfer** — supported natively by Fincode (`bank-iwillpaylater-wallet` / `notify-bank-transfer-payment` flow).
- **Sanctions + PEP screening** — handled natively in Fincode's transaction flow (OFAC, EU, UN lists + PEP database).
- **KYC document submission** — Fincode has `attach-documents` endpoint; integration with Sumsub is either direct or via Fincode's Sumsub layer. Sumsub is the confirmed KYC provider.
- **Operational tooling** — Fincode provides back-office functionality covering payments, wallets, and transaction management. Combined with Sumsub's compliance dashboard, expected to cover most go-live ops needs.

## Integration approach

Flutter/React Native app → VL-built BFF → Fincode. The BFF abstracts Fincode's API, handles authentication/session management, and translates responses to a clean JSON API for the app. All Fincode calls are routed through the BFF; the app never hits Fincode directly. When Transpara is ready, only the BFF's downstream integration changes.

## API documentation

- Public docs: https://docs.fincode.technology/remittance/overview
- Full LLM-friendly docs: https://docs.fincode.technology/llms-full.txt
- Quote API: https://docs.fincode.technology/api/transactions/call-quote
- **Sandbox:** `https://remitjunction.fincode.software/api/v6/services/` — SocialRemit's tenant is `remitjunction`.

## Still open

- **Sandbox credentials** — field-level API verification requires confirmed test credentials from Joseph/SocialRemit.
- **Fincode technical walkthrough** — Joseph has requested VL schedule a session with Fincode to assess operational tooling, webhooks, and any lightweight admin gaps before finalising MVP scope.
- **Contract status** — Fincode contract was "under review" as of 19 May 2026; confirmation of signing not yet received.
