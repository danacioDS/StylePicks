# STYLE PICKS
## Business Capabilities Specification

**Stage A.3 — Capability Definition**
**Physical Foundation of the Style Picks Capability Model**

**Document ID:** A.3-CAP-STYP-001

**Version:** 1.1 RC.4 — Capability Definition Release Candidate

**Status:** Stage A — Engineering Definition (Conceptual Level) — Release Candidate

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Parent Documents:**
- A.2-FUNC-STYP-001 — Value Proposition Functional Specification (v1.1 RC)
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.0)

**Child Documents:**
- A.4-CONTR-STYP-001 — Capability Contracts Specification (v1.0 RC.4)

**Domain:** Domain A.3 — Business Capabilities

---

**Business Model:** Content Commerce + Affiliate Commerce
**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**Initial Categories:** Home Decor + Home Organization
**Stage:** Commercial Validation
**Operational Start:** October 7, 2026
**Document Type:** Business Capabilities Specification
**Derives from:** A.2-FUNC-STYP-001

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 7, 2026 | Initial capability decomposition |
| 1.1 RC | Oct 7, 2026 | Added Evidence Management, Publication & Lifecycle, Rubric Management; dependencies; destination clarification; evidence confidence; tracking ID; imagery metadata; capability-vs-business metrics |
| 1.1 RC.2 | Oct 7, 2026 | Moved evidence confidence to Recommendation Generation; aligned Evidence Source Policy with Functional Spec 9.6.2; separated runtime dependencies from feedback inputs; redefined uncomputable metrics; fixed cross-reference; clarified Validation → Publication handoff; added missing dependency; relocated Open Item #9; corrected status label; defined execution notation; formally separated core and transversal capabilities |
| 1.1 RC.3 | Oct 7, 2026 | Reconciled Medium confidence definition; added survival checkpoints to CD1; unified tracking ID source of truth; removed leftover verifiability threshold; enumerated Recommendation statuses; made reconciliation metric conditional; generalized opening statement of Section 5 to "operating loop" |
| 1.1 RC.4 | Oct 7, 2026 | Reclassified Performance Measurement → Compliance as a **monitoring input** (not a runtime dependency); fixed cross-reference to Functional Spec; documented runtime vs monitoring dependency in Section 19 |
| **1.1 RC.4 (Baselined header)** | Oct 8, 2026 | Normalized document header per Stage A codification; cross-references updated to A.x IDs; Open Items Register (`PH1-REG-STYP-001`) referenced; Change Proposals register referenced; Sign-Off block added |

---

## Open Items

> **This document cannot be treated as final while any of the following remain empty. The authoritative source is `PH1-REG-STYP-001`.**

| # | Open item | Priority | Owner | Status |
|---|-----------|----------|-------|--------|
| **OI-001** | Amazon Associates account creation date | **Blocking** | Editorial Owner | **EMPTY — CLOSE FIRST** |
| **OI-002** | Amazon Associates deadline (account date + 180 days) | **Blocking** | Editorial Owner | **EMPTY** |
| OI-003 | Verification: qualifying-sales rule | Defaultable | Editorial Owner | EMPTY |
| OI-004 | Verification: Creators API access requirements | Defaultable | Editorial Owner | EMPTY |
| OI-005 | Verification: image and price display rules | Defaultable | Editorial Owner | EMPTY |
| OI-006 | Verification: required disclosure wording | Defaultable | Editorial Owner | EMPTY |
| OI-007 | Verification: link-format rules | Defaultable | Editorial Owner | EMPTY |
| OI-008 | Evidence Source Policy — formalized (see 16.5) | Defaultable | Editorial Owner | EMPTY |

**Change Proposals affecting this document:**

| CP ID | Title | Status |
|-------|-------|--------|
| CP-002 | AI-Generated Contextual Imagery | Pending |

**Moved to Rubric Management backlog (not a document blocker):**
- Rubric V0.1 empirical validation (tracked in 17.13).

**Provisional operational rules (do not block release, subject to post-launch revision):**
- Corrective-action window: 72 hours (13.5).
- Post-publication validation cadence: weekly (12.7).

**Deferred to Capability Contracts (`A.4-CONTR-STYP-001`):**
- exact definition of a "material claim";
- exact definition of "factual error";
- exact calculation of evidence confidence;
- versioning semantics for Evidence Records;
- what constitutes a "material product change";
- precise lifecycle states for a published Pin.

---

# 1. Purpose

This document defines the **business capabilities required for Style Picks to repeatedly and reliably execute the business functions established in `A.2-FUNC-STYP-001` Value Proposition Functional Specification V1.1 Release Candidate**.

The document translates:

> **Business Functions → Business Capabilities**

without prescribing the technical architecture used to implement those capabilities.

> **Business capabilities describe what the business must be able to do consistently. Engineering determines how those capabilities are implemented.**

---

# 2. Relationship to Previous Specification

The Business Capabilities Specification derives directly from:

**`A.2-FUNC-STYP-001` — Value Proposition Functional Specification V1.1 Release Candidate**

That specification established eight business functions:

1. Context Definition
2. Discover
3. Select
4. Recommend
5. Present
6. Align
7. Learn
8. Govern

The present document decomposes them into stable capabilities. **The capability layer is not a one-to-one renaming of the functions.** It surfaces cross-cutting abilities that the function list did not name explicitly:

- **Evidence Management** — deferred from `A.2-FUNC-STYP-001` §9.6.2.
- **Publication & Lifecycle** — implicit in the Align failure path (`A.2-FUNC-STYP-001` §11.7) but never assigned.
- **Rubric Management** — a precondition of Evaluate in `A.2-FUNC-STYP-001` §7.6.4 that had no owner.

---

# 3. Capability Definition

For Style Picks, a **Business Capability** is defined as:

> **A stable organizational ability that enables Style Picks to repeatedly perform a defined business responsibility and produce a controlled business outcome.**

A capability is not: a software component, an AI agent, a workflow, an API, a database, a prompt, a human job title, or a specific implementation technology.

A capability may be implemented through any of the execution mechanisms defined in Section 4.10.

Those implementation decisions belong to the Engineering Proposal (`A.5-ENG-STYP-001`).

---

# 4. Capability Design Principles

## 4.1 Business-first definition
Capabilities are defined from business requirements rather than available technology.

## 4.2 Stable responsibility
A capability should represent a recurring business ability rather than a temporary operational task.

## 4.3 Clear boundaries
Each capability must have a defined responsibility and must not duplicate another capability unnecessarily.

## 4.4 Contract readiness
Each capability must be sufficiently defined to support a future **Capability Contract** (`A.4-CONTR-STYP-001`).

## 4.5 Evidence-based operation
Where a capability produces factual or commercial decisions, those decisions must be traceable to appropriate business evidence.

## 4.6 Human accountability
Automation does not eliminate business ownership. Each capability must have an accountable owner.

## 4.7 Measurability
Each capability must have measurable indicators that allow operational quality to be evaluated. **Capability metrics measure whether the capability is working, not whether the business is succeeding.**

## 4.8 Implementation neutrality
No capability definition may require a particular technical architecture unless that requirement is itself a business constraint.

## 4.9 Cross-cutting capabilities are surfaced
When a business ability cuts across multiple functions, the capability layer names it explicitly rather than distributing it implicitly.

## 4.10 Execution Type Notation

| Notation | Meaning |
|----------|---------|
| **H** | Human execution |
| **D** | Deterministic execution (rules, calculations, scripts) |
| **AI** | Probabilistic/LLM-assisted execution |
| **H+D** | Human-led with deterministic support |
| **H+AI** | Human-led with AI-assisted drafting |
| **H+D+AI** | Human-led with both deterministic and AI support |
| **D+H** | Deterministic with human exception handling |

---

# 5. Capability Map

The Style Picks capability model distinguishes two formal categories:

- **Core Execution Capabilities** — the operating loop that transforms emerging consumer demand and editorial context into curated product discovery, published content, measurable commercial signals, and continuous improvement.
- **Cross-Cutting Capabilities** — abilities that operate across the core sequence.

## 5.1 Core Execution Capabilities

```text
                    STYLE PICKS
                         │
                         ↓
              ┌─────────────────────┐
              │ Context Management   │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Product Discovery   │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Product Evaluation  │
              │ & Curation          │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Recommendation      │
              │ Generation          │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Content Presentation│
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Consistency         │
              │ Validation          │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Publication &       │
              │ Lifecycle           │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Performance         │
              │ Measurement         │
              └──────────┬──────────┘
                         ↓
              ┌─────────────────────┐
              │ Learning &          │
              │ Improvement         │
              └─────────────────────┘
```

## 5.2 Cross-Cutting Capabilities

```text
       ┌────────────────────────────────────────────┐
       │ Compliance & Governance                    │
       │ Cross-Cutting Control Capability           │
       └────────────────────────────────────────────┘

       ┌────────────────────────────────────────────┐
       │ Evidence Management                        │
       │ Cross-Cutting Control Capability           │
       └────────────────────────────────────────────┘

       ┌────────────────────────────────────────────┐
       │ Rubric Management                          │
       │ Cross-Cutting Control Capability           │
       └────────────────────────────────────────────┘
```

**Total: 9 core execution capabilities + 3 cross-cutting capabilities = 12 capabilities.**

---

# 6. Function-to-Capability Mapping

| Business Function | Primary Capability | Cross-Cutting Dependency |
|---|---|---|
| Context Definition | Context Management | — |
| Discover | Product Discovery | Evidence Management |
| Select | Product Evaluation & Curation | Rubric Management, Evidence Management |
| Recommend | Recommendation Generation | Evidence Management |
| Present | Content Presentation | — |
| Align | Consistency Validation | — |
| Publication (implicit in Spec) | Publication & Lifecycle | Compliance & Governance |
| Learn | Performance Measurement & Attribution | — |
| Learn | Learning & Improvement | Rubric Management |
| Govern | Compliance & Governance | Evidence Management |

---

# 7. Capability 1 — Context Management

## 7.1 Purpose
Maintain structured definitions of the consumer situations that Style Picks intends to address.

## 7.2 Business Responsibility
Establishes the business context within which products are discovered, evaluated, recommended, and presented. **Contexts may originate from emerging consumer demand signals (Pinterest trends, seasonal demand, historical performance) as well as from editorial judgment.**

## 7.3 Inputs
Consumer needs, observed problems, editorial strategy, market signals, trends, historical performance, category opportunities, business constraints.

## 7.4 Outputs
A structured **Context Record** containing:

- context identifier (unique);
- context name;
- consumer problem or need;
- desired outcome;
- applicable category;
- relevant constraints;
- approved price range;
- editorial opportunity;
- status;
- owner;
- creation date;
- version.

## 7.5 Business Rules
A context must: belong to an approved business category; describe a recognizable consumer situation; have a defined intended outcome; contain sufficient information for product discovery; have an accountable owner.

## 7.6 Preconditions
A context may enter operational use only after editorial approval.

## 7.7 Postconditions
An approved context must be available as a stable input to Product Discovery.

## 7.8 Dependencies

**Runtime dependencies** (block operation if missing): none.

**Feedback inputs** (improve operation over time): Learning & Improvement.

## 7.9 Owner
**Editorial Owner**

## 7.10 Execution Type
H+D, H+AI, or H+D+AI (Engineering discretion).

## 7.11 Metrics
- contexts created per period;
- context approval rate;
- context revision rate (pre-approval);
- context-to-content traceability.

## 7.12 Failure Modes
- ambiguous context;
- duplicate context;
- unsupported consumer problem;
- context outside approved categories;
- missing constraints;
- outdated context.

---

# 8. Capability 2 — Product Discovery

## 8.1 Purpose
Identify product candidates that may address an approved consumer context.

## 8.2 Business Responsibility
Converts an approved context into a normalized candidate product set.

## 8.3 Inputs
Context Record, category, search concepts, approved product sources, product information, market information.

## 8.4 Outputs
A **Product Candidate Set** containing normalized product records. Each candidate should contain, where available:

- product identifier (internal, unique);
- ASIN;
- product name;
- category;
- price information;
- rating;
- review count;
- dimensions;
- relevant features;
- source;
- source timestamp;
- **approved destination reference** (see 11.6);
- evidence references.

## 8.5 Business Rules
Products must: belong to an approved category; originate from an accepted source; contain sufficient factual information for subsequent evaluation; be distinguishable from duplicate candidates.

## 8.6 Preconditions
An approved Context Record must exist.

## 8.7 Postconditions
Candidate products must be available for evaluation. **Every candidate must carry at least one evidence reference.**

## 8.8 Dependencies

**Runtime dependencies:**
- **Context Management** (upstream).
- **Evidence Management** (upstream — see 8.13).

**Feedback inputs:** Learning & Improvement.

## 8.9 Owner
**Editorial Owner**

## 8.10 Execution Type
H initially; D and H+D in later stages.

## 8.11 Metrics
- candidates discovered per context;
- candidate normalization completeness;
- duplicate rate;
- discovery time;
- source coverage;
- evidence-reference completeness.

## 8.12 Failure Modes
- incomplete product data;
- duplicate products;
- inaccessible source;
- incorrect product identification;
- outdated information;
- candidate outside approved category;
- missing evidence reference.

## 8.13 Evidence Registration Ordering

> **Primary evidence** — raw facts retrieved from a source (e.g., an Amazon product page snapshot) — may be registered **independently of whether a recommendation exists**. Product Discovery registers primary evidence as part of candidate creation. Recommendation Generation later registers **claim-level evidence** — the specific facts that support the specific claims being made — by linking to the primary evidence already registered.

There is no circular dependency. Evidence Management is foundational; Product Discovery and Recommendation Generation consume it at different levels of abstraction.

---

# 9. Capability 3 — Product Evaluation & Curation

## 9.1 Purpose
Determine which discovered products meet Style Picks' editorial standards.

## 9.2 Business Responsibility
Applies the active Editorial Rubric and hard constraints to candidate products.

## 9.3 Inputs
Product Candidate Set, Context Record, active Editorial Rubric, factual product attributes, evidence records, hard constraints.

## 9.4 Outputs
An **Evaluation Record** containing:

- evaluation identifier (unique);
- product identifier;
- rubric version used;
- criterion scores (including **factual verifiability score**);
- weighted score;
- hard-constraint status;
- eligibility status;
- rejection reason where applicable;
- evaluator (human or process);
- evaluation timestamp.

> **Note:** Evaluation produces the **verifiability score** (how verifiable the product's claims are, in the abstract), not evidence confidence. Evidence confidence is computed by Recommendation Generation over the claims actually made — see 10.6.

## 9.5 Business Rules
The capability must enforce: approved category; approved price range; minimum rating; minimum review count; prohibited-category restrictions; minimum weighted editorial score; claim substantiation requirements.

## 9.6 Decision States
A candidate may be: **Eligible**, **Rejected**.

Candidates whose weighted score falls below the minimum eligibility threshold (`A.2-FUNC-STYP-001` §7.6.2) are Rejected. **The factual verifiability criterion contributes to the weighted score only; it is not a standalone hard constraint.**

> **Note:** "Human Review Required" is **not** a state of Evaluation. It is a routing state produced by Recommendation Generation when evidence confidence is Low (`A.2-FUNC-STYP-001` §9.6).

## 9.7 Preconditions
- Valid Product Record exists.
- Valid Context Record exists.
- Active Editorial Rubric exists (provided by Rubric Management).
- Evidence records for the candidate exist (provided by Evidence Management).

## 9.8 Postconditions
Every evaluated candidate has a documented decision. The Evaluation Record is available to Recommendation Generation.

## 9.9 Dependencies

**Runtime dependencies:**
- **Product Discovery** (upstream).
- **Rubric Management** (upstream — supplies the active rubric).
- **Evidence Management** (upstream — supplies evidence records).

**Feedback inputs:** Learning & Improvement.

## 9.10 Owner
**Editorial Owner**

## 9.11 Execution Type
H+D+AI.

## 9.12 Metrics
- evaluation completion rate;
- rejection rate;
- average evaluation score;
- hard-constraint violation rate;
- review overturn rate;
- evidence-reference completeness;
- rubric-version consistency.

## 9.13 Failure Modes
- incomplete evaluation;
- rubric misapplication;
- unsupported score;
- hard constraint missed;
- inconsistent evaluation;
- stale product information;
- rubric version drift.

---

# 10. Capability 4 — Recommendation Generation

## 10.1 Purpose
Transform an eligible product into a contextual, evidence-supported recommendation.

## 10.2 Business Responsibility
Explains why a selected product is relevant to a specific consumer context.

## 10.3 Inputs
Context Record, Product Record, Evaluation Record, evidence records, editorial criteria, limitations, applicable business rules.

## 10.4 Outputs
A **Recommendation Record** containing:

- recommendation identifier (unique);
- product identifier;
- context identifier;
- recommendation statement;
- rationale;
- supporting facts (each linked to an evidence reference);
- limitations;
- editorial score (from Evaluation Record);
- **evidence confidence** (computed here — see 10.6);
- **recommendation status** (enumerated in 10.5);
- creation timestamp.

## 10.5 Recommendation Status (Enumerated)

A Recommendation Record is always in exactly one of the following states:

| State | Meaning |
|-------|---------|
| **Draft** | Being written. Not yet eligible for Content Presentation. |
| **Low-Confidence** | Written, but evidence confidence = Low. Awaiting human review. |
| **Human-Review-Approved** | Reviewed and accepted despite Low evidence confidence. Eligible for Content Presentation. |
| **Approved** | Evidence confidence = High or Medium. Eligible for Content Presentation. |
| **Rejected** | Withdrawn before Content Presentation. |

## 10.6 Evidence Confidence (Computed Here)

| Evidence Confidence | Condition | Reachable under interim policy |
|---------------------|-----------|-------------------------------|
| **High** | Every material claim is traceable to an Evidence Record classified **Verified** (Amazon product page or manufacturer site). | **Yes** |
| **Medium** | Every material claim is traceable to an Evidence Record, and at least one is Limited Reliability. | **No** — no source is currently classified Limited Reliability. |
| **Low** | At least one material claim is traceable only to an **Unverified** source. | **Yes** |

**Postcondition failure — no evidence record:** If a material claim has **no** Evidence Record at all, the Recommendation Record cannot be finalized. This is a **postcondition failure**, not a Low-confidence outcome. It is caught before routing.

**Routing rule:**

| Editorial Score | Evidence Confidence | Routing |
|-----------------|---------------------|---------|
| ≥ 3.5 | High | Status → **Approved** |
| ≥ 3.5 | Medium | (Not reachable under interim policy) |
| ≥ 3.5 | Low | Status → **Low-Confidence**; routes to human review |
| < 3.5 | any | **Rejected** |
| any | hard constraint violated | **Rejected** |

A human review that accepts a Low-Confidence recommendation moves its status to **Human-Review-Approved**.

## 10.7 Preconditions
The product must have passed Product Evaluation & Curation (state = Eligible). An Evaluation Record must exist.

## 10.8 Postconditions
Every material claim in the Recommendation Record must reference at least one Evidence Record. Evidence confidence must be recorded. Recommendation status must be one of the states in 10.5.

## 10.9 Dependencies

**Runtime dependencies:**
- **Product Evaluation & Curation** (upstream).
- **Evidence Management** (upstream).

**Feedback inputs:** Learning & Improvement.

> **Note on boundary:** Recommendation Generation **reads** the Product Record and **writes** to the Recommendation Record. It does **not** write to the Product Record.

## 10.10 Owner
**Editorial Owner**

## 10.11 Execution Type
H+D+AI.

## 10.12 Metrics
- recommendation approval rate;
- factual error rate;
- context-match rate;
- evidence completeness;
- human correction rate;
- human-review pass rate;
- production time.

## 10.13 Failure Modes
- unsupported claim;
- incorrect product attribute;
- context mismatch;
- omission of material limitation;
- evidence-confidence miscalculation;
- **recommendation produced with a material claim lacking an Evidence Record** (postcondition failure);
- recommendation produced for a candidate not in the Eligible state;
- editorial inconsistency.

---

# 11. Capability 5 — Content Presentation

## 11.1 Purpose
Transform an approved recommendation into a consumer-facing discovery asset suitable for Pinterest.

## 11.2 Business Responsibility
Determines how the recommendation is visually and editorially communicated.

## 11.3 Inputs
Recommendation Record, Product Record, Context Record, brand identity, Pinterest requirements, approved imagery, content format, **approved destination reference (from the Product Record — see 11.6)**.

## 11.4 Outputs
A **Content Asset** containing:

- asset identifier (unique);
- title;
- description;
- product representation (with source metadata);
- contextual imagery (with source metadata);
- editorial framing;
- call to action;
- **affiliate destination URL** (derived from the Product Record's approved destination reference — see 11.6);
- **tracking ID** (derived from the same reference — see 11.6);
- required metadata;
- creation timestamp.

## 11.5 Business Rules
The asset must: accurately represent the recommended product; use permitted imagery; avoid misleading visual substitution; preserve the recommendation's meaning; carry the affiliate destination URL; carry the correct tracking ID; comply with approved content standards.

Prices are not displayed in Pins under the Stage A functional rule.

## 11.6 Destination and Tracking ID — Single Source of Truth

**Source of truth:** The **Product Record** holds an **approved destination reference** for each product. That reference contains both the affiliate destination URL and the tracking ID embedded in that URL.

Content Presentation **derives both** from this single reference. It does not choose either.

Consistency Validation **verifies** that the tracking ID in the Content Asset matches the tracking ID embedded in the affiliate URL, and that both match the Product Record's approved destination reference.

> **Business framing:** The Product Record identifies the approved destination associated with the selected product. How that destination is materialized is an Engineering decision.

## 11.7 Preconditions
A valid Recommendation Record exists, in state **Approved** or **Human-Review-Approved**.

## 11.8 Postconditions
A publication-ready asset exists and is available to Consistency Validation. The tracking ID and affiliate URL embedded in the asset are consistent with the Product Record.

## 11.9 Dependencies

**Runtime dependencies:**
- **Recommendation Generation** (upstream).
- **Evidence Management** (upstream — imagery permissions and product image sources are evidence records).

**Feedback inputs:** Learning & Improvement.

## 11.10 Owner
**Editorial Owner**

## 11.11 Execution Type
H+D+AI.

## 11.12 Metrics
- production time per asset;
- asset completion rate;
- first-pass validation rate;
- visual quality review rate;
- tracking ID assignment completeness (100% target);
- publication rate.

## 11.13 Failure Modes
- wrong product image;
- misleading composition;
- missing affiliate destination URL;
- missing or incorrect tracking ID;
- tracking ID mismatch between URL and asset metadata;
- content mismatch;
- unauthorized imagery;
- incomplete metadata.

---

# 12. Capability 6 — Consistency Validation

## 12.1 Purpose
Verify internal consistency across the consumer-facing recommendation chain.

## 12.2 Business Responsibility
Verifies: **Promise → Content → Recommendation → Product → Destination**

## 12.3 Inputs
Content Asset, Recommendation Record, Product Record, destination URL, relevant metadata.

## 12.4 Outputs
A **Validation Result** containing:

- validation identifier (unique);
- asset identifier;
- validation phase (pre-publication or post-publication);
- validation status;
- checks performed (list);
- detected inconsistencies;
- severity;
- corrective action (where applicable);
- validation timestamp.

## 12.5 Decision States
**PASS** / **FAIL**

## 12.6 Business Rules
Validation must confirm, in order:

1. Pin promise corresponds to content.
2. Content corresponds to recommendation.
3. Recommendation corresponds to product.
4. Product corresponds to destination.
5. Destination is reachable.
6. Tracking ID embedded in the affiliate URL matches the tracking ID carried in the Content Asset metadata.
7. Material product changes have not invalidated the recommendation.

## 12.7 Timing

Validation runs in **two phases**:

- **Pre-publication**: before the Pin is published.
- **Post-publication**: at a weekly cadence or on-demand when a Product Record change is detected.

> **Provisional operational cadence:** weekly post-publication validation is the default for Stage A, subject to revision after the first 30 days of live operation.

## 12.8 Failure Path — Post-Publication

| Failure type | Corrective action | Handed to |
|--------------|-------------------|-----------|
| Product out of stock (temporary) | No action; monitor | — |
| Product discontinued permanently | Archive Pin | Publication & Lifecycle |
| Destination URL broken | Re-link to current product URL | Publication & Lifecycle |
| Product materially changed | Archive Pin and create new content | Publication & Lifecycle |
| Recommendation no longer accurate | Archive Pin | Publication & Lifecycle |
| Tracking ID mismatch detected post-publication | Re-link Pin to corrected URL | Publication & Lifecycle |

> Consistency Validation **detects** failures and hands the corrective action to **Publication & Lifecycle**, which executes it.

## 12.9 Preconditions
Content Asset and Recommendation Record exist. For post-publication validation, a published Pin exists.

## 12.10 Postconditions
The asset has an explicit validation state. Post-publication failures have been handed to Publication & Lifecycle with a corrective action specified. The Validation Result is the handoff artifact consumed by Publication & Lifecycle.

## 12.11 Dependencies

**Runtime dependencies:**
- **Content Presentation** (upstream).
- **Evidence Management** (for the imagery and product-fact references used in validation).

**Feedback inputs:** Learning & Improvement.

## 12.12 Owner
**Editorial Owner**

## 12.13 Execution Type
D+H.

## 12.14 Metrics
- first-pass validation rate;
- inconsistency rate;
- broken destination rate;
- tracking ID mismatch detection rate;
- corrective action rate;
- post-publication failure rate;
- post-publication failure detection latency.

## 12.15 Failure Modes
- incorrect destination;
- product/content mismatch;
- stale recommendation;
- broken URL;
- misleading product representation;
- tracking ID mismatch between URL and asset;
- failed corrective handoff.

---

# 13. Capability 7 — Publication & Lifecycle

## 13.1 Purpose
Publish approved content and execute post-publication corrective actions.

## 13.2 Business Responsibility
Bridges the gap between "approved asset" and "live asset on Pinterest," and maintains published Pins over time.

## 13.3 Inputs
Approved Content Asset (with tracking ID), Validation Result (PASS), Compliance Record (Approve), corrective actions from Consistency Validation.

## 13.4 Outputs
A **Publication Record** containing:

- publication identifier (unique);
- asset identifier;
- tracking ID used;
- Pin URL;
- publication timestamp;
- publication status;
- lifecycle events (archive, re-link, replace, no-action-monitor) with timestamps;
- current lifecycle state.

## 13.5 Business Rules
A Pin may be published only when:

- Consistency Validation = **PASS**;
- Compliance & Governance = **Approve**;
- the tracking ID is present and matches the active tracking strategy.

A corrective action from Consistency Validation must be executed within a defined window or escalated.

> **Provisional operational rule:** the corrective-action window is **72 hours**, subject to revision after the first 30 days of live operation.

## 13.6 Preconditions
A Content Asset exists with: a passing Validation Result; an approving Compliance Record; a correct tracking ID.

## 13.7 Postconditions
A Publication Record exists with the current lifecycle state. Corrective actions are recorded with outcome.

## 13.8 Dependencies

**Runtime dependencies:**
- **Content Presentation** (upstream — supplies the asset).
- **Consistency Validation** (upstream — supplies the PASS and the corrective actions).
- **Compliance & Governance** (upstream — supplies the Approve).

**Downstream consumers:** Performance Measurement & Attribution.

**Feedback inputs:** Learning & Improvement.

> **Note on the publishing gate:** The publication gate is satisfied by Align = PASS and Govern = Approve. Performance Measurement is **not** a precondition for publication — it consumes published content, it does not gate it.

## 13.9 Owner
**Editorial Owner**

## 13.10 Execution Type
H+D.

## 13.11 Metrics
- publication success rate;
- gate-consistency rate;
- tracking ID correctness at publication (100% target);
- corrective-action execution rate;
- corrective-action latency;
- lifecycle event rate.

## 13.12 Failure Modes
- publication without both gates passing;
- publication with incorrect or missing tracking ID;
- publication URL mismatch;
- corrective action not executed within window;
- corrective action executed incorrectly;
- lifecycle state not updated after action;
- orphaned Pin.

---

# 14. Capability 8 — Performance Measurement & Attribution

## 14.1 Purpose
Capture and organize performance information required to evaluate Style Picks' commercial validation.

## 14.2 Business Responsibility
Converts platform and affiliate performance signals into structured business performance records.

## 14.3 Inputs
Pinterest impressions, Pinterest saves, Pinterest outbound clicks, Amazon clicks, Amazon qualifying purchases, Amazon revenue, tracking IDs, ASINs, production data, Publication Records.

## 14.4 Outputs
A **Performance Record** containing:

- performance identifier (unique);
- reporting period;
- **attribution unit** (tracking ID, ASIN, or Pin-level Pinterest engagement — see 14.5);
- metric name;
- metric value;
- source (Pinterest or Amazon);
- collection timestamp.

## 14.5 Stage A Attribution Scope
Supported: **tracking-ID-level** Amazon data; **ASIN-level** product data; **Pin-level** Pinterest engagement.

Not fully supported without additional tracking infrastructure: exact context-level Amazon attribution; exact content-format Amazon attribution; **Pin-level Amazon attribution**.

## 14.6 Business Rules
Every published Pin must have the correct tracking identifier according to the active tracking strategy. Performance data must be collected at a defined cadence and reconciled against Publication Records **at the tracking-ID level**.

## 14.7 Preconditions
Published content contains valid tracking metadata. Publication Records exist for the period being measured.

## 14.8 Postconditions
Performance data is available for analysis at the supported attribution level. Data completeness and freshness are known.

## 14.9 Dependencies

**Runtime dependencies:**
- **Publication & Lifecycle** (upstream).
- **External sources**: Pinterest analytics, Amazon Associates reports.

**Monitoring outputs** (not runtime dependencies of any capability, but consumed by CD1):
- Performance Records feed CD1's survival-checkpoint monitoring (see 18.7). This is a **monitoring relationship**, not a runtime dependency: no publication is gated by Performance Measurement, and no capability is blocked if measurement data is late.

**Feedback inputs:** Learning & Improvement.

## 14.10 Owner
**Editorial Owner**

## 14.11 Execution Type
D+H.

## 14.12 Metrics

> **These metrics measure whether measurement is working, not whether the business is succeeding.**

- **tracking-ID attribution completeness** — % of active tracking IDs with Amazon-side data returned.
- **tracking-ID reconciliation errors** — active tracking IDs where **Pinterest shows outbound clicks > 0** but Amazon records no clicks, **or** Amazon records clicks for a tracking ID not in the active list.
- **data freshness** — time since last collection.
- **coverage** — % of the reporting period with complete data.
- **ID integrity** — % of published Pins whose tracking ID matches the Publication Record.

## 14.13 Failure Modes
- missing tracking ID;
- incorrect tracking ID;
- incomplete data;
- inconsistent identifiers;
- unavailable performance data;
- stale data;
- unreconciled data.

---

# 15. Capability 9 — Learning & Improvement

## 15.1 Purpose
Convert observed performance into evidence-based improvements to Style Picks' editorial decisions.

## 15.2 Business Responsibility
Identifies patterns, generates hypotheses, evaluates evidence, and proposes changes to editorial practice.

## 15.3 Inputs
Performance Records, Evaluation Records, Recommendation Records, Publication Records, historical content, active Editorial Rubric, operational metrics, failure records.

## 15.4 Outputs
A **Learning Record** containing:

- learning identifier (unique);
- observed pattern;
- evidence (linked to Performance Records);
- hypothesis;
- confidence;
- proposed action;
- affected capability;
- affected rubric or rule;
- owner;
- status;
- creation timestamp.

## 15.5 Business Rules
Learning must: distinguish observation from interpretation; distinguish correlation from demonstrated causation; identify attribution limitations; avoid modifying business rules solely on insufficient evidence; document material rubric changes.

## 15.6 Preconditions
Relevant performance and operational data must exist.

## 15.7 Postconditions
Insights are documented and either accepted for action, rejected, deferred, or escalated for additional evidence. Accepted rubric change proposals are handed to Rubric Management as feedback inputs.

## 15.8 Dependencies

**Runtime dependencies** (block operation if missing):
- **Performance Measurement & Attribution** (upstream — supplies Performance Records).

**Feedback outputs** (not runtime dependencies):
- Rubric change proposals to **Rubric Management**.

## 15.9 Owner
**Editorial Owner**

## 15.10 Execution Type
H+D+AI.

## 15.11 Metrics
- number of validated insights;
- hypothesis-to-action rate;
- rubric improvement proposals produced;
- repeated failure reduction;
- performance improvement after changes.

## 15.12 Failure Modes
- false attribution;
- insufficient evidence;
- overfitting;
- undocumented rule changes;
- confusing correlation with causation.

---

# 16. Capability 10 — Evidence Management

## 16.1 Purpose
Maintain the record of factual evidence that supports product claims, recommendations, and content.

## 16.2 Business Responsibility
Provides a single, governed source of truth for all factual claims made by Style Picks about products.

> **This capability was deferred from `A.2-FUNC-STYP-001` §9.6.2.**

## 16.3 Inputs
Amazon product page data, manufacturer specifications, source metadata, source reliability classification, license and permission metadata for imagery.

## 16.4 Outputs
An **Evidence Record** containing:

- evidence identifier (unique);
- **evidence type** (primary or claim-level);
- claim being supported (for claim-level evidence);
- source (name and URL);
- source classification (Verified / Unverified — see 16.5);
- retrieval timestamp;
- content snapshot (where permitted);
- license or permission (for imagery);
- applicable constraints;
- linked product identifier;
- linked recommendation identifier (where applicable).

## 16.5 Evidence Source Policy (Interim)

> **This policy is aligned with `A.2-FUNC-STYP-001` §9.6.2.** Formalizing it is **OI-008** in `PH1-REG-STYP-001`.

**Verified sources:**
- Amazon product page;
- Manufacturer's official site.

**Unverified sources:**
- Customer reviews;
- Third-party publications;
- Pinterest posts;
- LLM-generated information without a verifiable source;
- Unknown or unattributed sources.

**Rule:** Any material claim sourced from anything other than Amazon's product page or the manufacturer's official site **lowers Evidence Confidence to Low**, which routes the recommendation to human review.

> **On the "Limited Reliability" tier:** Preserved in the schema as a **future** classification. Not currently mapped to any source. Operational tiers today are **Verified** and **Unverified**.

> **On fact volatility (deferred):** Source reliability and fact volatility are distinct dimensions. Price, availability, and rating are volatile even when sourced from a Verified source. Distinguishing these belongs to a future Evidence Source Policy.

## 16.6 Business Rules
Every factual claim must reference at least one Evidence Record. Imagery must have recorded license and permission metadata. Evidence records must be versioned when sources change. Primary evidence may be registered independently of any recommendation (see 8.13).

## 16.7 Preconditions
A claim exists that requires factual support, **or** primary evidence is being registered for a discovered product.

## 16.8 Postconditions
An Evidence Record exists and is available to the capabilities that consume it. Evidence records are never deleted; they are superseded.

## 16.9 Dependencies

**Runtime dependencies:** external sources (Amazon, manufacturer sites, licensed imagery providers).

**Consumers** (downstream): Product Discovery, Product Evaluation, Recommendation Generation, Content Presentation, Consistency Validation, Compliance & Governance.

## 16.10 Owner
**Editorial Owner**

## 16.11 Execution Type
H+D+AI.

## 16.12 Metrics
- evidence records created per period;
- coverage;
- source classification completeness;
- evidence reuse rate;
- staleness.

## 16.13 Failure Modes
- unsupported claim;
- missing evidence record;
- misclassified source;
- stale evidence;
- missing imagery license metadata;
- duplicate evidence records;
- evidence not versioned after source change.

---

# 17. Capability 11 — Rubric Management

## 17.1 Purpose
Maintain the Editorial Recommendation Rubric as a versioned, evidence-justified business artifact.

## 17.2 Business Responsibility
Owns the life cycle of the rubric: authoring, versioning, activation, change log, and retirement of prior versions.

## 17.3 Inputs
Active rubric (current version), Learning Record proposals (as feedback inputs), Editorial Owner decisions, observed evaluation outcomes.

## 17.4 Outputs
A **Rubric Version Record** containing:

- rubric version identifier;
- effective date;
- criteria with weights;
- hard constraints;
- minimum thresholds;
- change justification;
- approver;
- status (Draft / Active / Retired);
- change log entry.

## 17.5 Business Rules
Only one rubric version may be Active at a time. Any change to weights, thresholds, or hard constraints requires: a documented justification, an approval by the Editorial Owner, and a change log entry. Retired versions are preserved for audit.

## 17.6 Preconditions
A change proposal exists from Learning & Improvement (feedback), or an initial rubric is being established.

## 17.7 Postconditions
An Active rubric version exists and is available to Product Evaluation & Curation.

## 17.8 Dependencies

**Runtime dependencies** (block operation if missing): none.

**Feedback inputs** (improve operation over time): **Learning & Improvement**.

Rubric V0.1 is authored from business judgment. Learning improves subsequent versions but is not required to author V0.1.

## 17.9 Owner
**Editorial Owner**

## 17.10 Execution Type
H.

## 17.11 Metrics
- rubric versions created per period;
- approval-to-activation time;
- change log completeness;
- evaluation-rubric-version match;
- retroactive corrections rate.

## 17.12 Failure Modes
- two Active versions simultaneously;
- change without justification;
- change without approval;
- missing change log entry;
- retired version not preserved;
- evaluation performed against a retired version.

## 17.13 Backlog
- Rubric V0.1 empirical validation. Cannot be completed until validation data exists.

---

# 18. Capability 12 — Compliance & Governance

## 18.1 Purpose
Ensure that Style Picks operates within applicable external rules and internal business constraints.

## 18.2 Business Responsibility
Provides cross-cutting control across the core execution capabilities.

## 18.3 Control Domains

| # | Control Domain | Rules applied |
|---|----------------|---------------|
| CD1 | **Amazon Associates — Eligibility & Survival** | Qualifying-sales rule; account deadline; API access conditions; survival checkpoints (see 18.7) |
| CD2 | **Amazon Associates — Content Rules** | Image display rules; price display rules; link format rules; required disclosure |
| CD3 | **FTC Endorsement Disclosure** | Endorsement and testimonial disclosure (US) |
| CD4 | **Pinterest Policies** | Affiliate content policies; format requirements |
| CD5 | **Factual Integrity** | Claims supported by Evidence Records; source traceability |
| CD6 | **Editorial Governance** | Internal content standards; rubric application; prohibited claims |

Each domain has its own verification record, last-verified date, and escalation conditions.

## 18.4 Inputs
External policies, business rules, editorial rules, Content Assets, Recommendations, Product Records, Evidence Records, compliance requirements, **Performance Records (as a monitoring input for CD1 survival checkpoints — see 18.7)**.

## 18.5 Outputs
A **Compliance Record** containing:

- compliance identifier (unique);
- asset or recommendation identifier;
- control domains checked;
- checks performed within each domain;
- applicable rules at the time of check;
- rule version or verification date per domain;
- decision (Approve / Reject / Correct / Escalate);
- error code (where applicable);
- compliance evidence;
- timestamp;
- reviewer (human or process).

## 18.6 Business Rules
Compliance & Governance enforces: Amazon Associates Operating Agreement rules; FTC endorsement disclosure requirements; Pinterest policies on affiliate content; internal editorial rules.

**No asset may be published without a Compliance Record with decision = Approve.**

## 18.7 Survival Checkpoints (CD1)

> **Restored from `A.2-FUNC-STYP-001` §13.6 and §18.3.** Compliance & Governance monitors these checkpoints. Performance Measurement provides the data **as a monitoring input** — the checkpoints never gate a publication and are not a runtime prerequisite for any other capability.

| Deadline minus | Condition | Action |
|----------------|-----------|--------|
| **135 days** | Outbound clicks well below expected (< 20 total) | Escalate — strategic review |
| **135 days** | Outbound clicks present but attribution ratio < 50% | Escalate immediately — tracking failure |
| **90 days** | Zero qualifying purchases | Escalate — strategic review |
| **60 days** | Fewer than 2 qualifying purchases | Escalate — strategic review |
| **30 days** | Fewer than 3 qualifying purchases | Escalate — survival threshold at risk |

> **Survival floor:** 3 qualifying purchases is the minimum to keep the Associates account, not evidence that the value proposition works.

## 18.8 Decision States
**Approve** / **Reject** / **Correct** / **Escalate**

## 18.9 Escalation Rules

| Condition | Action |
|-----------|--------|
| Hard constraint violation | Block and escalate |
| Soft constraint violation | Return with error code |
| Recurring violation of the same rule | Escalate and trigger rubric review |
| Stale external rule (used beyond verification date) | Escalate and update Open Items |
| **Survival checkpoint triggered (18.7)** | Escalate to Editorial Owner |

## 18.10 Preconditions
A Content Asset or Recommendation exists that is being considered for publication. **For CD1 survival checkpoints, Performance Records must exist for the current period.**

## 18.11 Postconditions
A Compliance Record exists with a decision. If Approve, the asset is eligible for Publication & Lifecycle (in combination with Consistency Validation = PASS).

## 18.12 Dependencies

**Runtime dependencies:**
- **Content Presentation** (upstream — supplies the Content Asset that is checked).
- **Evidence Management** (upstream — supplies evidence for claim verification).
- **External sources**: Amazon Associates Operating Agreement, FTC guidance, Pinterest policies.

**Monitoring inputs** (not runtime dependencies):
- **Performance Measurement & Attribution** — supplies data for CD1 survival checkpoints. Late or missing measurement data does not block any compliance check that gates publication.

**Feedback inputs:** Learning & Improvement.

## 18.13 Owner
**Editorial Owner**

## 18.14 Execution Type
D+H.

## 18.15 Metrics
- compliance check completion rate;
- violation rate;
- rule coverage;
- verification freshness per control domain;
- escalation rate;
- corrective-action rate;
- survival checkpoint monitoring rate.

## 18.16 Failure Modes
- missing disclosure;
- incorrect disclosure placement or wording;
- non-conforming link format;
- non-conforming image use;
- non-conforming price display;
- unsubstantiated claim;
- prohibited category;
- unverified source;
- missing compliance record;
- stale external rules;
- compliance record not linked to the asset it approves;
- domain coverage gap;
- survival checkpoint missed.

---

# 19. Capability Dependencies (Consolidated)

> **Runtime dependencies** block operation if missing.
> **Monitoring inputs** supply data to a checkpoint or report but never block operation.
> **Feedback inputs** improve operation over time but do not block it.

| Capability | Runtime dependencies | Monitoring inputs | Feedback inputs |
|-----------|---------------------|-------------------|-----------------|
| Context Management | — | — | Learning & Improvement |
| Product Discovery | Context Management, Evidence Management | — | Learning & Improvement |
| Product Evaluation & Curation | Product Discovery, Rubric Management, Evidence Management | — | Learning & Improvement |
| Recommendation Generation | Product Evaluation & Curation, Evidence Management | — | Learning & Improvement |
| Content Presentation | Recommendation Generation, Evidence Management | — | Learning & Improvement |
| Consistency Validation | Content Presentation, Evidence Management | — | Learning & Improvement |
| Publication & Lifecycle | Content Presentation, Consistency Validation, Compliance & Governance | — | Learning & Improvement |
| Performance Measurement & Attribution | Publication & Lifecycle | — | Learning & Improvement |
| Learning & Improvement | Performance Measurement & Attribution | — | — |
| Evidence Management | (External sources) | — | — |
| Rubric Management | — | — | Learning & Improvement |
| Compliance & Governance | Content Presentation, Evidence Management | Performance Measurement & Attribution (for CD1 survival checkpoints only) | Learning & Improvement |

**No runtime cycles.** The dependency graph is acyclic. Performance Measurement feeds Compliance **only for monitoring**, and never gates a publication.

**Build order implication (for the Engineering Proposal):** Context Management, Evidence Management, and Rubric Management have no runtime dependencies and can be built first. The Engineering Proposal (`A.5-ENG-STYP-001`) determines actual build order.

---

# 20. Data Objects and Flow

| Data Object | Produced by | Consumed by |
|-------------|-------------|-------------|
| Context Record | Context Management | Product Discovery, Product Evaluation, Recommendation Generation, Content Presentation |
| Product Candidate Set | Product Discovery | Product Evaluation & Curation |
| Evaluation Record | Product Evaluation & Curation | Recommendation Generation |
| Recommendation Record | Recommendation Generation | Content Presentation, Consistency Validation |
| Content Asset | Content Presentation | Consistency Validation, Compliance & Governance, Publication & Lifecycle |
| Validation Result | Consistency Validation | Publication & Lifecycle (as precondition and as corrective-action handoff) |
| Compliance Record | Compliance & Governance | Publication & Lifecycle (as precondition), Editorial Owner (survival escalations) |
| Publication Record | Publication & Lifecycle | Performance Measurement |
| Performance Record | Performance Measurement | Learning & Improvement, Compliance & Governance (monitoring input for CD1) |
| Learning Record | Learning & Improvement | Rubric Management (feedback input) |
| Evidence Record | Evidence Management | Product Discovery, Product Evaluation, Recommendation Generation, Content Presentation, Consistency Validation, Compliance & Governance |
| Rubric Version Record | Rubric Management | Product Evaluation & Curation |

---

# 21. Metrics Roll-up

| Functional threshold (`A.2-FUNC-STYP-001` §18.1) | Aggregated from |
|---------------------------------------------|-----------------|
| Recommendations passing Align on first attempt ≥ 90% | Consistency Validation: first-pass validation rate |
| Factual error rate ≤ 2% | Recommendation Generation: factual error rate + Compliance & Governance: violation rate |
| Recommendation-context match rate ≥ 95% | Recommendation Generation: context-match rate |
| Governance violation rate ≤ 2% | Compliance & Governance: violation rate |
| Attribution completeness 100% | Publication & Lifecycle: tracking ID correctness at publication |

> **Naming note:** `A.2-FUNC-STYP-001` §18.1 defines "attribution completeness" as **Pins with a correct tracking ID** — a Pin-level, computable metric. Capability 8's metric of the same name is defined at the **tracking-ID level** (14.12) because Amazon reports per tracking ID, not per Pin.

**Business Validation Thresholds (`A.2-FUNC-STYP-001` §18.2) are not capability metrics.** They are business outcomes tracked in the Business Plan (`A.1-BIZ-STYP-001`).

---

# 22. Ownership Model

| Capability | Category | Owner |
|-----------|----------|-------|
| Context Management | Core | Editorial Owner |
| Product Discovery | Core | Editorial Owner |
| Product Evaluation & Curation | Core | Editorial Owner |
| Recommendation Generation | Core | Editorial Owner |
| Content Presentation | Core | Editorial Owner |
| Consistency Validation | Core | Editorial Owner |
| Publication & Lifecycle | Core | Editorial Owner |
| Performance Measurement & Attribution | Core | Editorial Owner |
| Learning & Improvement | Core | Editorial Owner |
| Evidence Management | Cross-cutting | Editorial Owner |
| Rubric Management | Cross-cutting | Editorial Owner |
| Compliance & Governance | Cross-cutting | Editorial Owner |

---

# 23. Version Control

This specification represents the **V1.1 RC.4** business capability model.

It becomes **V1.1 Final** only when all Open Items (`OI-001` to `OI-008`) are closed.

**Provisional operational rules** may evolve after the first 30 days of live operation without requiring a version increment.

Changes to capability structure, boundaries, runtime dependencies, or the dependency classification (runtime / monitoring / feedback) require a version increment.

---

# 24. Final Capability Definition

Style Picks operates through **twelve business capabilities**, organized as:

**9 Core Execution Capabilities:**
> Context Management → Product Discovery → Product Evaluation & Curation → Recommendation Generation → Content Presentation → Consistency Validation → Publication & Lifecycle → Performance Measurement & Attribution → Learning & Improvement

**3 Cross-Cutting Capabilities:**
> Evidence Management
> Rubric Management
> Compliance & Governance

Together, these capabilities define the minimum business abilities required for Style Picks to transform emerging consumer demand into contextual, curated, trustworthy, and commercially useful product discovery.

The next engineering artifact should be the **Capability Contracts Specification** (`A.4-CONTR-STYP-001`), which will formalize each capability's inputs, outputs, rules, preconditions, postconditions, and failure handling.

---

## Note on OI-001

> **OI-001 (Amazon Associates account creation date) remains the single most consequential unclosed item.** Every survival checkpoint in CD1, every escalation rule, and the entire validation schedule depend on it.
>
> Close it before writing the Capability Contracts (`A.4-CONTR-STYP-001`).

---

# 25. Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.3 — Capability Definition

**Document ID:** A.3-CAP-STYP-001

**Version:** 1.1 RC.4 — Capability Definition Release Candidate

**Status:** **Release Candidate**

**Authorization:** This document decomposes the eight functions of `A.2-FUNC-STYP-001` into twelve capabilities. `A.4-CONTR-STYP-001` is authorized to derive from it.

**Blocking dependencies:** OI-001, OI-002.

**Language:** English

---

*End of Business Capabilities Specification — A.3-CAP-STYP-001 v1.1 RC.4*