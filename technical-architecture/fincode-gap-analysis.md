---
type: concept
title: Fincode Gap Analysis — Build scope buckets
tags: [fincode, gap-analysis, scope, estimation, architecture]
sources:
  - ../client-inputs/2026-05-19-governance-notes-v1.md
  - https://docs.fincode.technology/llms-full.txt
  - https://docs.fincode.technology/remittance/overview
  - https://docs.fincode.technology/api/transactions/call-quote
  - https://docs.fincode.technology/api/transactions/create-transaction
  - https://docs.fincode.technology/api/webhooks
last_updated: 2026-05-20
status: draft
---

# Fincode Gap Analysis — Build scope buckets

Based on the Fincode public API documentation (May 2026). Four buckets for proposal and estimation purposes.

> **Sandbox access still needed** — field-level API verification, beneficiary endpoint detail, and dynamic field coverage require SocialRemit's tenant credentials. Items marked with ⚠️ are confirmed from docs but field-level detail pending sandbox review.

---

## Bucket 1 — Fincode native: BFF facade only

Fincode covers the backend capability. VL's work is wiring it up through the BFF: authentication, response mapping, error normalisation, caching where appropriate. No custom business logic needed beyond translation.

| Capability | Fincode endpoint(s) | Notes |
|---|---|---|
| FX quote / pricing | `POST /quote/callQuote` | Real-time rate + fees + recipient amount. Supports inverse calculation (receive-first), promo codes, mobile operator routing. |
| Transaction creation | `POST` (create-transaction) | ACCOUNTPAYMENT, MOBILE_MONEY, CASHPICKUP transaction types. Requires pre-existing sender + recipient customer codes. Idempotency key required. |
| Customer registration | `POST /usermanagement/register-customer` | firstName, lastName, email, phone, dob, address, customerType (INDIVIDUAL/BUSINESS). RSA payload encryption supported. |
| Customer profile (get/edit) | `GET /usermanagement/profile`, `PUT /usermanagement/profile-edit` | BFF calls on behalf of authenticated user. |
| Session management (Fincode side) | Login / logout / refresh-token | BFF holds Fincode JWTs server-side; app never touches Fincode directly. |
| Transaction PIN + login PIN | `POST /usermanagement/create-transaction-pin`, `POST /securitymanagement/create-user-pin` | Created in Fincode; BFF orchestrates when to prompt. |
| OTP generation + verification | `GET /securitymanagement/generate-and-send-otp-toemail/{email}`, `POST /securitymanagement/verify-login-otp` | Fincode sends OTP by email; BFF triggers. |
| Beneficiary management ⚠️ | Create / update / list beneficiaries | Bank account + mobile money. Validation handled by Fincode. Full endpoint detail needs sandbox. |
| Supported payment methods + fees | `POST /paymentmanagement/supported-payment-methods`, `POST /paymentmanagement/payment-methods-charges` | Returns available methods per corridor + transaction type, with fees. BFF caches. |
| Wallet payment | `POST /paymentmanagement/makepaymentfromwalletaccount` | Pay transaction from Fincode wallet balance. |
| Manual bank transfer flow | `PUT /paymentmanagement/bank-iwillpaylater-wallet`, `POST /paymentmanagement/notify-bank-transfer-payment` | Customer marks "I will pay later" via bank and confirms when sent. BFF orchestrates awaiting state. |
| Card top-up via payment token | `POST /paymentmanagement/processpaymentwithpaymenttoken` | Tokenised card flow: third-party gateway SDK tokenises card on-device → token passed to BFF → BFF calls Fincode with `paymentGatewayRef` + `supportedPaymentGatewayProvider`. Raw card data never touches VL servers. VL is out of PCI-DSS scope. Supported gateways: `SECURE_TRADING` (TrustPayments), `STRIPE_ACH` (Stripe), `RAVE_FLUTTERWAVE`, `POLI_PAYMENT_API`, `COINBASE_PAYMENT_API`. UK candidates: TrustPayments or Stripe. **Need to confirm which gateway is active on SocialRemit's Fincode tenant.** |
| Awaiting payments list + actions | `GET /paymentmanagement/awaiting-payments`, `POST /paymentmanagement/awaiting-payment-actions` | Mark paid or cancel a pending bank transfer. |
| Transaction history / ledger | `GET /ledger/account-ledger-history/{account_id}/{page}/{size}` | Paginated, with executionDate, ledgerType, amount, newBalance. |
| Account balance | `GET /ledger/account-balance/{account_id}` | Current balance retrieval. |
| KYC document submission ⚠️ | `POST /documentmanagement/attach-documents` | Attach identity documents to customer profile. Relationship to Sumsub TBD — see Bucket 3. |
| Compliance / awaiting requirements check | `GET /compliance/awaiting-compliance-requirements` | Check what KYC is still outstanding for the current user. |
| KYC requirements by country + trigger point | `GET /complaince/kyc-requirements-by-isocountry/{countryIso}/{triggerPoint}` | Returns what's required per country and trigger (first transaction, threshold, etc.). BFF uses to route KYC flow. |
| Sanctions + PEP screening | Built into Fincode transaction flow | OFAC, EU, UN lists + PEP database. Results included in webhook payload (`compliance_status`, `sanction_screening_results`). |
| Webhooks (transaction lifecycle) | `PAID`, `FAILED`, `CANCELLED`, `kyc.verification.completed`, `payment.received` | Terminal-state only. BFF receives, deduplicates, and dispatches downstream (notifications, state updates). |
| Dynamic fields | `GET /dynamicfields/dynamic-fields-group/{processGroupCode}` | Corridor-specific form requirements. BFF fetches and caches; app renders dynamically. Equivalent to RemitONE's UISettings. |
| Payout points / cash pickup locations | `POST /branches/listpayoutpoints`, `POST /branches/listpayoutCenter`, etc. | List available cash pickup locations. |
| Countries + currency pairs ⚠️ | (per overview: 100+ countries, 50+ currencies) | Full corridor/currency list needs sandbox confirmation. |
| Account activation / deactivation | `GET /usermanagement/activate-user-account/{id}` | Admin operation via BFF. |
| Password reset / change | `GET /securitymanagement/reset-password/{email}`, `PUT /securitymanagement/change-password` | Standard account management. |

---

## Bucket 2 — VL must-build: platform does not work without this

These have no Fincode coverage. Every item is a hard dependency for the MVP to be functional.

### Mobile application (React Native or Flutter)
Fincode has no mobile SDK, no white-label app, no UI components. VL builds the entire mobile app: all screens, navigation, state management, animations, app store deployment.

### BFF / Control Layer
The orchestration middleware itself. The entire layer is VL-built:
- All Fincode API calls routed through here; app never hits Fincode directly
- JSON/REST surface for the app (Fincode's API is not app-friendly raw)
- Session lifecycle: Fincode JWT acquisition, storage, refresh, revocation
- Dynamic field caching (avoid repeated Fincode calls for form config)
- Error normalisation across all Fincode error codes → consistent app-facing errors
- Retry and timeout handling with idempotency key management
- Webhook receiver endpoint + deduplication on reference field (Fincode can re-deliver)
- Provider abstraction interfaces — all Fincode calls behind internal service interfaces so that swapping Fincode → Transpara requires only BFF changes, zero app changes

### Progressive KYC routing logic
Fincode tells you what KYC is required per country and trigger point. The BFF decides *when* to trigger which level based on transaction amount, cumulative user volume, and risk signals. This is FCA-mandated business logic that lives entirely in the BFF:
- Threshold tracking per user
- Routing: when to show Sumsub SDK, when to gate a transaction behind further verification
- State machine: onboarding → basic → enhanced CDD levels
See Bucket 3 for the Sumsub/Fincode KYC design question.

### Transaction state machine
Fincode webhooks only fire on terminal states (PAID/FAILED/CANCELLED). The BFF needs to maintain a local transaction state model covering intermediate states (submitted, processing, payout-pending) so the app can show meaningful status screens without polling endlessly.

### SocialRemit's internal database
Governance non-negotiable: "own the internal data model." The BFF must maintain its own database (PostgreSQL or equivalent) storing:
- Customer profile mirror (enriched beyond what Fincode stores)
- KYC progression state (which level reached, when, by which trigger)
- Transaction records with SocialRemit's internal reference model (decoupled from Fincode references)
- Webhook event log (for deduplication, replay, and audit trail)
- Reward and referral state (see Bucket 4)
This is the continuity layer for the Fincode → Transpara migration. Without it, migrating means losing all historical data visibility.

### Fincode abstraction / provider exit ramp
The internal service interfaces in the BFF must be designed so Fincode is swappable. This is architectural design work upfront — not just coding — that shapes every integration decision made during the build. Deferring this design decision creates expensive rework later.

### Card top-up — gateway SDK integration (mobile app side)
Fincode's tokenised payment flow (`processpaymentwithpaymenttoken`) requires a third-party payment gateway SDK to be integrated in the mobile app for card capture and tokenisation. The SDK renders a secure card input UI, handles card data entirely client-to-gateway, and returns a token. VL integrates the SDK and wires the token through the BFF to Fincode. This is a contained piece of work — a single payment screen with the gateway's native card widget. **Gateway to be confirmed with SocialRemit/Fincode** (TrustPayments or Stripe most likely for UK).

### App authentication layer (device-side)
Fincode handles credential verification server-side. The mobile app must implement:
- Secure session token storage (Fincode JWT from BFF, stored in device keychain / encrypted storage)
- Device binding
- Biometric unlock (FaceID / TouchID)
- PIN login with lockout
- App-level session expiry and re-auth flow

### CI/CD pipeline and environments
Governance delivery non-negotiable: dev / staging / production environments with structured deployment pipeline and rollback capability. Includes: infrastructure-as-code, environment secrets management, deployment automation, app store build pipeline. This is DevOps scope that must be in the estimate.

### Observability baseline
Governance operational non-negotiable: "critical failures must be detectable internally before customers report them." Minimum viable: structured logging, CloudWatch dashboards, alerts on error rate, API latency, webhook delivery failures. Without this, SocialRemit cannot operate the platform.

---

## Bucket 3 — Needs discussion before we can scope or price

These items cannot be cleanly estimated without a decision on approach. They should be agenda items for the next call with Joseph and Paul.

### 1. Sumsub vs Fincode KYC — who handles what?

Fincode has a built-in KYC engine (document submission, CRA form, external screening via `continue-enrolment`). SocialRemit has separately contracted Sumsub for identity verification. These overlap. Three architecturally distinct options:

| Option | Description | Implication for VL |
|---|---|---|
| **A — Sumsub only** | Sumsub SDK in-app for document capture + liveness check; BFF passes verified status to Fincode via admin verify endpoint | Cleanest UX; VL integrates Sumsub SDK + manages verification state in BFF. Need to confirm Fincode accepts external verification signal. |
| **B — Fincode native KYC only** | Use Fincode's `attach-documents` + `continue-enrolment` flow; Sumsub contract may be redundant | Simpler integration; need to confirm what external provider Fincode's `continue-enrolment` calls and whether it meets SocialRemit's UX expectations. |
| **C — Split** | Sumsub handles document capture + liveness; Fincode handles AML/sanctions/PEP screening | Both integrations needed; BFF orchestrates both. Most compliance-complete but highest complexity. |

This decision affects: BFF scope, SDK in-app, onboarding UX flow, and compliance documentation for FCA. **Must be resolved before estimation.**

### 2. Operational admin portal — day-one requirement or deferred?

Fincode provides raw admin APIs (customer search, transaction lookup, AML rule management, employee management). What it does NOT provide is a ready-to-use operational dashboard. For a live remittance business, the operations team needs to:
- Look up customers and transactions in real time
- Manually review flagged transactions
- Manage failed payouts
- Override or cancel transactions

Options:
- **A — Fincode admin portal exists** (needs confirmation from Fincode directly — their documentation does not clearly describe a web admin portal)
- **B — Retool / internal tool** built on top of Fincode admin APIs (fast to build, cheaper than bespoke)
- **C — Custom admin portal** built by VL (full control, higher cost)
- **D — Defer** (accept operational risk for first weeks post-launch; Joseph's team manages manually)

Joseph's governance doc §26 says "operational blindness is a major business risk" informed by his UnityLink experience. Option D is unlikely to be acceptable.

### 3. Push notifications — MVP or Phase 2?

The governance doc (§14) describes customer communication as "a core operational and behavioural component" including OTP delivery, transactional notifications (transaction sent/received/failed), and onboarding reminders. These were Phase 2 in the Dec 2025 proposal (RemitONE had no webhook support).

Fincode does fire webhooks (`transaction.completed`, `transaction.failed`). The BFF can receive these and forward to FCM/APNs. The question is whether SocialRemit needs push notifications at go-live or can operate with email + in-app status only for the first weeks.

**Recommendation:** Transactional push (send confirmed, send failed) should be MVP — users expect it from a money transfer app and it directly affects trust. Behavioural nudges (inactivity, referral prompts) can be Phase 2.

---

## Bucket 4 — Separate pricing: modular/shopping list

These items are desirable and referenced in the governance doc, but are not required for the platform to be functional and transact. They should be broken out as priced line items so SocialRemit can choose what to include, defer, or descope depending on budget and timeline.

| Item | Description | Priority signal from governance doc |
|---|---|---|
| **Open banking top-up** | Account-to-account instant top-up (GoCardless VRP, TrueLayer Pay by Bank, or Yapily). No Fincode coverage — separate provider integration required. Not a blocker for MVP launch; card + manual bank transfer cover the deposit requirement at go-live. | Optional post-launch enhancement |
| **Rewards & referral engine** | Welcome bonuses, referral attribution, reward eligibility/release logic, abuse prevention. Entirely VL-built — no Fincode coverage. | §16: "core behavioural infrastructure" — high priority but not a go-live blocker |
| **Analytics integration** | Mixpanel / PostHog / Firebase Analytics in-app + BFF event forwarding. Onboarding funnel, transaction funnel, retention. | §17: MVP optional at minimum |
| **Enhanced observability** | Datadog / Grafana / PagerDuty on top of CloudWatch baseline. Operational dashboards, SLA alerting, webhook monitoring. | §25–26: "major business risk" — baseline included in Bucket 2; this is the enhanced tier |
| **Admin / operational portal** | Retool or custom dashboard on Fincode admin APIs for customer ops, transaction management, manual compliance review. | §26: Joseph's "operational blindness" concern — see Bucket 3 for approach discussion |
| **Event-driven behavioural engine** | Configurable triggers (KYC completed → send bonus, first transfer → reward, inactivity → nudge). Requires event bus and workflow config layer. | §19: MVP foundations, but configurable automation is Phase 2 |
| **PDF statement generation** | BFF-generated transaction history PDFs. Was Phase 2 in Dec 2025 proposal. | Low priority; deferred |
| **Multi-language support** | App copy in multiple languages. Joseph's UX prototype includes language selection on onboarding. | Not confirmed as MVP requirement |
| **SR Tribe / community features** | Future gamification, loyalty tiers, community engagement concepts. | §16: explicitly future |
| **CRM integration** | Zendesk / Intercom connection to customer profile + transaction history. For support team operations. | §18: future |
| **Future Transpara integration planning** | Architecture planning doc + BFF interface specification for the Fincode → Transpara migration. A deliverable VL could produce alongside MVP delivery. | Strategic — not operational MVP |

---

## Must-resolve before estimation can be finalised

1. **Sumsub vs Fincode KYC** — approach determines BFF scope and in-app SDK work (Bucket 3, item 1)
2. **Card gateway selection** — which `supportedPaymentGatewayProvider` is active on SocialRemit's Fincode tenant (TrustPayments vs Stripe)? Determines which mobile SDK to integrate. Small decision but needs confirming with Joseph/Fincode.
3. **Admin portal — day-one or deferred?** — if day-one, adds scope (Bucket 3, item 2)
4. **Push notifications — MVP or not** — affects notification service scope (Bucket 3, item 3)
5. **Sandbox credentials** — `remitjunction.fincode.software` sandbox appears to be available; VL needs confirmed access to verify field coverage, dynamic fields, and beneficiary endpoint detail
6. **Corridors confirmed** — specific destination countries determine payout rails, dynamic field sets, and KYC requirements in scope
