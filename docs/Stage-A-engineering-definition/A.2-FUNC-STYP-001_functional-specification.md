# STYLE PICKS
## Value Proposition Functional Specification

**Stage A.2 — Functional Definition**
**Physical Foundation of the Style Picks Functional Model**

**Document ID:** A.2-FUNC-STYP-001

**Version:** 1.3 — Functional Definition (Traction Demonstration Reconciled)

**Status:** Stage A — Engineering Definition (Conceptual Level) — Baselined

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Parent Documents:**
- A.1-BIZ-STYP-001 — Business Plan and Commercial Validation (v2.0 Traction Demonstration Baseline)
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.1)

**Child Documents:**
- A.3-CAP-STYP-001 — Business Capabilities Specification (v1.3 Traction Demonstration Reconciled)

**Domain:** Domain A.2 — Business Functions

---

**Business Model:** Content Commerce + Affiliate Commerce
**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**Initial Categories:** Home Decor + Home Organization
**Stage:** Traction Demonstration
**Amazon Associates Account Created:** 2026-04-15
**Amazon Associates Deadline:** 2026-10-12
**Operating Window:** From 2026-10-07 to 2026-10-12 (5 days)
**Actual Objective for This Cycle:** First Operational Milestone (FOM) — one published Pin with complete internal traceability
**Deferred Objective:** Commercial validation (≥ 5 qualifying purchases) — next cycle
**Destination Model:** Pinterest → Amazon (direct link)
**Document Type:** Business Functional Specification

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 7, 2026 | Initial functional specification |
| 1.1 | Oct 7, 2026 | Govern diagram, Align/Govern boundary, confidence model, thresholds, imagery, FTC/Pinterest disclosure, attribution scope, sources |
| 1.1 RC | Oct 7, 2026 | Checkpoint 135d split into two distinct alarms; interim evidence rule added; 12.3 attribution slip corrected; version label aligned with Section 22 |
| 1.1 RC (Baselined header) | Oct 8, 2026 | Normalized document header per Stage A codification; cross-references updated to A.x IDs; Open Items Register (`PH1-REG-STYP-001`) referenced; Change Proposals register referenced; Sign-Off block added |
| 1.2 | Oct 8, 2026 | **Consistency reconciliation with A.1 v1.5, A.3 v1.2, A.4 v1.0 Reconciled, A.5 v1.2.1.** (1) §13.3.1 placeholders `[OI-001]` and `[OI-002]` replaced with the actual closed values. (2) §18.2 marks "Amazon clicks ≥ 100" as **Provisional**, aligning with A.1 v1.5 §15. (3) §18.3 adds a note on checkpoint relevance when the remaining operating window is shorter than the checkpoint offset, aligning with A.1 v1.5 §18 and A.3 v1.2 §18.7. (4) §22 version label updated to reflect Baselined status. (5) §6.6 and §13.3.2 reference note about PA-API → Creators API aligned with A.4 and A.5 §48. (6) §10.6 explicit reference to CP-002 pending status retained. (7) Formal Sign-Off block added. |
| **1.3** | Oct 8, 2026 | **Structural reconciliation with A.1 v2.0 (Traction Demonstration Baseline).** (1) The document no longer declares commercial validation as the objective of this cycle. The **First Operational Milestone (FOM)** is now the declared objective, per A.1 v2.0 §17-A and A.5-ENG-STYP-001 §46. (2) §18.2 (Business Validation Thresholds) is restructured: the FOM appears as the **current-cycle** target; the survival floor (3) and success target (≥5) are marked as **deferred to the next cycle**. (3) §18.3 (Interim Checkpoints) is replaced by a **single end-of-window checkpoint** — "Was the FOM achieved?" — with the 135/90/60/30-day table moved to a historical note. (4) §15 (Conversion Hypothesis) clarifies that the 3% figure and the "≥100 Amazon clicks" target are planning tools for the next cycle, not commitments of this one. (5) §18.4 (new) defines the **Decision Frame at Window Close** by reference to A.1 v2.0 §18-A. (6) §22 version label updated. (7) §1 (Purpose) gains an explicit statement of what this cycle attempts and does not attempt. (8) All cross-references to A.1 updated from v1.5 §18 to v2.0 §17-A and §18-A. |

---

## Open Items

> **This document cannot be treated as final while any of the following remain empty. The authoritative source is `PH1-REG-STYP-001`.**

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

**Change Proposals affecting this document:**

| CP ID | Title | Affected sections | Status |
|-------|-------|-------------------|--------|
| CP-002 | AI-Generated Contextual Imagery | §10.6 | Pending |

> **On CP-002:** This CP, filed in `A.5-ENG-STYP-001` §47, proposes amending §10.6 of this document to admit AI-generated contextual imagery under labeling and evidence conditions, and to reference CD4 (Pinterest policies on AI-generated content labeling). Until CP-002 is accepted, only licensed and stock imagery are used.

---

# 1. Purpose

This document defines the **business functions required to deliver the Style Picks value proposition**.

> **Business functions define what Style Picks must accomplish. Engineering determines how those functions are executed.**

No technology, agent architecture, LLM framework, or implementation mechanism is prescribed.

## 1.1 What This Cycle Attempts — And What It Does Not

This document inherits the objective structure of `A.1-BIZ-STYP-001` v2.0.

**This cycle attempts:**

> **The First Operational Milestone (FOM): produce, validate, publish, and record one Pin end-to-end within the Style Picks internal system.**

The FOM is defined operationally in `A.5-ENG-STYP-001` §46.

**This cycle does not attempt:**

- commercial validation;
- reaching the survival floor of 3 qualifying purchases;
- reaching the success target of ≥ 5 qualifying purchases;
- producing statistically meaningful performance data.

The operating window is 5 days (2026-10-07 to 2026-10-12). It cannot support validation. It can support the FOM.

**Functional consequence:** The eight business functions defined below must be executable **at least once, manually**, within the operating window. They do not need to be automated, scaled, or optimized in this cycle. The functional model is the target; the FOM is the first instance of it operating.

---

# 2. Value Proposition

Style Picks reduces the friction of home-product discovery by transforming an overwhelming selection of products into **curated, contextual, and visually compelling recommendations**.

### Core Value Proposition

> **Discover better home products without having to search through hundreds of options.**

---

# 3. Functional Objective

```text
Consumer Context
       ↓
Context Definition
       ↓
Product Discovery
       ↓
Product Selection
       ↓
Recommendation
       ↓
Presentation
       ↓
Alignment & Validation
       ↓
Publication
       ↓
Consumer Action
       ↓
Measurement & Learning
       ↺
```

Governance operates transversally across the entire flow.

> **Cycle note:** In this cycle, the flow is executed **once**, manually, for the first Pin. The feedback arrow (Measurement & Learning) is present in the model but produces no statistically meaningful input in 5 days. It becomes operational in the next cycle.

---

# 4. Functional Model

| # | Function | Primary responsibility |
|---|----------|------------------------|
| 1 | **Context Definition** | Define the consumer situation, need, problem, or opportunity |
| 2 | **Discover** | Identify relevant product candidates |
| 3 | **Select** | Determine which products deserve editorial consideration |
| 4 | **Recommend** | Produce a contextual and evidence-based recommendation |
| 5 | **Present** | Transform the recommendation into a compelling discovery experience |
| 6 | **Align** | Verify internal consistency between promise, content, product, and destination |
| 7 | **Learn** | Measure outcomes and improve future decisions |
| 8 | **Govern** | Enforce conformance to external rules and constraints |

> **Cycle note:** All eight functions must be executable at least once for the FOM. Function 7 (Learn) produces its first record but no actionable insight in this cycle.

---

# 5. Function 1 — Context Definition

## 5.1 Purpose
Define the consumer situation that Style Picks intends to address before searching for products.

## 5.2 Responsibility
Determine: consumer need, physical or situational environment, relevant constraints, desired outcome, aesthetic or functional preferences, applicable product category, potential search concepts.

## 5.3 Inputs
Consumer needs, observed problems, editorial strategy, market signals, trends, historical performance, existing content opportunities.

## 5.4 Outputs
Structured context definition with: context name, problem/need, target outcome, constraints, product categories, editorial opportunity, approved price range for the context.

## 5.5 Boundary
Context Definition does **not** select products.

## 5.6 Ownership
**Editorial Owner.** No automated system introduces a new context without explicit editorial approval.

## 5.7 Cycle Note
For the FOM, **one context** is defined. It belongs to one of the two approved categories (Home Decor or Home Organization). Multiple contexts are deferred to the next cycle.

---

# 6. Function 2 — Discover

## 6.1 Purpose
Identify products that may be relevant to the defined context.

## 6.2 Responsibility
Locate products relevant to the defined context, category, consumer problem, and desired outcome.

## 6.3 Inputs
Defined context, category, search concepts, product sources, product data, market information.

## 6.4 Outputs
A normalized set of product candidates containing available factual information.

## 6.5 Boundary
Discover answers: **"What products could potentially solve this need?"**
It does not answer: **"Which product deserves to be recommended?"**

## 6.6 Programmatic Data Access Constraint

Discover depends on product data. Two sources exist:

### Source A — Amazon Creators API

Access to the API has historically required recent qualifying sales.

> **OI-004:** Verify current requirements. Record source and date here once verified.

**Functional consequence:** Discover must operate in **manual or semi-manual mode** during early validation until API access is confirmed.

> **Reference note:** PA-API has been deprecated and replaced by **Creators API**. All references in this document to PA-API should be read as referring to Creators API. See `A.5-ENG-STYP-001` §48 and `A.4-CONTR-STYP-001` Notes on External Facts.

### Source B — Manual product research
Amazon Best Sellers, Movers & Shakers, Amazon search within approved categories, Pinterest search.

**Functional consequence:** The candidate product record must be structurally identical regardless of source.

## 6.7 Ownership
**Editorial Owner**, supported by deterministic scripts when available.

## 6.8 Cycle Note
For the FOM, Discover operates **entirely manually**. The operator identifies one product candidate through Amazon search or Best Sellers. Source A (Creators API) is not required for the FOM. The fallback path in `A.5-ENG-STYP-001` §37-A applies.

---

# 7. Function 3 — Select

## 7.1 Purpose
Evaluate candidate products against Style Picks' editorial criteria and determine which are worthy of recommendation.

## 7.2 Responsibility
Evaluate according to: relevance to context, functionality, design, usefulness, suitability for space, dimensions, price/value, quality indicators, ease of use, problem solved.

## 7.3 Inputs
Defined context, product candidates, factual attributes, editorial rubric, hard constraints.

## 7.4 Outputs
Ranked or approved set of products eligible for recommendation.

## 7.5 Boundary
Select answers: **"Does this product deserve to be considered by Style Picks?"**

## 7.6 The Editorial Rubric

### 7.6.1 Rubric Contents
Evaluation criteria with scale, weights, hard constraints, minimum thresholds, contextual suitability rules, acceptable evidence sources, unacceptable claims, confidence model, treatment of limitations.

### 7.6.2 Rubric V0.1 — Minimum Operational Version

> **Note:** These weights are **provisional hypotheses, not empirically validated coefficients.** They will be revised based on evidence from Learn.

Each criterion scored 1–5:

| Criterion | Weight | Hard constraint |
|-----------|--------|-----------------|
| Relevance to context | 30% | Minimum 3 |
| Functional fit | 25% | Minimum 3 |
| Price/value ratio | 15% | — |
| Visual suitability for Pinterest | 15% | — |
| Factual verifiability of claims | 15% | — |

> **Verifiability note:** Factual verifiability is a **scoring criterion**, not a hard constraint. Its relationship to Evidence Confidence is defined in Section 9.6.

**Hard constraints (any violation disqualifies):**

- Category not in the approved list (Home Decor, Home Organization)
- Price outside the approved range for the context (see 7.6.3)
- Rating below 3.5 stars
- Fewer than 50 reviews
- Prohibited or restricted Amazon category
- Product whose recommended use depends on a claim that cannot be substantiated at all (see 9.6)

**Minimum eligibility threshold:** weighted score ≥ 3.5.

### 7.6.3 Approved Price Range

Default: $15–$80. The Editorial Owner may adjust per context, recorded in the context definition (Section 5.4).

### 7.6.4 Rubric Evolution
Documented as a versioned update, justified by evidence from Learn, approved by the Editorial Owner.

## 7.7 Ownership
**Editorial Owner.** No automated system modifies the rubric.

## 7.8 Cycle Note
For the FOM, the rubric is applied **manually** to one candidate product. Rubric V0.1 is used as authored. No empirical validation is attempted in this cycle.

---

# 8. Function 4 — Recommend

## 8.1 Purpose
Transform a selected product into a **contextual, explained, evidence-based recommendation**.

## 8.2 Responsibility
Communicate: what the product is, why it is relevant, how it addresses the context, benefits supported by facts, limitations and trade-offs.

## 8.3 Inputs
Selected product, category, context, factual attributes, editorial criteria, applicable constraints.

## 8.4 Outputs
Structured recommendation: recommendation text, rationale, supporting facts, limitations, **editorial score**, **evidence confidence**.

## 8.5 Boundary
Recommend does not independently discover products nor replace Select.

## 8.6 Ownership
**Editorial Owner.** LLM-assisted output is a **draft** until it passes Align and Govern.

## 8.7 Cycle Note
For the FOM, the recommendation is **authored by the Editorial Owner** using the structured fields defined in §9.4. LLM assistance is optional and not required.

---

# 9. Product Recommendation Contract

## 9.1 Input
Product, category, context, factual attributes.

## 9.2 Preconditions
- Product data verified against at least one source
- Category approved (in the active category list)
- A valid destination has been identified

> Reachability is verified by Align (Section 11), not Recommend.

## 9.3 Decision Rules
Eligible only when editorial score meets threshold (7.6.2) and no hard constraint violated.

## 9.4 Output
Recommendation, rationale, supporting facts, limitations, editorial score, evidence confidence.

## 9.5 Postconditions
- Every factual claim traceable to source data
- Recommendation matches defined context
- No unsupported product characteristics introduced
- Material limitations not intentionally omitted

## 9.6 Editorial Score and Evidence Confidence

**Two separate signals drive routing.**

### Editorial Score
How good the product is according to the rubric (weighted score 1–5).

### Evidence Confidence
How certain we are that the recommendation is factually supported.

| Evidence Confidence | Condition |
|---------------------|-----------|
| **High** | All claims traceable to verified sources |
| **Medium** | All claims traceable, but at least one source has limited reliability |
| **Low** | At least one claim has weak traceability |

**Routing rule:**

| Editorial Score | Evidence Confidence | Routing |
|-----------------|---------------------|---------|
| ≥ 3.5 | High or Medium | Proceeds to Present |
| ≥ 3.5 | Low | Routes to **human review** |
| < 3.5 | any | **Rejected** |
| any | any hard constraint violated | **Rejected** |

### 9.6.1 Verifiability vs Evidence Confidence

These are distinct:

- **Factual verifiability score** (rubric criterion) = how verifiable the product's claims are, in the abstract.
- **Evidence confidence** (routing signal) = for this specific recommendation, how well-supported the claims we are actually making.

A product may have **high verifiability score** but **Low evidence confidence**. In that case, it routes to human review, not rejection.

A product whose recommended use depends on a claim that **cannot be substantiated at all** is rejected by the hard constraint in 7.6.2.

### 9.6.2 Interim Evidence Rule (Applicable Until Evidence Source Policy Exists)

> **Requirement for the next layer:** The full Evidence Source Policy belongs in the **Business Capabilities Specification / Capability Contracts** (`A.3-CAP-STYP-001` §16.5, `A.4-CONTR-STYP-001` I.1.3).

**Interim rule for Stage A:**

Until that policy exists, only two sources count as **verified**:

1. The Amazon product page (product facts: dimensions, materials, weight, color, function as stated)
2. The manufacturer's official site (specifications not present on the product page)

Any claim sourced from anything else — customer reviews, third-party publications, Pinterest posts, LLM-generated information — **lowers Evidence Confidence to Low**, which routes the recommendation to human review.

This rule is deliberately strict. It keeps routing operable from the first Pin and will be relaxed only when the Evidence Source Policy defines reliability tiers.

> **Tracked as OI-008** in `PH1-REG-STYP-001`.

## 9.7 Cycle Note
For the FOM, the recommendation is expected to be **High confidence**, because the only material claims made are drawn directly from the Amazon product page. If a claim requires a source other than the Amazon product page or the manufacturer site, it is either removed or the recommendation is routed to human review (which, in this cycle, is the Editorial Owner reviewing their own draft).

---

# 10. Function 5 — Present

## 10.1 Purpose
Transform the recommendation into a visually compelling and commercially usable discovery experience.

## 10.2 Responsibility
Present determines: visual composition, title, description, imagery, format, editorial framing, call to action.

> Destination is defined by the destination model (10.3) and validated by Align.

## 10.3 Destination Model
```text
Pin → Amazon product page (via affiliate link)
```
**Consequences:** Present produces a single asset; Align verifies a single link; Learn relies on Amazon tracking IDs; Govern applies all applicable disclosure rules.

## 10.4 Inputs
Recommendation, product, context, brand identity, content format, platform requirements.

## 10.5 Outputs
Publication-ready content asset.

## 10.6 Imagery Rule

**Rule:** The recommended product must be **visibly and accurately represented** in the Pin.

**Permitted use of imagery:**

| Element | Source |
|---------|--------|
| Product image | Amazon-provided image (within Associates Program permissions) or original photography of the same product |
| Setting / lifestyle context | Licensed or stock lifestyle imagery |
| Composition | Product composite, when the product image is used within program permissions |

**What stock imagery may supply:** only the setting around the product. It may **not** be used to depict the product itself if it is not the same product.

**Prohibited:**
- Using a stock photo of a similar-but-different product to represent the recommended product
- Using an Amazon product image outside the permissions granted by the Associates Program
- Using unlicensed third-party images

**Recorded metadata per Pin:** source of the product image, permission under which it is used, source and license of any stock imagery.

> **Rationale:** Without this rule, a Pin could show a lamp that is not the recommended lamp. That would fail Align by design and would be misleading to the consumer.

> **Pending CP-002:** A Change Proposal filed in `A.5-ENG-STYP-001` §47 proposes admitting AI-generated contextual imagery under labeling and evidence conditions. Until CP-002 is accepted, only licensed and stock imagery are used.

## 10.7 Price Display Rule

> **Stage A rule: Pins do not display prices.**

**Rationale:** Prices go stale, create Govern exposure, and complicate post-publication Align checks.

## 10.8 Ownership
**Editorial Owner.** Tools assist but do not decide.

## 10.9 Cycle Note
For the FOM, one Content Asset is produced. If a suitable licensed or stock image cannot be found within the operating window, the Editorial Owner may publish a Pin with the Amazon product image alone, provided the Associates Program permissions allow it. This is a permissible simplification for the FOM.

---

# 11. Function 6 — Align

## 11.1 Purpose
Verify that consumer-facing content remains **internally consistent** from promise through destination.

## 11.2 Alignment Chain
```text
Promise → Content → Recommendation → Product → Destination
```

## 11.3 Verification Criteria (Internal Consistency)
- Pin promise corresponds to content
- Content corresponds to recommendation
- Recommendation corresponds to product
- Destination corresponds to promised product
- Destination is **reachable**
- Material changes have not invalidated the original recommendation

## 11.4 Inputs
Pin content (title, description, image), recommendation, product record, affiliate destination URL.

## 11.5 Outputs
- **Pass** — coherent and valid
- **Fail** — incoherent; specific inconsistency identified and routed for correction

## 11.6 Timing
- **Pre-publication:** verify coherence
- **Post-publication:** verify nothing has invalidated the content

## 11.7 Failure Path — Post-Publication

| Failure type | Corrective action |
|--------------|-------------------|
| Product out of stock (temporary) | No action; monitor |
| Product discontinued permanently | Archive Pin |
| Destination URL broken | Re-link to current product URL |
| Product materially changed | Archive Pin and create new content |
| Recommendation no longer accurate | Archive Pin |

## 11.8 Boundary
Align does not create the recommendation. It determines whether the result is still valid.

## 11.9 Relationship with Govern

| Function | Checks |
|----------|--------|
| **Align** | Internal consistency along the chain |
| **Govern** | Conformance to external rules |

> Disclosure verification, link-format conformance, and price-display compliance belong to **Govern only**.

## 11.10 Publication Gate

> **Publication requires Align = Pass AND Govern = Approve.**

## 11.11 Ownership
**Editorial Owner.** Deterministic checks may be automated; non-deterministic checks remain human.

## 11.12 Cycle Note
For the FOM, Align is performed **manually by the Editorial Owner** immediately before publication. Post-publication Align checks are scheduled but not required within the 5-day window unless the Pin is published early enough to allow one check.

---

# 12. Function 7 — Learn

## 12.1 Purpose
Convert observed outcomes into improvements in editorial decisions and future content.

## 12.2 Inputs (Stage A Scope)

> **Attribution scope:** Category-level tracking IDs give **category attribution**. "Performance by context" and "performance by content format" are **not achievable in Stage A** unless IDs are assigned at that granularity from the start.

**Achievable Stage A inputs:**
- impressions (Pinterest)
- saves (Pinterest)
- outbound clicks (Pinterest, per Pin)
- Amazon clicks (Amazon, per tracking ID)
- qualifying purchases (Amazon, per tracking ID)
- conversion (derived)
- revenue (Amazon)
- performance by category (via tracking ID)
- performance by product (via ASIN)
- production time (manual log)

**Not achievable in Stage A without additional tracking IDs:**
- performance by context
- performance by content format

## 12.3 Responsibility (Qualified to Match 12.2)

Learn identifies patterns **that are attributable within Stage A scope**:

- **categories** generating stronger **commercial action** (via tracking ID)
- **products** generating stronger commercial action (via ASIN)
- **recommendations** that repeatedly fail
- **editorial criteria** associated with successful products

**Engagement signals** (impressions, saves) come from **Pinterest analytics**, not from tracking IDs, and are treated as a separate signal from commercial action.

The following are addressed only through **partial attribution** (Pinterest per-Pin outbound clicks joined with Amazon category-level purchases):

- **contexts** generating engagement — approximate, not exact
- **content formats** producing traffic — approximate, not exact

> **Attribution limitation:** This is a partial bridge, not a full attribution mechanism.

## 12.4 Outputs
Performance insights, hypotheses, recommended editorial adjustments, new opportunities, rubric change proposals.

## 12.5 Boundary
Learn does not automatically redefine strategy. It provides evidence.

## 12.6 Tracking ID Strategy (Functional Requirement)

> **Tracking ID assignment is a functional requirement.** Without correct IDs, Learn cannot attribute performance.

### 12.6.1 Stage A Convention

| Tracking ID | Applied to |
|-------------|-----------|
| `stylepicks-home-20` | Home Decor category |
| `stylepicks-org-20` | Home Organization category |

### 12.6.2 Future Expansion
May subdivide by context if Amazon tracking ID capacity allows.

## 12.7 Cadence

| Cadence | Scope |
|---------|-------|
| Weekly | Operational review during validation |
| Monthly | Category and rubric review |
| On-demand | Hypothesis testing |

## 12.8 Weekly Review Questions
1. Are we producing enough content?
2. Is Pinterest distributing the content?
3. Is the content generating outbound clicks?
4. Are those users reaching Amazon?
5. Is the traffic producing purchases?

## 12.9 Ownership
**Editorial Owner**, assisted by analytical tools.

## 12.10 Cycle Note
For the FOM, Learn produces **one Learning Record** whose content is: *"The FOM was achieved (or not achieved), and the production-time baseline for the first Pin was X minutes."* The five weekly review questions are answered **once**, at window close, as inputs to the Decision Frame (`A.1-BIZ-STYP-001` v2.0 §18-A).

The weekly cadence in 12.7 is aspirational for this cycle. It becomes operational in the next cycle.

---

# 13. Function 8 — Govern

## 13.1 Purpose
Ensure Style Picks operates within defined quality, factual, commercial, legal, affiliate, and platform constraints.

## 13.2 Responsibility
Govern controls: factual accuracy, product-claim integrity, affiliate disclosure, platform requirements, content standards, prohibited claims, source traceability, editorial consistency, risk conditions.

## 13.3 External Rules Enforced by Govern

Each rule below requires verification against its current source. Verification status is recorded in Open Items (`PH1-REG-STYP-001`).

### 13.3.1 Amazon Associates — Qualifying Sales Requirement

> **OI-003:** Verify current rule. Record source and date.

**Functional consequence:**
- The Style Picks **survival horizon** = Associates account creation date + 180 days
- **Account created:** 2026-04-15 (OI-001, CLOSED)
- **Actual deadline:** 2026-10-12 (OI-002, CLOSED)
- The survival clock is **not** the operational start of October 7, 2026. The operating window from the operational start to the deadline is 5 days.
- **This cycle does not attempt to reach the survival floor.** The qualifying-sales rule governs the account's long-term survival, not this cycle's objective. See §18.2.

### 13.3.2 Amazon Associates — API Access

> **OI-004:** Verify current requirements. Record source and date.

> **Reference note:** PA-API has been deprecated and replaced by **Creators API**. All references in this document to PA-API should be read as referring to Creators API. See `A.5-ENG-STYP-001` §48 and `A.4-CONTR-STYP-001` Notes on External Facts.

### 13.3.3 Amazon Associates — Image and Price Display

> **OI-005:** Verify current rules. Record source and date.

### 13.3.4 Amazon Associates — Disclosure

> **OI-006:** Verify **exact required statement and placement**. Record source and date.

### 13.3.5 Amazon Associates — Link Format

> **OI-007:** Verify current link-format rules. Record source and date.

### 13.3.6 FTC Endorsement Disclosure (US)

> **Independent of Amazon.** For a US audience, FTC endorsement disclosure requirements apply.

### 13.3.7 Pinterest Policies on Affiliate Content

> **Independent of Amazon.** Pinterest's own policies on affiliate content apply.

## 13.4 Inputs
Business rules, editorial rules, platform requirements, affiliate requirements, source data, generated content, published content.

## 13.5 Outputs
Approve, Reject, Correct, Escalate, Compliance evidence.

## 13.6 Escalation Rules

> **All checkpoints are anchored to the Amazon Associates deadline (OI-002).**

| Condition | Action |
|-----------|--------|
| Hard constraint violation (missing disclosure, prohibited claim, non-conforming link format, non-conforming price display) | **Block** and **escalate** |
| Soft constraint violation (factual inconsistency, tone issue) | **Return** with error code |
| **At window close:** FOM not achieved | **Escalate** to Editorial Owner — proceed to Decision Frame (`A.1-BIZ-STYP-001` v2.0 §18-A) |
| Recurring violation of the same rule | **Escalate** and trigger rubric review |

> **Note:** Broken destination is an **Align** failure (11.3), not a Govern violation.

> **Historical note (V1.3):** The V1.2 checkpoint table (deadline minus 135/90/60/30 days) is retained in `A.1-BIZ-STYP-001` v2.0 §18 as a historical artifact but is **not operative** in the current cycle. All those checkpoints fall before the operational start (2026-10-07) and were never actionable. The only operative checkpoint is the FOM check at window close.

## 13.7 Boundary
Govern does not create the recommendation. It establishes the conditions under which the recommendation and its publication are acceptable.

## 13.8 Ownership
Govern rules defined by the **Editorial Owner** in consultation with current Amazon Associates, FTC, and Pinterest terms.

## 13.9 Cycle Note
For the FOM, the Govern rules that **must** be verified before publication are the ones governing the first Pin:

- required disclosure wording (OI-006);
- link-format rules (OI-007);
- image and price display rules (OI-005).

This is a **precondition to the FOM**, not a separate phase. It is estimated at a few hours of reading in `A.5-ENG-STYP-001` §32-B.

---

# 14. Functional Relationships

```text
                 ┌──────────────────────┐
                 │ Context Definition   │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Discover             │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Select               │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Recommend            │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Present              │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Align                │
                 │ Consistency Gate     │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Govern               │
                 │ Compliance Gate      │
                 │ (also transversal)   │
                 └──────────┬───────────┘
                            ↓
              Publication (requires Align = Pass
                       AND Govern = Approve)
                            │
                            ↓
                 ┌──────────────────────┐
                 │ Learn                │
                 └──────────┬───────────┘
                            │
                            └──────────────→ improves
                                            future decisions

   ┌───────────────────────────────────────────────────┐
   │ Govern — transversal control across the system    │
   │ (conformance to external rules at every stage)    │
   └───────────────────────────────────────────────────┘
```

> **Cycle note:** In the current cycle, this flow is executed **once**. The loop back from Learn to future decisions is present in the model but produces no actionable improvement in 5 days.

---

# 15. Functional Separation

| Function | Core question |
|----------|---------------|
| Context Definition | What consumer situation are we trying to solve? |
| Discover | What products could potentially solve it? |
| Select | Which products deserve consideration? |
| Recommend | Why is this selected product appropriate? |
| Present | How should that recommendation be communicated? |
| Align | Is everything still internally consistent? |
| Learn | What did the market teach us? |
| Govern | Does everything conform to external rules? |

---

# 16. Editorial Rubric as Core Business Artifact

The central decision-making asset of Style Picks is the **Editorial Recommendation Rubric**.

Its V0.1 operational version is defined in Section 7.6.2.

The rubric is upstream of Select, Recommend, Align, and Learn.

Its evolution is an explicit learning process, not an undocumented change in personal judgment.

> **Contractual basis:** Rubric Management is formalized as capability C-11 in `A.3-CAP-STYP-001` v1.3 §17 and contracted in `A.4-CONTR-STYP-001` C-11.
>
> **Cycle note:** Rubric V0.1 is used as authored in this cycle. No empirical validation is attempted.

---

# 17. Execution Mechanisms

This document intentionally does **not** assign agents to functions.

Possible mechanisms: deterministic, probabilistic, human, hybrid.

### 17.1 Preliminary Mechanism Mapping

> Preliminary and subject to revision in the Engineering Proposal (`A.5-ENG-STYP-001`).

| Function | Preliminary mechanism |
|----------|----------------------|
| Context Definition | Human |
| Discover | Deterministic (manual initially, scripted later) |
| Select | Human (rubric-assisted) |
| Recommend | Hybrid (LLM draft + human approval) |
| Present | Human + tools |
| Align | Deterministic + human |
| Learn | Deterministic + human analysis |
| Govern | Deterministic + human escalation |

> **Cycle note:** For the FOM, **all eight functions are executed manually**. The mechanisms above describe the target state of the next cycle, not the current one. Manual execution is a valid instantiation of each function per `A.5-ENG-STYP-001` §32 (Phase 0).

---

# 18. Functional Success Criteria

## 18.1 Functional Thresholds

These measure whether the **functions** are working.

| Threshold | Target | Audit method |
|-----------|--------|--------------|
| Recommendations passing Align on first attempt | ≥ 90% | Every Pin for the first 30; then 1 in 5 |
| Factual error rate found in review | ≤ 2% | Every Pin for the first 30; then 1 in 5 |
| Recommendation-context match rate | ≥ 95% | Every Pin for the first 30; then 1 in 5 |
| Governance violation rate | ≤ 2% | Every Pin for the first 30; then 1 in 5 |
| Pin-level ID integrity (Pins with correct tracking ID) | 100% | Every Pin |

> **Naming note:** This metric was previously named "Attribution completeness." It is now named **Pin-level ID integrity** to distinguish it from the tracking-ID-level metric in `A.3-CAP-STYP-001` v1.3 §14.12, now named **Tracking-ID attribution coverage**. The two metrics are related but distinct. See `A.3-CAP-STYP-001` v1.3 §21.
>
> **Cycle note:** For the FOM, the audit is performed on the first (and possibly only) Pin. The "1 in 5" sampling cadence becomes meaningful in the next cycle.

## 18.2 Business Validation Thresholds

> **These are business targets, not functional requirements.** They belong conceptually to the Business Plan (`A.1-BIZ-STYP-001`).
>
> **Cycle restructuring (V1.3):** The FOM is now the **current-cycle** target. The survival floor and success target are **deferred** to the next cycle, consistent with `A.1-BIZ-STYP-001` v2.0 §11 and §17-A.

| Threshold | Target | Cycle |
|-----------|--------|-------|
| **First Operational Milestone (FOM)** | **1 published Pin with complete internal traceability** | **This cycle** |
| Qualifying purchases — survival floor | 3 by deadline | Deferred |
| Qualifying purchases — success target | ≥ 5 by deadline | Deferred |
| Amazon clicks | ≥ 100 by deadline | Deferred (provisional) |
| Outbound click rate | ≥ 1.5% | Deferred (provisional) |
| Pins published | ≥ 120 by deadline | Deferred |
| Production time per Pin | ≤ 45 min average | Measured this cycle on the first Pin |

> **Provisional status of deferred targets:** The "≥ 100 Amazon clicks" target, the "≥ 1.5%" outbound click rate, and the "≥ 120 Pins" target are planning hypotheses aligned with the 3% conversion hypothesis in `A.1-BIZ-STYP-001` v2.0 §15–§16. They are not empirically validated coefficients and are not commitments of this cycle.

## 18.3 End-of-Window Checkpoint (Replaces Interim Checkpoints)

> **All checkpoints are anchored to the Amazon Associates deadline (OI-002 = 2026-10-12).**

**Single operative checkpoint:**

| Checkpoint | Condition | Action |
|------------|-----------|--------|
| **Window close (2026-10-12)** | FOM achieved | Proceed to Decision Frame (`A.1-BIZ-STYP-001` v2.0 §18-A) |
| **Window close (2026-10-12)** | FOM not achieved | Diagnose blocker (technical / rule-verification / time / external). Proceed to Decision Frame. |

> **Survival floor:** 3 qualifying purchases is the **minimum to keep the Associates account**, not evidence that the value proposition works. It is **not attempted in this cycle**.

> **Historical note:** The V1.2 checkpoint table (deadline minus 135/90/60/30 days) is retained in `A.1-BIZ-STYP-001` v2.0 §18 as a historical artifact. All those checkpoints fall before the operational start (2026-10-07) and were never actionable. The note on checkpoint relevance that V1.2 carried is now replaced by §18-A of A.1 v2.0.

## 18.4 Decision Frame at Window Close (New)

> **This section formalizes the handoff from this document to the next cycle.**

At the close of the operating window, the Editorial Owner chooses one of four paths, defined in `A.1-BIZ-STYP-001` v2.0 §18-A:

| Path | When | Action |
|------|------|--------|
| **1 — Extend the survival clock** | OI-003 verification or Amazon extension changes the deadline | Recompute the operating window; if large enough, revert to validation framing |
| **2 — Reapply for Amazon Associates** | Account lapses; business still pursues Amazon monetization | Reapply; use the new window to attempt validation with the system already built |
| **3 — Operate without Amazon Associates** | Account lapses; reapplication not immediately possible | Continue publishing without affiliate monetization; pursue alternative monetization |
| **4 — Redefine the model** | Diagnosis reveals the model is not viable under available conditions | Redefine business model, channel, monetization, or target market; re-enter Stage A |

> **The Decision Frame forces an explicit choice.** It does not permit declaring "validation in progress" when validation was never attempted. It does not permit treating the FOM as if it were the survival floor.

---

# 19. Relationship to the Engineering Proposal

```text
Business Plan (A.1-BIZ-STYP-001 v2.0)
      ↓
Value Proposition
      ↓
Value Proposition Functional Specification  ← this document
      ↓
Business Capabilities Specification (A.3-CAP-STYP-001)
      ↓
Capability Contracts Specification (A.4-CONTR-STYP-001)
      ↓
Engineering Proposal (A.5-ENG-STYP-001)
      ↓
System Architecture (Stage B)
      ↓
Implementation (Stage D)
```

The Engineering Proposal must answer:

> **What engineering system should Style Picks build to reliably execute these functions?**

> **Cycle note:** For the current cycle, the Engineering Proposal's answer is **Phase 0 — Manual Operating Baseline**, which achieves the FOM without requiring the full system. The full system is the target of the next cycle.

---

# 20. Architectural Principle

> **Agents are implementation mechanisms, not business functions.**

---

# 21. Ownership Summary

| Artifact / Decision | Owner |
|---------------------|-------|
| Editorial Rubric | Editorial Owner |
| Category list | Editorial Owner |
| Context definitions | Editorial Owner |
| Exception handling | Editorial Owner |
| Post-publication corrective actions | Editorial Owner |
| Rubric updates | Editorial Owner (evidence-based) |
| Govern escalation review | Editorial Owner |
| Tracking ID strategy | Editorial Owner |
| Open Items closure | Editorial Owner |
| **Decision Frame at window close (§18.4)** | **Editorial Owner** |

---

# 22. Version Control

This specification represents the **V1.3** functional model.

It becomes **V1.3 Final** only when all Open Items (`OI-001` to `OI-008`) are closed.

Changes should be made when:
1. New evidence demonstrates a function is missing
2. Two functions overlap materially
3. A functional boundary proves incorrect
4. The business model changes
5. Validation reveals the value proposition cannot be delivered
6. **The cycle objective changes (as it did from V1.2 to V1.3: validation → traction demonstration)**

---

# 23. Final Functional Definition

> **Context Definition → Discover → Select → Recommend → Present → Align → Learn**

with:

> **Govern**

operating transversally and acting as a publication gate.

Together, these functions define the minimum business behavior required for Style Picks to transform product abundance into contextual, curated, trustworthy, and commercially useful product discovery.

> **Cycle note:** In this cycle, the eight functions are executed **once**, manually, to achieve the **First Operational Milestone**. The functional model is the target. The FOM is the first instance of it operating.

---

## Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.2 — Business Functions

**Document ID:** A.2-FUNC-STYP-001

**Version:** 1.3 — Functional Definition (Traction Demonstration Reconciled)

**Status:** **Baselined**

**Authorization:** This document derives from `A.1-BIZ-STYP-001` v2.0. `A.3-CAP-STYP-001` v1.3 is authorized to derive from it.

**Pending Change Proposals:** CP-002 (AI-Generated Contextual Imagery).

**Language:** English

---

*End of Value Proposition Functional Specification — A.2-FUNC-STYP-001 v1.3*

---

## Note on OI-001 and OI-002

> **OI-001 is CLOSED.** Amazon Associates account was created on **2026-04-15**.
>
> **OI-002 is CLOSED.** The survival deadline is **2026-10-12** (account date + 180 days).
>
> The operational start of October 7, 2026 is confirmed as **not** the survival clock. The operating window is **5 days**.
>
> **This cycle does not attempt commercial validation.** It attempts the **First Operational Milestone (FOM)** — one published Pin with complete internal traceability. The survival floor and success target are deferred to the next cycle, per `A.1-BIZ-STYP-001` v2.0 §11 and §18-A.
>
> The single operative checkpoint is at **window close (2026-10-12)**: was the FOM achieved? The Decision Frame in §18.4 governs what happens next.
