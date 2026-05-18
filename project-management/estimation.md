---
type: status
title: Estimation — December 2025
tags: [estimation, commercial, scope, budget]
sources:
  - ../team-inputs/2025-12-17-fe-build-proposal.md
last_updated: 2026-05-18
status: active
---

# Estimation — December 2025

Estimates from the December 2025 proposal. Source: [`team-inputs/2025-12-17-fe-build-proposal.md`](../team-inputs/2025-12-17-fe-build-proposal.md) and estimation spreadsheet (GDrive: `1dtFIsOFSStKSoILUpYtVtwdBTtDf7JlEa4jMRNoJEZQ`).

Contract type offered: **Time & Material**, with stated ±30% range.

## Option 1 — FE + BFF delivery only

| Role | Seniority | FTE | Days | MDs |
|------|-----------|-----|------|-----|
| Full-stack Developer | Senior | 1 | 50 | 50 |
| FE Developer | Mid | 1 | 50 | 50 |
| Product Manager | Senior | 0.5 | 50 | 25 |
| Product Designer | Lead | 0.5 | 50 | 25 |
| Project Manager | Senior | 0.5 | 50 | 25 |
| **Total** | | | | **175 MD** |

**Estimated fee: £118,125**

## Option 2 — FE + BFF + parallel Discovery track

Discovery track runs in parallel with delivery and produces: post-MVP feature map, product docs (epics/stories), product roadmap, vendor list, wireframes/prototype.

| Role | Seniority | FTE | Days | MDs |
|------|-----------|-----|------|-----|
| Tech Lead | Lead | 0.5 | 50 | 25 |
| Product Manager | Senior | 0.5 | 50 | 25 |
| Product Designer | Lead | 0.5 | 50 | 25 |
| **Discovery subtotal** | | | | **75 MD** |

**Discovery fee: £50,625**
**Combined total (Option 2): £168,750**

## Component breakdown (from estimation spreadsheet)

### Mobile App — 55 MDs

| Area | Scope | MDs |
|------|-------|-----|
| App foundation & infra | Repo, shell, navigation, theming, i18n, secure storage, env config | 8 |
| Onboarding & authentication | Signup (quick reg), OTP, login (pwd/PIN), 2FA, reset password | 8 |
| Progressive KYC & profile | KYC states, dynamic forms, profile edit, blocking rules | 3 |
| Dashboard & wallets | Wallet list, balances, activity, rates snippet | 3 |
| Beneficiaries | List/search, add/edit, dynamic fields, validation | 3 |
| Send money flow | Calculator, delivery method, fees, create/confirm tx, OTP | 8 |
| Wallet top-ups | Add money, charges, instructions, pending/completed | 8 |
| Transactions & statements | History, filters, details, PDF download | 3 |
| Support & settings | Help, contact support, settings, logout | 3 |
| QA, polish & store prep | Bug fixing, edge cases, perf, store readiness | 8 |

### BFF Layer — 43 MDs

| Area | Scope | MDs |
|------|-------|-----|
| Core service setup | Project setup, API structure, logging, envs | 8 |
| RemitONE integration core | XML↔JSON mapping, RSA encryption, sessions, retries | 12 |
| Auth & user lifecycle APIs | Register, confirm, login, PIN login, 2FA, logout | 3 |
| Profile & KYC APIs | Get/update profile, KYC state logic, UISettings cache | 3 |
| Beneficiaries APIs | List, create, update, destination metadata | 3 |
| Transactions APIs | Quote, create, confirm, instructions, list/details | 3 |
| Wallet APIs | Wallets, activity, load wallet, load status | 3 |
| Cross-cutting concerns | Infra setup, rate limiting, monitoring, alarms, versioning | 8 |

## Assumptions and caveats

- Estimates are ballpark (±30%); a T&M contract was offered, not fixed-price.
- One environment initially (prod-like); additional environments would add cost.
- RemitONE UISettings complexity and corridor count could shift the beneficiary and transaction work significantly.
- These estimates were based on React Native. A Flutter re-estimation would be required if SocialRemit's May 2026 Flutter preference is confirmed.
- No admin portal build included (assumed provided by RemitONE).
- No card issuance, webhooks, or Phase 2 features included.
