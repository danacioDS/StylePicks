# STYLE PICKS
## Engineering Proposal

**Stage A.5 — Engineering Definition**
**Physical Foundation of the Style Picks Operational System**

**Document ID:** A.5-ENG-STYP-001

**Version:** 1.3 — Engineering Definition Baseline (Reconciled)

**Status:** Stage A — Engineering Definition (Conceptual Level) — Baselined

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Parent Documents:**
- A.1-BIZ-STYP-001 — Business Plan and Commercial Validation (v1.5 Reconciled)
- A.2-FUNC-STYP-001 — Value Proposition Functional Specification (v1.2 Reconciled)
- A.3-CAP-STYP-001 — Business Capabilities Specification (v1.2 Reconciled)
- A.4-CONTR-STYP-001 — Capability Contracts Specification (v1.0 Reconciled)
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.0)

**Child Documents:**
- STAGE-A-CONSOL-REPORT-STYP-001 — Stage A Consolidation Report (v1.0)
- None (terminal document in Stage A)

**Domain:** Domain A.5 — Engineering

---

**Business Model:** Content Commerce + Affiliate Commerce
**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**Initial Categories:** Home Decor + Home Organization
**Stage:** Commercial Validation
**Document Type:** Engineering Proposal
**Derives from:** A.1-BIZ-STYP-001, A.2-FUNC-STYP-001, A.3-CAP-STYP-001, A.4-CONTR-STYP-001

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 8, 2026 | Initial Engineering Proposal (sections 1–45) |
| 1.1 | Oct 8, 2026 | Added Phase 0 / FOM; committed default stack; added external dependency fallbacks; filed three change proposals |
| 1.2 | Oct 8, 2026 | Build-time budget and evidence-gated phases; compliance verification in Phase 0; ED-05 closed; AI provider default; CP-02 and CP-03 wording corrected; Workflow Execution Model added; refined defaults |
| 1.2 Final | Oct 8, 2026 | Phase 0 uses Django models + admin directly on PostgreSQL (no SQLite, no migration from spreadsheets); scheduling mechanism unified to cron + management commands (APScheduler dropped); status set to Frozen |
| 1.2 Final (Baselined header) | Oct 8, 2026 | Normalized document header per Stage A codification; cross-references updated to A.x IDs; Open Items Register (`PH1-REG-STYP-001`) referenced; Change Proposals and Engineering Dependencies registers integrated; Sign-Off block added |
| 1.2.1 | Oct 8, 2026 | CP-001 accepted. §19 re-evaluation semantics aligned with INV-12 of A.4. No divergence remains. |
| **1.3** | Oct 8, 2026 | **Consistency reconciliation with A.1 v1.5, A.2 v1.2, A.3 v1.2, A.4 v1.0 Reconciled.** (1) CP-003 status corrected from Pending to **Accepted 2026-10-08** in the header table and §47. (2) §13 wording aligned with A.4 C-06 postcondition #3 (C-06 issues; C-07 executes). (3) §32-A references the checkpoint relevance note from A.1 v1.5 §18 and A.3 v1.2 §18.7. (4) §46 FOM aligns with A.4 INV-13. (5) All parent document versions updated. (6) Formal Sign-Off updated to Baselined. |

---

## Open Items

> **This document depends on the same Open Items as the rest of Stage A. The authoritative source is `PH1-REG-STYP-001`.**

| # | Open item | Priority | Owner | Status |
|---|-----------|----------|-------|--------|
| **OI-001** | Amazon Associates account creation date | **Blocking** | Editorial Owner | **CLOSED — 2026-04-15** |
| **OI-002** | Amazon Associates deadline (account date + 180 days) | **Blocking** | Editorial Owner | **CLOSED — 2026-10-12** |
| OI-003 | Verification: qualifying-sales rule | Defaultable | Editorial Owner | EMPTY |
| OI-004 | Verification: Creators API access requirements | Defaultable | Editorial Owner | EMPTY |
| OI-005 | Verification: image and price display rules | Defaultable | Editorial Owner | EMPTY |
| OI-006 | Verification: required disclosure wording | Defaultable | Editorial Owner | EMPTY |
| OI-007 | Verification: link-format rules | Defaultable | Editorial Owner | EMPTY |
| OI-008 | Evidence Source Policy — formalized | Defaultable | Editorial Owner | EMPTY |

**Change Proposals filed against this document (also affecting A.4-CONTR-STYP-001):**

| CP ID | Title | Affected sections | Status |
|-------|-------|-------------------|--------|
| CP-001 | Re-evaluation vs Revocation on Superseded Evidence | §19, §47 | **Accepted 2026-10-08** |
| CP-002 | AI-Generated Contextual Imagery | §12, §47 | Pending |
| CP-003 | Review Cleared Sole-Writer Assignment | §13, §47 | **Accepted 2026-10-08** |

**Engineering Dependencies Register:**

| ED ID | Description | Status |
|-------|-------------|--------|
| ED-001 | Amazon External Parameters | Open |
| ED-002 | Amazon API Availability | Open |
| ED-003 | Pinterest API Capabilities | Open |
| ED-004 | AI Provider Selection | **Closed** — Anthropic Claude |
| ED-005 | Infrastructure Selection | **Closed** — §39-A |

> **On CP-003 (Accepted):** A.4-CONTR-STYP-001 v1.0 Reconciled reworded C-06 postcondition #3. C-06 issues Validation Results; C-07 executes lifecycle transitions. This aligns with INV-13. §13 of this document reflects the accepted wording.

> **On CP-002 (Pending):** Until accepted, only licensed and stock imagery are used. §12 reflects this.

---

# 1. Purpose

This Engineering Proposal defines how Style Picks will be implemented as a software system capable of executing and governing the business capabilities and capability contracts defined in the preceding specifications.

It translates contractual requirements into system architecture, execution mechanisms, storage models, tooling, external integrations, automation, human-in-the-loop controls, sequencing, and operational infrastructure.

This document does **not** redefine business capabilities or capability contracts. Where an implementation constraint makes a contractual requirement impossible or materially impractical, the implementation **must** return a formal change proposal to `A.4-CONTR-STYP-001` rather than silently changing the contract.

---

# 2. Engineering Objective

Style Picks will be implemented as a **private internal commerce operations platform**.

Pinterest and Amazon are external systems and channels. They are not the Style Picks system itself.

The initial engineering objective is:

> Build a controlled internal system that orchestrates product research, evidence, evaluation, recommendation, content production, validation, compliance, publication, attribution, and learning across external commerce and distribution platforms.

---

# 3. System Boundary

## 3.1 Inside Style Picks

The Style Picks platform owns: contexts, product records, evidence records, evaluations, recommendations, content assets, validation results, compliance records, publication records, performance records, learning records, rubric versions, contract failure records, workflow orchestration, audit trail, operator dashboard.

## 3.2 Outside Style Picks

External systems: Pinterest, Amazon Associates infrastructure, Amazon product data interfaces, external manufacturer/product sources, AI model providers, image-generation providers, analytics sources, authentication infrastructure where externally provided.

---

# 4. Engineering Principles

- **EP-01 — Contract First.** Capability Contracts (`A.4-CONTR-STYP-001`) are authoritative.
- **EP-02 — Single Ownership.** Enforce sole-writer rule at service and, where practical, data layer.
- **EP-03 — Traceability by Default.** Every material operation leaves an auditable trail.
- **EP-04 — Human Control at Critical Gates.** AI must not silently bypass publication gates, compliance decisions, material evidence requirements, rubric approval, exceptional lifecycle actions.
- **EP-05 — External Systems Are Untrusted Dependencies.** Isolate external dependencies from core business records.
- **EP-06 — Automation Is Incremental and Evidence-Gated.** Automate deterministic work first, and only when operational evidence justifies it.
- **EP-07 — Operational Velocity Is a Safety Requirement.** The Associates survival clock runs from account creation. The system must enable the first Pin quickly, not only the full platform eventually.
- **EP-08 — Build Time Is a Scarce Resource.** During validation, build capacity competes directly with Pin production capacity. Every hour spent building is an hour not spent producing. Build effort is capped, and Pin production has priority.

---

# 5. Proposed System Architecture

The initial architecture is a **modular monolith**.

```text
┌──────────────────────────────────────────────────────────┐
│                    STYLE PICKS UI                        │
│ Dashboard | Products | Evidence | Content | Publishing   │
│ Analytics | Compliance | Learning | Settings             │
└──────────────────────────┬───────────────────────────────┘
                           ↓
┌──────────────────────────────────────────────────────────┐
│                 STYLE PICKS APPLICATION                  │
│ Context | Product | Evaluation | Recommendation          │
│ Content | Validation | Compliance | Publication          │
│ Performance | Learning | Evidence | Rubric               │
│ Workflow / Contract Engine                               │
└──────────────────────────┬───────────────────────────────┘
                           ↓
              ┌────────────┼────────────┐
              ↓            ↓            ↓
       ┌───────────┐ ┌───────────┐ ┌────────────┐
       │ PostgreSQL│ │ Object    │ │ cron +    │
       │           │ │ Storage   │ │ mgmt cmds │
       └───────────┘ └───────────┘ └────────────┘
                           ↓
┌──────────────────────────────────────────────────────────┐
│                    INTEGRATION LAYER                     │
│ Pinterest | Amazon | Product Sources | AI Providers      │
│ Image Providers | Analytics Sources                      │
└──────────────────────────────────────────────────────────┘
```

Favor simplicity, observability, and rapid iteration over premature distribution.

---

# 6. User Interface

## 6.1 Primary Interface

Private authenticated **operator dashboard**. Not a public SaaS product.

The initial dashboard is provided by **Django Admin** for CRUD over the Part I record types, plus custom views for the workflows that require them (see §6.2).

## 6.2 Initial Dashboard

**Overview** — products discovered, under evaluation, active recommendations, content awaiting validation/publication, published Pins, Pins under review, recent performance, compliance alerts, contract failures, learning opportunities.

**Product Workspace** — view Product Records, inspect evidence, review product changes, inspect evaluations, see linked recommendations and Pins.

**Recommendation Workspace** — inspect recommendation, material claims, supporting evidence, confidence, approve/reject human-review items, inspect revoked recommendations.

**Content Workspace** — inspect generated Content Assets, review images, disclosure, destination, send to validation.

**Publication Workspace** — see publication-ready assets, inspect both gates, publish, relink, archive, restore exceptionally.

**Analytics Workspace** — inspect Pinterest performance, Amazon attribution, compare products, Pin-level performance, review learning candidates.

**Governance Workspace** — inspect compliance decisions, contract failures, evidence history, rubric versions, audit history.

---

# 7. Execution Mechanism by Contract

## C-01 — Context Management

**Mechanism:** Human-assisted form (Django admin). Operator creates or edits Context Record. System validates required fields, approved categories, price range, status transitions. Approval is human-controlled.

**Storage:** PostgreSQL record.

---

# 8. C-02 — Product Discovery

**Mechanism:** Hybrid automated + human-assisted discovery.

**Product sources (preferred order):**
1. Amazon product data interface currently available to the account (see §16 and ED-002).
2. Manufacturer/product pages.
3. Other approved evidence sources.

**Fallback when programmatic access is unavailable:** manual entry through the Django admin. The manual path uses the same record schemas and the same contract checks as the automated path. Only the source of the data differs.

**Change detection:** daily scheduled worker when compliant automated access is available; otherwise, **weekly manual change-detection over live Product Records only** (see §24 and `A.4-CONTR-STYP-001` I.5).

**Human role:** review required when product identity is ambiguous, sources conflict, destination cannot be verified, evidence is insufficient, or extraction confidence is low.

---

# 9. C-03 — Product Evaluation & Curation

**Mechanism:** Deterministic scoring engine. Loads Active Rubric Version; calculates criterion scores, weighted score, hard constraints, verifiability score, eligibility.

**Human role:** operator may review borderline products, rejected products, unusual evidence, rubric exceptions.

**Rule:** evaluation engine records the exact rubric version used.

---

# 10. C-04 — Recommendation Generation

**Mechanism:** Hybrid rules + LLM generation.

System supplies: approved Context Record, eligible Product Record, Evaluation Record, Active Evidence Records, material-claim rules, editorial constraints. Model generates statement, rationale, limitations, supporting facts. System performs deterministic post-generation checks.

**Rule:** No recommendation becomes Approved merely because an LLM generated it.

**Confidence:** calculated from Evidence Records using `A.4-CONTR-STYP-001` D-3.

**Human review:** Low-Confidence → Human Review → Human-Review-Approved / Rejected.

---

# 11. C-05 — Content Presentation

**Mechanism:** Hybrid template + AI generation.

AI may generate title, description, editorial framing, visual concepts. Deterministic logic controls destination, tracking ID, disclosure, product identity, required metadata.

**Rule:** generative layer must not invent or modify critical commerce fields.

---

# 12. Image Generation and Image Evidence

Images are treated separately from product factual evidence.

**Image sources:** licensed product imagery; permitted external imagery; AI-generated contextual imagery; operator-provided imagery.

**Rules:**
- Every image used as evidence has an associated Evidence Record where required by the contract.
- AI-generated contextual imagery must not be represented as a photograph of the actual product unless that representation is truthful and permitted.
- The system distinguishes **Actual Product Image** vs. **Contextual / Generated Image**.
- Use of AI-generated imagery is contingent on **CP-002** (§47), which amends both `A.2-FUNC-STYP-001` and `A.4-CONTR-STYP-001` to admit AI imagery under labeling and evidence conditions, and references CD4 (Pinterest policies on AI-generated content labeling).

**Until CP-002 is accepted:** only licensed and stock imagery are used.

---

# 13. C-06 — Consistency Validation

Primarily deterministic. The seven validation checks defined by `A.2-FUNC-STYP-001` §11.3 and `A.4-CONTR-STYP-001` I.1.7 are implemented as executable validation rules.

**Validator checks:** Pin promise vs. content; product identity; destination; tracking ID; recommendation/content consistency; required metadata; relevant evidence relationships.

**Output:** Validation Result — PASS / FAIL / CLEARED.

Human review may be required for ambiguous semantic checks.

**Lifecycle transitions triggered by a Validation Result are executed by C-07 only** (INV-13; CP-003 accepted 2026-10-08). C-06 issues Validation Results; C-07 executes lifecycle transitions. This aligns with `A.4-CONTR-STYP-001` C-06 postcondition #3 and §47 CP-003.

---

# 14. C-07 — Publication & Lifecycle

Publication is a gated workflow.

```
Validation = PASS  AND  Compliance = Approve
        ↓
Publication permitted
```

Operator may trigger publication manually. Where approved Pinterest API capabilities permit, C-07 may publish programmatically.

**Lifecycle:** Publication records track Pin URL, tracking ID, publication timestamp, validation reference, compliance reference, lifecycle events, current state.

**INV-13 (CP-003 accepted 2026-10-08):** Every lifecycle transition — including Review triggered, Review cleared, Re-linked, Replaced, Archived, Restored — is executed by C-07 only, even when triggered by a Validation Result issued by C-06.

---

# 15. Pinterest Integration

Pinterest is an external distribution platform. The integration layer isolates Pinterest-specific implementation from core records.

**Potential operations:** authenticate; create/publish Pin where supported; assign board; retrieve Pin identifier/URL; retrieve available engagement data; update lifecycle state where supported.

**Rule:** do not assume every lifecycle operation is available through the Pinterest API. Unsupported operations remain operator-assisted.

**Storefront Linking:** the business decision about whether to adopt Pinterest ↔ Amazon Storefront Linking is owned by the destination model in `A.2-FUNC-STYP-001`, not by this Engineering Proposal. Until that decision is made, the system assumes **Style Picks remains the source of truth for the tracking ID** (INV-3 holds). If Storefront Linking is later adopted, it must be reflected in the destination model, in INV-3, and in C-05's derivation logic.

---

# 16. Amazon Integration

Amazon is an external commerce and affiliate dependency.

**Preferred interface for product data:** Amazon Creators API (PA-API is deprecated). Access conditions must be verified under ED-002. Where the account does not yet meet the requirements, the manual path in §8 applies.

**Integration layer supports, where available and permitted:** product discovery; product information retrieval; identifiers; variations; destination generation; affiliate attribution; performance data.

**Rule:** external API changes must not require changes to the core Product Record contract unless the external change makes a contractual requirement impossible.

**Fallbacks (see §37-A):** manual Discover, CSV-based performance import for C-08, manual Pinterest publishing.

---

# 17. C-08 — Performance Measurement & Attribution

**Mechanism:** Scheduled data collection. Sources may include Pinterest analytics, Amazon affiliate reporting, other approved measurement sources. System normalizes into Performance Records.

**Fallback when reporting APIs are unavailable:** CSV import from the platform dashboards, entered through the Django admin, producing the same Performance Records as automated collection.

**Separation:** Performance data is Monitoring → Learning → Compliance survival monitoring. It is **not** a runtime publication gate (INV-9).

---

# 18. C-09 — Learning & Improvement

**Mechanism:** Analytics + human interpretation + AI assistance.

System identifies patterns such as high engagement / low conversion, low engagement, repeated product failures, recurring compliance failures, recurring evidence failures, recurring content failures. AI may propose hypotheses. Human approval is required before material changes to rubric, governance rules, or business strategy.

Learning Records preserve the evidence behind decisions.

---

# 19. C-10 — Evidence Management

Dedicated governance layer. System maintains evidence identity, source, source classification, retrieval time, content snapshot where permitted, linked product, linked recommendation, status, supersession relationship.

**Versioning:** evidence is never silently overwritten.

```
Evidence v1 → Superseded → Evidence v2
```

**Re-evaluation semantics (CP-001 accepted, 2026-10-08):** when a material claim's supporting evidence is superseded, the system adopts the two-step logic — re-point the claim to the successor if it supports the claim, otherwise Revoke the recommendation. This semantics is formalized in INV-12 of `A.4-CONTR-STYP-001`. No divergence exists between A.4 and A.5 on this point.

---

# 20. C-11 — Rubric Management

Rubrics are stored as versioned configuration.

```
Draft → Active → Retired
```

Only one version can be Active. Activation requires the designated approver. Evaluation records retain the rubric version used so historical decisions remain reproducible.

---

# 21. C-12 — Compliance & Governance

Implemented as a dedicated rule engine plus human review where external interpretation is required.

**Engine evaluates:** disclosure, link format, image usage, price display, prohibited categories, survival requirements, applicable external rules.

**Rules are versioned or timestamped.** The system distinguishes:

```
Rule exists  vs.  Rule parameter verified
```

Unverified external parameters are represented as **unverified configuration**, never silently treated as operationally confirmed.

**Phase 0 requirement (see §32-B):** the specific external rules that govern the **first Pin** — required disclosure wording, link-format rules, image rules — must be verified against the Associates Operating Agreement, FTC guidance, and Pinterest policies before the first Pin is published.

---

# 22. Data Storage Model

**PostgreSQL** as the system of record.

**Core entities:** Context, Product, Evidence, Evaluation, Recommendation, ContentAsset, ValidationResult, ComplianceRecord, Publication, Performance, Learning, RubricVersion, ContractFailure.

**Rules:** relationships through stable IDs; historical records remain queryable; no destructive updates for records requiring historical traceability. Product Records are keyed by `(product_id, version)` per `A.4-CONTR-STYP-001` I.1.2.1.

---

# 23. Object / File Storage

Large or binary assets are not stored in relational records.

Object storage holds generated images, approved image assets, content exports, source snapshots where permitted, other large artifacts. Database records retain references. Initial implementation: local filesystem; S3-compatible (MinIO or Wasabi) only if remote access is needed.

---

# 24. Job Scheduling

**Scheduling mechanism:** **cron** invoking **Django management commands**. A single, mature, universally available mechanism. No in-process scheduler (APScheduler dropped) and no Celery until volume justifies it.

**Daily:**
- `python manage.py detect_product_changes` — product change detection (when automated access available);
- `python manage.py monitor_evidence` — evidence monitoring;
- `python manage.py check_publications` — publication checks.

**Periodic (weekly, or as configured):**
- `python manage.py collect_pinterest_performance`;
- `python manage.py collect_amazon_performance`;
- `python manage.py reconcile_attribution`.

**Event-driven** (triggered by record changes, not cron):
- evidence supersession;
- recommendation re-evaluation;
- validation;
- compliance;
- publication;
- corrective actions.

**Fallback when automated change detection is not possible:** weekly manual change-detection pass over live Product Records only, using the Django admin.

Jobs must be observable and retryable. Missed scheduled jobs must be detectable (E-CD-01). Each management command writes a structured log entry on start, success, and failure.

## 24-A — Workflow Execution Model

The Engineering Proposal distinguishes **synchronous**, **transactional**, and **asynchronous** execution paths.

```text
Operator action (UI)
        ↓
Application Service
        ↓
Contract precondition checks (§27)
        ↓
Record transaction (PostgreSQL commit)
        ↓
Management command scheduled (if external effect required)
        ↓
cron executes command
        ↓
External system (Pinterest / Amazon / AI)
        ↓
Result handling
        ↓
Postcondition checks (§27)
        ↓
Audit entry
        ↓
Contract Failure Record (if applicable)
```

**Synchronous path:** record creation, precondition and postcondition checks, contract validation, audit entry.

**Transactional path:** any operation that creates or modifies a Part I record. Executed inside a PostgreSQL transaction; sole-writer rule enforced at the service layer and, where practical, by database constraints.

**Asynchronous path:** any operation whose primary effect is on an external system. Executed by cron-invoked management commands; results fed back through the same postcondition and audit pipeline.

**Idempotency requirement:** asynchronous operations that create external side effects (most importantly publication) must carry a stable request identifier so retries cannot produce duplicate external records.

---

# 25. AI Architecture

AI is an execution component, not the source of truth.

**AI is appropriate for:** product research assistance, summarization, evidence extraction, recommendation drafting, editorial copy, image concepts, contextual imagery, pattern detection, learning hypotheses.

**Deterministic systems must control:** identifiers, tracking IDs, URLs, state transitions, contract gates, rubric activation, compliance decisions where deterministic rules apply, audit records.

> **AI generates and assists; the contract engine verifies and governs.**

---

# 26. Human-in-the-Loop Model

**Human approval required initially for:** Context approval; low-confidence recommendations; exceptional product decisions; rubric activation; compliance ambiguity; exceptional Pin restoration; major learning/rule changes.

**Automation preferred for:** field validation; evidence linkage; score calculation; tracking consistency; lifecycle transitions where deterministic; scheduled monitoring; data collection; routine validation.

---

# 27. Contract Enforcement Layer

A dedicated contract-validation layer implements precondition checks, postcondition checks, invariant checks, error codes, traceability validation, failure recording.

Example:

```
C-05 creates Content Asset
      ↓
Contract Validator
      ↓
Check INV-3, INV-7, disclosure, required references
      ↓
PASS / CONTRACT FAILURE
```

**Failure routing (aligned with `A.4-CONTR-STYP-001` I.7.3):**
- Operational → Contract Failure Record with `escalated_to_learning = false`.
- Material → Contract Failure Record with `escalated_to_learning = true`.
- Systemic → Contract Failure Record with `escalated_to_learning = true` and a review proposal routed to the affected capability.

Contract enforcement must not depend exclusively on human discipline.

---

# 28. Audit Trail

Maintain audit history for material operations: record creation, modification, state transition, evidence supersession, recommendation revocation, rubric activation, compliance decision, publication, corrective action, contract failure, learning decision.

**Fields:** actor, timestamp, action, affected record, previous state where applicable, resulting state, reason where required.

---

# 29. Security

**Initial requirements:**
- authenticated operator access;
- role-based authorization architecture (V1 may have one role);
- encrypted credentials/secrets, with encryption at rest for affiliate and API credentials;
- **separation between development secrets and production secrets**;
- external API credentials stored outside source code;
- secret rotation policy;
- encrypted transport;
- protected database access;
- audit trail;
- verified backup (frequency, retention, tested restore);
- two-factor authentication for the operator account.

Affiliate and API credentials must never be stored in frontend code.

---

# 30. External Dependency Isolation

External integrations implemented behind adapters.

```
Style Picks Core → Integration Interface
                          ↓
              ┌───────────┴───────────┐
              │                       │
        Pinterest Adapter      Amazon Adapter
```

External API changes must not rewrite business logic.

---

# 31. Failure and Recovery

Every asynchronous external operation supports timeout, safe retry, failure logging, escalation, idempotency where required.

**Publication operations** require protection against duplicate publication. A publication request must be identifiable and recoverable without accidentally creating duplicate Pins.

---

# 32. Implementation Sequence

The implementation follows dependency order, not visual feature order. All build activity is subject to the budget in §32-A.

## Phase 0 — Manual Operating Baseline (runs from day one)

**Goal:** operate the business before the full platform exists, using the Part I record schemas as Django models.

**Deliverables:**
- Django project initialized against PostgreSQL (per §39-A).
- **Part I models defined as Django models**, migrations applied to the production PostgreSQL database.
- **Django admin configured** as the manual operating interface for all 13 record types.
- Contract-check script (`python manage.py check_invariants`) that validates INV-1, INV-3, INV-4 before a Pin is published.
- Manual publishing of Pins on Pinterest.
- Production-time logging per Pin (a simple field on the Publication Record).
- A simple failure log for manual operations.
- **External rule verification (§32-B):** disclosure wording, link-format rules, image rules. Closes OI-003 through OI-007.

**Estimated effort:** ~1 day for setup (Django project + models + admin) plus the external rule verification (a few hours of reading).

**Key decision:** Phase 0 uses Django models and Django admin **directly on PostgreSQL** — no SQLite, no spreadsheet migration. The data is in its final home from the first record. Phase 1 adds the contract-validation framework and custom UI on top of the same models.

**Milestone (First Operational Milestone, §46):** the first Pin is live on Pinterest with a complete internal record trail.

## Phase 1 — Platform Foundation
**Deliverables:** custom operator views beyond admin; contract validation framework (extending §27); audit trail middleware; error handling; dashboard shell.
**Estimated effort:** 1–2 weeks.

## Phase 2 — Product Intelligence
**Deliverables:** automated Context Management UI; Product Discovery ingestion; Evidence Management versioning; change detection command.
**Estimated effort:** 2–3 weeks.

## Phase 3 — Evaluation & Recommendation
**Deliverables:** Rubric Management; deterministic evaluation engine; LLM-assisted Recommendation Generation with post-generation checks; human review workflow.
**Estimated effort:** 2 weeks.

## Phase 4 — Content Production
**Deliverables:** Content Assets; image management; AI content generation; disclosure; destination/tracking derivation.
**Estimated effort:** 1–2 weeks.

## Phase 5 — Governance & Publication
**Deliverables:** Consistency Validation engine; Compliance rule engine; Pinterest integration; Publication & Lifecycle workflow.
**Estimated effort:** 2 weeks.

## Phase 6 — Measurement
**Deliverables:** Pinterest measurement; Amazon attribution; Performance Records; reconciliation; CSV import fallback.
**Estimated effort:** 1–2 weeks.

## Phase 7 — Learning
**Deliverables:** Learning Records; performance analysis; failure analysis; learning proposals; rubric-change workflow.
**Estimated effort:** 1–2 weeks.

**Total estimated effort if all phases are built unconditionally:** 12–18 weeks.

## 32-A — Build-Time Budget and Evidence-Gated Phases

> **This section is the operational consequence of EP-07 and EP-08.**

**Capacity reality.** One operator. The validation targets in `A.2-FUNC-STYP-001` v1.2 §18.2 (120 Pins at ≤45 min each) already require roughly 90 hours of production. A 12–18 week build program consumes most of the 180-day survival window. **Every hour of build is an hour not spent producing Pins.**

**Budget cap.** Build effort during commercial validation is capped at **10 hours per week**, with the remaining operator time reserved for Pin production. If a phase cannot be completed within the cap, it is deferred, not expanded.

**Evidence gating.** Phases 2–7 do **not** start automatically. Each phase starts **only when the operational evidence justifies automating what the phase automates** (consistent with `A.2-FUNC-STYP-001` v1.2 §17.1):

| Phase | Start condition (evidence gate) |
|-------|--------------------------------|
| 2 | Manual product and evidence entry is a measured bottleneck in the Phase 0 time log. |
| 3 | Manual evaluation or recommendation drafting is a measured bottleneck. |
| 4 | Manual content asset production is a measured bottleneck. |
| 5 | Manual validation, compliance, or publication is a measured bottleneck **or** the publishing cadence exceeds the operator's manual capacity. |
| 6 | Manual performance data collection is a measured bottleneck **or** the survival checkpoints (CD1) require structured data. |
| 7 | Sufficient performance data exists to make learning non-speculative. |

**Consequence.** In a realistic validation window, **Phases 0–3 are likely to be the only ones that justify themselves before the deadline.** Phases 4–7 may legitimately be deferred past the first survival checkpoint. This is not a failure of the plan; it is the plan working as designed.

> **Note on the compressed operating window (aligned with `A.1-BIZ-STYP-001` v1.5 §18 and `A.3-CAP-STYP-001` v1.2 §18.7):** The survival clock began on 2026-04-15 and the deadline is 2026-10-12. The operational start is 2026-10-07. The remaining operating window from the operational start to the deadline is short. If the window is shorter than the largest checkpoint offset (135 days), the checkpoints have either already passed or are not actionable, and the Editorial Owner must decide whether to treat the current date as the effective checkpoint, request a deadline extension, or accept that the survival floor may not be reached. This does not change the engineering plan; it changes the operational expectations against which the plan is executed.

## 32-B — External Rule Verification (Phase 0)

Before the first Pin is published, the following external rules must be verified against their sources and recorded as **verified configuration**:

| Rule | Source | Impact if unverified |
|------|--------|---------------------|
| Required affiliate disclosure wording | Amazon Associates Operating Agreement | First Pin publishes non-compliant content |
| Required placement of disclosure | Amazon Associates Operating Agreement | Same |
| FTC endorsement disclosure requirements | FTC guidance on endorsements and testimonials | Legal exposure independent of Amazon |
| Permitted link format | Amazon Associates Operating Agreement | Non-conforming link may invalidate attribution |
| Image use and permitted sources | Amazon Associates Program Policies + Pinterest policies | Non-compliant visual content |
| Price display rules | Amazon Associates Operating Agreement | Governs whether prices may appear on Pins |

**Estimated effort:** a few hours of reading. Completion closes OI-003 through OI-007.

---

# 33. MVP Definition

The minimum viable operational platform must support this complete controlled path:

```
Context → Product → Evidence → Evaluation → Recommendation
   → Content Asset → Validation → Compliance → Publication → Performance
```

The MVP does **not** require complete automation, and it does **not** require all seven phases.

**Distinction:** the First Operational Milestone (§46) is achieved at the end of Phase 0. The MVP is what Phases 1–5 (or fewer, per §32-A) produce. The two are not the same, and the survival clock binds to the FOM, not to the MVP.

**"The full MVP is a target, not a prerequisite for validation."**

---

# 34. Automation Maturity

- **Level 0 — Manual.** Human executes most operations.
- **Level 1 — AI-assisted.** AI generates or assists; human executes.
- **Level 2 — System-assisted.** System performs deterministic preparation and validation; human approves.
- **Level 3 — Controlled automation.** System executes low-risk operations automatically.
- **Level 4 — Adaptive automation.** System uses validated learning to optimize workflows while preserving governance gates.

**Initial Commercial Validation targets Levels 1–2.** Higher automation is earned through operational evidence, consistent with §32-A.

---

# 35. Observability

The system exposes operational metrics: workflow failures, failed jobs, contract failures, publication failures, evidence supersessions, recommendation revocations, compliance failures, API errors, data freshness, attribution completeness.

**Logging:** structured (JSON), no sensitive data in logs, minimum 90-day retention.

**Alerting:** the operator is notified on scheduled job misses, publication failures, contract failures with severity Material or Systemic, and repeated API errors. Initial channel: email or Telegram bot.

**Operational dashboard:** pending jobs, recent failures, data freshness, publication state by Pin.

Purpose is operational reliability, not business reporting alone.

---

# 36. External Rule Verification

External commercial rules must be verified before being treated as operational constants: Amazon account survival requirements; qualifying-sales requirements; applicable deadlines; disclosure requirements; link-format requirements; image rules; price-display rules; API access requirements.

Until verified, such parameters are represented as **unverified configuration**, not hard-coded assumptions. See §32-B.

---

# 37. Open Engineering Dependencies

- **ED-001 — Amazon External Parameters.** Resolve remaining Amazon Associates rules.
- **ED-002 — Amazon API Availability.** Confirm exact APIs and account permissions available to Style Picks (Creators API access conditions; any qualifying-sales requirement).
- **ED-003 — Pinterest API Capabilities.** Confirm which publication, board, Pin, and analytics operations are available.
- **ED-004 — AI Provider Selection.** **Closed.** Default: Anthropic Claude (primary LLM). Image generation deferred to Phase 4. Revisions require a change proposal.
- **ED-005 — Infrastructure Selection.** **Closed.** Covered by §39-A.

## 37-A — Fallbacks for Unresolved Dependencies

| Dependency | If unavailable | Fallback |
|-----------|----------------|----------|
| Amazon Creators API | Not yet accessible | Manual product entry through Django admin (§8) |
| Amazon performance reporting | No reporting API | CSV import into Performance Records (§17) |
| Pinterest publication API | Not approved | Manual publishing, recorded via Django admin (§15) |
| Pinterest analytics API | Not available | Manual weekly data entry |
| Automated change detection | Compliant automated access unavailable | Weekly manual change-detection over live Product Records only (§24) |
| Storefront Linking | (business decision) | Style Picks remains the tracking-ID source of truth |

---

# 38. Technology Selection Criteria

1. Contract compliance.
2. Reliability.
3. API maturity.
4. Development speed.
5. Operating cost.
6. Observability.
7. Data portability.
8. Vendor lock-in.
9. Security.
10. Ability to scale beyond initial validation.

---

# 39. Recommended Initial Architecture

For Commercial Validation, Style Picks begins with a **modular monolithic architecture**:

```
One Django application + PostgreSQL + Object storage
    + cron + management commands + External API adapters + AI providers
```

This is preferable to microservices at this stage. The architecture maintains clear internal module boundaries corresponding to the capability contracts.

## 39-A — Default Stack (Committed for V1 Final)

| Layer | Default | Rationale |
|-------|---------|-----------|
| Language / Runtime | Python 3.11+ | Ecosystem affinity with AI tooling; fast development for solo operator. |
| Web framework | **Django 5.x** | Built-in admin, authentication, ORM, migrations, and CRUD scaffolding cover much of Phase 0 and Phase 1. For a solo operator, this materially reduces build time, which is the scarce resource (EP-08). |
| Templates / UI | Django templates + HTMX + Alpine.js | Server-rendered, no SPA complexity; Django's admin provides the CRUD baseline. |
| Database | **PostgreSQL 15+** | Jobs, audit trail, contract failures, state machines, background commands, concurrent readers/writers. PostgreSQL is the system of record from Phase 0. |
| ORM / Migrations | Django ORM + Django migrations | Standard, mature, supports the sole-writer pattern through service-layer enforcement and database constraints. |
| Object storage | Local filesystem initially; S3-compatible (MinIO or Wasabi) if remote access needed | No premature cloud dependency. |
| Scheduling | **cron + Django management commands** | Single, mature, universally available. No in-process scheduler. No Celery until volume justifies it. |
| Secrets | Development `.env` and production `.env.production` strictly separated; both uncommitted; local encrypted file for production credentials | Prevents dev credentials from accidentally reaching production systems. |
| AI provider | **Anthropic Claude** (primary LLM, ED-004 closed); image generation deferred to Phase 4 | Single vendor initially to reduce operational surface. |
| Hosting | Single VPS (small tier) or equivalent managed service | Cost control and portability. |
| Logging | Structured JSON to local files; rotation enabled | Sufficient for observability (§35). |
| Backups | Daily PostgreSQL dump + object storage snapshot; weekly restore test | Verified backup is a security requirement (§29). |

**Rationale for committing defaults:** An Engineering Proposal that defers technology choices to implementation risks making them without review. Committing defaults fixes the review boundary: any deviation from §39-A during implementation returns as a formal change proposal.

**Django vs FastAPI — trade-off note.** Django was chosen over FastAPI because the scarce resource in this phase is operator time (EP-08), and Django's built-in admin, auth, ORM, and migrations replace a substantial amount of hand-built scaffolding.

---

# 40. Scaling Path

```
V1 Modular Monolith (Django)
   → High-volume workflows
   → Dedicated workers (Celery or equivalent)
   → Specialized services where justified
   → Distributed architecture if required
```

No service is extracted merely because a capability has a separate name.

---

# 41. Engineering Traceability

| Contract | Primary Engineering Mechanism | Phase |
|----------|-------------------------------|-------|
| C-01 | Django admin + Context module | 0, 2 |
| C-02 | Product ingestion + Product module + `detect_product_changes` command | 0 (manual), 2 |
| C-03 | Deterministic evaluation engine | 0 (manual), 3 |
| C-04 | LLM generation + evidence validator | 0 (manual), 3 |
| C-05 | Content templates + AI generation + asset manager | 0 (manual), 4 |
| C-06 | Deterministic validation engine | 0 (manual), 5 |
| C-07 | Publication workflow + Pinterest adapter | 0 (manual), 5 |
| C-08 | Analytics collectors + normalization | 0 (manual), 6 |
| C-09 | Learning engine + operator review | 0 (manual), 7 |
| C-10 | Evidence repository + versioning | 0 (manual), 2 |
| C-11 | Versioned rubric configuration | 0 (manual), 3 |
| C-12 | Compliance rule engine + human review | 0 (manual), 5 |

---

# 42. Non-Goals

This Engineering Proposal does not define: a public SaaS offering; a marketplace for third-party users; a public Style Picks community; a complete consumer e-commerce storefront; a replacement for Pinterest; a replacement for Amazon; autonomous publishing without governance; unrestricted autonomous AI decision-making.

A public Style Picks website or landing page may be introduced later as a separate customer-facing surface.

---

# 43. Engineering Decision Summary

The proposed V1 architecture is:

> **A private, modular, AI-assisted commerce operations platform built on Django and PostgreSQL, with an operator dashboard, object storage, cron-driven background commands, deterministic contract enforcement, human approval gates, and adapters for Pinterest, Amazon, and AI providers.**

---

# 44. Engineering Proposal Acceptance Criteria

Implementable when:

1. Every Capability Contract has an identified execution mechanism.
2. Every persistent Part I record has a storage model.
3. Every sole-writer rule is enforceable.
4. Every publication gate is technically enforceable.
5. Every critical invariant has an executable validation mechanism.
6. Every external dependency has an integration boundary **and a stated fallback (§37-A)**.
7. Human-required decisions have an explicit workflow.
8. Scheduled operations have a scheduler and failure detection.
9. Contract failures can be recorded and escalated per §27.
10. Historical traceability is preserved.
11. The system can execute the complete MVP workflow, **or** the FOM where the MVP is deferred (§32-A).
12. External rule uncertainties are isolated from hard-coded assumptions, **and the specific rules governing the first Pin are verified before publication (§32-B)**.
13. The First Operational Milestone is achieved without depending on any unresolved external dependency.
14. Build effort is capped and phases are evidence-gated (§32-A).

---

# 45. Final Engineering Position

Style Picks is engineered as a:

> **Private Content Commerce Operations Platform**

whose first operational surface is a web dashboard, whose first external execution channels are Pinterest and Amazon, and whose first operational milestone is a manually-run Pin with a complete internal record trail.

The platform's fundamental engineering property is controlled traceability.

---

# 46. First Operational Milestone (FOM)

The First Operational Milestone is the state in which:

- The operator has published at least one Pin on Pinterest manually.
- Every internal record required by the Part I schemas exists for that Pin: Context, Product (with version), Evidence (primary and claim-level), Evaluation, Recommendation, Content Asset (with disclosure and tracking ID), Validation Result (PASS), Compliance Record (Approve), Publication Record (Live).
- The invariants **INV-1, INV-3, INV-4** have been validated by `check_invariants` before publication.
- The external rules governing the first Pin — disclosure wording, link format, image rules — have been verified (§32-B).
- Production time has been logged.
- The Pin is traceable end-to-end within the internal system.

**The FOM does not depend on:** Amazon Creators API access, Pinterest API access, AI providers, automated change detection, automated performance collection. All of these are handled through the fallbacks in §37-A.

**The FOM does depend on:** verification of the specific external rules governing the first Pin (§32-B).

**The FOM is the target of Phase 0.** It aligns with `A.4-CONTR-STYP-001` INV-13 (C-07 executes lifecycle transitions) and with the reconciled state of CP-001 and CP-003.

---

# 47. Change Proposals Against `A.4-CONTR-STYP-001`

Under EP-01, where this Engineering Proposal diverges from the Capability Contracts Specification, a formal change proposal is required.

## CP-001 — Re-evaluation vs Revocation on Superseded Evidence

**Divergence:** Section 19 describes two-step logic — re-point if successor supports the claim, Revoke otherwise. INV-12 in `A.4-CONTR-STYP-001` RC.4 stated that recommendations whose supporting evidence is superseded "MUST transition to Revoked."

**Proposed resolution:** Adopt the two-step logic. **Impact:** INV-12 and I.5 need rewording. **Status:** **Accepted 2026-10-08.** INV-12 in `A.4-CONTR-STYP-001` v1.0 Reconciled now formalizes the two-step logic. No divergence remains.

## CP-002 — AI-Generated Contextual Imagery

**Divergence:** This document permits AI-generated contextual imagery. `A.2-FUNC-STYP-001` §10.6 explicitly approved licensed or stock imagery as the primary source. Admitting AI imagery is a change to a decision, not a gap-fill. Pinterest has its own policies on AI-generated content labeling (CD4).

**Proposed resolution:** Amend `A.2-FUNC-STYP-001` §10.6 and corresponding contracts to admit AI-generated contextual imagery under labeling, non-substitution, and evidence-registration conditions, and to reference CD4 for labeling compliance.

**Impact:** Content Asset schema gains a `contextual_image_type` field; C-05 gains one clause; CD4 gains an explicit AI-content labeling reference.

**Status:** Pending. **Until accepted, only licensed and stock imagery are used.**

## CP-003 — Review Cleared Sole-Writer Assignment

**Divergence:** `A.4-CONTR-STYP-001` RC.4 C-06 postcondition #3 said C-06 "executes" the Review cleared event, contradicting INV-10 and INV-13.

**Proposed resolution:** Reword C-06 postcondition #3 to: *"C-06 issues a Validation Result with status = CLEARED; C-07 executes the corresponding lifecycle transition on the Publication Record."*

**Impact:** Documentation-only text change in `A.4-CONTR-STYP-001`.

**Status:** **Accepted 2026-10-08.** C-06 postcondition #3 has been reworded in `A.4-CONTR-STYP-001` v1.0 Reconciled. §13 of this document reflects the accepted wording.

---

# 48. Reference Note on Amazon API

PA-API is deprecated and replaced by **Creators API**. All references in documents `A.2-FUNC-STYP-001` through `A.4-CONTR-STYP-001` that mention PA-API should be read as referring to Creators API.

---

# 49. Reference Note on Pinterest Storefront Linking

Pinterest permits creators enrolled in the Amazon Influencer Program to connect an Amazon Storefront, after which affiliate attribution is applied automatically. If adopted, per-category tracking IDs may be bypassed and INV-3 may be affected. This is a business decision for the destination model in `A.2-FUNC-STYP-001`, not for this document. Until decided, Style Picks remains the source of truth for the tracking ID.

---

# 51. What Comes Next

This document closes the documentation phase of the Stage A pipeline:

```
A.1-BIZ-STYP-001        Business Plan
A.2-FUNC-STYP-001       Functional Specifications
A.3-CAP-STYP-001        Business Capabilities
A.4-CONTR-STYP-001      Capability Contracts
A.5-ENG-STYP-001        Engineering Proposal  ← this document (Baselined)
```

The next artifacts are not documents:

1. **External rule verification (§32-B)** — closes OI-003 through OI-007.
2. **The first Pin, published manually, with a complete internal record trail** (FOM, §46).
3. **The Phase 0 Django project** — initialized against §39-A, PostgreSQL, cron + management commands.

Any further document — technical design notes, implementation logs, runbooks — is produced **reactively**, driven by real implementation needs, not by documentary completeness.

---

## Freeze Note

**Version 1.3 is Baselined.** CP-001 and CP-003 are accepted and reflected in `A.4-CONTR-STYP-001` v1.0 Reconciled. CP-002 remains pending and does not block the start of Phase 0. The next review cycle is triggered by operational evidence, not by further drafting. The next thing to look at is not this document — it is the result of §32-B, the production-time log from the first ten Pins, and the operational reality of the compressed remaining window.

---

# 52. Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.5 — Engineering Definition

**Document ID:** A.5-ENG-STYP-001

**Version:** 1.3 — Engineering Definition Baseline (Reconciled)

**Status:** **Baselined**

**Authorization:** This document closes Stage A. `STAGE-A-CONSOL-REPORT-STYP-001` is authorized to consolidate Stage A and authorize Stage B (System Architecture — HLD).

**Blocking dependencies:** OI-001, OI-002 (both CLOSED).

**Pending Change Proposals:** CP-002.

**Accepted Change Proposals:** CP-001 (2026-10-08), CP-003 (2026-10-08).

**Language:** English

---

*End of Engineering Proposal — A.5-ENG-STYP-001 v1.3*

---

## Note on OI-001 and OI-002

> **OI-001 is CLOSED.** Amazon Associates account was created on **2026-04-15**.
>
> **OI-002 is CLOSED.** The survival deadline is **2026-10-12** (account date + 180 days).
>
> All checkpoints in this document are computed against this date. The operational start of October 7, 2026 is confirmed as **not** the survival clock. The remaining operating window from the operational start to the deadline is short; §32-A carries the note on checkpoint relevance, aligned with `A.1-BIZ-STYP-001` v1.5 §18 and `A.3-CAP-STYP-001` v1.2 §18.7.
