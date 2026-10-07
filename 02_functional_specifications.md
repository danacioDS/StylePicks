# STYLE PICKS

## Value Proposition Functional Specification — V1.1 Release Candidate

**Business Model:** Content Commerce + Affiliate Commerce  
**Brand:** Style Picks  
**Target Market:** United States  
**Initial Channel:** Pinterest  
**Monetization:** Amazon Associates  
**Initial Categories:** Home Decor + Home Organization  
**Stage:** Commercial Validation  
**Operational Start:** October 7, 2026  
**Amazon Associates Account Created:** [OPEN ITEM — INSERT DATE]  
**Amazon Associates Deadline:** [OPEN ITEM — ACCOUNT DATE + 180 DAYS]  
**Validation Horizon:** Ends at the Amazon Associates deadline  
**Destination Model:** Pinterest → Amazon (direct link)  
**Document Type:** Business Functional Specification  
**Version:** 1.1 — Release Candidate

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 7, 2026 | Initial functional specification |
| 1.1 | Oct 7, 2026 | Govern diagram, Align/Govern boundary, confidence model, thresholds, imagery, FTC/Pinterest disclosure, attribution scope, sources |
| 1.1 RC | Oct 7, 2026 | Checkpoint 135d split into two distinct alarms; interim evidence rule added; 12.3 attribution slip corrected; version label aligned with Section 22 |

---

## Open Items

> **This document cannot be treated as final while any of the following remain empty.**

| # | Open item | Owner | Status |
|---|-----------|-------|--------|
| 1 | Amazon Associates account creation date | Editorial Owner | **EMPTY — CLOSE FIRST** |
| 2 | Amazon Associates deadline (account date + 180 days) | Editorial Owner | **EMPTY** |
| 3 | Verification: qualifying-sales rule | Editorial Owner | **EMPTY** |
| 4 | Verification: PA-API access requirements | Editorial Owner | **EMPTY** |
| 5 | Verification: image and price display rules | Editorial Owner | **EMPTY** |
| 6 | Verification: required disclosure wording | Editorial Owner | **EMPTY** |
| 7 | Verification: link-format rules | Editorial Owner | **EMPTY** |

---

# 1. Purpose

This document defines the **business functions required to deliver the Style Picks value proposition**.

> **Business functions define what Style Picks must accomplish. Engineering determines how those functions are executed.**

No technology, agent architecture, LLM framework, or implementation mechanism is prescribed.

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

### Source A — Amazon Product Advertising API (PA-API)

Access to PA-API has historically required recent qualifying sales.

> **Open Item #4:** Verify current requirements. Record source and date here once verified.

**Functional consequence:** Discover must operate in **manual or semi-manual mode** during early validation until PA-API access is confirmed.

### Source B — Manual product research
Amazon Best Sellers, Movers & Shakers, Amazon search within approved categories, Pinterest search.

**Functional consequence:** The candidate product record must be structurally identical regardless of source.

## 6.7 Ownership
**Editorial Owner**, supported by deterministic scripts when available.

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

> **Requirement for the next layer:** The full Evidence Source Policy belongs in the **Business Capabilities Specification / Capability Contracts**.

**Interim rule for V1.1 RC:**

Until that policy exists, only two sources count as **verified**:

1. The Amazon product page (product facts: dimensions, materials, weight, color, function as stated)
2. The manufacturer's official site (specifications not present on the product page)

Any claim sourced from anything else — customer reviews, third-party publications, Pinterest posts, LLM-generated information — **lowers Evidence Confidence to Low**, which routes the recommendation to human review.

This rule is deliberately strict. It keeps routing operable from the first Pin and will be relaxed only when the Evidence Source Policy defines reliability tiers.

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

## 10.6 Imagery Rule (Resolved)

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

## 10.7 Price Display Rule

> **V1.1 rule: Pins do not display prices.**

**Rationale:** Prices go stale, create Govern exposure, and complicate post-publication Align checks.

## 10.8 Ownership
**Editorial Owner.** Tools assist but do not decide.

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

---

# 12. Function 7 — Learn

## 12.1 Purpose
Convert observed outcomes into improvements in editorial decisions and future content.

## 12.2 Inputs (V1.1 Scope)

> **Attribution scope:** Category-level tracking IDs give **category attribution**. "Performance by context" and "performance by content format" are **not achievable in V1.1** unless IDs are assigned at that granularity from the start.

**Achievable V1.1 inputs:**
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

**Not achievable in V1.1 without additional tracking IDs:**
- performance by context
- performance by content format

## 12.3 Responsibility (Qualified to Match 12.2)

Learn identifies patterns **that are attributable within V1.1 scope**:

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

### 12.6.1 V1.1 Convention

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

---

# 13. Function 8 — Govern

## 13.1 Purpose
Ensure Style Picks operates within defined quality, factual, commercial, legal, affiliate, and platform constraints.

## 13.2 Responsibility
Govern controls: factual accuracy, product-claim integrity, affiliate disclosure, platform requirements, content standards, prohibited claims, source traceability, editorial consistency, risk conditions.

## 13.3 External Rules Enforced by Govern

Each rule below requires verification against its current source. Verification status is recorded in Open Items.

### 13.3.1 Amazon Associates — Qualifying Sales Requirement

> **Open Item #3:** Verify current rule. Record source and date.

**Functional consequence:**
- The Style Picks **survival horizon** = Associates account creation date + 180 days
- **Account created:** [Open Item #1]
- **Actual deadline:** [Open Item #2]
- This may differ from the operational start of October 7, 2026

### 13.3.2 Amazon Associates — PA-API Access

> **Open Item #4:** Verify current requirements. Record source and date.

### 13.3.3 Amazon Associates — Image and Price Display

> **Open Item #5:** Verify current rules. Record source and date.

### 13.3.4 Amazon Associates — Disclosure

> **Open Item #6:** Verify **exact required statement and placement**. Record source and date.

### 13.3.5 Amazon Associates — Link Format

> **Open Item #7:** Verify current link-format rules. Record source and date.

### 13.3.6 FTC Endorsement Disclosure (US)

> **Independent of Amazon.** For a US audience, FTC endorsement disclosure requirements apply.

### 13.3.7 Pinterest Policies on Affiliate Content

> **Independent of Amazon.** Pinterest's own policies on affiliate content apply.

## 13.4 Inputs
Business rules, editorial rules, platform requirements, affiliate requirements, source data, generated content, published content.

## 13.5 Outputs
Approve, Reject, Correct, Escalate, Compliance evidence.

## 13.6 Escalation Rules

> **All checkpoints are anchored to the Amazon Associates deadline.**

| Condition | Action |
|-----------|--------|
| Hard constraint violation (missing disclosure, prohibited claim, non-conforming link format, non-conforming price display) | **Block** and **escalate** |
| Soft constraint violation (factual inconsistency, tone issue) | **Return** with error code |
| **Deadline minus 135 days:** outbound clicks are **well below expected levels** (< 20 total) | **Escalate** — strategic review of context, category, or content |
| **Deadline minus 135 days:** outbound clicks occurring but **not reflected in Amazon clicks** (attribution ratio < 50%) | **Escalate immediately** — tracking, link, or destination failure |
| **Deadline minus 90 days:** zero qualifying purchases | **Escalate** for strategic review |
| **Deadline minus 60 days:** fewer than 2 qualifying purchases | **Escalate** for strategic review |
| **Deadline minus 30 days:** fewer than 3 qualifying purchases | **Escalate**; survival threshold at risk |
| Recurring violation of the same rule | **Escalate** and trigger rubric review |

> **Note:** Broken destination is an **Align** failure (11.3), not a Govern violation.

> **Why two rows at 135 days:** They measure different things. The first detects "no one is engaging with our content at all." The second detects "people are clicking, but Amazon isn't seeing them," which points to a broken link, wrong tracking ID, or a redirect that is being dropped.

## 13.7 Boundary
Govern does not create the recommendation. It establishes the conditions under which the recommendation and its presentation are acceptable.

## 13.8 Ownership
Govern rules defined by the **Editorial Owner** in consultation with current Amazon Associates, FTC, and Pinterest terms.

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

---

# 17. Execution Mechanisms

This document intentionally does **not** assign agents to functions.

Possible mechanisms: deterministic, probabilistic, human, hybrid.

### 17.1 Preliminary Mechanism Mapping

> Preliminary and subject to revision in the Engineering Proposal.

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
| Attribution completeness (Pins with correct tracking ID) | 100% | Every Pin |

## 18.2 Business Validation Thresholds

> **These are business targets, not functional requirements.** They belong conceptually to the Business Plan.

| Threshold | Target | Notes |
|-----------|--------|-------|
| Qualifying purchases | **≥ 5 by deadline** | Above the survival floor of 3 |
| Amazon clicks | ≥ 100 by deadline | |
| Outbound click rate | ≥ 1.5% | **Provisional; recalibrate after month 1** |
| Pins published | ≥ 120 by deadline | |
| Production time per Pin | ≤ 45 min average | |

## 18.3 Interim Checkpoints

> **All checkpoints are anchored to the Amazon Associates deadline.** Days are expressed as "deadline minus N."

| Deadline minus | Condition | Action |
|----------------|-----------|--------|
| **135 days** | Outbound clicks **well below expected** (< 20 total) | Escalate — strategic review |
| **135 days** | Outbound clicks present but **attribution ratio < 50%** | Escalate immediately — tracking failure |
| **90 days** | Zero qualifying purchases | Escalate — strategic review |
| **60 days** | Fewer than 2 qualifying purchases | Escalate — strategic review |
| **30 days** | Fewer than 3 qualifying purchases | Escalate — survival threshold at risk |

> **Survival floor:** 3 qualifying purchases is the **minimum to keep the Associates account**, not evidence that the value proposition works. The success target is set above that floor.

---

# 19. Relationship to the Engineering Proposal

```text
Business Plan
      ↓
Value Proposition
      ↓
Value Proposition Functional Specification  ← this document
      ↓
Business Capabilities Specification
      ↓
Capability Contracts
      ↓
Engineering Proposal
      ↓
System Architecture
      ↓
Implementation
```

The Engineering Proposal must answer:

> **What engineering system should Style Picks build to reliably execute these functions?**

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

---

# 22. Version Control

This specification represents the **V1.1 Release Candidate** functional model.

It becomes **V1.1 Final** only when all Open Items are closed.

Changes should be made when:
1. New evidence demonstrates a function is missing
2. Two functions overlap materially
3. A functional boundary proves incorrect
4. The business model changes
5. Validation reveals the value proposition cannot be delivered

---

# 23. Final Functional Definition

> **Context Definition → Discover → Select → Recommend → Present → Align → Learn**

with:

> **Govern**

operating transversally and acting as a publication gate.

Together, these functions define the minimum business behavior required for Style Picks to transform product abundance into contextual, curated, trustworthy, and commercially useful product discovery.

---

## Note on Open Item #1

> **Open Item #1 (Amazon Associates account creation date) is the single most consequential unclosed item in this document.**
>
> Every checkpoint in Section 13.6 and Section 18.3, every survival threshold, and the entire validation schedule depend on it. It takes one minute to find in the Associates welcome email or the account dashboard.
>
> **Close it before writing any other document.**