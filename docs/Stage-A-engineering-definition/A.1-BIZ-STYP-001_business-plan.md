# STYLE PICKS
## Business Plan and Commercial Validation

**Stage A.1 — Commercial Intent**
**Physical Foundation of the Style Picks Commercial Validation System**

**Document ID:** A.1-BIZ-STYP-001

**Version:** 1.5 — Commercial Intent Baseline (Reconciled)

**Status:** Stage A — Engineering Definition (Conceptual Level) — Baselined

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Parent Documents:**
- None (root document of the Style Picks pipeline)

**Child Documents:**
- A.2-FUNC-STYP-001 — Value Proposition Functional Specification (v1.1 RC)
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.0)
- STAGE-A-CONSOL-REPORT-STYP-001 — Stage A Consolidation Report (v1.0)

**Domain:** Domain A.1 — Commercial Strategy

---

**Business Model:** Content Commerce + Affiliate Commerce
**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**Initial Categories:** Home Decor + Home Organization
**Amazon Associates Account Created:** 2026-04-15
**Amazon Associates Deadline:** 2026-10-12
**Validation Horizon:** Ends at the Amazon Associates deadline
**Survival Floor:** 3 qualifying purchases
**Success Target:** ≥ 5 qualifying purchases by deadline

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0–1.2 | — | Prior drafts (not preserved in this pipeline) |
| 1.3 | Oct 7, 2026 | Reduced to five business questions; eliminated content that does not change decisions |
| 1.4 | Oct 8, 2026 | Aligned with downstream documents: deadline reframed as Amazon Associates account date + 180 days (OI-001); survival floor vs. success target separated; conversion hypothesis qualified as provisional; time economics reconciled with Engineering Proposal §32-A; explicit handoff to Functional Spec added; Open Items propagated; cross-references added |
| **1.4 (Baselined)** | Oct 8, 2026 | Normalized document header per Stage A codification; cross-references updated to A.x IDs; Open Items Register (PH1-REG-STYP-001) referenced; Change Proposals and Engineering Dependencies registers referenced; Sign-Off block added |
| **1.5** | Oct 8, 2026 | **Temporal reconciliation.** The survival clock is the Amazon Associates deadline (2026-10-12), not the operational start. All phase ranges, checkpoints, pace tables, and the validation horizon are now computed against the actual remaining days. Phase 1 is redefined as the period from the start of operations to the first checkpoint, not as "deadline minus 180." The 26-week assumption is removed. The distinction between *survival clock* (Amazon) and *operating window* (Style Picks) is stated explicitly in §1 and in the Note on OI-001. |

---

## Open Items

> **This document cannot be treated as final while any of the following remain empty. These are the same Open Items carried by the entire Stage A pipeline and consolidated in `PH1-REG-STYP-001`.**

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

---

# 1. Executive Summary

Style Picks is a digital product discovery and recommendation brand targeting the U.S. home market.

The business uses visual content to attract users who have an intention to discover, solve, or improve specific aspects of their home and direct them toward products sold on Amazon.

The model combines:

**Editorial content → Pinterest → commercial traffic → Amazon → purchase → affiliate commission.**

The first stage does not seek to maximize revenue or build a massive audience.

It seeks to answer a much more important business question:

> **Can Style Picks generate enough commercial traffic from Pinterest to produce qualifying purchases on a repeatable basis?**

Initial validation will be limited to **Home Decor** and **Home Organization**, avoiding dispersion across multiple categories.

### Two Clocks

The plan distinguishes two time references, and they are **not the same**:

| Clock | Definition | Date | Consequence |
|-------|------------|------|-------------|
| **Survival clock** | Amazon Associates account creation + 180 days | 2026-10-12 | If the account does not reach the survival floor by this date, Amazon may terminate it. |
| **Operating window** | The period in which Style Picks actually publishes content | From first Pin until the survival clock expires | This is the window in which the business must demonstrate traction. |

The operational start of October 7, 2026 is **not** the survival clock. The survival clock began on 2026-04-15, when the Amazon Associates account was created. **As of the operational start, the remaining operating window is short.**

### Survival Floor vs. Success Target

Two distinct thresholds govern this stage:

| Threshold | Value | Meaning |
|-----------|-------|---------|
| **Survival floor** | 3 qualifying purchases | Minimum to keep the Amazon Associates account. Not evidence that the value proposition works. |
| **Success target** | ≥ 5 qualifying purchases by deadline | Evidence that the value proposition is commercially viable. |

This plan tracks both. Reaching the survival floor prevents account termination; it does not validate the business. Validation requires exceeding it.

---

## Value Proposition

Style Picks reduces the friction of home-product discovery by transforming an overwhelming selection of products into curated, contextual, and visually compelling recommendations.

Instead of simply presenting products, Style Picks explains **which products make sense for a specific space, problem, need, or aesthetic—and why**.

For consumers, this means:

**less searching → better selection → easier decisions.**

For Amazon, Style Picks generates commercially relevant traffic from users who have already received contextual guidance and product recommendations.

For Style Picks, the model creates a continuous learning system that identifies which needs, products, categories, and content formats are most effective at converting visual discovery into commercial action.

### Core Value Proposition

> **Discover better home products without having to search through hundreds of options.**

### Strategic Differentiator

Style Picks is not a mirror of Amazon.

It is an **editorial selection layer between consumer intent and product inventory**, combining:

**Discovery + Curation + Context + Recommendation.**

---

# 2. Business Model

Style Picks does not intend to compete with Amazon as a marketplace.

Its function is to act as an **editorial layer for product discovery and selection**.

The user does not necessarily arrive looking for a specific product. They may arrive looking for:

- inspiration;
- a solution to a home-related problem;
- a decorating idea;
- a way to organize a space;
- a specific recommendation.

Style Picks transforms that need into a commercial recommendation.

### Value Proposition

**For the consumer:**

> Discover useful and attractive products to improve the home without having to browse through hundreds of options.

**For Amazon:**

> Generate traffic from consumers who have already received context and an editorial recommendation.

**For Style Picks:**

> Monetize the commercial intent generated by the content through affiliate commissions.

### Destination Model

For Stage A, the destination model is:

```text
Pin → Amazon product page (via affiliate link)
```

Each Pin promotes a single product and links directly to that product's Amazon page, using a tracking ID that identifies the category.

> **Open business decision (not owned by this plan):** Pinterest permits creators enrolled in the Amazon Influencer Program to connect an Amazon Storefront, after which affiliate attribution may be applied automatically. If adopted, this could bypass Style Picks' own tracking ID design. This decision belongs to the Functional Specification's destination model (`A.2-FUNC-STYP-001`). Until decided, Style Picks remains the source of truth for the tracking ID.

---

# 3. Target Market

The initial market is the United States.

The target consumer is a person interested in:

- home decor;
- organization;
- small spaces;
- apartments;
- functional solutions;
- home aesthetics;
- practical products;
- purchases inspired by visual content.

Pinterest is especially suitable for the initial stage because it allows content to be discovered before there is direct search intent for a particular brand.

---

# 4. Initial Categories

Style Picks will begin exclusively with:

### Home Decor

Products related to:

- lighting;
- decor;
- accessories;
- space aesthetics;
- furniture and decorative elements.

### Home Organization

Products related to:

- storage;
- organization;
- kitchen;
- closets;
- desk;
- bathroom;
- small-space solutions.

The reduction to two categories has an economic and operational purpose:

**concentrate production, learning, and data.**

New categories will not be added simply because an isolated opportunity exists.

### Tracking ID Strategy (Stage A)

Each category has its own Amazon tracking ID:

| Tracking ID | Applied to |
|-------------|-----------|
| `stylepicks-home-20` | Home Decor category |
| `stylepicks-org-20` | Home Organization category |

This is the functional requirement that makes category-level attribution possible. Without it, Learn cannot attribute performance by category.

> **Contractual basis:** The tracking ID convention is defined in `A.3-CAP-STYP-001` §12.6.1 and enforced by **INV-3** and **INV-7** in `A.4-CONTR-STYP-001`.

---

# 5. Problem Style Picks Solves

Amazon offers an enormous number of products, but precisely that abundance can make decision-making more difficult.

Style Picks attempts to reduce that friction through:

**context + selection + recommendation.**

Instead of:

> "Here is a product."

the content should answer:

> **"This product makes sense for this problem, space, style, or need."**

The brand, therefore, should not function as a mirror of Amazon.

It should function as an **editorial selection brand**.

---

# 6. Content Strategy

Initial content will have three levels of intent.

### Level 1 — Inspiration

Objective: generate discovery.

Examples:

- Cozy Small Living Room Ideas
- Minimalist Home Inspiration
- Small Apartment Organization Ideas

### Level 2 — Solution

Objective: connect a need with a possible solution.

Examples:

- How to Organize a Small Kitchen
- Storage Ideas for Small Bathrooms
- How to Make a Small Living Room Feel Bigger

### Level 3 — Commercial

Objective: directly connect the need with a product.

Examples:

- Best Slim Floor Lamps for Small Living Rooms
- Small Kitchen Storage Solutions
- Minimalist Desk Organizers

The proportion between these levels may be modified according to the data obtained.

> **Attribution note:** In Stage A, performance can be attributed by **category** (via tracking ID) and by **product** (via ASIN). Performance by content level and by context is **not fully attributable** in Stage A without additional tracking IDs. This is a known limitation of the initial measurement scope.

---

# 7. Product Selection Principle

Every recommendation must have an editorial reason.

A product will not be selected simply because it:

- has many sales;
- has many reviews;
- is inexpensive;
- appears first on Amazon.

There must be an explanation of why it is appropriate for the context presented.

Criteria may include:

- functionality;
- design;
- size;
- usefulness;
- price/value relationship;
- suitability for the space;
- style;
- ease of use;
- problem it solves.

> **Operational note:** The formal selection criteria and weights are defined in the **Editorial Rubric**, an artifact owned by the Functional Specification (`A.2-FUNC-STYP-001` §7.6) and maintained by Rubric Management (`A.3-CAP-STYP-001` §17). The Rubric V0.1 weights are **provisional hypotheses**, not empirically validated coefficients. They will be revised based on evidence from Learn.

---

# 8. Pin Architecture

The commercial principle will be:

> **Every commercial Pin must represent a clear and coherent recommendation with its destination.**

Therefore, when a Pin promotes an individual product, the user must find exactly that product after following the link.

Curation of multiple products will be carried out through:

- series;
- boards;
- editorial collections;
- different Pins around the same need.

Initially, a model in which a Pin promises five products but sends the user directly to only one will not be used.

This protects coherence between:

**promise → content → destination → product.**

> **Contractual basis:** This principle is enforced downstream by **INV-1** (publication gate), **INV-3** (tracking ID consistency), and the **Consistency Validation** capability (C-06) in `A.4-CONTR-STYP-001`.

---

# 9. Differentiation

Style Picks does not intend to differentiate itself through proprietary technology.

Its initial advantage should be built through:

### Selection

Choosing relevant products.

### Context

Explaining who they are for and what they are for.

### Presentation

Turning the product into an attractive visual recommendation.

### Consistency

Creating a recognizable editorial identity.

### Learning

Using real data to identify which needs, products, and formats generate commercial traffic.

---

# 10. Monetization

The initial revenue source will be Amazon Associates.

The economic flow is:

**User → Pinterest → Amazon → qualifying purchase → commission for Style Picks.**

The commission will depend on the specific product category and the rates in effect under the program.

Therefore, financial projections should not assume that all products generate exactly the same commission.

The actual economics will be determined through the data obtained during validation.

> **External rule dependency:** The qualifying-sales rule, commission rates, and account-survival conditions are external parameters. They are tracked as **OI-003 and OI-004** in `PH1-REG-STYP-001` and must be verified before being treated as operational constants.

---

# 11. Initial Financial Objective

The first financial objective is not to reach a specific dollar amount.

It is to achieve two distinct thresholds:

### Survival floor

> **3 qualifying purchases within the period established by Amazon.**

Below this floor, the Amazon Associates account may be terminated.

### Success target

> **≥ 5 qualifying purchases by the Amazon Associates deadline.**

This is the evidence threshold for commercial validation.

After reaching the first sales, the analysis will move to:

1. traffic volume;
2. number of purchases;
3. commission generated;
4. revenue per visitor;
5. revenue per hour of work;
6. repeatability.

---

# 12. Time Economics

The primary initial resource of Style Picks will be the founder's time.

In order to compare Style Picks with other opportunities, an **internal reference value of US$10 per hour** is established.

This does not mean that the founder must pay themselves US$10 per hour.

It is simply a tool for determining whether the business is using time in an economically rational manner.

The evaluation will be:

**Affiliate revenue − direct costs − economic value of time.**

> **Build-time constraint.** The US$10/hour reference applies to the founder's time as a whole. During commercial validation, that time is divided between **Pin production** and **platform build**. The Engineering Proposal (`A.5-ENG-STYP-001` §32-A) caps build effort at **10 hours per week**, reserving the remainder for Pin production. This is the operational consequence of the time-economics rule: an hour spent building is an hour not spent producing, and both count against the same reference value.

---

# 13. Main Metrics

Style Picks will use five main indicators:

| KPI | What it measures |
| --- | --- |
| Pins published | Production |
| Impressions | Distribution |
| Outbound clicks | Commercial interest on Pinterest |
| Amazon clicks | Actual commercial traffic |
| Qualifying purchases | Economic conversion |

These metrics represent different stages of the funnel.

**Production → distribution → interest → commercial intent → monetization.**

> **Attribution scope (Stage A):** Impressions and outbound clicks are available at **Pin level** (Pinterest analytics). Amazon clicks and qualifying purchases are available at **tracking-ID level** (Amazon Associates reports), which in Stage A means **category level**. Pin-level Amazon attribution is **not supported** in Stage A. This is a known limitation.

---

# 14. Secondary Metrics

Once sufficient volume exists, the following will be analyzed:

- conversion;
- revenue;
- average commission;
- EPC;
- performance by category;
- performance by content type;
- performance by product;
- production time;
- revenue per hour.

These metrics should not dominate decision-making while the volume is too small.

> **Attribution caveat:** Performance by **category** is fully attributable in Stage A (via tracking ID). Performance by **product** is attributable via ASIN. Performance by **content type** and by **context** is only partially attributable in Stage A, through a partial bridge between Pinterest per-Pin outbound clicks and Amazon category-level purchases. This is not a full attribution mechanism.

---

# 15. Conversion Hypothesis

For initial planning, a central hypothesis of **3%** will be used.

Scenarios of:

- 2%;
- 3%;
- 5%.

will also be considered.

This does not represent a conversion promise.

It is solely a tool for calculating how much commercial traffic would be necessary to achieve the initial three purchases.

> **Provisional status:** The 3% figure is a planning hypothesis, not an empirically validated coefficient. The business should progressively replace it with its own data. The Functional Specification (`A.2-FUNC-STYP-001` §18.2) treats the "≥ 100 Amazon clicks" target as provisional and subject to recalibration after month 1.

---

# 16. Traffic Requirement

With three purchases as the objective:

| Hypothetical conversion | Clicks required |
| --- | --- |
| 2% | 150 |
| 3% | 100 |
| 5% | 60 |

Therefore, the central planning scenario will be approximately:

**100 Amazon clicks → 3 purchases.**

The business should progressively replace these hypotheses with its own data.

---

# 17. Required Pace

The weekly pace depends on the weeks remaining until the deadline, **not** on a fixed 26-week horizon.

### Remaining Operating Window

| Reference | Date |
|-----------|------|
| Amazon Associates account created (OI-001) | 2026-04-15 |
| Amazon Associates deadline (OI-002) | 2026-10-12 |
| Operational start | 2026-10-07 |
| **Remaining days from operational start to deadline** | **5 days** |

> **This is the central operational reality of Stage A.** The survival clock began in April 2026. By the time operations start in October 2026, the remaining window is measured in days, not months. The pace tables below reflect this.

### Pace Required to Reach the Survival Floor

With **5 days** available:

| Scenario | Total clicks | Approximate daily average | Approximate weekly equivalent |
| --- | --- | --- | --- |
| 2% | 150 | 30.0 | 210 |
| 3% | 100 | 20.0 | 140 |
| 5% | 60 | 12.0 | 84 |

**These rates are not realistic for a new Pinterest account with no distribution history.** The plan must state this explicitly rather than present a 26-week schedule that does not exist.

> **Implication:** Reaching the survival floor of 3 qualifying purchases within the remaining window is **unlikely under the current timeline**. The realistic objective is to **demonstrate distribution and commercial traffic** within the remaining days, and to use that evidence to decide whether to request an extension, redefine the timeline, or accept that the Associates account may lapse.

### If the Deadline Is Extended or Recalculated

If OI-002 is revised (for example, because the qualifying-sales rule is verified to run from a different date, or because Amazon grants an extension), the pace table must be recomputed against the actual remaining days. The formula is:

```
Required weekly Amazon clicks = (Total clicks required) / (Remaining weeks)
```

where:

```
Total clicks required = Survival floor (3) / Conversion hypothesis
```

For the central 3% hypothesis: `3 / 0.03 = 100 Amazon clicks` over the remaining window.

---

# 18. Validation Horizon

> **All phases are anchored to the Amazon Associates deadline (OI-002).** Because the remaining window is short, the phase structure is compressed and conditional. If the deadline is extended or recalculated, this section must be revised.

### Phase 0 — Rule Verification (Before the First Pin)

**Objective:**

> verify the external rules that govern the first Pin.

Required before publication:

- required disclosure wording (OI-006);
- link-format rules (OI-007);
- image and price display rules (OI-005);
- qualifying-sales rule (OI-003).

This is a Phase 0 requirement in `A.5-ENG-STYP-001` §32-B.

### Phase 1 — Distribution

**From the first Pin to the first checkpoint.**

Objective:

> determine whether Pinterest begins distributing the content.

Main observations:

- production;
- impressions;
- distribution growth;
- first outbound clicks.

A specific number of sales is not yet required.

### Phase 2 — Commercial Traffic

**From the first outbound clicks to the first Amazon clicks.**

Objective:

> determine whether the content generates traffic to Amazon.

Attention shifts toward:

- outbound clicks;
- Amazon clicks;
- content types that generate commercial intent.

### Phase 3 — Conversion

**From the first Amazon clicks to the first qualifying purchases.**

Objective:

> determine whether the generated traffic can convert into purchases.

Here the following acquire greater importance:

- purchases;
- conversion;
- products;
- categories;
- EPC.

### Phase 4 — Decision

**At or before the Amazon Associates deadline.**

Objective:

> determine whether Style Picks should continue, be modified, or be abandoned.

### Interim Checkpoints

> **Checkpoints are expressed as "days remaining until the Amazon Associates deadline," not as fixed offsets from a 180-day horizon.** With the operational start on 2026-10-07 and the deadline on 2026-10-12, the checkpoints below fall at or before the operational start and are therefore **historical or immediate**, not future milestones.

| Days remaining | Condition | Action |
|----------------|-----------|--------|
| **135 days** | Outbound clicks well below expected (< 20 total) | Escalate — strategic review |
| **135 days** | Outbound clicks present but attribution ratio < 50% | Escalate immediately — tracking failure |
| **90 days** | Zero qualifying purchases | Escalate — strategic review |
| **60 days** | Fewer than 2 qualifying purchases | Escalate — strategic review |
| **30 days** | Fewer than 3 qualifying purchases | Escalate — survival threshold at risk |

> **Note on checkpoint relevance:** If the remaining window is shorter than the largest checkpoint offset, the checkpoint has either already passed or is not actionable. In that case, the Editorial Owner must decide whether to (a) treat the current date as the effective checkpoint, (b) request a deadline extension, or (c) accept that the survival floor may not be reached and plan accordingly.

---

# 19. Minimum Content Standard

A valid commercial Pin must:

- clearly present the product or need;
- use an image appropriate for Pinterest;
- have a title consistent with the intent;
- provide context;
- direct to the corresponding destination;
- comply with applicable affiliate disclosure requirements;
- honestly represent what the user will find after the click.

The quantity of Pins will never substitute for minimum quality.

> **External rule dependency:** The specific disclosure wording, placement, link-format rules, and image rules that govern the first Pin must be verified against the Amazon Associates Operating Agreement, FTC guidance, and Pinterest policies before the first Pin is published. This is tracked as **OI-005, OI-006, and OI-007**, and is a Phase 0 requirement in `A.5-ENG-STYP-001` §32-B.

---

# 20. Editorial Standard

Style Picks must add its own value.

The content should provide at least a combination of:

- selection;
- explanation;
- comparison;
- context;
- recommendation;
- interpretation;
- visual or editorial transformation.

The internal rule will be:

> **Style Picks must be an editorial brand, not a mirror of Amazon.**

---

# 21. Distribution Strategy

Pinterest will be the primary channel during validation.

There will be no simultaneous attempt to build:

- Instagram;
- TikTok;
- YouTube;
- blog;
- newsletter;
- Facebook;
- multiple marketplaces.

Initial concentration makes it possible to identify whether there is a functional relationship between:

**content → distribution → traffic → sales.**

---

# 22. Production Strategy

The system must be simple enough to maintain consistent production.

The priority will be:

**consistency > complexity.**

Time spent on the following will be tracked:

- product selection;
- research;
- visual creation;
- copywriting;
- publishing.

This will later make it possible to calculate the true production cost.

> **Operational note:** Production time is logged per Pin. The target of **≤ 45 minutes per Pin** is defined in `A.2-FUNC-STYP-001` §18.2. The Engineering Proposal (`A.5-ENG-STYP-001` §32-A) caps weekly build effort at **10 hours per week** so that production is not displaced by platform development.

---

# 23. Tracking

Initial tracking may be organized by category or content line.

For example:

- Home Decor
- Home Organization

Multiple unnecessary identifiers will not be created for every Pin during the first stage.

The initial objective is to obtain enough information to compare categories and content types without turning system administration into a burden.

> **Contractual basis:** The Stage A tracking ID convention (`stylepicks-home-20`, `stylepicks-org-20`) is defined in `A.3-CAP-STYP-001` §12.6.1 and enforced by **INV-3** and **INV-7** in `A.4-CONTR-STYP-001`.

---

# 24. Economics by Category

Categories will be compared not only by traffic but by:

**traffic → clicks → sales → commission → production time.**

This is especially important because products that appear similar may belong to different commission categories.

For example, some organization products may be classified within categories related to kitchen, while others may be classified differently.

The actual product category will be the one that determines the economic analysis.

---

# 25. Traffic Value Analysis

The central metric after the first sales will be:

> **How much economic value does each unit of commercial traffic generate?**

The following will be observed:

- Amazon clicks;
- purchases;
- commissions;
- EPC;
- category;
- product.

EPC will initially be interpreted as an exploratory metric and will become more useful as the number of sales increases.

---

# 26. Decision Criteria

Style Picks will have three possible decisions:

### Continue

When there is evidence of:

- growing distribution;
- commercial traffic;
- initial conversions;
- potentially positive economics.

### Adjust

When there is traffic but:

- little conversion;
- certain products underperform;
- certain categories perform worse;
- the content generates attention but not commercial intent.

### Abandon

Only when there is sufficient evidence that the model does not work economically under the available conditions.

It will not be abandoned because of:

- few followers;
- one bad week;
- low initial impressions;
- zero sales after very few clicks.

> **Strategic review checkpoints** are the formal moments at which this decision is evaluated. See §18 for the checkpoint table and the note on checkpoint relevance when the remaining window is short.

---

# 27. Review Thresholds

### Distribution

After 30 days:

**Positive signal:** an increasing trend in impressions during at least three of the four weeks.

If distribution remains flat, the following will be reviewed:

- topics;
- titles;
- visual quality;
- consistency;
- publishing frequency.

### Commercial Traffic

If the Amazon click rate remains below **50% of the required rate for three consecutive weeks**, this will be considered a signal that the distribution or intent strategy needs modification.

### Conversion

With approximately **100 Amazon clicks without three purchases**, the central 3% scenario will not have materialized and a deep review will be required.

This does not automatically mean that the business has failed, because actual conversion may differ from the hypothesis.

> **Statistical note (from §28):** 100 clicks without 3 purchases is a signal for review, not a verdict. See §28 for the sample-size reasoning.

---

# 28. Statistical Interpretation

The absence of sales with few clicks does not constitute sufficient evidence of failure.

For example, if the true conversion rate were 5%, there would still be approximately a **60% probability of obtaining zero sales in the first 10 clicks**.

With 60 clicks, that probability would fall to approximately **4.6%**.

Therefore:

> **Important decisions will not be made based on extremely small samples.**

---

# 29. Weekly Review

Every week Style Picks will answer five questions:

1. Are we producing enough content?
2. Is Pinterest distributing the content?
3. Is the content generating outbound clicks?
4. Are those users reaching Amazon?
5. Is the traffic producing purchases?

The next question will always depend on the answer to the previous one.

> **Operational basis:** These five questions are formalized as the weekly review cadence of the Learn function (`A.2-FUNC-STYP-001` §12.8; `A.3-CAP-STYP-001` §15).

---

# 30. Example of Weekly Analysis

**Week 1**

If, in the first week of operation:

- Pins published: 15
- Impressions: 400
- Outbound clicks: 3
- Amazon clicks: 1
- Sales: 0

Interpretation:

Production exists. Distribution is beginning. Commercial traffic is far below the pace required to reach the survival floor within the remaining window.

**Decision:** optimize topics, titles, and product selection before aggressively increasing production. At the same time, reassess whether the remaining window is sufficient and whether a deadline extension or timeline revision is required.

---

# 31. Competitive Advantage Sought

The initial advantage of Style Picks will not be a technological barrier.

It will be the accumulation of knowledge about:

- which needs generate traffic;
- which products receive clicks;
- which products convert;
- which categories produce better commissions;
- which content works;
- how much it costs to produce it;
- which combination produces the best return on time.

With sufficient volume, this knowledge can become an editorial advantage that is difficult to replicate quickly.

> **Attribution caveat:** The first two items ("which needs generate traffic" and "which content works") are only **partially attributable** in Stage A. Full attribution of needs and content formats would require additional tracking IDs. See §6 and §14.

---

# 32. Main Risks

### Dependence on Pinterest

A change in distribution can affect traffic.

**Mitigation:** build knowledge and reusable content.

### Dependence on Amazon

Program rates, policies, or conditions may change.

**Mitigation:** do not permanently depend on a single source of monetization.

### Low Conversion

There may be traffic without purchases.

**Mitigation:** increase commercial intent and improve product selection.

### Time Cost

The business may generate insufficient revenue to justify the effort.

**Mitigation:** measure hours from the beginning; cap build effort; prioritize production.

### Lack of Differentiation

Content may become a simple copy of existing products.

**Mitigation:** maintain a clear editorial identity.

### External Rule Uncertainty

Disclosure, link-format, image, and survival rules are external and may change.

**Mitigation:** represent unverified parameters as unverified configuration, not hard-coded assumptions; verify the rules governing the first Pin before publishing.

### Compressed Operating Window

The survival clock began in April 2026, but operations start in October 2026. The remaining window may be too short to reach the survival floor.

**Mitigation:** treat the remaining days as a **traction demonstration window**, not a full validation window. If the survival floor cannot be reached, decide explicitly whether to request an extension, redefine the timeline, or accept that the Associates account may lapse. Do not pretend the 26-week schedule exists.

---

# 33. What Style Picks Will NOT Do Initially

The following will not be prioritized:

- development of a proprietary platform;
- inventory;
- dropshipping;
- marketplace;
- paid advertising;
- international expansion;
- multiple categories;
- hiring;
- complex automation;
- large investments;
- building a massive audience before validating sales.

> **Clarification:** "Development of a proprietary platform" means a **consumer-facing** platform. Style Picks does build a **private internal operations platform** (the Engineering Proposal's modular monolith). The distinction is between a public product and an internal tool.

---

# 34. Definitive Economic Criterion

At the end of the validation horizon, Style Picks must answer:

> **Does the potential economic benefit justify the time invested?**

The indicator will be:

**Affiliate revenue − direct costs − economic cost of time.**

With an internal value of **US$10/hour**, the business must demonstrate that it can approach or exceed this threshold as scale increases and efficiency improves.

> **Time-allocation caveat:** During validation, the founder's time is split between production and build. The Engineering Proposal (`A.5-ENG-STYP-001` §32-A) caps build at 10 hours/week. The economic criterion applies to the total, but the plan assumes production has priority.

---

# 35. Conditions for Scaling

Style Picks will only move to an expansion phase when there is evidence of:

1. consistent traffic;
2. qualifying purchases;
3. observable conversion;
4. best-performing products/categories;
5. sustainable production;
6. positive or clearly promising economics.

Scale will not be decided by follower count.

It will be decided by **demonstrated economics**.

> **Phase-gate basis:** The Engineering Proposal (`A.5-ENG-STYP-001` §32-A) makes the same principle operational: Phases 2–7 are **evidence-gated**, and each starts only when operational evidence justifies automating what the phase automates.

---

# 36. Scalability Principle

The process will be:

**Validate → measure → identify winners → repeat → optimize → scale.**

Not:

**publish massively → wait → spend money → hope it works.**

---

# 37. Long-Term Objective

If validation is successful, Style Picks may evolve from an affiliate project into a home-product discovery commerce media brand.

Possible future extensions include:

- new categories;
- new channels;
- proprietary content;
- commercial agreements;
- multiple monetization sources;
- proprietary digital assets.

But none of these extensions is part of the current priority.

---

# 38. Central Strategic Decision

The objective of the validation horizon can be summarized in a single question:

> **Can Style Picks convert visual content into commercial traffic and commercial traffic into purchases in a sufficiently repeatable and profitable manner?**

If the answer is yes, scale.

If the answer is partially yes, modify.

If the answer is no after a sufficient test, abandon or redefine the model.

> **Timeline caveat:** If the remaining operating window is too short to produce a sufficient test, the answer may be "insufficient evidence" rather than "no." That is a distinct outcome and must be treated as such. See §32 (Compressed Operating Window).

---

# 39. Guiding Principle

> **Do not optimize scale before demonstrating conversion.**

And there is a second principle:

> **Do not optimize the plan before generating real data.**

From this point forward, the most important asset of Style Picks will not be another version of the document.

It will be **the commercial evidence generated through execution**.

---

# 40. Handoff to the Functional Specification

This Business Plan defines **what the business is trying to achieve and how success will be judged.**

It does **not** define:

- the business functions required to deliver the value proposition;
- the business capabilities required to execute those functions;
- the contracts those capabilities must satisfy;
- the engineering system that implements them.

Those are defined, in order, in:

| Document | Role |
|----------|------|
| **A.2-FUNC-STYP-001** — Value Proposition Functional Specification (v1.1 RC) | Defines the eight business functions and the value-proposition flow. |
| **A.3-CAP-STYP-001** — Business Capabilities Specification (v1.1 RC.4) | Decomposes functions into 12 capabilities with dependencies and ownership. |
| **A.4-CONTR-STYP-001** — Capability Contracts Specification (v1.0 RC.4) | Formalizes each capability's inputs, outputs, rules, preconditions, postconditions, and failure handling. |
| **A.5-ENG-STYP-001** — Engineering Proposal (v1.2 Final) | Defines the system architecture, storage, execution mechanisms, and phased implementation. |

### Five Business Questions (Summary of This Plan)

**What do we sell?**
Editorial product-discovery content.

**To whom?**
U.S. consumers interested in improving and organizing their homes.

**How do we reach them?**
Pinterest.

**How do we monetize?**
Amazon Associates.

**How do we know if it works?**
Distribution → traffic → purchases → economics per hour, measured against the survival floor (3) and the success target (≥ 5).

That is the business plan. Everything else should be **execution and data**, not more planning.

---

## V1.5 Verdict

This version is superior to V1.4 because it **reconciles the temporal contradiction** that V1.4 left unresolved.

The changes are:

1. The distinction between the **survival clock** (Amazon Associates, started 2026-04-15) and the **operating window** (Style Picks, starting 2026-10-07) is now explicit in §1.
2. The phase structure in §18 is **anchored to the actual remaining days**, not to a hypothetical 180-day horizon.
3. The pace table in §17 is **recomputed against the 5-day remaining window**, with the implication stated plainly: reaching the survival floor under the current timeline is unlikely.
4. The checkpoint table in §18 carries an explicit note on **checkpoint relevance** when the remaining window is shorter than the checkpoint offset.
5. The risk register in §32 adds **Compressed Operating Window** as an explicit risk with mitigation.
6. §38 distinguishes "no" from **"insufficient evidence"** as a decision outcome.
7. The imprecise cross-reference in §15 (Amazon clicks recalibration) is corrected.
8. The imprecise cross-reference in §22 (≤45 min/Pin source) is corrected.
9. The example in §30 uses **Week 1** rather than "Week 3," consistent with a 5-day window.

The architecture is still reduced to five business questions:

**What do we sell?**
Editorial product-discovery content.

**To whom?**
U.S. consumers interested in improving and organizing their homes.

**How do we reach them?**
Pinterest.

**How do we monetize?**
Amazon Associates.

**How do we know if it works?**
Distribution → traffic → purchases → economics per hour.

That is the business plan. Everything else should be **execution and data**, not more planning.

---

## 11. Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.1 — Commercial Intent

**Document ID:** A.1-BIZ-STYP-001

**Version:** 1.5 — Commercial Intent Baseline (Reconciled)

**Status:** **Baselined**

**Authorization:** This document is the root of the Stage A pipeline. `A.2-FUNC-STYP-001` is authorized to derive from it.

**Duration:** The validation horizon ends at the Amazon Associates deadline (OI-002 = 2026-10-12).

**Language:** English

---

*End of Business Plan and Commercial Validation — A.1-BIZ-STYP-001 v1.5*

---

## Note on OI-001 and OI-002

> **OI-001 is CLOSED.** Amazon Associates account was created on **2026-04-15**.
>
> **OI-002 is CLOSED.** The survival deadline is **2026-10-12** (account date + 180 days).
>
> **The operational start of October 7, 2026 is not the survival clock.** The survival clock began on 2026-04-15. The remaining operating window from the operational start to the deadline is **5 days**.
>
> This is the central temporal fact of Stage A. All phase ranges, checkpoints, and pace tables in this document are computed against the actual remaining days. Where a checkpoint offset exceeds the remaining window, the checkpoint is marked as historical or immediate. The plan does not pretend that a 26-week schedule exists.
>
> **If OI-002 is revised** — for example, because the qualifying-sales rule is verified to run from a different date, or because Amazon grants an extension — the phase ranges, checkpoint offsets, and pace tables in §17 and §18 must be recomputed against the new remaining window.
