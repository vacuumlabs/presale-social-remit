---
type: other
title: Social Remit MVP Technology Governance Notes v1
source_type: client-authored
author: Joseph Owusu / Social Remit Technologies
status: active
version: 1
last_updated: 2026-05-19
gdrive_id: 1yx2-eambgF4-xbyE69UQ2oHQbuYuj2Y-
---

# Social Remit MVP Technology Governance Notes v1

_Founder Technical Governance Framework. For MVP Delivery, Vendor Alignment & Architecture Direction._

Shared by Joseph Owusu via email on 19 May 2026. Intended for all technical partners, agencies, and solution architects working on the Social Remit MVP.

---

## 1. Purpose

Defines core technology, architecture, operational, product, and engineering principles to guide the MVP build. Ensures: long-term scalability, operational resilience, migration flexibility, reduced technical debt, maintainable architecture, fintech-grade operational standards, extensible infrastructure foundations, strong customer experience governance, operational visibility, future infrastructure flexibility.

## 2. Product Philosophy

Social Remit is designed around: financial inclusion, trust, operational reliability, emotional customer experience, simplicity, behavioural engagement, long-term customer retention, operational transparency.

Customer experience priorities: clarity, simplicity, accessibility, dignity, transparency, reliability, trust.

## 3. Core Architecture Principle

> "We control the customer experience, orchestration layer, and internal data model, while leveraging external financial infrastructure providers (e.g. FinCode) to handle remittance rails, payment processing, and regulatory infrastructure during the initial phases."

Allows Social Remit to: launch efficiently, reduce early infrastructure complexity, remain operationally flexible, preserve long-term optionality, reduce unnecessary provider lock-in, support future infrastructure evolution.

Architecture priorities: modularity, provider abstraction, operational visibility, scalability, extensibility, maintainability.

## 4. System Layering Strategy (3 Layers)

### 4.1 Product Layer — owned by Social Remit
Everything the customer directly interacts with: frontend applications, customer UX, onboarding journeys, messaging, rewards, referrals, behavioural engagement, analytics, customer lifecycle experiences, operational messaging.

### 4.2 Control Layer — owned by Social Remit
Operational brain and orchestration layer. Includes: middleware, orchestration logic, internal transaction model, provider abstraction, routing logic, event orchestration, behavioural triggers, operational visibility, analytics orchestration, future operational intelligence systems.

> "Over time, this layer is expected to become increasingly valuable and strategically important."

### 4.3 Infrastructure Layer — leveraged from external providers initially
Underlying regulated financial infrastructure: remittance rails, payout infrastructure, FX, banking rails, compliance infrastructure, KYC, settlement, payment processing, open banking.

## 5. Strategic Principle

Long-term strategy is NOT to immediately rebuild all financial infrastructure. Instead: own the customer relationship, own the orchestration layer, own operational intelligence, own behavioural systems, own internal data models, preserve infrastructure flexibility — while leveraging mature external providers where commercially and operationally sensible.

## 6–7. Frontend Principles

- Must remain API-driven; avoid provider-specific coupling
- Support modular growth and future backend evolution
- Support async transaction states, graceful error handling, operational messaging, behavioural prompts, onboarding guidance, accessibility, fintech-grade reliability
- Priorities: simplicity, customer clarity, low friction, operational consistency

## 8. Middleware Principles

Middleware is strategically important. Must gradually become: orchestration layer, operational control layer, provider abstraction layer, business rules layer, future migration bridge.

Must support: provider abstraction, webhook handling, retry handling, async transaction processing, event-driven orchestration, operational visibility, analytics hooks, behavioural triggers, future multi-provider capability.

## 9–10. Provider Abstraction & Vendor Dependency Governance

- Frontend must NOT directly depend on provider response formats, workflows, business logic, or provider-specific UI assumptions
- Architecture should minimise unnecessary dependency, preserve portability, support future migration flexibility
- Social Remit should preserve visibility into: transaction states, operational events, customer lifecycle events, provider responses, webhook events, operational metrics

## 11. Integration & Extensibility

Platform should support integration with: compliance providers, KYC providers, payment gateways, open banking providers, messaging providers, analytics tooling, CRM systems, support tooling, fraud systems, treasury tooling, AI systems, operational tooling. Support: SDK integrations, API integrations, webhook integrations, future provider replacement, modular extensibility.

## 12. Compliance & KYC Integration Principles

Architecture must support: SDK-based onboarding, API-driven KYC workflows, async verification states, webhook updates, **sanctions screening**, **PEP screening**, **ongoing monitoring**, auditability, provider flexibility.

Potential providers mentioned: **Sumsub** (contracted), ComplyAdvantage, Onfido, Sardine, LexisNexis.

## 13. Payments, Banking & Open Banking

Must support: card processors, payment gateways, open banking providers, payout providers, banking APIs, wallet infrastructure.

Potential providers mentioned: **Volume**, **Checkout.com**, SagePay/Opayo, Google Pay, Apple Pay, **GoCardless**.

## 14. Customer Communication & Engagement

Must support: OTP delivery, onboarding/verification reminders, transactional notifications, operational alerts, behavioural nudges, re-engagement messaging, push notifications, email, future WhatsApp/SMS.

## 15–16. Behavioural Infrastructure & Rewards/Referrals

Behavioural engagement is a strategic differentiator. Must support: event-triggered messaging, onboarding engagement, customer lifecycle orchestration, inactivity engagement, promotional campaigns, configurable customer journeys, future gamification.

Rewards and referrals are "core behavioural infrastructure, not isolated marketing features." Must support: welcome bonuses, referral campaigns, reward eligibility/release logic, event-triggered rewards, referral attribution, abuse prevention. Future expansion to: loyalty tiers, points systems, gamification, community engagement, **"SR Tribe concepts"**.

## 17. Analytics & Customer Behaviour Tracking

Must support: onboarding funnel analysis, reward engagement tracking, referral analytics, customer retention analysis, inactivity analysis, operational bottleneck visibility, transaction funnel visibility.

Potential tools: Mixpanel, PostHog, Firebase Analytics, Amplitude, BI tooling.

## 18. CRM & Customer Operations

Future integration with: Zendesk, Intercom, HubSpot, Salesforce.

## 19. Event-Driven Product Orchestration

Events may trigger: notifications, rewards, analytics updates, operational workflows, engagement campaigns, lifecycle automation. Examples: customer completes KYC, customer performs first transfer, referral becomes eligible, customer becomes inactive, provider webhook received. Automated workflows should support operational override for compliance, support, fraud, or operational intervention.

## 20–22. Data Ownership, Structure & Auditability

Core platform data is a strategic business asset. Architecture must support: structured data ownership, operational visibility, auditability, future analytics capability, future AI capability, data portability, infrastructure independence.

Core data categories: customer profiles, KYC states, onboarding progress, transaction history, wallet balances, reward states, referral relationships, operational events, provider responses, webhook events, audit logs, fraud signals, support interactions, behavioural events, analytics events, treasury events, reconciliation records.

## 23. Data Privacy & Security

Must support: GDPR compliance, secure storage, RBAC, auditability, secure data access, customer privacy protection.

## 24. Technical Debt Governance

Technical debt must be: transparent, documented, risk-assessed, intentionally accepted, mitigation-defined, removable over time. Hidden technical debt is strongly discouraged.

## 25–26. Observability & Operational Excellence

> "Operational blindness is considered a major business risk."

Must support: monitoring, logging, alerting, operational dashboards, provider visibility, payout visibility, API monitoring, OTP visibility, webhook monitoring, transaction lifecycle visibility. Critical failures must be detectable internally before customers report them.

> "This principle is informed by real-world remittance operational experience and is considered strategically important." _(Joseph's direct operational background at UnityLink.)_

## 27. Security Expectations

Fintech-grade: secure auth, encrypted storage, secure APIs, HTTPS/TLS everywhere, token security, RBAC, session management, auditability, secure secrets handling.

## 28–30. Scalability, CI/CD & Operational Resilience

MVP must support: modular growth, future service separation, increased transaction volume, additional corridors, additional providers, future infrastructure ownership — without unnecessary overengineering.

CI/CD must include: dev/staging/production environments, structured deployment pipelines, rollback capability, version control discipline, release management.

Resilience must include: graceful degradation, retry handling, timeout handling, provider failure handling, async transaction handling, webhook resilience.

## 31. Build vs Buy

Open to mature off-the-shelf tooling (observability, analytics, support, fraud, monitoring). However: strategic infrastructure layers should remain extensible and controllable by Social Remit.

## 32. AI-Assisted Development

Permitted for: scaffolding, development, testing, prototyping, documentation. However: all generated code must meet production-grade standards, maintainability expectations, security expectations, architectural consistency. Code quality remains the engineering team's responsibility.

## 33–34. Documentation & Collaboration Expectations

Platform should minimise key-person dependency. Technology partners are expected to: communicate transparently, challenge weak assumptions, think structurally, prioritise maintainability, consider operational realities. "Social Remit values collaborative engineering relationships rather than purely transactional development relationships."

## 35. Non-Negotiable Principles Summary

**Architectural non-negotiables:**
- Frontend must not be tightly coupled to provider infrastructure
- Provider-specific logic must remain isolated wherever practical
- Critical operational workflows must remain observable internally
- Architecture decisions must preserve future migration flexibility
- Hidden technical debt is strongly discouraged
- Significant technical compromises must be documented transparently

**Operational non-negotiables:**
- Critical failures must ideally be detectable internally before customers report them
- Production systems must support monitoring, alerting, and operational visibility
- Critical workflows must support auditability and traceability
- Operational blind spots must be minimised wherever practical

**Delivery non-negotiables:**
- Production deployments must support staging/testing environments
- Critical integrations must be documented appropriately
- Engineering decisions must prioritise maintainability over unnecessary shortcuts
- Security-sensitive workflows must follow fintech-grade practices

**Strategic non-negotiables:**
- MVP must prioritise strong foundations over unnecessary complexity
- Architecture must support future infrastructure evolution
- Strategic operational and customer data must remain accessible and controllable by Social Remit
- System must remain extensible for future integrations, orchestration layers, and behavioural systems

## 36. MVP Priorities (in order)

1. Operational stability
2. Security & compliance readiness
3. Scalability foundations
4. Maintainability
5. Customer trust
6. Clean architecture direction
7. Migration flexibility
8. Delivery quality
9. Operational visibility
10. Behavioural simplicity

## 37–38. Long-Term Direction

MVP is the first phase of a broader infrastructure evolution strategy. Long-term direction may include: expanded middleware ownership, operational intelligence systems, treasury intelligence, reconciliation intelligence, multi-provider orchestration, AI-assisted operations, behavioural intelligence systems, proprietary infrastructure layers.

> "The objective of the Social Remit technology strategy is not simply to build an app. The objective is to build trusted financial infrastructure."
