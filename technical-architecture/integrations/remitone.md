---
type: integration
title: RemitONE — Integration Reference (superseded)
tags: [remitone, integration, api, white-label, remittance]
sources:
  - ../../client-inputs/Socialremit_Customer_Flow_Nov2025.md
  - ../../client-inputs/2026-05-19-call-transcript.md
last_updated: 2026-05-19
status: superseded
supersedes: null
---

> **Superseded.** SocialRemit switched from RemitONE to **Fincode** after the December 2025 discussions. See [`fincode.md`](./fincode.md). This page is retained for reference — the integration patterns (BFF, XML→JSON translation, RSA encryption, UISettings caching) are likely similar and informed the Fincode approach.

# RemitONE — Integration Reference

RemitONE is SocialRemit's chosen white-label remittance backend. The full API specification (v3.3, March 2020) is at `../../../../RemitONE_Remitter_WebServices_Specification.pdf` (GDrive: `1G0VpKFMQP5Ic9-pZKL1aAnR2ESyLmT95`).

## Protocol

REST-style: all calls are HTTP POST. Responses are XML. Authentication uses a session token obtained via `login` or `loginPin`, passed as a POST variable on every subsequent call. Sensitive fields (passwords, PINs) are RSA-encrypted in an `encrypted_data` envelope.

Base URL pattern: `https://<client-system-url>/remitterws/<GROUP>/<METHOD>`

## API surface summary

### Authentication
`getSeed`, `login`, `loginPin`, `confirmTwoFactorAuthentication`, `requestTwoFactorAuthentication`, `logout`, `forgotPassword`, `changePassword`, `changePin`

### Beneficiary
`getDestinationCountries`, `createBeneficiary`, `updateBeneficiary`, `listBeneficiaries`, `getBeneficiary`, `searchWalletBeneficiary`

### Transactions
`getMobileNetworkOperators`, `getMobileNetworkCreditTypes`, `getUtilityBillCompanies`, `searchUtilityBillCompanies`, `getDeliveryBanks`, `getDeliveryBranchStates`, `getDeliverybranchCities`, `getDeliveryBranches`, `getCollectionPointStates`, `getCollectionPointCities`, `getCollectionPoints`, `getCharges`, `createTransaction`, `confirmTransaction`, `requestTransactionConfirmationCode`, `paymentCleared`, `listTransactions`, `getTransaction`, `getTransactionPaymentInstructions`, `getTempTransaction`

### Rates
`getRates`

### Remitter (user profile)
`getProfile`, `updateProfile`, `uploadProfileKYCVideo`, `getProfileKYCVideo`, `getSourceCountries`, `register`, `confirmRegistration`, `requestRegistrationConfirmationCode`

### Wallet
`getWallets`, `getWalletActivity`, `getLoadWalletCharges`, `getLoadWalletPaymentMethods`, `loadWallet`, `getLoadWalletDetails`, `loadWalletPaymentCleared`, `calculateMoveFundsBetweenWallets`, `moveFundsBetweenWallets`

### UI Settings
`getCarouselImages`, `getCountryPrefixes`, `getChangePasswordSettings`, `getBeneficiaryUISettings`, `getRemitterUISettings`, `getTransactionUISettings`

### Support
`getSupportDetails`, `sendEmailToSupport`

## Key integration constraints

- **XML-only responses** — the BFF must translate all responses to JSON before the app sees them.
- **Dynamic forms via UISettings** — field requirements for registration, beneficiary creation, and transaction creation are driven by `getRemitterUISettings`, `getBeneficiaryUISettings`, and `getTransactionUISettings`. The BFF must cache these (they are slow to fetch and change rarely).
- **RSA encryption** — PIN changes, password changes, and registration require an `encrypted_data` block. The BFF holds the public key and performs encryption server-side; the app never sees RemitONE credentials.
- **Session management** — RemitONE sessions are stateful. The BFF manages the session token lifecycle (login, refresh, logout) and maps it to BFF-issued tokens for the app.
- **Two-step transaction** — `createTransaction` + `confirmTransaction` with optional OTP (`requestTransactionConfirmationCode`). Quote drift between these two steps must be handled (BFF should detect and return a 409 QUOTE_CHANGED error).
- **Progressive KYC** — registration uses `register` (quick registration), then `updateProfile` for progressive KYC data collection. KYC state is managed by RemitONE business rules.

## Features not supported by RemitONE out of the box

The following features from the client's UX spec require custom BFF implementation or are Phase 2:

- Request money / P2P payments
- Direct Debit mandates
- Recurring / scheduled transfers
- Real-time webhooks (RemitONE is poll-based)
- Cancel / reverse transfer
- Card issuance

## API version note

The spec in our possession is v3.3 (March 2020). This is likely not the latest version. SocialRemit should be asked to share the current version of the API docs once a contract is signed.
