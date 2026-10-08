# STYLE PICKS
## Capability Contracts Specification

**Stage A.4 — Contract Formalization**
**Physical Foundation of the Style Picks Contract Model**

**Document ID:** A.4-CONTR-STYP-001

**Version:** 1.0 RC.4 — Contract Formalization Release Candidate

**Status:** Stage A — Engineering Definition (Conceptual Level) — Release Candidate

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Parent Documents:**
- A.3-CAP-STYP-001 — Business Capabilities Specification (v1.1 RC.4)
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.0)

**Child Documents:**
- A.5-ENG-STYP-001 — Engineering Proposal (v1.2 Final)

**Domain:** Domain A.4 — Capability Contracts

---

**Business Model:** Content Commerce + Affiliate Commerce
**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**Initial Categories:** Home Decor + Home Organization
**Stage:** Commercial Validation
**Document Type:** Capability Contracts Specification
**Derives from:** A.3-CAP-STYP-001

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 RC.1 | Oct 7, 2026 | Initial capability contracts; D-1 to D-6 formalized |
| 1.0 RC.2 | Oct 7, 2026 | Part I added (schemas, state machines, invariants, error codes); Product Record ownership resolved; Change Detection added; D-6 split into states + events; Contract Failure Record added |
| 1.0 RC.3 | Oct 7, 2026 | Sole-writer ownership for every record; Revoked state + Review cleared event; Evidence Record supports imagery; Publication Record references Validation and Compliance; disclosure field added; error table extended; Product Record versioning semantics; systemic-failure routing fixed |
| 1.0 RC.4 | Oct 7, 2026 | INV-12 refined: re-point claims to successor evidence before revoking; "Review triggered" and "Review cleared" transitions reassigned to C-07; Revoked → Pin dependency added; Product Record references keyed to (product_id, version); E-ALIGN-02 corrected to re-link; C-10 wording tightened |
| **1.0 RC.4 (Baselined header)** | Oct 8, 2026 | Normalized document header per Stage A codification; cross-references updated to A.x IDs; Open Items Register (`PH1-REG-STYP-001`) referenced; Change Proposals register referenced; Sign-Off block added |

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
| OI-008 | Evidence Source Policy — formalized | Defaultable | Editorial Owner | EMPTY |

**Change Proposals affecting this document:**

| CP ID | Title | Affected sections | Status |
|-------|-------|-------------------|--------|
| CP-001 | Re-evaluation vs Revocation on Superseded Evidence | INV-12, I.5 | Pending |
| CP-002 | AI-Generated Contextual Imagery | C-05, CD4 | Pending |
| CP-003 | Review Cleared Sole-Writer Assignment | C-06 postcondition #3 | Pending |

> **Until CP-001, CP-002, and CP-003 are accepted, the literal wording of this document governs.**

---

## Contract Conventions

### Notation

- **MUST** — mandatory. Violation is a contract failure.
- **SHOULD** — recommended. Deviation requires documented justification.
- **MAY** — optional. Implementation discretion.
- **Contract boundary** — what the contract does not cover, and which other contract covers it.

### Document Structure

- **Part I — Shared Contract Assets:** data dictionary, state machines, invariants, error codes, Change Detection, deferred definitions, compliance requirements.
- **Part II — Capability Contracts:** one per capability. Each contract cites BC (`A.3-CAP-STYP-001`) for purpose, inputs, business rules, failure conditions, dependencies, ownership, evidence requirements, boundary — and adds only verification, failure handling by code, and any contract-specific detail.

### Contract Identifiers

C-01 Context Management · C-02 Product Discovery · C-03 Product Evaluation & Curation · C-04 Recommendation Generation · C-05 Content Presentation · C-06 Consistency Validation · C-07 Publication & Lifecycle · C-08 Performance Measurement & Attribution · C-09 Learning & Improvement · C-10 Evidence Management · C-11 Rubric Management · C-12 Compliance & Governance

---

# PART I — SHARED CONTRACT ASSETS

# I.1 — Data Dictionary

Field types: `string`, `integer`, `decimal`, `boolean`, `date`, `timestamp`, `enum`, `reference`, `list<...>`, `map<...>`. Required: **R**. Optional: **O**. **Sole writer** = single contract permitted to create or modify (INV-10). All other contracts read.

## I.1.1 — Context Record

**Sole writer:** C-01.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| context_id | string | R | Unique. |
| name | string | R | |
| consumer_problem | string | R | |
| desired_outcome | string | R | |
| category | enum | R | Approved list. |
| constraints | list<string> | R | May be empty. |
| approved_price_range | map<min,max> | R | Decimal, USD. |
| editorial_opportunity | string | O | |
| status | enum | R | Draft / Approved / Retired. |
| owner | reference | R | |
| created_at | timestamp | R | |
| version | integer | R | Increments on any change. |

## I.1.2 — Product Record

**Sole writer:** C-02.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| product_id | string | R | Unique per product identity (ASIN). |
| version | integer | R | Increments on material change. |
| asin | string | R | |
| name | string | R | |
| category | enum | R | |
| price | decimal | R | Snapshot. |
| rating | decimal | R | Snapshot. |
| review_count | integer | R | Snapshot. |
| dimensions | map<string,decimal> | O | |
| features | list<string> | O | |
| source | string | R | |
| source_timestamp | timestamp | R | |
| approved_destination_reference | string | R | Contains affiliate URL and embedded tracking ID. |
| evidence_references | list<reference> | R | ≥1. |
| is_current | boolean | R | Exactly one version per product_id is current. |

### I.1.2.1 — Product Record Reference Semantics

> **Correction from RC.3:** The pair `(product_id, version)` uniquely identifies a Product Record.

**Reference convention:** All references to a Product Record across records are of the form `(product_id, version)`.

When a record must reference "the current Product Record," it stores `(product_id, current_version)` at the moment of reference. If a material change later supersedes that version, the referencing record keeps the original pair — which is exactly what change detection needs to detect the mismatch.

**Versioning:** non-material source change → update in place (`source_timestamp`); material change → new version created with `is_current = true`, previous version `is_current = false`. Prior versions preserved.

## I.1.3 — Evidence Record

**Sole writer:** C-10.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| evidence_id | string | R | |
| evidence_type | enum | R | Primary / Claim-level / Imagery. |
| claim | string | O | Required for Claim-level. |
| source | string | R | |
| source_url | string | R | |
| source_classification | enum | R | Verified / Unverified. |
| retrieval_timestamp | timestamp | R | |
| content_snapshot | string | O | |
| license_or_permission | string | O | Required for Imagery. |
| applicable_constraints | list<string> | O | |
| linked_product_id | reference | O | Required for Primary and Claim-level. |
| linked_product_version | integer | O | Required when `linked_product_id` present. |
| linked_recommendation_id | reference | O | Required for Claim-level. |
| status | enum | R | Active / Superseded. |
| superseded_by | reference | O | Required when Superseded. |

## I.1.4 — Evaluation Record

**Sole writer:** C-03.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| evaluation_id | string | R | |
| product_id | string | R | |
| product_version | integer | R | |
| context_id | reference | R | |
| rubric_version | string | R | |
| criterion_scores | map<string,decimal> | R | |
| weighted_score | decimal | R | |
| hard_constraint_status | boolean | R | |
| verifiability_score | decimal | R | |
| eligibility_status | enum | R | Eligible / Rejected. |
| rejection_reason | string | O | Required when Rejected. |
| evaluator | string | R | |
| evaluated_at | timestamp | R | |

## I.1.5 — Recommendation Record

**Sole writer:** C-04.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| recommendation_id | string | R | |
| product_id | string | R | |
| product_version | integer | R | |
| context_id | reference | R | |
| statement | string | R | |
| rationale | string | R | |
| supporting_facts | list<map<claim,evidence_reference>> | R | Each material claim (D-1). |
| limitations | list<string> | R | |
| editorial_score | decimal | R | |
| evidence_confidence | enum | R | High / Medium / Low. |
| status | enum | R | See I.2.2. |
| revoked_reason | string | O | Required when Revoked. |
| created_at | timestamp | R | |

## I.1.6 — Content Asset

**Sole writer:** C-05.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| asset_id | string | R | |
| recommendation_id | reference | R | |
| product_id | string | R | |
| product_version | integer | R | |
| context_id | reference | R | |
| title | string | R | |
| description | string | R | |
| product_image_reference | reference | R | Evidence Record (Imagery). |
| contextual_image_reference | reference | R | Evidence Record (Imagery). |
| editorial_framing | string | R | |
| call_to_action | string | R | |
| disclosure_text | string | R | Affiliate disclosure shown on Pin. |
| affiliate_destination_url | string | R | Derived from Product Record. |
| tracking_id | string | R | Same reference. |
| metadata | map<string,string> | O | |
| created_at | timestamp | R | |

## I.1.7 — Validation Result

**Sole writer:** C-06.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| validation_id | string | R | |
| asset_id | reference | R | |
| phase | enum | R | Pre-publication / Post-publication. |
| status | enum | R | PASS / FAIL / CLEARED. |
| checks_performed | list<string> | R | |
| inconsistencies | list<map<check,severity>> | R | Empty when PASS or CLEARED. |
| corrective_action | enum | O | Required when FAIL and post-publication. |
| validated_at | timestamp | R | |

> **Note:** C-06 **issues** Validation Results (PASS, FAIL, CLEARED). C-07 **executes** lifecycle transitions. C-06 does not modify Publication Records.

## I.1.8 — Compliance Record

**Sole writer:** C-12.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| compliance_id | string | R | |
| subject_id | reference | R | |
| control_domains_checked | list<enum> | R | CD1–CD6. |
| checks_performed | map<domain,list<string>> | R | |
| rules_applied | map<domain,string> | R | |
| rule_version_or_date | map<domain,date> | R | |
| decision | enum | R | Approve / Reject / Correct / Escalate. |
| error_code | enum | O | See I.4. |
| compliance_evidence | string | O | |
| checked_at | timestamp | R | |
| reviewer | string | R | |

## I.1.9 — Publication Record

**Sole writer:** C-07.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| publication_id | string | R | |
| asset_id | reference | R | |
| tracking_id_used | string | R | |
| pin_url | string | R | |
| published_at | timestamp | R | |
| validation_result_id | reference | R | Authorizing Validation Result. |
| compliance_record_id | reference | R | Authorizing Compliance Record. |
| status | enum | R | See I.2.1. |
| lifecycle_events | list<map<event,timestamp,reason>> | R | |
| updated_at | timestamp | R | |

## I.1.10 — Performance Record

**Sole writer:** C-08.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| performance_id | string | R | |
| reporting_period | map<start,end> | R | |
| attribution_unit | enum | R | Tracking-ID / ASIN / Pin-level Pinterest engagement. |
| attribution_value | string | R | |
| metric_name | string | R | |
| metric_value | decimal | R | |
| source | enum | R | Pinterest / Amazon. |
| collected_at | timestamp | R | |

## I.1.11 — Learning Record

**Sole writer:** C-09.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| learning_id | string | R | |
| observed_pattern | string | R | |
| evidence | list<reference> | R | |
| hypothesis | string | R | |
| confidence | enum | R | Low / Medium / High. |
| proposed_action | string | R | |
| affected_capability | reference | R | |
| affected_rubric_or_rule | reference | O | |
| status | enum | R | Accepted / Rejected / Deferred / Escalated. |
| created_at | timestamp | R | |

## I.1.12 — Rubric Version Record

**Sole writer:** C-11.

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| rubric_version | string | R | |
| effective_date | date | R | |
| criteria | list<map<name,weight,scale,threshold>> | R | Threshold per criterion. |
| hard_constraints | list<string> | R | |
| minimum_weighted_score | decimal | R | Global eligibility threshold. |
| change_justification | string | R | |
| change_log_entry | string | R | |
| approver | reference | R | |
| status | enum | R | Draft / Active / Retired. |

## I.1.13 — Contract Failure Record

**Sole writer:** the detecting contract (exception to INV-10).

| Field | Type | R/O | Notes |
|-------|------|-----|-------|
| failure_id | string | R | |
| contract_id | string | R | C-NN. |
| failure_type | enum | R | Precondition / Postcondition / Rule / Evidence / Traceability. |
| error_code | enum | R | See I.4. |
| detected_at | timestamp | R | |
| detected_by | string | R | |
| severity | enum | R | Operational / Material / Systemic. |
| escalated_to_learning | boolean | R | |
| resolution | string | O | |

---

# I.2 — State Machines

States are persistent. Events are transitions. A record is in exactly one state at any time.

## I.2.1 — Pin Lifecycle

**States:** Live / Under Review / Archived.

**Events (issued by the record's sole writer):**

| Event | From | To | Triggered by | Executed by |
|-------|------|-----|--------------|-------------|
| Published | — | Live | C-07 | C-07 |
| Review triggered | Live | Under Review | C-06 (CLEARED not applicable; failure detected) | C-07 |
| Review cleared | Under Review | Live | C-06 (Validation Result = CLEARED) | C-07 |
| Re-linked | Under Review | Live | C-06 (corrective action = re-link) | C-07 |
| Replaced | Live or Under Review | Archived | C-06 | C-07 |
| Archived | Live or Under Review | Archived | C-06 | C-07 |
| Restored | Archived | Live | Editorial Owner | C-07 |

> **Correction from RC.3:** C-06 **issues** Validation Results; C-07 **executes** lifecycle transitions. This preserves INV-10 (C-07 is sole writer of the Publication Record).

> **Pending CP-003:** C-06 postcondition #3 currently states that C-06 "executes" the Review cleared event. CP-003 proposes rewording it to align with INV-13. Until CP-003 is accepted, the literal text of C-06 postcondition #3 governs.

## I.2.2 — Recommendation Status

| State | Meaning | Allowed next states |
|-------|---------|---------------------|
| **Draft** | Being written. | Approved, Low-Confidence, Rejected |
| **Approved** | Evidence confidence = High. | Revoked |
| **Low-Confidence** | Awaiting human review. | Human-Review-Approved, Rejected, Revoked |
| **Human-Review-Approved** | Accepted despite Low confidence. | Revoked |
| **Rejected** | Withdrawn before presentation. | (Terminal.) |
| **Revoked** | Withdrawn after approval, typically due to superseded evidence no longer supporting a material claim. | (Terminal.) |

> **Correction from RC.3:** A recommendation moves to Revoked only when **a material claim is no longer supported by any Active Evidence Record**. If successor evidence is available for the same claim, the reference is re-pointed to the successor and the recommendation remains in its current approved state.

> **Pending CP-001:** This is the two-step logic that CP-001 proposes to formalize in INV-12. Until CP-001 is accepted, INV-12's literal wording governs.

## I.2.3 — Rubric Version Status

| State | Allowed next states |
|-------|---------------------|
| Draft | Active, Retired |
| Active | Retired |
| Retired | (Terminal.) |

Exactly one version Active at a time.

## I.2.4 — Evidence Record Status

| State | Allowed next states |
|-------|---------------------|
| Active | Superseded |
| Superseded | (Terminal.) |

---

# I.3 — Global Invariants

| # | Invariant |
|---|-----------|
| INV-1 | No Pin is published unless Validation = PASS AND Compliance = Approve. Auditable via Publication Record's `validation_result_id` and `compliance_record_id`. |
| INV-2 | At most one rubric version is Active at any time. |
| INV-3 | URL tracking ID = Content Asset tracking ID = Product Record's approved destination reference tracking ID. |
| INV-4 | Every material claim in a Recommendation Record references at least one Active Evidence Record. |
| INV-5 | Every published Pin has a Publication Record in state Live, Under Review, or Archived. |
| INV-6 | Every Product Record has an approved destination reference. |
| INV-7 | Every Content Asset derives its affiliate URL and tracking ID from the same Product Record reference. |
| INV-8 | Contract failures of severity Material or Systemic produce a Contract Failure Record with `escalated_to_learning = true`. |
| INV-9 | Performance Measurement is a monitoring input to Compliance (CD1), never a runtime gate for publication. |
| INV-10 | Every record type in I.1 has exactly one sole writer, except the Contract Failure Record which is written by the detecting contract. |
| INV-11 | Every published Pin has a Publication Record whose `validation_result_id` and `compliance_record_id` are set. |
| INV-12 | **A Recommendation Record whose material claim is no longer supported by any Active Evidence Record MUST transition to Revoked.** If successor evidence is available, the claim reference is re-pointed and Revocation is not required. |
| INV-13 | **Every lifecycle transition of a Pin is executed by C-07 only, even when triggered by a Validation Result issued by C-06.** |
| INV-14 | **Every reference to a Product Record is of the form `(product_id, version)`.** |

> **Pending CP-001:** INV-12 currently contains both the literal wording ("MUST transition to Revoked") and the two-step logic ("If successor evidence is available, the claim reference is re-pointed"). CP-001 proposes to formally adopt the two-step logic. Until CP-001 is accepted, the current wording of INV-12 governs.

---

# I.4 — Error Codes

Each code carries: detection method, default response, severity, deadline.

| Code | Meaning | Detection | Default response | Severity | Deadline |
|------|---------|-----------|------------------|----------|----------|
| E-PRE-01 | Missing required precondition. | Deterministic | Block | Operational | Immediate |
| E-POST-01 | Postcondition not satisfied. | Deterministic | Block | Material | Immediate |
| E-RULE-01 | Hard constraint violated. | Deterministic | Block | Material | Immediate |
| E-RULE-02 | Soft constraint violated. | Deterministic or human | Return for correction | Operational | 24h |
| E-EV-01 | Material claim missing an Evidence Record. | Deterministic | Block | Material | Immediate |
| E-EV-02 | Evidence source classification missing. | Deterministic | Return for correction | Operational | 24h |
| E-EV-03 | Evidence Record superseded and material claim no longer supported. | Deterministic | Revoke recommendation | Material | Immediate |
| E-EV-04 | Evidence Record superseded but successor available for the claim. | Deterministic | Re-point claim to successor; no status change | Operational | 24h |
| E-TR-01 | Traceability link missing. | Deterministic | Block | Material | Immediate |
| E-TR-02 | Traceability link inconsistent (e.g., tracking ID mismatch). | Deterministic | Block | Material | Immediate |
| E-ALIGN-01 | Pin promise does not match content. | Deterministic or human | Block | Material | Immediate |
| E-ALIGN-02 | **Destination not reachable (product still available).** | Deterministic | **Re-link** | Material | 24h |
| E-ALIGN-03 | Product Record materially changed. | Deterministic | Review triggered | Material | 24h |
| E-ALIGN-04 | **Destination not reachable and product discontinued.** | Deterministic | **Archive Pin** | Material | 24h |
| E-GOV-01 | Disclosure missing or incorrect. | Deterministic or human | Block | Material | Immediate |
| E-GOV-02 | Link format non-conforming. | Deterministic | Block | Material | Immediate |
| E-GOV-03 | Image use non-conforming. | Deterministic or human | Block | Material | Immediate |
| E-GOV-04 | Price display non-conforming. | Deterministic | Block | Material | Immediate |
| E-GOV-05 | Prohibited category. | Deterministic | Block | Material | Immediate |
| E-GOV-06 | Survival checkpoint missed. | Human review | Escalate | Systemic | Immediate |
| E-RUB-01 | Evaluation against non-Active rubric version. | Deterministic | Return for correction | Operational | 24h |
| E-RUB-02 | Rubric change without justification or approval. | Deterministic | Block | Material | Immediate |
| E-PUB-01 | Publication attempted without both gates. | Deterministic | Block | Material | Immediate |
| E-PUB-02 | Publication with incorrect or missing tracking ID. | Deterministic | Block | Material | Immediate |
| E-PUB-03 | Corrective action exceeded the corrective-action window. | Deterministic | Escalate | Material | Immediate |
| E-PERF-01 | Data staleness beyond cadence. | Deterministic | Return for correction | Operational | 48h |
| E-PERF-02 | Unreconciled data when outbound clicks > 0. | Deterministic | Escalate | Operational | 48h |
| E-CD-01 | Change-detection run missed. | Human review | Escalate | Operational | 24h |

---

# I.5 — Change Detection

**Responsibility:** **C-02 Product Discovery** owns change detection. C-02 **detects**; C-10 **versions** Evidence Records; C-04 **re-evaluates** affected recommendations.

**What is watched:** Amazon product pages referenced by active Product Records; manufacturer pages referenced by Active Evidence Records.

**What is checked:** product identity (ASIN); dimensions, materials, functional capabilities referenced in material claims; price ±30% (informational only); availability; rating < 3.5; review count < 50; source content changes affecting Active Evidence Records.

**Detection semantics:**

- An Evidence Record is superseded **only when the specific fact it supports changes**, not when the page snapshot changes trivially.
- When supersession is required and a successor Evidence Record is available for the same claim, the claim reference is re-pointed (code **E-EV-04**, no status change).
- When no successor is available for a material claim, the recommendation transitions to **Revoked** (code **E-EV-03**).

**What it produces:**

- Material product change detected → new Product Record version; `is_current` updated; C-06 post-publication scheduled for Pins referencing the earlier `(product_id, version)`.
- Evidence source changed → C-02 requests C-10 to supersede the Evidence Record and create a successor (D-4).
- Revoked recommendation → C-06 post-publication check scheduled; C-07 executes resulting lifecycle transitions.
- Change-detection run missed → Contract Failure Record (E-CD-01).

**Cadence:** provisional daily. Subject to revision after 30 days of live operation.

---

# I.6 — Deferred Definitions (Formalized)

### D-1 — Material Claim
Includes dimensions, weight, size, materials, functional capability, compatibility (including derived statements), safety, durability, performance, availability. Subjective statements excluded.

### D-2 — Factual Error Rate
Missing Evidence Record is a **postcondition failure of C-04**, not a factual error. Rate = factual_errors / total_material_claims per reporting period.

### D-3 — Evidence Confidence Calculation
Only Active Evidence Records count. Postcondition failure if any material claim lacks an Active Evidence Record.

### D-4 — Evidence Record Versioning
Successor records are created only when the specific fact the record supports changes. Claims are re-pointed (E-EV-04) when a successor is available; Revocation (E-EV-03) only when no successor supports the claim.

### D-5 — Material Product Change
Price ±30% is informational and does not trigger C-06.

### D-6 — Pin Lifecycle States and Events
Per I.2.1. States: Live, Under Review, Archived. Events: Published, Review triggered, Review cleared, Re-linked, Replaced, Archived, Restored. Executed by C-07 only (INV-13).

---

# I.7 — Contract Compliance Requirements

A contract is satisfied when:

1. All preconditions are met before execution.
2. All business rules are enforced.
3. All postconditions hold after execution.
4. All failure conditions are detectable (per I.4).
5. All evidence requirements are met.
6. All traceability links exist.

## I.7.1 — Failure Handling Inheritance
Every failure condition carries an error code (I.4) with detection method, default response, default severity, and default deadline. Part II contracts cite codes only.

## I.7.2 — Traceability
Every produced record carries references to source and destination records. Missing or inconsistent links produce **E-TR-01** or **E-TR-02**.

## I.7.3 — Failure Severity and Learning Escalation

| Severity | Definition | Learning escalation |
|----------|-----------|---------------------|
| **Operational** | Single instance, self-correctable within the corrective-action window. | No. |
| **Material** | Affects a published Pin, a claim, or a compliance check. | Yes. |
| **Systemic** | Recurring (≥3 in a rolling 30-day window) or affects multiple assets. | Yes, and triggers review at the **affected capability** (not the rubric by default). |

---

# PART II — CAPABILITY CONTRACTS

Each contract cites BC for purpose, inputs, business rules, failure conditions, dependencies, ownership, evidence requirements, and boundary. Below: outputs (schema + sole writer), preconditions, postconditions with verification, failure handling by code, contract-specific notes.

---

# C-01 — Context Management

**Outputs:** Context Record (I.1.1). Sole writer: C-01.
**Preconditions / Postconditions / Failure handling / Boundary:** per BC `A.3-CAP-STYP-001` §7.6, §7.7, §7.12, §7.5.

**Failure codes:** E-PRE-01, E-POST-01, E-RULE-01.

---

# C-02 — Product Discovery

**Outputs:**
- Product Candidate Set;
- Product Record (I.1.2). Sole writer: C-02.
- Change-detection outcomes (per I.5). C-02 **detects**; C-10 **versions**.

**Preconditions / Failure handling / Boundary:** per BC `A.3-CAP-STYP-001` §8.6, §8.12, §8.5.

**Failure codes:** E-PRE-01, E-EV-01, E-EV-02, E-TR-01, E-CD-01.

**Contract-specific note:** C-02 is the sole writer of Product Records and detects source changes. It does **not** version Evidence Records (that is C-10, E-EV-04).

---

# C-03 — Product Evaluation & Curation

**Outputs:** Evaluation Record (I.1.4). Sole writer: C-03.
**Preconditions / Failure handling / Boundary:** per BC `A.3-CAP-STYP-001` §9.7, §9.13, §9.6.

**Failure codes:** E-PRE-01, E-RULE-01, E-RUB-01.

---

# C-04 — Recommendation Generation

**Outputs:** Recommendation Record (I.1.5). Sole writer: C-04.

**Postconditions (with verification):**

| # | Postcondition | Verification |
|---|---------------|--------------|
| 1 | Every material claim references ≥1 Active Evidence Record. | Deterministic (E-EV-01). |
| 2 | Evidence confidence computed per D-3. | Deterministic. |
| 3 | Status is one of the states in I.2.2. | Deterministic. |
| 4 | When a supporting Evidence Record is superseded and a successor exists, the claim is re-pointed (E-EV-04). | Deterministic. |
| 5 | When a material claim is no longer supported by any Active Evidence Record, the recommendation transitions to Revoked (E-EV-03, INV-12). | Deterministic. |

**Failure codes:** E-POST-01, E-EV-01, E-EV-03, E-EV-04, E-RULE-01.

**Contract-specific note:** C-04 **reads** the Product Record and **writes** to the Recommendation Record.

---

# C-05 — Content Presentation

**Outputs:** Content Asset (I.1.6). Sole writer: C-05.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §11.7, §11.6.

**Postconditions:** affiliate URL and tracking ID derived from the same Product Record reference (INV-3, INV-7); `disclosure_text` present; asset available to C-06.

**Failure codes:** E-TR-02, E-RULE-01, E-GOV-01.

**Contract-specific note:** The `contextual_image_reference` field is used for licensed or stock imagery only. AI-generated contextual imagery is not permitted until CP-002 is accepted (see `A.5-ENG-STYP-001` §47).

---

# C-06 — Consistency Validation

**Outputs:** Validation Result (I.1.7). Sole writer: C-06.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §12.9, §12.8.

**Postconditions:** Asset has explicit state PASS, FAIL, or CLEARED; post-publication failures handed to C-07 for corrective action; **C-06 issues Validation Results but does not modify Publication Records** (INV-13).

**Failure codes:** E-ALIGN-01, E-ALIGN-02, E-ALIGN-03, E-ALIGN-04, E-TR-02.

**Contract-specific note:** Postcondition #3 currently states that C-06 "executes" the Review cleared event. This is the subject of CP-003. Until CP-003 is accepted, the literal text governs. Under INV-13, C-06 issues Validation Results and C-07 executes lifecycle transitions.

---

# C-07 — Publication & Lifecycle

**Outputs:** Publication Record (I.1.9). Sole writer: C-07.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §13.6, §13.5.

**Postconditions:**

| # | Postcondition | Verification |
|---|---------------|--------------|
| 1 | Publication Record references the Validation Result and Compliance Record (INV-11). | Deterministic. |
| 2 | Current lifecycle state recorded per I.2.1. | Deterministic. |
| 3 | Corrective actions recorded with outcome. | Deterministic. |
| 4 | Corrective actions executed within window (72h provisional). | Deterministic (E-PUB-03). |
| 5 | **All Pin lifecycle transitions are executed by C-07** (INV-13), including Review triggered, Review cleared, Re-linked, Replaced, Archived, Restored. | Deterministic. |
| 6 | **Post-publication checks are scheduled whenever a Recommendation transitions to Revoked**, closing the dependency between Revoked recommendations and affected Pins. | Deterministic scheduling. |

**Failure codes:** E-PUB-01, E-PUB-02, E-PUB-03.

---

# C-08 — Performance Measurement & Attribution

**Outputs:** Performance Record (I.1.10). Sole writer: C-08.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §14.7, §14.6.

**Postconditions:** Data available at supported attribution level; completeness and freshness recorded.

**Failure codes:** E-PERF-01, E-PERF-02.

**Contract-specific note:** C-08 is a **monitoring input** to C-12 CD1 (INV-9), never a publication gate.

---

# C-09 — Learning & Improvement

**Outputs:** Learning Record (I.1.11). Sole writer: C-09.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §15.6, §15.5.

**Postconditions:** Every Learning Record links to supporting Performance Records; every hypothesis states its evidence basis and confidence; accepted rubric change proposals handed to C-11.

**Contract-specific note:** C-09 receives only Material or Systemic failures (I.7.3).

---

# C-10 — Evidence Management

**Outputs:** Evidence Record (I.1.3). Sole writer: C-10.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §16.7, §16.6.

**Postconditions:**

| # | Postcondition | Verification |
|---|---------------|--------------|
| 1 | Every material claim references ≥1 Active Evidence Record (INV-4). | Deterministic. |
| 2 | Evidence Records are versioned by C-10 when a source change is detected by C-02 or otherwise identified through C-10's evidence-governance process (D-4). | Deterministic state transition. |
| 3 | Claims referencing a superseded record are re-pointed to the successor when available (E-EV-04). | Deterministic. |

**Failure codes:** E-EV-01, E-EV-02, E-EV-03, E-EV-04.

---

# C-11 — Rubric Management

**Outputs:** Rubric Version Record (I.1.12). Sole writer: C-11.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §17.6, §17.5.

**Postconditions:** Exactly one rubric version Active (INV-2); change justification and approver recorded.

**Failure codes:** E-RUB-02.

---

# C-12 — Compliance & Governance

**Outputs:** Compliance Record (I.1.8). Sole writer: C-12.
**Preconditions / Boundary:** per BC `A.3-CAP-STYP-001` §18.10, §18.6.

**Postconditions:** Compliance Record exists with a decision; if Approve, asset eligible for C-07 subject to Validation = PASS (INV-1).

**Failure codes:** E-GOV-01 through E-GOV-06.

---

# Cross-Contract Traceability Matrix

| Contract | Produces | Consumes | Gates |
|----------|----------|----------|-------|
| C-01 | Context Record | — | — |
| C-02 | Product Record, Product Candidate Set, change-detection outcomes | C-01, C-10 | — |
| C-03 | Evaluation Record | C-02, C-10, C-11 | — |
| C-04 | Recommendation Record | C-03, C-10 | — |
| C-05 | Content Asset | C-04, C-10 | — |
| C-06 | Validation Result | C-05, C-10 | — |
| C-07 | Publication Record | C-05, C-06, C-12 | Publication gate (INV-1) |
| C-08 | Performance Record | C-07 | — |
| C-09 | Learning Record | C-08, C-03, C-04, C-07, C-11, Contract Failure Records | — |
| C-10 | Evidence Record | External sources | — |
| C-11 | Rubric Version Record | C-09 (feedback) | — |
| C-12 | Compliance Record | C-05, C-10, C-08 (monitoring) | Publication gate (Approve) |

---

# What This Document Does Not Do

- Does not prescribe implementation (deterministic, human, LLM, hybrid).
- Does not prescribe architecture, storage, or APIs.
- Does not re-open capability boundaries from `A.3-CAP-STYP-001` V1.1 RC.4.
- Does not define business metrics — those remain in the Business Plan (`A.1-BIZ-STYP-001`).

---

# Handoff to the Engineering Proposal

The next document (`A.5-ENG-STYP-001`) MUST derive, for each contract:

- the execution mechanism (per Section 17 of `A.2-FUNC-STYP-001`);
- the storage model for each record in Part I.1;
- the tooling required to satisfy each rule;
- the sequencing of contract implementation based on runtime dependencies;
- the human roles required at each step.

It MUST NOT redefine contracts.

---

## Notes on External Facts Affecting This Document

> **Amazon API:** PA-API has been deprecated and replaced by **Creators API**. Any reference to PA-API in earlier documents (`A.2-FUNC-STYP-001` §6.6, OI-004, CD1) is superseded by Creators API. Access conditions for Creators API (Associates status, recent qualifying sales) must be verified before operationalizing C-02's programmatic mode. This is tracked as **OI-004** in `PH1-REG-STYP-001`.

> **Pinterest Storefront Linking:** Pinterest permits creators enrolled in the Amazon Influencer Program to connect an Amazon Storefront, after which affiliate attribution is applied automatically when eligible products are tagged. If adopted, this may bypass Style Picks' own tracking ID design and break INV-3. This is a **business decision** for the destination model in `A.2-FUNC-STYP-001`, not for the Engineering Proposal. Until decided, the publication model assumes Style Picks remains the source of truth for the tracking ID.

---

## Note on OI-001

> Survival checkpoints (C-12 / CD1) are fully specified in structure; their external parameters (Associates account creation date, deadline, qualifying-sales rule) remain unverified. The contract distinguishes **rule exists** from **rule parameters verified**. Closing OI-001 does not block writing the Engineering Proposal; it blocks operationalizing the CD1 calendar.

---

# Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.4 — Contract Formalization

**Document ID:** A.4-CONTR-STYP-001

**Version:** 1.0 RC.4 — Contract Formalization Release Candidate

**Status:** **Release Candidate**

**Authorization:** This document formalizes the twelve capabilities of `A.3-CAP-STYP-001` into twelve capability contracts. `A.5-ENG-STYP-001` is authorized to derive from it.

**Blocking dependencies:** OI-001, OI-002.

**Pending Change Proposals:** CP-001, CP-002, CP-003.

**Language:** English

---

*End of Capability Contracts Specification — A.4-CONTR-STYP-001 v1.0 RC.4*