---
type: concept
title: Fincode Gap Analysis — What Fincode covers vs what VL must build
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

# Fincode Gap Analysis

What Fincode covers natively, what VL must build, and what requires custom orchestration on top of Fincode APIs. Based on the public Fincode API documentation (May 2026). Sandbox access and full API review with SocialRemit's tenant credentials will be needed to confirm coverage at the field level.

---

## Integration model

Fincode offers two integration modes. SocialRemit's architecture sits in between:

| Mode | Description | SocialRemit approach |
|---|---|---|
| **Full Journey** | Fincode manages everything — customer onboarding through payout | Not used — SocialRemit owns the customer experience layer |
| **Transaction-Only** | Integrator manages customers, passes transactions directly | Partial — SocialRemit owns the UX and orchestration, but uses Fincode's customer and KYC APIs |

SocialRemit's architecture is essentially "Full Journey with a VL-built Control Layer in front." The BFF maps SocialRemit's internal model to Fincode's API.

---

## What Fincode covers natively

### Authentication & session management ✅
- JWT login / logout / token refresh
- OTP generation and email delivery
- Password management (reset, change)
- Transaction PIN and login PIN creation
- Account locking on failed login attempts
- RSA payload encryption support

**VL implication:** Fincode's auth tokens are a backend concern only. The mobile app authenticates against the BFF, which holds Fincode credentials server-side. The app never talks to Fincode directly.

---

### Customer registration & profile ✅
- `POST /usermanagement/register-customer` — creates a customer record in Fincode
- Required at registration: firstName, lastName, email, phone (international), dob (min 18), address, customerType (INDIVIDUAL / BUSINESS), password
- Profile retrieval, editing, activation/deactivation, profile picture upload
- Customer search by name or phone (admin operation)

**VL implication:** The BFF calls Fincode's register endpoint as part of the onboarding flow. Fincode stores the customer record. However, SocialRemit's governance principles require owning the internal data model — so the BFF/database must mirror key customer state (see Gaps section below).

---

### KYC & compliance ✅ (partial — see design risk below)
- `POST /documentmanagement/attach-documents` — submit KYC documents
- `POST /admin/compliance/submit-cra` — Customer Risk Assessment form submission
- `GET /admin/compliance/continue-enrolment` — triggers external screening, returns URLs for external verification flow
- `GET /compliance/awaiting-compliance-requirements` — checks what KYC is still outstanding for the authenticated user
- `GET /complaince/kyc-requirements-by-isocountry/{countryIso}/{triggerPoint}` — returns KYC requirements by country and trigger point (e.g., first transaction, threshold crossed)
- AML rule management: list, activate, deactivate, configure
- KYC rule management: add, edit rules

**Compliance screening included:** Fincode's overview states it screens against OFAC, EU, and UN sanctions lists, PEP databases, unusual activity patterns, and applies dynamic risk assessment. The webhook payload includes `compliance_status` and `sanction_screening_results` fields.

**VL implication:** Fincode has a KYC and AML engine. However, SocialRemit has separately contracted Sumsub for KYC. **This creates a design question that must be resolved before estimation** — see Design Risks section.

---

### FX quote / pricing ✅
- `POST /quote/callQuote` — real-time FX rate + fees + total cost + recipient amount
- Supports inverse calculation (calculate send amount from receive amount)
- Takes: principalAmount, currency pair, paymentType, transactionType, destinationCountry, promoCode, mobileOperator
- Returns: guaranteed rate, recipient amount, fee breakdown

**VL implication:** The BFF calls this for the FX calculator and the send money quote screen. Response shaping to the app format is BFF responsibility.

---

### Transaction creation ✅
- `POST /remittance/create-transaction` (or equivalent) — initiates remittance
- Supported transaction types: ACCOUNTPAYMENT (bank deposit), MOBILE_MONEY, CASHPICKUP, WALLET, BILL_PAYMENT
- Requires pre-existing sender and recipient customer codes

**VL implication:** The BFF creates the transaction in Fincode. Must hold idempotency keys to prevent duplicates. Error normalisation is BFF responsibility.

---

### Payment collection ✅ (partial — see open banking gap below)

**Card payment (native):**
- `POST /paymentmanagement/process-card-payment` — direct card processing in Fincode
- Takes raw PAN, expiry, CVV — Fincode handles card processing natively through their own processor relationships

**Wallet payment:**
- `POST /paymentmanagement/makepaymentfromwalletaccount` — pay from Fincode wallet balance

**Payment token (third-party gateways):**
- `POST /paymentmanagement/processpaymentwithpaymenttoken` — fund via external payment token
- Supports: Stripe ACH, Coinbase, Poli, Secure Trading (TrustPayments), Flutterwave, Custom POS

**Manual bank transfer flow:**
- `PUT /paymentmanagement/bank-iwillpaylater-wallet/{pcn}/{payableType}` — marks as pending bank transfer
- `POST /paymentmanagement/notify-bank-transfer-payment` — customer confirms they've sent the bank transfer manually

**Supported payment methods query:**
- `POST /paymentmanagement/supported-payment-methods` — returns available methods with fees and metadata for a given transaction type and corridor

---

### Beneficiary management ✅
- Confirmed in Fincode overview: create, manage, and retrieve beneficiary profiles
- Bank account validation and mobile money phone number validation
- Both ACCOUNTPAYMENT and MOBILE_MONEY beneficiary types supported
- _(Specific endpoint details 404 in public docs — requires sandbox to confirm full field set)_

---

### Transaction history & ledger ✅
- `GET /ledger/account-ledger-history/{account_id}/{page}/{size}` — paginated ledger with executionDate, ledgerType, transactionAmount, newBalance
- `GET /ledger/account-balance/{account_id}` — current balance
- Ledger history by idempotency key (audit trail)

---

### Webhooks ✅
- Events: `transaction.created`, `transaction.completed`, `transaction.failed`, `kyc.verification.completed`, `payment.received`
- Terminal status webhooks: PAID, FAILED, CANCELLED
- Payload includes: eventType, reference, status, 23+ fields of transaction metadata including compliance status and sanction screening results
- **Important:** Same event may be delivered multiple times — BFF must deduplicate on reference

---

### Dynamic fields ✅
- `GET /dynamicfields/dynamic-fields-group/{processGroupCode}` — returns structured fields required for a specific process
- Analogous to RemitONE's UISettings — Fincode drives form requirements dynamically per corridor/transaction type

**VL implication:** BFF must fetch and cache dynamic fields. App renders forms based on BFF-provided field definitions. Same pattern as RemitONE, different API.

---

### Payout point / cash pickup support ✅
- List payout points, pay centres, payment collectors by address
- Payout point branches

---

### Sandbox environment ✅
- Sandbox base URL available: `https://{domain}.fincode.software/api/v6/services/`
- Test credentials, test bank account, test card data provided in documentation
- Separate from production (`*.fincode.tech`)

---

### Admin / back-office APIs ✅ (raw APIs only — no portal confirmed)
- Customer list, search, profile lookup
- Employee management
- Organisation preferences
- AML/KYC rule configuration
- Fee management
- Connector management

---

## What VL must build entirely

### Mobile application (React Native or Flutter) 🔴 VL builds
All screens, navigation, state management, biometric unlock, secure session storage, device binding. Fincode has no mobile SDK or white-label app.

---

### BFF / Control Layer 🔴 VL builds
The entire orchestration middleware. Includes:
- API translation (Fincode's API → clean JSON/REST for the app)
- Session and token lifecycle management (Fincode JWTs held server-side)
- Dynamic field caching (equivalent to RemitONE's UISettings caching)
- Error normalisation across all Fincode error codes
- Retry and timeout handling for all Fincode calls
- Idempotency key management
- Progressive KYC threshold logic (which trigger point to apply per user + transaction amount)
- Fincode abstraction layer (provider-portable interfaces so Transpara replacement requires only BFF changes)

---

### Open banking top-up 🔴 VL builds + integrates
**This is a confirmed gap.** Fincode's bank transfer flow is a manual "I will pay later" notification model, not open banking. There is no open banking (account-to-account, consent-based, instant) integration in Fincode's API.

For open banking top-up (which is in MVP scope and a key low-friction deposit method), VL must integrate a separate open banking provider — GoCardless, TrueLayer, or Yapily. This is additional integration scope not present in the Dec 2025 estimate in the same form.

---

### Push notifications 🔴 VL builds + integrates
Fincode has webhook events but no push notification delivery to mobile devices. VL must integrate Firebase Cloud Messaging (FCM) / Apple Push Notifications (APNs) via a notification service (Firebase, OneSignal, or similar). The BFF receives Fincode webhooks, processes them, and triggers push notifications to the app.

---

### Analytics 🔴 VL builds + integrates
Fincode has no analytics. Mixpanel, PostHog, Firebase Analytics, or Amplitude integration must be built into the mobile app (client-side events) and optionally the BFF (server-side events). Per governance doc §36, this is an MVP priority.

---

### Rewards and referral engine 🔴 VL builds
Fincode has no rewards or referral capability. Per governance doc §16, rewards and referrals are "core behavioural infrastructure." This includes: welcome bonuses, referral attribution, reward eligibility logic, reward release logic, abuse prevention. All of this lives in the BFF / a dedicated service, with its own data store.

---

### Observability infrastructure 🔴 VL builds + configures
Fincode does not provide operational dashboards. Per governance non-negotiables: VL must implement monitoring, logging, alerting, API performance dashboards, webhook monitoring, and payout visibility. Baseline: CloudWatch + structured logging. Enhanced: consider Datadog, Grafana, or similar.

---

### Internal data model / SocialRemit's own database 🔴 VL designs + builds
Governance principle: "own the internal data model." The BFF must maintain SocialRemit's own database records for:
- User profiles (mirrored from Fincode, enriched)
- KYC state and progression history
- Transaction records (with SocialRemit's internal reference model)
- Reward and referral state
- Audit logs
- Webhook event log (for deduplication + replay)

This is essential for the Fincode → Transpara migration: when Fincode is replaced, SocialRemit's internal data model is the continuity layer.

---

### CI/CD pipeline and environments 🔴 VL builds + configures
Three environments (dev / staging / prod) with structured deployment pipelines and rollback. Per governance delivery non-negotiables. This is DevOps scope that must be in the estimate.

---

## What requires BFF orchestration on top of Fincode (not purely Fincode-native)

### Progressive KYC routing ⚠️ BFF logic
Fincode provides the KYC requirements API (`kyc-requirements-by-isocountry/{countryIso}/{triggerPoint}`), but the decision of *when* to trigger which level of KYC (based on transaction amount, cumulative volume, risk signals) is business logic that lives in the BFF. The BFF must track where each user is in the KYC lifecycle and decide when to gate transactions behind further verification.

### Sumsub / Fincode KYC orchestration ⚠️ Design question — MUST RESOLVE BEFORE ESTIMATION
SocialRemit has contracted Sumsub for identity verification. Fincode has its own KYC flow (`attach-documents`, `continue-enrolment`, `submit-cra`). These are potentially redundant or complementary. Three possible architectures:

| Option | Description | Implication |
|---|---|---|
| A — Sumsub only | Use Sumsub SDK for all identity verification; pass verification status to Fincode via its `verify-customer` admin endpoint | Sumsub is the truth for KYC; Fincode is informed of the result. Simplest if Fincode accepts external verification signal. |
| B — Fincode only | Use Fincode's native KYC flow (which may invoke external providers via `continue-enrolment`) | Sumsub contract may be redundant or used differently. Need to confirm what provider Fincode's external screening uses. |
| C — Split responsibility | Sumsub handles identity document verification + liveness; Fincode handles AML/sanctions/PEP screening | Two separate flows in the BFF; Sumsub SDK in the app for document capture; Fincode compliance APIs for AML. |

**This needs to be confirmed with Joseph/Fincode before the architecture can be finalised.** The wrong choice here creates double-KYC friction for users or a compliance gap.

### Card payment PCI-DSS scope ⚠️ Risk
Fincode's card payment API accepts raw PAN, expiry, and CVV. This means if the BFF routes card payment requests through Fincode, the BFF is handling raw card data — which creates PCI-DSS scope for VL's infrastructure. This must be reviewed: either Fincode's card processing is handled entirely client-side (Fincode-provided JS widget or equivalent), or VL's servers are in PCI scope. Checkout.com, Stripe, and similar providers solve this via tokenisation (client-side tokenises the card, only a token touches the server). **PCI scope should be discussed with SocialRemit's compliance team and Fincode before the architecture is locked.**

### Transaction state management ⚠️ BFF logic
Fincode webhooks only fire on terminal states (PAID, FAILED, CANCELLED). Intermediate states (processing, pending payout, etc.) must be polled or managed by the BFF. The BFF must maintain a local transaction state machine that reconciles app state with Fincode webhook events.

---

## Confirmed gaps (items in MVP scope with no Fincode coverage)

| Feature | In MVP scope? | Fincode covers? | VL must provide |
|---|---|---|---|
| Open banking top-up | Yes | ❌ No | Third-party integration (GoCardless/TrueLayer) |
| Push notifications | Yes (governance §14) | ❌ No | FCM/APNs + notification service |
| Analytics tracking | Yes (governance §17) | ❌ No | Mixpanel/PostHog/Firebase |
| Rewards & referrals | Yes (governance §16) | ❌ No | Custom service in BFF |
| Observability dashboards | Yes (governance §25) | ❌ No | CloudWatch + tooling |
| Internal data model / own DB | Yes (governance §20) | ❌ No | PostgreSQL or equivalent in BFF |
| CI/CD pipeline (3 envs) | Yes (governance §29) | ❌ No | DevOps work |
| Biometric unlock | Yes (MVP scope) | ❌ No | Mobile app native (FaceID/TouchID) |
| Admin/operational portal | TBD | ⚠️ APIs only | Custom dashboard or Retool/similar on top of Fincode admin APIs |
| PDF statements | Phase 2 | ❌ No | BFF-generated (deferred) |
| Cancel/reverse transfer | Phase 2 | ❌ Not confirmed | Deferred |
| Scheduled transfers | Phase 2 | ❌ No | Deferred |

---

## Items that appeared in Phase 2 (Dec 2025) but may now be in MVP scope

The governance doc expands scope relative to the December 2025 proposal. The following were previously deferred but are now flagged as MVP or near-MVP:

| Item | Dec 2025 status | Governance doc signal | Action needed |
|---|---|---|---|
| Push notifications | Deferred | §14: "core operational + behavioural component" | Confirm with Joseph — likely MVP |
| Analytics | Deferred | §17: MVP optional at minimum | Confirm phasing |
| Rewards/referrals | Deferred | §16: "core behavioural infrastructure, not marketing" | Confirm if MVP or Phase 1.5 |
| Webhooks (real-time status) | Deferred (RemitONE-specific) | Fincode webhooks available natively | Include in MVP — changes the delivery confirmation flow |

---

## What must be confirmed with Fincode / Joseph before estimation

1. **Sumsub vs Fincode KYC** — which handles what? Is Fincode's `continue-enrolment` pointing to Sumsub, or a different external provider?
2. **Card processing via Fincode** — is PCI-DSS scope manageable (client-side tokenisation available)? Or do we need Checkout.com/Volume alongside Fincode?
3. **Open banking provider selection** — GoCardless vs TrueLayer vs Yapily; has SocialRemit decided?
4. **Does Fincode provide an operational admin portal** beyond raw APIs? If not, what does SocialRemit need for day-one operations?
5. **Corridor and currency confirmation** — which specific corridors are in MVP? Determines which payout rails and dynamic field sets are in scope.
6. **Sandbox credentials** — VL needs tenant-specific sandbox access to confirm all of the above at the API level.
