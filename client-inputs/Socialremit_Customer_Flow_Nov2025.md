---
type: concept
title: SocialRemit Customer Flow — Nov 2025
tags: [customer-flow, ux, product, screens, remittance]
sources:
  - ../../../Socialremit_Customer Flow Nov 2025.pdf
last_updated: 2026-05-18
status: active
---

# SocialRemit Customer Flow — Nov 2025

Companion summary for `../../../Socialremit_Customer Flow Nov 2025.pdf` (client-authored, immutable).

This document defines the full screen-by-screen UX specification for the SocialRemit mobile app as of November 2025. It covers seven major screen areas.

## 1. Welcome Screen

App logo, Sign Up / Log In options, optional language selection.

## 2. Sign-Up / Log-In

**Sign-up:** Full name, email, phone number, password. Verification via OTP (phone) and email link.

**Log-in:** Email/phone + password, "Forgot Password?" link, Google / Apple SSO, biometric unlock.

## 3. Dashboard / Home

Current balance/wallet amount with quick-action buttons: **Send**, **Add Money**, **Request**. FX calculator widget, multiple wallet balances, and transaction history list.

## 4. Send Money Screen

### A. Calculator
Source country + amount, exchange rate, fees, destination country + received amount, optional notes.

### B. Delivery Method

**Bank Deposit:**
- Choose recipient: search saved contacts, enter manually, or pick from previous recipients.
- Add beneficiary: bank name, account number, first/last name, email (optional), account number/IBAN.
- Confirm & Continue.

**Mobile Money:**
- Choose recipient: search saved contacts, enter name, or pick from previous recipients.
- Add beneficiary: input mobile number → auto-populate name from lookup.
- Save beneficiary / Continue.

### C. Confirmation
Review recipient details, amount, fees; option to add a note.

### D. Payment Method
Credit/debit card, wallet balance, or bank transfer (open banking).

### E. Finalize Transfer
OTP confirmation.

### F. Transaction Success Screen
Confirmation message with transaction ID, estimated delivery time, share receipt / save as PDF, "Send Another" or "Return to Dashboard".

## 5. Footer Navigation

Home | Transactions | Help

## 6. Transactions Tab

Past transactions with filters (date, recipient, status). Status indicators: Pending / Completed / Failed. Clickable for detail view. Download/export statements.

## 7. Account / Profile

**Profile:** Full name, DOB, address, city, postcode, email, phone, country.

**Account limits** and **Account statements** (currency, date range, PDF export).

**Wallets/Cards:** Show PIN, card details, freeze card, Add to Apple Wallet.

**Security:** Password reset, transaction PIN, Face/Touch ID toggle, document uploads, notification preferences (SMS/Email/App), delete account.

**Payments:** Schedule transfers, direct debits, payment requests.

**Support & FAQs:** Help section, contact support.
