---
type: concept
title: Regulatory brief — SocialRemit
tags: [regulatory, compliance, P2]
sources:
  - ../team-inputs/T1-sales-deal-brief.md
  - product-management/domain-research.md
last_updated: 2026-05-19
status: draft
---

# Regulatory brief — SocialRemit

## 1. Key regulatory framework

SocialRemit operates in the UK consumer remittance market as an FCA-regulated Electronic Money Institution. The following bodies and regulations are directly applicable.

**Financial Conduct Authority (FCA)**
The FCA is the primary regulator. SocialRemit holds an EMI licence, which permits it to issue e-money and provide payment services. EMI authorisation is confirmed from the T1 brief and the May 2026 call. _(Confirmed.)_

**Payment Services Regulations 2017 (PSR 2017) / Electronic Money Regulations 2011 (EMR 2011)**
These are the UK implementations of PSD2 and the EMD2 Directive. Key obligations include:
- Safeguarding customer funds (ring-fenced from operational accounts)
- Providing transparent pricing and execution timelines
- Complaint handling and redress obligations
- Strong Customer Authentication (SCA) for payment initiation

**Anti-Money Laundering and Counter-Terrorist Financing (AML/CTF)**
The Money Laundering, Terrorist Financing and Transfer of Funds Regulations 2017 (MLR 2017) apply in full. SocialRemit has confirmed an AML board is in place. Obligations include:
- Customer Due Diligence (CDD) — identity verification at onboarding
- Enhanced Due Diligence (EDD) — triggered for high-value or high-risk customers
- Suspicious Activity Reporting (SAR) to the National Crime Agency
- Transaction monitoring for unusual patterns
Sumsub has been contracted for the KYC/identity verification layer. _(Confirmed.)_

**HM Treasury — Office of Financial Sanctions Implementation (OFSI)**
Cross-border remittance operators must screen senders, recipients, and beneficiary accounts against UK financial sanctions lists. This is a real-time or near-real-time obligation at point of transaction.

**GDPR / UK GDPR**
As a UK company processing personal data of UK residents, the UK GDPR (retained from EU GDPR post-Brexit) applies in full. Key obligations: lawful basis for processing, data subject rights, data minimisation, breach notification (72-hour window to ICO). Data residency for UK user data — whether Fincode's infrastructure stores data in the UK or offshore — is a material question. _(Not confirmed — Fincode API docs outstanding.)_

---

## 2. Constraints most likely to affect this engagement

### 1. Progressive KYC and regulatory thresholds _(High impact — architecture constraint)_
The FCA requires identity verification tied to transaction volume thresholds. SocialRemit's product uses progressive KYC: minimal data collected at onboarding (phone number + OTP), escalating to full CDD as the user approaches regulatory thresholds. The Sumsub SDK integration must implement this correctly — the business logic for threshold tracking and KYC escalation lives in the BFF, not the app. Getting this wrong (too early, too late, or inconsistently applied) is a direct compliance risk for the EMI licence. This affects both architecture design and QA scope.

### 2. Sanctions screening at transaction time _(High impact — integration constraint)_
Every send-money transaction must be screened against UK and potentially UN/EU sanctions lists in real time. If Fincode handles this natively, VL needs to confirm it. If it does not, a sanctions screening integration (e.g., ComplyAdvantage, Dow Jones) must be added to the BFF — this is additional scope not currently in the estimate. _(Status: unconfirmed — Fincode API docs outstanding.)_

### 3. Safeguarding of customer e-money _(Operational — not architecture, but affects go-live sign-off)_
EMI operators must safeguard customer funds in a segregated account or via an insurance/guarantee. This is an operational obligation but relevant to go-live: the FCA could request evidence of safeguarding arrangements before or after launch. SocialRemit's team should own this, but VL should confirm it is in place before go-live, as a failure here would halt operations immediately.

### 4. Data residency and Fincode hosting location _(Medium impact — architecture risk)_
UK GDPR does not prohibit processing personal data outside the UK, but it does require adequate safeguards for international transfers (adequacy decisions, standard contractual clauses, binding corporate rules). If Fincode's API infrastructure sits outside the UK (e.g., in the US or an EEA country without an adequacy decision), the BFF design must not pass personally identifiable information to Fincode beyond what is strictly necessary — or a data transfer mechanism must be in place. This is a question for the Fincode API review. _(Not confirmed.)_

---

## 3. VL's relevant experience

VL has operated in FCA-regulated fintech environments on multiple prior engagements. The team has direct experience with:
- Sumsub SDK integration (KYC/onboarding flows) — directly relevant; VL has pre-built patterns for progressive KYC that can be adapted.
- BFF / middleware design for regulated payment flows — the pattern of isolating compliance-sensitive operations (KYC routing, threshold checking) in the BFF layer is established VL practice.
- PSD2-adjacent open banking integrations (UK and EEA).

VL does not have specific Fincode integration experience (new provider). The regulatory posture of the Fincode platform — whether it is itself FCA-regulated, or a tool used by a regulated firm — needs to be confirmed. _(Gap: Fincode API docs outstanding.)_

---

## Top 3 regulatory factors most likely to constrain architecture or timeline

| # | Factor | Risk |
|---|--------|------|
| 1 | **Progressive KYC thresholds and Sumsub routing logic** | Must be implemented correctly in the BFF; wrong thresholds = compliance breach. Cannot be tested without Sumsub sandbox access. |
| 2 | **Sanctions screening at transaction time** | If not natively handled by Fincode, requires a separate integration — additional scope and timeline impact. Needs Fincode API review to resolve. |
| 3 | **Data residency / Fincode hosting location** | If Fincode stores UK user PII outside the UK, BFF design must minimise data passed to Fincode. Needs Fincode API review to resolve. |
