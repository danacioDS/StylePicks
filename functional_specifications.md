# STYLE PICKS

## Value Proposition Functional Specification — V1.0

**Business Model:** Content Commerce + Affiliate Commerce  
**Brand:** Style Picks  
**Target Market:** United States  
**Initial Channel:** Pinterest  
**Monetization:** Amazon Associates  
**Initial Categories:** Home Decor + Home Organization  
**Stage:** Commercial Validation  
**Operational Start:** October 7, 2026  
**Validation Horizon:** 180 days  
**Document Type:** Business Functional Specification  
**Version:** 1.0

---

# 1. Purpose

This document defines the **business functions required to deliver the Style Picks value proposition**.

It establishes what Style Picks must do as a business system before defining how those functions will be implemented through software, automation, AI agents, APIs, deterministic processes, or human work.

The purpose of this document is therefore to provide the formal bridge between the **Business Plan** and the subsequent **Engineering Proposal**.

The central principle is:

> **Business functions define what Style Picks must accomplish. Engineering determines how those functions are executed.**

No technology, agent architecture, LLM framework, or implementation mechanism is prescribed by this document.

---

# 2. Value Proposition

Style Picks reduces the friction of home-product discovery by transforming an overwhelming selection of products into **curated, contextual, and visually compelling recommendations**.

Instead of requiring consumers to search through hundreds of products, Style Picks helps them understand:

- what products are relevant to a particular situation;
- which products are worth considering;
- why a product may be appropriate;
- how the product fits a specific space, need, or aesthetic; and
- where the consumer can evaluate or purchase the product.

### Core Value Proposition

> **Discover better home products without having to search through hundreds of options.**

The value proposition is therefore not simply the aggregation of products.

Style Picks operates as an **editorial selection layer between consumer intent and product inventory**.

Its value is created through:

**Discovery + Curation + Context + Recommendation + Presentation + Validation + Learning**

---

# 3. Functional Objective

The functional objective of Style Picks is to transform an identified consumer context into a trustworthy commercial recommendation.

At a high level:

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

Governance and compliance operate across the entire flow.

---

# 4. Functional Model

Style Picks is defined by eight core business functions:

| # | Function | Primary responsibility |
|---|---|---|
| 1 | **Context Definition** | Define the consumer situation, need, problem, or opportunity |
| 2 | **Discover** | Identify relevant product candidates |
| 3 | **Select** | Determine which products deserve editorial consideration |
| 4 | **Recommend** | Produce a contextual and evidence-based recommendation |
| 5 | **Present** | Transform the recommendation into a compelling discovery experience |
| 6 | **Align** | Verify consistency between promise, content, product, and destination |
| 7 | **Learn** | Measure outcomes and improve future decisions |
| 8 | **Govern** | Enforce quality, factuality, commercial, and platform constraints |

These functions form the core functional architecture of the value proposition.

---

# 5. Function 1 — Context Definition

## 5.1 Purpose

Define the consumer situation that Style Picks intends to address before searching for products.

The context establishes **why a product is being considered**.

Examples include:

- organizing a small apartment;
- improving storage in a small bathroom;
- decorating a rental without permanent modifications;
- creating a cozy bedroom;
- organizing a kitchen with limited counter space;
- improving functionality in a low-light room.

## 5.2 Responsibility

Context Definition determines:

- the consumer need;
- the physical or situational environment;
- relevant constraints;
- desired outcome;
- aesthetic or functional preferences;
- applicable product category;
- potential search concepts.

## 5.3 Inputs

- consumer needs;
- observed problems;
- editorial strategy;
- market signals;
- trends;
- historical performance;
- existing content opportunities.

## 5.4 Outputs

A structured context definition containing, at minimum:

- context name;
- problem or need;
- target outcome;
- relevant constraints;
- relevant product categories;
- editorial opportunity.

## 5.5 Functional boundary

Context Definition does **not** select products.

It establishes the situation against which products will subsequently be discovered and evaluated.

---

# 6. Function 2 — Discover

## 6.1 Purpose

Identify products that may be relevant to the defined context.

Discovery creates the **candidate product universe**.

## 6.2 Responsibility

Discover should locate products potentially relevant to:

- the defined context;
- the applicable category;
- the consumer problem;
- the desired outcome.

Discovery should favor relevance over immediate recommendation.

## 6.3 Inputs

- defined context;
- category;
- search concepts;
- product sources;
- product data;
- market information.

## 6.4 Outputs

A normalized set of product candidates containing available factual information.

## 6.5 Functional boundary

Discover answers:

> **“What products could potentially solve this need?”**

It does not answer:

> **“Which product deserves to be recommended?”**

That decision belongs to Select.

---

# 7. Function 3 — Select

## 7.1 Purpose

Evaluate candidate products against Style Picks' editorial criteria and determine which products are worthy of recommendation.

Selection is where the **editorial standard** becomes operational.

## 7.2 Responsibility

Select evaluates products according to criteria such as:

- relevance to context;
- functionality;
- design;
- usefulness;
- suitability for the space;
- dimensions;
- price/value;
- quality indicators;
- ease of use;
- problem solved;
- consistency with the Style Picks editorial standard.

## 7.3 Inputs

- defined context;
- product candidates;
- factual product attributes;
- editorial rubric;
- hard constraints.

## 7.4 Outputs

A ranked or approved set of products eligible for recommendation.

## 7.5 Functional boundary

Select answers:

> **“Does this product deserve to be considered by Style Picks?”**

Selection does not write the final recommendation.

---

# 8. Function 4 — Recommend

## 8.1 Purpose

Transform a selected product into a **contextual, explained, and evidence-based recommendation**.

Recommend combines the product with the defined context and editorial criteria.

## 8.2 Responsibility

The recommendation must communicate:

- what the product is;
- why it is relevant;
- how it addresses the context;
- what benefits are supported by available facts;
- what limitations or trade-offs should be considered.

The recommendation is not merely product description.

It is an editorial judgment expressed in a form useful to the consumer.

## 8.3 Inputs

- selected product;
- category;
- context;
- factual attributes;
- editorial criteria;
- applicable constraints.

## 8.4 Outputs

A structured recommendation containing:

- recommendation;
- rationale;
- supporting facts;
- limitations;
- confidence.

## 8.5 Functional boundary

Recommend does not independently discover products.

It also does not replace the selection function.

Its responsibility is to explain **why an already-selected product is relevant to the defined context**.

---

# 9. Product Recommendation Contract

Every recommendation must satisfy the following contract.

## 9.1 Input

- product;
- category;
- context;
- factual attributes.

## 9.2 Preconditions

Before a recommendation can be produced:

- product data must be verified;
- category must be approved;
- destination must be available.

## 9.3 Decision Rules

A product is eligible for recommendation only when:

- editorial score meets or exceeds the applicable threshold;
- no hard constraint is violated.

## 9.4 Output

The recommendation must contain:

- recommendation;
- rationale;
- supporting facts;
- limitations;
- confidence.

## 9.5 Postconditions

After recommendation generation:

- every factual claim must be traceable to source data;
- the recommendation must match the defined context;
- unsupported product characteristics must not be introduced;
- material limitations must not be intentionally omitted.

This contract establishes the minimum functional standard for Style Picks recommendations.

---

# 10. Function 5 — Present

## 10.1 Purpose

Transform the recommendation into a visually compelling and commercially usable discovery experience.

Presentation is the interface between Style Picks' editorial judgment and the consumer.

## 10.2 Responsibility

Present determines how the recommendation is expressed through:

- visual composition;
- title;
- description;
- imagery;
- format;
- editorial framing;
- call to action;
- destination.

For the initial business model, the principal presentation medium is Pinterest content.

## 10.3 Inputs

- recommendation;
- product;
- context;
- brand identity;
- content format;
- platform requirements.

## 10.4 Outputs

A publication-ready content asset.

## 10.5 Functional boundary

Present does not change the underlying product decision.

Its responsibility is to communicate the recommendation effectively.

---

# 11. Function 6 — Align

## 11.1 Purpose

Verify that the consumer-facing content remains coherent from the initial promise through the final destination.

Align is a **control function**, not a transformation step.

## 11.2 Alignment Chain

The fundamental relationship is:

```text
Promise
   ↓
Content
   ↓
Recommendation
   ↓
Product
   ↓
Destination
```

These elements must remain consistent.

## 11.3 Verification Criteria

Alignment includes verification that:

- the Pin promise corresponds to the content;
- the content corresponds to the recommendation;
- the recommendation corresponds to the product;
- the destination corresponds to the promised product;
- the commercial destination is available;
- required disclosures are present;
- material changes have not invalidated the original recommendation.

## 11.4 Timing

Alignment occurs at least twice:

### Pre-publication

Before publication, verify that the content is commercially and editorially coherent.

### Post-publication

After publication, verify that changes such as:

- product unavailability;
- destination changes;
- materially changed product information;
- broken links;
- price changes;
- discontinued products;

have not invalidated the content.

## 11.5 Functional boundary

Align does not create the recommendation.

It determines whether the result of the previous functions is still valid for publication and continued distribution.

---

# 12. Function 7 — Learn

## 12.1 Purpose

Convert observed business outcomes into improvements in Style Picks' editorial decisions and future content.

Learn closes the system's feedback loop.

## 12.2 Inputs

Examples include:

- impressions;
- saves;
- outbound clicks;
- Amazon clicks;
- qualifying purchases;
- conversion;
- revenue;
- revenue per visitor;
- performance by category;
- performance by context;
- performance by product;
- performance by content format;
- production time.

## 12.3 Responsibility

Learn identifies patterns such as:

- contexts generating stronger engagement;
- products generating stronger commercial action;
- content formats producing better traffic;
- categories producing better economics;
- recommendations that repeatedly fail;
- editorial criteria associated with successful products.

## 12.4 Outputs

Learn produces:

- performance insights;
- hypotheses;
- recommended editorial adjustments;
- new context opportunities;
- product/category opportunities;
- changes to editorial criteria.

## 12.5 Functional boundary

Learn does not automatically redefine Style Picks' strategy.

It provides evidence for improving the system.

Strategic changes remain subject to appropriate human/business judgment during the validation stage.

---

# 13. Function 8 — Govern

## 13.1 Purpose

Ensure that Style Picks operates within its defined quality, factual, commercial, legal, affiliate, and platform constraints.

Govern is a **transversal function**.

It does not occur only at one point in the pipeline.

## 13.2 Responsibility

Govern controls areas including:

- factual accuracy;
- product-claim integrity;
- affiliate disclosure;
- platform requirements;
- content standards;
- prohibited or restricted claims;
- source traceability;
- editorial consistency;
- risk conditions.

## 13.3 Inputs

- business rules;
- editorial rules;
- platform requirements;
- affiliate requirements;
- source data;
- generated content;
- published content.

## 13.4 Outputs

- approval;
- rejection;
- correction requirement;
- escalation;
- compliance evidence.

## 13.5 Functional boundary

Govern does not create the commercial recommendation.

It establishes the conditions under which the recommendation and its presentation are acceptable.

---

# 14. Functional Relationships

The primary functional flow is:

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
                 │ Quality Gate         │
                 └──────────┬───────────┘
                            ↓
                       Publication
                            │
                            ↓
                 ┌──────────────────────┐
                 │ Learn                │
                 └──────────┬───────────┘
                            │
                            └──────────────→ improves
                                            future decisions

          ┌──────────────────────────────────────────┐
          │ Govern — transversal control function    │
          └──────────────────────────────────────────┘
```

---

# 15. Functional Separation

The following distinctions are fundamental to the Style Picks system.

| Function | Core question |
|---|---|
| Context Definition | **What consumer situation are we trying to solve?** |
| Discover | **What products could potentially solve it?** |
| Select | **Which products deserve consideration?** |
| Recommend | **Why is this selected product appropriate for this context?** |
| Present | **How should that recommendation be communicated?** |
| Align | **Is everything still consistent and valid?** |
| Learn | **What did the market teach us?** |
| Govern | **Is the system operating within acceptable constraints?** |

This separation prevents different system components from performing overlapping responsibilities.

---

# 16. Editorial Rubric as a Core Business Artifact

The central decision-making asset of Style Picks is not an AI agent.

It is the **Editorial Recommendation Rubric**.

The rubric defines what makes a product worthy of being recommended.

It should establish:

- evaluation criteria;
- weights or priorities;
- hard constraints;
- minimum thresholds;
- contextual suitability;
- acceptable evidence;
- unacceptable claims;
- recommendation confidence;
- treatment of limitations and trade-offs.

The rubric is therefore upstream of:

- Select;
- Recommend;
- Align;
- Learn.

As Style Picks accumulates evidence, the rubric may evolve.

The evolution of the rubric should itself become an explicit learning process rather than an undocumented change in personal judgment.

---

# 17. Human, Deterministic, and Probabilistic Execution

This document intentionally does **not** assign agents to functions.

Each function may eventually be implemented through one or more execution mechanisms:

### Deterministic execution

Appropriate where the rule is explicit and reproducible.

Examples:

- validation;
- calculations;
- filtering by hard constraints;
- link verification;
- structured data processing.

### Probabilistic execution

Appropriate where interpretation, semantic matching, generation, or pattern recognition is required.

Examples:

- contextual interpretation;
- recommendation drafting;
- semantic classification;
- content generation;
- performance analysis.

### Human execution

Appropriate where responsibility, taste, strategy, or judgment is material.

Examples:

- editorial policy;
- brand direction;
- strategic decisions;
- exception handling;
- final approval during validation.

### Hybrid execution

Many Style Picks capabilities will combine these mechanisms.

The implementation mechanism is an engineering decision derived from the functional requirements.

---

# 18. Functional Success Criteria

The functional system succeeds when it can consistently transform:

```text
Consumer Need
      ↓
Relevant Context
      ↓
Relevant Products
      ↓
Editorial Selection
      ↓
Contextual Recommendation
      ↓
Compelling Presentation
      ↓
Trustworthy Destination
      ↓
Commercial Action
      ↓
Evidence
      ↓
Improved Future Decisions
```

The ultimate business outcome is not merely content production.

It is the ability to **reduce consumer decision friction while generating measurable commercial value**.

---

# 19. Relationship to the Engineering Proposal

This document precedes the Engineering Proposal.

The Engineering Proposal should be derived from the functions and requirements defined here.

The sequence is:

```text
Business Plan
      ↓
Value Proposition
      ↓
Value Proposition Functional Specification
      ↓
Business Capabilities
      ↓
Functional / Capability Contracts
      ↓
Engineering Proposal
      ↓
System Architecture
      ↓
Implementation
```

The Engineering Proposal must therefore answer:

> **What engineering system should Style Picks build to reliably execute these functions?**

It should not redefine the business functions unless new business evidence demonstrates that the functional model itself is incorrect.

---

# 20. Architectural Principle

Style Picks should not begin with:

> “How many AI agents should we build?”

It should begin with:

> “What capabilities are required to deliver the value proposition reliably?”

Only after the capabilities and their contracts are defined should the system determine whether each capability requires:

- deterministic software;
- an API;
- an LLM;
- an AI agent;
- a workflow;
- human review;
- or a combination.

Therefore:

> **Agents are implementation mechanisms, not business functions.**

The number of agents is not a business requirement.

The required capabilities are.

---

# 21. Version Control

This specification represents the **V1 functional model** for the commercial validation stage.

Changes should be made when:

1. new evidence demonstrates that a function is missing;
2. two functions are found to overlap materially;
3. a functional boundary proves incorrect;
4. the business model changes;
5. validation reveals that the current value proposition cannot be reliably delivered through the defined functions.

Implementation changes alone do not require changing this document.

---

# 22. Final Functional Definition

The Style Picks value proposition is operationalized through eight functions:

> **Context Definition → Discover → Select → Recommend → Present → Align → Learn**

with:

> **Govern**

operating transversally across the system.

Together, these functions define the minimum business behavior required for Style Picks to transform product abundance into contextual, curated, trustworthy, and commercially useful product discovery.

The next engineering artifacts should therefore be derived from this specification rather than designed independently of it.