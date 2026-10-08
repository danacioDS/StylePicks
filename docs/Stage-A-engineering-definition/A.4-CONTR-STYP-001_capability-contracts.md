# A.4-CONTR-STYP-001 — Capability Contracts Specification v1.1

Oct 8, 2026 · @Daniel Ignacio Canedo Donoso

## Document Header

This specification defines the contracts that every Style Picks capability must satisfy, in any operating cycle. Version 1.1 reconciles it with the rest of the Stage A pipeline and removes cycle-specific content, which now lives only in `A.1-BIZ-STYP-001`.

| Field | Value |
| --- | --- |
| Document ID | A.4-CONTR-STYP-001 |
| Stage | A.4 — Contract Formalization |
| Version | 1.1 — Contract Formalization (Pipeline Reconciled) |
| Status | Stage A — Engineering Definition (Conceptual Level) — Baselined, pending sign-off of CP-004 and CP-005 |
| Project | Style Picks — Content Commerce + Affiliate Commerce |
| Engagement | STYP-VALIDATION-2026 |
| Domain | Domain A.4 — Capability Contracts |
| Parent documents | A.3-CAP-STYP-001 v1.3 (Traction Demonstration Reconciled); PH1-REG-STYP-001 v1.1 |
| Child documents | A.5-ENG-STYP-001 v1.4 (Traction Demonstration Reconciled) |
| Derives from | A.3-CAP-STYP-001 v1.3 |
| Document type | Capability Contracts Specification |

**Scope: cycle-independent.** These contracts carry no dates, deadlines, or cycle objectives. They apply identically to the First Operational Milestone (FOM) and to any later validation cycle. The current cycle's objective, dates, and Decision Frame are defined only in `A.1-BIZ-STYP-001` v2.0 (§17-A, §18-A). Where this document needs a date-dependent value, it references that document rather than copying it.

**Business context (by reference):** content commerce + affiliate commerce; brand Style Picks; U.S. market; Pinterest channel; Amazon Associates monetization; Home Decor + Home Organization categories. Authoritative source: `A.1-BIZ-STYP-001`.

## Change Log

v1.1 changes references, removes duplication, and resolves four internal contradictions; it adds two Change Proposals (CP-004, CP-005) that require Editorial Owner sign-off.

| Version | Date | Change |
| --- | --- | --- |
| **1.1** | Oct 8, 2026 | **Pipeline reconciliation.** (1) Parent/child references updated to A.3 v1.3, A.5 v1.4, PH1-REG v1.1; all BC citations now point to A.3 v1.3 (section numbers unchanged). (2) Stage label "Commercial Validation" removed; document declared cycle-independent. (3) Dated OI note and repeated CP acceptance notes removed; each fact now stated once. (4) I.2.2: Approved now means High **or Medium** confidence, matching A.3 §10.6. (5) INV-1 split into a pre-publication gate form (INV-1a) and a post-publication audit form (INV-1b), so it can be checked before a Pin exists. (6) New I.8 defines the minimum record set for a published Pin, giving A.1 §17-A, A.3 §1.1 and A.5 §46 one shared definition. (7) CP-004: `contextual_image_reference` becomes optional. (8) CP-005: new error code E-TR-03 for tracking IDs of an inactive Associates account. (9) Publication Record gains optional \`production\_time\_minutes\`, matching A.5 §32. (10) D-5 now defines a material product change explicitly (D-1 facts, ASIN, hard-constraint fields). (11) I.5 cadence aligned with A.5 §24 manual fallback. |
| 1.0 (Reconciled) | Oct 8, 2026 | Reconciliation with A.1 v1.5, A.2 v1.1, A.3 v1.2, A.5 v1.2.1; CP-003 accepted (C-06 issues, C-07 executes); I.5 duplicate removed; Sign-Off added. |
| 1.0 RC.5 | Oct 8, 2026 | CP-001 accepted: INV-12 formalized as two-step logic. |
| 1.0 RC.4 (Baselined header) | Oct 8, 2026 | Header normalized; A.x IDs; PH1-REG referenced; Sign-Off block added. |
| 1.0 RC.4 | Oct 7, 2026 | INV-12 refined; Review transitions reassigned to C-07; Revoked → Pin dependency; `(product_id, version)` references; E-ALIGN-02 corrected. |
| 1.0 RC.3 | Oct 7, 2026 | Sole-writer ownership; Revoked state; imagery evidence; Publication Record references; disclosure field; extended error table. |
| 1.0 RC.2 | Oct 7, 2026 | Part I added; Product Record ownership; Change Detection; Contract Failure Record. |
| 1.0 RC.1 | Oct 7, 2026 | Initial capability contracts; D-1 to D-6. |

## Open Items and Change Proposals

The authoritative status of every Open Item is `PH1-REG-STYP-001`; this table only shows which contracts each open item affects.

| OI | Subject | Contracts affected |
| --- | --- | --- |
| OI-003 | Qualifying-sales rule | C-12 (CD1) |
| OI-004 | Creators API access | C-02 (programmatic mode only) |
| OI-005 | Image and price display rules | C-05, C-12 (CD2) |
| OI-006 | Required disclosure wording | C-05 (`disclosure_text`), C-12 (CD2, CD3) |
| OI-007 | Link-format rules | C-05, C-12 (CD2) |
| OI-008 | Evidence Source Policy | C-04 (Medium confidence), C-10 (`Limited Reliability` tier) |

OI-001 and OI-002 (account date and deadline) are closed and affect no contract, because contracts carry no dates.

### Change Proposals

| CP | Title | Affected sections | Status |
| --- | --- | --- | --- |
| CP-001 | Re-evaluation vs Revocation on Superseded Evidence | INV-12, I.5, D-4 | Accepted 2026-10-08 |
| CP-002 | AI-Generated Contextual Imagery | C-05, CD4 | Pending — only licensed, stock, or original imagery until accepted |
| CP-003 | Review Cleared Sole-Writer Assignment | C-06 postcondition #3, I.2.1 | Accepted 2026-10-08 |
| CP-004 | Optional Contextual Image | I.1.6, C-05 | Proposed in v1.1 — requires Editorial Owner sign-off |
| CP-005 | Inactive Tracking ID Error Code | I.4 (E-TR-03), I.5, C-06, C-07 | Proposed in v1.1 — requires Editorial Owner sign-off |

**CP-004 rationale.** v1.0 marked `contextual_image_reference` as Required, which contradicts the FOM simplification in A.2 §10.9 (a Pin with the product image alone). A.2 §10.6 requires the product to be represented, not a lifestyle setting. The product image stays Required; the contextual image becomes Optional, and when present it still needs its own Imagery Evidence Record.

**CP-005 rationale.** If the Associates account is closed, tracking IDs on live Pins stop attributing while the destination stays reachable. No v1.0 error code covered that state. E-TR-03 routes it to Review triggered and a re-link once a valid tracking ID exists.

## Contract Conventions

Every contract uses the same notation, structure, and identifiers.

**Notation.** **MUST** = mandatory; violation is a contract failure. **SHOULD** = recommended; deviation needs documented justification. **MAY** = optional, implementation discretion. **Contract boundary** = what the contract does not cover and which contract covers it.

**Structure.** Part I holds the shared contract assets: data dictionary, state machines, invariants, error codes, change detection, deferred definitions, compliance requirements, and the minimum record set. Part II holds one contract per capability. Each contract cites BC (`A.3-CAP-STYP-001` v1.3) for purpose, inputs, business rules, failure conditions, dependencies, ownership, evidence requirements, and boundary, and adds only verification, failure handling by code, and contract-specific detail.

**Contract identifiers.**

| ID | Capability | ID | Capability |
| --- | --- | --- | --- |
| C-01 | Context Management | C-07 | Publication & Lifecycle |
| C-02 | Product Discovery | C-08 | Performance Measurement & Attribution |
| C-03 | Product Evaluation & Curation | C-09 | Learning & Improvement |
| C-04 | Recommendation Generation | C-10 | Evidence Management |
| C-05 | Content Presentation | C-11 | Rubric Management |
| C-06 | Consistency Validation | C-12 | Compliance & Governance |

## Part I.1 — Data Dictionary

Thirteen record types, each with exactly one sole writer (INV-10); all other contracts read. Types: `string`, `integer`, `decimal`, `boolean`, `date`, `timestamp`, `enum`, `reference`, `list<…>`, `map<…>`. R = required, O = optional.

### I.1.1 — Context Record (sole writer: C-01)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| context\_id | string | R | Unique. |
| name | string | R |  |
| consumer\_problem | string | R |  |
| desired\_outcome | string | R |  |
| category | enum | R | Approved list. |
| constraints | list\<string> | R | May be empty. |
| approved\_price\_range | map\<min,max> | R | Decimal, USD. |
| editorial\_opportunity | string | O |  |
| status | enum | R | Draft / Approved / Retired. |
| owner | reference | R |  |
| created\_at | timestamp | R |  |
| version | integer | R | Increments on any change. |

### I.1.2 — Product Record (sole writer: C-02)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| product\_id | string | R | Unique per product identity (ASIN). |
| version | integer | R | Increments on material change. |
| asin | string | R |  |
| name | string | R |  |
| category | enum | R |  |
| price | decimal | R | Snapshot. |
| rating | decimal | R | Snapshot. |
| review\_count | integer | R | Snapshot. |
| dimensions | map\<string,decimal> | O |  |
| features | list\<string> | O |  |
| source | string | R |  |
| source\_timestamp | timestamp | R |  |
| approved\_destination\_reference | string | R | Contains affiliate URL and embedded tracking ID. |
| evidence\_references | list\<reference> | R | At least 1. |
| is\_current | boolean | R | Exactly one version per product\_id is current. |

**I.1.2.1 — Reference semantics.** The pair `(product_id, version)` uniquely identifies a Product Record, and every reference to one uses that pair (INV-14). A record referencing "the current Product Record" stores `(product_id, current_version)` at the moment of reference and keeps it after supersession; change detection relies on that mismatch. A non-material source change updates `source_timestamp` in place. A material change creates a new version with `is_current = true` and sets the previous one to `false`; prior versions are preserved.

### I.1.3 — Evidence Record (sole writer: C-10)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| evidence\_id | string | R |  |
| evidence\_type | enum | R | Primary / Claim-level / Imagery. |
| claim | string | O | Required for Claim-level. |
| source | string | R |  |
| source\_url | string | R |  |
| source\_classification | enum | R | Verified / Unverified. `Limited Reliability` reserved until OI-008 closes. |
| retrieval\_timestamp | timestamp | R |  |
| content\_snapshot | string | O |  |
| license\_or\_permission | string | O | Required for Imagery. |
| applicable\_constraints | list\<string> | O |  |
| linked\_product\_id | reference | O | Required for Primary and Claim-level. |
| linked\_product\_version | integer | O | Required when `linked_product_id` present. |
| linked\_recommendation\_id | reference | O | Required for Claim-level. |
| status | enum | R | Active / Superseded. |
| superseded\_by | reference | O | Required when Superseded. |

Until OI-008 closes, no source is classified `Limited Reliability`, so Evidence Confidence = Medium cannot occur. High/Low is the only operational dichotomy.

### I.1.4 — Evaluation Record (sole writer: C-03)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| evaluation\_id | string | R |  |
| product\_id | string | R |  |
| product\_version | integer | R |  |
| context\_id | reference | R |  |
| rubric\_version | string | R | Must reference an Active Rubric Version Record. |
| criterion\_scores | map\<string,decimal> | R |  |
| weighted\_score | decimal | R |  |
| hard\_constraint\_status | boolean | R |  |
| verifiability\_score | decimal | R |  |
| eligibility\_status | enum | R | Eligible / Rejected. |
| rejection\_reason | string | O | Required when Rejected. |
| evaluator | string | R |  |
| evaluated\_at | timestamp | R |  |

### I.1.5 — Recommendation Record (sole writer: C-04)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| recommendation\_id | string | R |  |
| product\_id | string | R |  |
| product\_version | integer | R |  |
| context\_id | reference | R |  |
| statement | string | R |  |
| rationale | string | R |  |
| supporting\_facts | list\<map\<claim,evidence\_reference>> | R | Each material claim (D-1). |
| limitations | list\<string> | R |  |
| editorial\_score | decimal | R |  |
| evidence\_confidence | enum | R | High / Medium / Low. |
| status | enum | R | See I.2.2. |
| revoked\_reason | string | O | Required when Revoked. |
| created\_at | timestamp | R |  |

### I.1.6 — Content Asset (sole writer: C-05)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| asset\_id | string | R |  |
| recommendation\_id | reference | R |  |
| product\_id | string | R |  |
| product\_version | integer | R |  |
| context\_id | reference | R |  |
| title | string | R |  |
| description | string | R |  |
| product\_image\_reference | reference | R | Imagery Evidence Record. Original photography or a source permitted under OI-005. |
| contextual\_image\_reference | reference | **O** | **Changed by CP-004.** When present, an Imagery Evidence Record. Licensed or stock only until CP-002 is accepted. |
| editorial\_framing | string | R |  |
| call\_to\_action | string | R |  |
| disclosure\_text | string | R | Affiliate disclosure shown on the Pin. |
| affiliate\_destination\_url | string | R | Derived from the Product Record. |
| tracking\_id | string | R | Derived from the same reference. |
| metadata | map\<string,string> | O |  |
| created\_at | timestamp | R |  |

### I.1.7 — Validation Result (sole writer: C-06)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| validation\_id | string | R |  |
| asset\_id | reference | R |  |
| phase | enum | R | Pre-publication / Post-publication. |
| status | enum | R | PASS / FAIL / CLEARED. |
| checks\_performed | list\<string> | R |  |
| inconsistencies | list\<map\<check,severity>> | R | Empty when PASS or CLEARED. |
| corrective\_action | enum | O | Required when FAIL and post-publication. |
| validated\_at | timestamp | R |  |

C-06 issues Validation Results; C-07 executes lifecycle transitions. C-06 never modifies Publication Records (INV-13).

### I.1.8 — Compliance Record (sole writer: C-12)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| compliance\_id | string | R |  |
| subject\_id | reference | R |  |
| control\_domains\_checked | list\<enum> | R | CD1–CD6. |
| checks\_performed | map\<domain,list\<string>> | R |  |
| rules\_applied | map\<domain,string> | R |  |
| rule\_version\_or\_date | map\<domain,date> | R |  |
| decision | enum | R | Approve / Reject / Correct / Escalate. |
| error\_code | enum | O | See I.4. |
| compliance\_evidence | string | O |  |
| checked\_at | timestamp | R |  |
| reviewer | string | R |  |

### I.1.9 — Publication Record (sole writer: C-07)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| publication\_id | string | R |  |
| asset\_id | reference | R |  |
| tracking\_id\_used | string | R |  |
| pin\_url | string | R |  |
| published\_at | timestamp | R |  |
| validation\_result\_id | reference | R | Authorizing Validation Result. |
| compliance\_record\_id | reference | R | Authorizing Compliance Record. |
| production\_time\_minutes | integer | O | Operator-logged production time (A.5 §32, Phase 0). |
| status | enum | R | See I.2.1. |
| lifecycle\_events | list\<map\<event,timestamp,reason>> | R |  |
| updated\_at | timestamp | R |  |

### I.1.10 — Performance Record (sole writer: C-08)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| performance\_id | string | R |  |
| reporting\_period | map\<start,end> | R |  |
| attribution\_unit | enum | R | Tracking-ID / ASIN / Pin-level Pinterest engagement. |
| attribution\_value | string | R |  |
| metric\_name | string | R |  |
| metric\_value | decimal | R |  |
| source | enum | R | Pinterest / Amazon. |
| collected\_at | timestamp | R |  |

### I.1.11 — Learning Record (sole writer: C-09)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| learning\_id | string | R |  |
| observed\_pattern | string | R |  |
| evidence | list\<reference> | R |  |
| hypothesis | string | R |  |
| confidence | enum | R | Low / Medium / High. |
| proposed\_action | string | R |  |
| affected\_capability | reference | R |  |
| affected\_rubric\_or\_rule | reference | O |  |
| status | enum | R | Accepted / Rejected / Deferred / Escalated. |
| created\_at | timestamp | R |  |

### I.1.12 — Rubric Version Record (sole writer: C-11)

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| rubric\_version | string | R |  |
| effective\_date | date | R |  |
| criteria | list\<map\<name,weight,scale,threshold>> | R | Threshold per criterion. |
| hard\_constraints | list\<string> | R |  |
| minimum\_weighted\_score | decimal | R | Global eligibility threshold. |
| change\_justification | string | R |  |
| change\_log\_entry | string | R |  |
| approver | reference | R |  |
| status | enum | R | Draft / Active / Retired. |

### I.1.13 — Contract Failure Record (sole writer: the detecting contract)

This is the only exception to INV-10.

| Field | Type | R/O | Notes |
| --- | --- | --- | --- |
| failure\_id | string | R |  |
| contract\_id | string | R | C-NN. |
| failure\_type | enum | R | Precondition / Postcondition / Rule / Evidence / Traceability. |
| error\_code | enum | R | See I.4. |
| detected\_at | timestamp | R |  |
| detected\_by | string | R |  |
| severity | enum | R | Operational / Material / Systemic. |
| escalated\_to\_learning | boolean | R |  |
| resolution | string | O |  |

## Part I.2 — State Machines

States are persistent and events are transitions; a record is in exactly one state at any time.

### I.2.1 — Pin Lifecycle

States: **Live**, **Under Review**, **Archived**. Every transition is executed by C-07 (INV-13), even when triggered by a C-06 Validation Result.

| Event | From | To | Triggered by | Executed by |
| --- | --- | --- | --- | --- |
| Published | — | Live | C-07 | C-07 |
| Review triggered | Live | Under Review | C-06 (Validation Result = FAIL) | C-07 |
| Review cleared | Under Review | Live | C-06 (Validation Result = CLEARED) | C-07 |
| Re-linked | Under Review | Live | C-06 (corrective action = re-link) | C-07 |
| Replaced | Live or Under Review | Archived | C-06 | C-07 |
| Archived | Live or Under Review | Archived | C-06 | C-07 |
| Restored | Archived | Live | Editorial Owner | C-07 |

### I.2.2 — Recommendation Status

| State | Meaning | Allowed next states |
| --- | --- | --- |
| Draft | Being written. | Approved, Low-Confidence, Rejected |
| Approved | Evidence confidence = High or Medium (Medium unreachable until OI-008). | Revoked |
| Low-Confidence | Evidence confidence = Low; awaiting human review. | Human-Review-Approved, Rejected, Revoked |
| Human-Review-Approved | Accepted by human review despite Low confidence. | Revoked |
| Rejected | Withdrawn before presentation. | Terminal |
| Revoked | Withdrawn after approval because a material claim is no longer supported by any Active Evidence Record (INV-12). | Terminal |

### I.2.3 — Rubric Version Status

| State | Allowed next states |
| --- | --- |
| Draft | Active, Retired |
| Active | Retired |
| Retired | Terminal |

Exactly one version is Active at a time (INV-2).

### I.2.4 — Evidence Record Status

| State | Allowed next states |
| --- | --- |
| Active | Superseded |
| Superseded | Terminal |

## Part I.3 — Global Invariants

Fifteen invariants hold across all contracts; v1.1 splits INV-1 into a gate form and an audit form.

| # | Invariant |
| --- | --- |
| INV-1a | **Pre-publication gate.** A Content Asset may be published only if a Validation Result with phase = Pre-publication and status = PASS and a Compliance Record with decision = Approve both exist for that asset. Checkable before any Publication Record exists. |
| INV-1b | **Post-publication audit.** Every Publication Record's `validation_result_id` and `compliance_record_id` point to the records that satisfied INV-1a. |
| INV-2 | At most one rubric version is Active at any time. |
| INV-3 | URL tracking ID = Content Asset tracking ID = tracking ID in the Product Record's approved destination reference. |
| INV-4 | Every material claim in a Recommendation Record references at least one Active Evidence Record. |
| INV-5 | Every published Pin has a Publication Record in state Live, Under Review, or Archived. |
| INV-6 | Every Product Record has an approved destination reference. |
| INV-7 | Every Content Asset derives its affiliate URL and tracking ID from the same Product Record reference. |
| INV-8 | Contract failures of severity Material or Systemic produce a Contract Failure Record with `escalated_to_learning = true`. |
| INV-9 | Performance Measurement is a monitoring input to Compliance (CD1), never a runtime gate for publication. |
| INV-10 | Every record type in I.1 has exactly one sole writer, except the Contract Failure Record, written by the detecting contract. |
| INV-11 | Every published Pin has a Publication Record whose `validation_result_id` and `compliance_record_id` are set. |
| INV-12 | When a material claim's supporting Evidence Record is superseded: (1) if a successor supports the same claim, the reference is re-pointed and the recommendation keeps its state; (2) if none does, the recommendation transitions to Revoked. |
| INV-13 | Every Pin lifecycle transition is executed by C-07 only, even when triggered by a C-06 Validation Result. |
| INV-14 | Every reference to a Product Record is of the form `(product_id, version)`. |

INV-11 is the existence check and INV-1b the correctness check of the same references; both are evaluated after publication.

## Part I.4 — Error Codes

Each code carries detection method, default response, severity, and deadline; Part II contracts cite codes only.

| Code | Meaning | Detection | Default response | Severity | Deadline |
| --- | --- | --- | --- | --- | --- |
| E-PRE-01 | Missing required precondition. | Deterministic | Block | Operational | Immediate |
| E-POST-01 | Postcondition not satisfied. | Deterministic | Block | Material | Immediate |
| E-RULE-01 | Hard constraint violated. | Deterministic | Block | Material | Immediate |
| E-RULE-02 | Soft constraint violated. | Deterministic or human | Return for correction | Operational | 24h |
| E-EV-01 | Material claim missing an Evidence Record. | Deterministic | Block | Material | Immediate |
| E-EV-02 | Evidence source classification missing. | Deterministic | Return for correction | Operational | 24h |
| E-EV-03 | Evidence superseded; material claim no longer supported. | Deterministic | Revoke recommendation | Material | Immediate |
| E-EV-04 | Evidence superseded; successor available for the claim. | Deterministic | Re-point claim; no status change | Operational | 24h |
| E-TR-01 | Traceability link missing. | Deterministic | Block | Material | Immediate |
| E-TR-02 | Traceability link inconsistent (e.g., tracking ID mismatch). | Deterministic | Block | Material | Immediate |
| **E-TR-03** | **Tracking ID inactive (Associates account closed or tag deactivated). New, CP-005.** | Human review or deterministic | Review triggered; re-link when a valid tracking ID exists; block new publications using it | Material | 72h after a valid tracking ID exists |
| E-ALIGN-01 | Pin promise does not match content. | Deterministic or human | Block | Material | Immediate |
| E-ALIGN-02 | Destination not reachable (product still available). | Deterministic | Re-link | Material | 24h |
| E-ALIGN-03 | Product Record materially changed. | Deterministic | Review triggered | Material | 24h |
| E-ALIGN-04 | Destination not reachable and product discontinued. | Deterministic | Archive Pin | Material | 24h |
| E-GOV-01 | Disclosure missing or incorrect. | Deterministic or human | Block | Material | Immediate |
| E-GOV-02 | Link format non-conforming. | Deterministic | Block | Material | Immediate |
| E-GOV-03 | Image use non-conforming. | Deterministic or human | Block | Material | Immediate |
| E-GOV-04 | Price display non-conforming. | Deterministic | Block | Material | Immediate |
| E-GOV-05 | Prohibited category. | Deterministic | Block | Material | Immediate |
| E-GOV-06 | Survival checkpoint missed. | Human review | Escalate | Systemic | Immediate |
| E-RUB-01 | Evaluation against non-Active rubric version. | Deterministic | Return for correction | Operational | 24h |
| E-RUB-02 | Rubric change without justification or approval. | Deterministic | Block | Material | Immediate |
| E-PUB-01 | Publication attempted without both gates (INV-1a). | Deterministic | Block | Material | Immediate |
| E-PUB-02 | Publication with incorrect or missing tracking ID. | Deterministic | Block | Material | Immediate |
| E-PUB-03 | Corrective action exceeded the corrective-action window. | Deterministic | Escalate | Material | Immediate |
| E-PERF-01 | Data staleness beyond cadence. | Deterministic | Return for correction | Operational | 48h |
| E-PERF-02 | Unreconciled data when outbound clicks > 0. | Deterministic | Escalate | Operational | 48h |
| E-CD-01 | Change-detection run missed. | Human review | Escalate | Operational | 24h |

The E-TR-03 deadline runs from the moment a valid tracking ID exists, because no re-link is possible before then; the Pin stays Under Review meanwhile.

## Part I.5 — Change Detection

C-02 detects changes, C-10 versions Evidence Records, and C-04 re-evaluates affected recommendations.

**Watched sources:** Amazon product pages referenced by current Product Records; manufacturer pages referenced by Active Evidence Records; the status of active tracking IDs (CP-005).

**Checked facts:** product identity (ASIN); dimensions, materials, and functional capabilities referenced in material claims; price ±30% (informational only); availability; rating < 3.5; review count < 50; source changes affecting Active Evidence Records; tracking ID still active on the Associates account.

**Detection semantics.** An Evidence Record is superseded only when the specific fact it supports changes, not when the page snapshot changes trivially. With a successor for the claim, the reference is re-pointed (E-EV-04, no status change). Without one, the recommendation is Revoked (E-EV-03, INV-12).

**Outputs.**

| Detected | Result |
| --- | --- |
| Material product change | New Product Record version; `is_current` updated; C-06 post-publication check scheduled for Pins referencing the earlier `(product_id, version)`. |
| Evidence source changed | C-02 requests C-10 to supersede the record and create a successor (D-4). |
| Recommendation Revoked | C-06 post-publication check scheduled; C-07 executes the resulting transitions. |
| Tracking ID inactive | E-TR-03; C-06 issues FAIL for each affected Pin; C-07 executes Review triggered. |
| Change-detection run missed | Contract Failure Record (E-CD-01). |

**Cadence:** provisional daily when compliant automated access exists; otherwise weekly manual review of current Product Records (A.5 §24). Subject to revision after 30 days of live operation.

## Part I.6 — Deferred Definitions

**D-1 — Material claim.** Dimensions, weight, size, materials, functional capability, compatibility (including derived statements), safety, durability, performance, availability. Subjective statements are excluded.

**D-2 — Factual error rate.** factual\_errors / total\_material\_claims per reporting period. A missing Evidence Record is a C-04 postcondition failure, not a factual error.

**D-3 — Evidence confidence.** Only Active Evidence Records count. High = every material claim traces to a Verified record. Medium = every claim traces to a record and at least one is Limited Reliability (unreachable until OI-008). Low = at least one claim traces only to an Unverified record. A claim with no record at all is a postcondition failure (E-EV-01), not Low.

**D-4 — Evidence versioning.** A successor is created only when the specific supported fact changes. Re-point (E-EV-04) when a successor exists; Revoke (E-EV-03) only when none supports the claim.

**D-5 — Material product change.** Any change to a fact covered by D-1, to ASIN identity, or to hard-constraint fields (category, rating, review count). Price ±30% is informational and does not trigger C-06.

**D-6 — Pin lifecycle.** Per I.2.1; executed by C-07 only (INV-13).

## Part I.7 — Contract Compliance Requirements

A contract is satisfied when all six conditions hold:

1. All preconditions are met before execution.
2. All business rules are enforced.
3. All postconditions hold after execution.
4. All failure conditions are detectable (I.4).
5. All evidence requirements are met.
6. All traceability links exist.

**I.7.1 — Failure handling inheritance.** Every failure carries an I.4 code with its detection method, default response, severity, and deadline.

**I.7.2 — Traceability.** Every record references its source and destination records. Missing links raise E-TR-01; inconsistent links raise E-TR-02.

**I.7.3 — Severity and learning escalation.**

| Severity | Definition | Learning escalation |
| --- | --- | --- |
| Operational | Single instance, self-correctable within the corrective-action window. | No |
| Material | Affects a published Pin, a claim, or a compliance check. | Yes |
| Systemic | Recurs at least 3 times in a rolling 30-day window, or affects multiple assets. | Yes, plus review at the affected capability (not the rubric by default) |

## Part I.8 — Minimum Record Set for a Published Pin

A Pin is contract-complete at publication when the twelve records below exist and are linked; this is the single definition that A.1 §17-A, A.3 §1.1, and A.5 §46 reference.

| # | Record | Minimum | Required state |
| --- | --- | --- | --- |
| 1 | Rubric Version Record | 1 | Active |
| 2 | Context Record | 1 | Approved |
| 3 | Product Record | 1 version | `is_current = true` |
| 4 | Evidence Record — Primary | 1 | Active |
| 5 | Evidence Record — Claim-level | 1 per material claim | Active |
| 6 | Evidence Record — Imagery | 1 per image used | Active, `license_or_permission` set |
| 7 | Evaluation Record | 1 | Eligible, citing the Active rubric |
| 8 | Recommendation Record | 1 | Approved or Human-Review-Approved |
| 9 | Content Asset | 1 | `disclosure_text` and `tracking_id` set |
| 10 | Validation Result | 1 | Pre-publication, PASS |
| 11 | Compliance Record | 1 | Approve, CD2–CD4 verification dates set |
| 12 | Publication Record | 1 | Live |

Records 1–11 must exist before publishing (INV-1a, INV-3, INV-4 checked then); record 12 is created at publication. Performance and Learning Records are not part of this set: they depend on time after publication, so a cycle may require them separately, as A.1 §17-A does at window close.

## Part II — Capability Contracts

Each contract states its outputs and sole writer, cites BC (`A.3-CAP-STYP-001` v1.3) for preconditions and boundaries, and adds verification and failure codes.

### C-01 — Context Management

**Outputs:** Context Record (I.1.1); sole writer C-01. **Preconditions / postconditions / failures / boundary:** BC §7.6, §7.7, §7.12, §7.5. **Failure codes:** E-PRE-01, E-POST-01, E-RULE-01.

### C-02 — Product Discovery

**Outputs:** Product Candidate Set; Product Record (I.1.2), sole writer C-02; change-detection outcomes (I.5). **Preconditions / failures / boundary:** BC §8.6, §8.12, §8.5. **Failure codes:** E-PRE-01, E-EV-01, E-EV-02, E-TR-01, E-TR-03, E-CD-01.

C-02 writes Product Records and detects source changes. It does not version Evidence Records; that is C-10 (E-EV-04). Programmatic mode depends on OI-004; the manual path uses the same schema and checks.

### C-03 — Product Evaluation & Curation

**Outputs:** Evaluation Record (I.1.4); sole writer C-03. **Preconditions / failures / boundary:** BC §9.7, §9.13, §9.6. **Failure codes:** E-PRE-01, E-RULE-01, E-RUB-01.

### C-04 — Recommendation Generation

**Outputs:** Recommendation Record (I.1.5); sole writer C-04. C-04 reads the Product Record and never writes it.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | Every material claim references at least one Active Evidence Record. | Deterministic (E-EV-01) |
| 2 | Evidence confidence computed per D-3. | Deterministic |
| 3 | Status is one of the states in I.2.2. | Deterministic |
| 4 | When supporting evidence is superseded and a successor exists, the claim is re-pointed. | Deterministic (E-EV-04) |
| 5 | When a material claim has no Active supporting record, the recommendation becomes Revoked. | Deterministic (E-EV-03, INV-12) |

**Failure codes:** E-POST-01, E-EV-01, E-EV-03, E-EV-04, E-RULE-01.

### C-05 — Content Presentation

**Outputs:** Content Asset (I.1.6); sole writer C-05. **Preconditions / boundary:** BC §11.7, §11.6.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | Affiliate URL and tracking ID derived from the same Product Record reference. | Deterministic (INV-3, INV-7) |
| 2 | `disclosure_text` present, using the wording verified under OI-006. | Deterministic + human (E-GOV-01) |
| 3 | `product_image_reference` points to an Active Imagery Evidence Record with permission recorded. | Deterministic (E-GOV-03) |
| 4 | `contextual_image_reference`, if present, points to an Active Imagery Evidence Record for licensed or stock imagery. | Deterministic (E-GOV-03) |
| 5 | Asset available to C-06 and C-12. | Deterministic |

**Failure codes:** E-TR-02, E-RULE-01, E-GOV-01, E-GOV-03.

AI-generated contextual imagery stays excluded until CP-002 is accepted. A Pin without a contextual image is valid under CP-004.

### C-06 — Consistency Validation

**Outputs:** Validation Result (I.1.7); sole writer C-06. **Preconditions / boundary:** BC §12.9, §12.8.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | Asset has explicit state PASS, FAIL, or CLEARED. | Deterministic |
| 2 | Post-publication failures are handed to C-07 with a corrective action. | Deterministic |
| 3 | C-06 issues a Validation Result with status CLEARED; C-07 executes the transition on the Publication Record. | Deterministic (INV-13) |

**Failure codes:** E-ALIGN-01 to E-ALIGN-04, E-TR-02, E-TR-03.

### C-07 — Publication & Lifecycle

**Outputs:** Publication Record (I.1.9); sole writer C-07. **Preconditions / boundary:** BC §13.6, §13.5.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | INV-1a held at the moment of publication. | Deterministic (E-PUB-01) |
| 2 | Publication Record references the authorizing Validation Result and Compliance Record. | Deterministic (INV-1b, INV-11) |
| 3 | Current lifecycle state recorded per I.2.1. | Deterministic |
| 4 | Corrective actions recorded with outcome and executed within the 72h provisional window. | Deterministic (E-PUB-03) |
| 5 | All Pin lifecycle transitions are executed by C-07. | Deterministic (INV-13) |
| 6 | A post-publication check is scheduled whenever a linked Recommendation becomes Revoked or a tracking ID becomes inactive. | Deterministic scheduling |

**Failure codes:** E-PUB-01, E-PUB-02, E-PUB-03.

### C-08 — Performance Measurement & Attribution

**Outputs:** Performance Record (I.1.10); sole writer C-08. **Preconditions / boundary:** BC §14.7, §14.6. **Postconditions:** data available at the supported attribution level; completeness and freshness recorded. **Failure codes:** E-PERF-01, E-PERF-02.

C-08 is a monitoring input to C-12 CD1 and never a publication gate (INV-9). Manual or CSV entry is a valid implementation.

### C-09 — Learning & Improvement

**Outputs:** Learning Record (I.1.11); sole writer C-09. **Preconditions / boundary:** BC §15.6, §15.5. **Postconditions:** every Learning Record links to supporting Performance Records; every hypothesis states its evidence basis and confidence; accepted rubric proposals are handed to C-11.

C-09 receives only Material or Systemic failures (I.7.3).

### C-10 — Evidence Management

**Outputs:** Evidence Record (I.1.3); sole writer C-10. **Preconditions / boundary:** BC §16.7, §16.6.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | Every material claim references at least one Active Evidence Record. | Deterministic (INV-4) |
| 2 | Records are versioned when C-02 or C-10's own governance detects a source change. | Deterministic (D-4) |
| 3 | Claims on a superseded record are re-pointed to the successor when one exists. | Deterministic (E-EV-04) |
| 4 | Every Imagery record has `license_or_permission` set. | Deterministic (E-GOV-03) |

**Failure codes:** E-EV-01 to E-EV-04.

### C-11 — Rubric Management

**Outputs:** Rubric Version Record (I.1.12); sole writer C-11. **Preconditions / boundary:** BC §17.6, §17.5. **Postconditions:** exactly one Active version (INV-2); justification and approver recorded. **Failure codes:** E-RUB-02.

### C-12 — Compliance & Governance

**Outputs:** Compliance Record (I.1.8); sole writer C-12. **Preconditions / boundary:** BC §18.10, §18.6.

| # | Postcondition | Verification |
| --- | --- | --- |
| 1 | Compliance Record exists with a decision. | Deterministic |
| 2 | If Approve, `rule_version_or_date` is set for CD2, CD3, and CD4, i.e., the rules were verified, not assumed. | Deterministic |
| 3 | If Approve, the asset is eligible for C-07 subject to Validation = PASS (INV-1a). | Deterministic |

**Failure codes:** E-GOV-01 to E-GOV-06.

## Cross-Contract Traceability Matrix

Two contracts gate publication (C-07 and C-12); every other contract produces inputs for them.

| Contract | Produces | Consumes | Gates |
| --- | --- | --- | --- |
| C-01 | Context Record | — | — |
| C-02 | Product Record, Product Candidate Set, change-detection outcomes | C-01, C-10 | — |
| C-03 | Evaluation Record | C-02, C-10, C-11 | — |
| C-04 | Recommendation Record | C-03, C-10 | — |
| C-05 | Content Asset | C-04, C-10 | — |
| C-06 | Validation Result | C-05, C-10 | — |
| C-07 | Publication Record | C-05, C-06, C-12 | Publication gate (INV-1a) |
| C-08 | Performance Record | C-07 | — |
| C-09 | Learning Record | C-08, C-03, C-04, C-07, C-11, Contract Failure Records | — |
| C-10 | Evidence Record | External sources | — |
| C-11 | Rubric Version Record | C-09 (feedback) | — |
| C-12 | Compliance Record | C-05, C-10, C-08 (monitoring only) | Publication gate (Approve) |

## What This Document Does Not Do

It does not prescribe implementation mechanisms, architecture, storage, or APIs; those belong to `A.5-ENG-STYP-001`. It does not reopen capability boundaries from `A.3-CAP-STYP-001` v1.3. It does not define business metrics, cycle objectives, dates, or the Decision Frame; those live only in `A.1-BIZ-STYP-001`.

## Handoff to the Engineering Proposal

`A.5-ENG-STYP-001` must derive, for each contract, the execution mechanism, the storage model for each I.1 record, the tooling for each rule, the build sequence from runtime dependencies, and the human roles at each step. It must not redefine contracts; divergences return as Change Proposals.

Two v1.1 items require action in A.5: `check_invariants` should validate INV-1a (not INV-1) before publication, and the Publication Record model gains the optional `production_time_minutes` field already described in A.5 §32.

## Notes on External Facts

**Amazon API.** PA-API is deprecated and replaced by Creators API; any earlier reference to PA-API means Creators API. Access conditions are tracked as OI-004 and gate only C-02's programmatic mode.

**Pinterest Storefront Linking.** Creators in the Amazon Influencer Program can connect a Storefront, after which attribution is applied automatically. Adopting it could bypass Style Picks' tracking IDs and break INV-3. That is a destination-model decision for `A.2-FUNC-STYP-001`; until made, Style Picks remains the tracking-ID source of truth.

**Associates account status.** If the account is closed, existing tracking IDs stop attributing. E-TR-03 (CP-005) defines the contract response; the business response belongs to the Decision Frame in `A.1-BIZ-STYP-001` §18-A.

## Formal Sign-Off

| Field | Value |
| --- | --- |
| Prepared by | Style Picks Editorial Owner |
| Engagement | STYP-VALIDATION-2026 |
| Stage / Level | A — Engineering Definition (Conceptual) / A.4 — Capability Contracts |
| Document ID | A.4-CONTR-STYP-001 |
| Version | 1.1 — Contract Formalization (Pipeline Reconciled) |
| Status | Baselined on acceptance of CP-004 and CP-005 |
| Authorization | Derives from `A.3-CAP-STYP-001` v1.3. `A.5-ENG-STYP-001` v1.4 remains authorized, subject to the two actions in the Handoff section. |
| Change Proposals | CP-001 Accepted 2026-10-08; CP-002 Pending; CP-003 Accepted 2026-10-08; CP-004 Proposed; CP-005 Proposed |
| Language | English |

*End of Capability Contracts Specification — A.4-CONTR-STYP-001 v1.1*