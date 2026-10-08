# A.6-AFFIL-STYP-001 — Affiliate Provider Strategy

**Document ID:** A.6-AFFIL-STYP-001

**Version:** 1.4 — Editorial Cleanup (Baseline Final)

**Status:** Stage A — Commercial Architecture — **Baselined, closed for refinement**

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Language:** English

**Document Type:** Commercial Architecture Specification

**Position:** Annex to A.1 (Business Plan) + Change Proposals against A.2 and A.4. **Not a new pipeline level.**

**Parent Documents:**
- A.1-BIZ-STYP-001 — Business Plan and Commercial Validation (v2.0)
- A.4-CONTR-STYP-001 — Capability Contracts Specification (v1.1)

**Cross-Cutting Reference:**
- PH1-REG-STYP-001 — Phase 1 Clarification & Open Items Register (v1.3)

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 8, 2026 | Initial A.6. |
| 1.1 | Oct 8, 2026 | Provider Domain Model & Verification Hardening. |
| 1.2 | Oct 8, 2026 | Provider Domain Refinement & Tracking Neutrality. |
| 1.3 | Oct 8, 2026 | Final Baseline. INV-3a added. C-12 authority clarified. §4.1 self-applied. CD1 generalized. |
| **1.4** | Oct 8, 2026 | **Editorial Cleanup.** (1) **§8.4 example corrected**: removed the "publisher ID + clickref" example, since the publisher ID is static and belongs to the Merchant Program. Replaced with a dynamic example: `clickref` + `sub_id`. (2) **INV-3a wording corrected**: the Content Asset reaches the Merchant Program through the Product Record; the invariant now reads "referenced via the Content Asset's Product Record". (3) **§8.3 clarified**: `static_tracking_parameters` explicitly holds the publisher ID and the category→tag mapping. (4) No architectural change. |

---

## Open Items

| # | Open item | Priority | Owner | Status |
|---|-----------|----------|-------|--------|
| **OI-A6-01** | Amazon Associates US payout rail for Bolivia | **Decision Frame input (2026-10-12)** — not FOM-blocking | Editorial Owner | OPEN |
| **OI-A6-02** | Awin publisher eligibility from Bolivia | Blocking for Awin activation (next cycle) | Editorial Owner | OPEN |
| **OI-A6-03** | Payoneer payout mechanics per network | Defaultable | Editorial Owner | OPEN |
| **OI-A6-04** | US banking infrastructure acceptance (Lead Bank / Meru) per program | Defaultable | Editorial Owner | OPEN |
| **OI-A6-05** | Wayfair affiliate program geographic eligibility | Defaultable | Editorial Owner | OPEN |
| **OI-A6-06** | Walmart Creator publisher terms | Defaultable | Editorial Owner | OPEN |

> **OI-A6-01 is the only A.6 item that affects a decision this week.** Amazon's payment configuration page shows which payout methods are available for your country. Verifying it takes minutes and should be done **before 2026-10-12**.

---

# 1. Purpose

This document defines the **Affiliate Provider Layer** of Style Picks.

It exists because the current Business Plan (A.1) treats Amazon Associates as a **single point of dependency**. That dependency is now **conditional** — the current Amazon Associates application may lapse on 2026-10-12 (A.1 §18-A). Whether a rejected application can be reinstated is recorded in **PH1 v1.3 OI-003**.

This document:

1. Converts the Amazon dependency into a **replaceable architectural capability**.
2. Defines the **Provider / Merchant Program / Product Destination** domain model.
3. Declares the **provider portfolio**, its selection criteria, and its activation sequence.
4. Defines the **Bolivia operating model** for publisher eligibility and payment rails.
5. Files the Change Proposals required against A.2 and A.4.

This document does **not** redefine any business function (A.2), capability (A.3), contract (A.4), or engineering mechanism (A.5). It extends them.

> **Position note.** This document is an **annex to A.1 (Business Plan)**, not a new pipeline level. The A.6 prefix is retained for traceability only. CP-006, CP-007, and CP-008 are filed against A.2 and A.4.

---

# 2. Strategic Context

## 2.1 The Single-Provider Risk

Stage A was originally designed around a single affiliate provider:

```
StylePicks → Amazon Associates → Commission
```

That design carries three risks:

| Risk | Consequence |
|------|-------------|
| **Account survival** | If the 180-day qualification window closes without 3 qualifying sales, the application is withdrawn. See PH1 v1.3 OI-003. |
| **Geographic eligibility** | Amazon Associates and alternative networks apply jurisdiction-specific publisher terms. |
| **Platform policy** | Amazon may change commission rates, cookie windows, or content rules at any time (Operating Agreement §13). |

## 2.2 The Architectural Response

Style Picks is designed as:

```
StylePicks → Affiliate Provider Layer → Merchant → Commission
```

The provider layer is a **logical abstraction at Stage A**. Concrete provider integrations are implementation mechanisms deferred to Stage B.

## 2.3 Scope of This Document

This document defines the **commercial architecture**. It does not define:

- the software adapters (Stage B);
- the final merchant portfolio (evolves with evidence);
- the commission economics (belong to A.1);
- the destination model (belongs to A.2 §10.3; CP-006).

---

# 3. Affiliate Provider Layer

## 3.1 Definition

The **Affiliate Provider Layer** is a logical boundary between Style Picks and any external affiliate program. It exposes a uniform interface to the rest of the system, regardless of which network or merchant is behind it.

## 3.2 Logical vs. Concrete

| Level | Description | Stage |
|-------|-------------|-------|
| **Logical abstraction** | Provider / Merchant Program / Product Destination | A.6 (this document) |
| **Concrete integration** | Network-specific adapter, API, tracking URL construction | Stage B |

## 3.3 Conceptual Structure

```
                    StylePicks
                        │
                        ▼
             Affiliate Provider Layer
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
     Amazon           Awin           Impact
        │               │               │
        ▼               ▼               ▼
    Merchant        Merchant        Merchant
```

## 3.4 What the Layer Owns

| Concern | Owner |
|---------|-------|
| Provider identity | Provider |
| Merchant identity | Merchant Program |
| Commission model metadata | Merchant Program |
| Attribution window metadata | Merchant Program |
| Static tracking parameters (publisher ID, category→tag mapping) | Merchant Program |
| Market / geography metadata | Merchant Program |
| Provider status | Provider |
| Merchant Program status | Merchant Program |

## 3.5 What the Layer Does Not Own

- The product record (A.4 C-02)
- The destination model (A.2 §10.3)
- The affiliate URL derivation (A.4 C-05)
- The compliance rules (A.4 C-12)
- The performance measurement (A.4 C-08)
- Dynamic tracking parameters per Pin (belong to the Content Asset)

The layer **informs** these; it does not replace them.

---

# 4. Provider Selection Criteria

## 4.1 Evidence Classification

Every provider and merchant claim in this document carries one of the following statuses:

| Status | Definition | Required support |
|--------|-----------|------------------|
| **VERIFIED** | Supported by current provider terms or official documentation. | **Source + section + date** |
| **CANDIDATE** | Strategically attractive, but not yet verified. | None |
| **OPEN** | Requires explicit investigation before activation. | A tracked Open Item |
| **EXCLUDED** | Fails a mandatory activation criterion based on verified evidence. | Source + section + date |
| **DEPRECATED** | Previously supported but no longer eligible or strategically relevant. | Reason recorded |

> **Enforcement rule (applies to this document).** A claim marked VERIFIED **without** source + section + date is downgraded to CANDIDATE. This rule is applied to every entry below.

## 4.2 Hard Constraints (mandatory)

A provider is **eligible for activation** only if it satisfies **all** of:

| # | Hard constraint | Verification |
|---|-----------------|--------------|
| H-1 | Legal eligibility for a publisher resident in Bolivia | Publisher terms |
| H-2 | A documented payout rail compatible with Payoneer or an equivalent | Payment terms |
| H-3 | Merchants in Home Decor or Home Organization | Merchant catalog |
| H-4 | No jurisdiction-specific legal entity required that Style Picks cannot form | Program terms |
| H-5 | No bank account required in a jurisdiction Style Picks cannot access | Program terms |
| H-6 | Compliance compatibility (disclosure, link format, image rules) | Program policies |

**Any hard constraint failure = EXCLUDED until satisfied.**

## 4.3 Commercial Preferences (non-blocking)

| Preference | Rationale |
|------------|-----------|
| Attribution window ≥ 24h | Reduces conversion loss from delayed purchases |
| Commission compatible with A.1 §12 economics | Ensures the time-economics rule can be met |
| High AOV | Improves revenue per click |
| Low approval friction | Speeds activation |
| Pin-level attribution capability (e.g., Awin's `clickref`) | Enables content-level learning |

> **Note.** A provider with a 12-hour attribution window and excellent conversion may still be selected. The 24h figure is a preference, not a gate.

---

# 5. Provider Portfolio

## 5.1 Tier 1 — Amazon Associates

| Attribute | Value | Status | Source + section + date |
|-----------|-------|--------|--------------------------|
| Role | Initial provider / benchmark | — | — |
| Coverage | Broad catalog, Home Decor / Organization | CANDIDATE | — |
| Commission | Variable by category (A.1 §10) | CANDIDATE | — |
| Attribution window | 24 hours, extended to 89 days if item added to cart within 24h | **VERIFIED** | Amazon Associates Commission Income Statement, §"Qualifying Purchases", verified 2026-10-08 |
| Payout rail for Bolivia | To be verified | **OPEN** | OI-A6-01 |
| Bolivia publisher eligibility | To be verified | **OPEN** | — |
| Activation status | **Active — DR-1 and DR-5 exceptions (see §13)** | — | — |

> **Dual role.** Amazon is both the network and the merchant in this portfolio. It is the only provider in this document with that dual condition. See §8.6.

## 5.2 Tier 2 — Awin

### 5.2.1 Provider-level facts

| Attribute | Value | Status | Source + section + date |
|-----------|-------|--------|--------------------------|
| Role | Primary alternative candidate | — | — |
| Coverage | ~30,000 merchants (public figure) | CANDIDATE | — |
| Awin supports Payoneer | Documented by Awin for international publishers | **CANDIDATE** — pending section + date | Awin publisher payment documentation (section + date pending) |
| Awin publisher approval | May depend on traffic history | CANDIDATE | — |

> **Note.** "Awin supports Payoneer" was VERIFIED in v1.2. It is downgraded here because the required section + date are not recorded. Once recorded, it returns to VERIFIED.

### 5.2.2 Bolivia-specific facts

| Attribute | Value | Status | Source |
|-----------|-------|--------|--------|
| Bolivia publisher eligibility | To be verified | **OPEN** (OI-A6-02) | — |
| Payoneer available to a Bolivian publisher | To be verified | **OPEN** | — |
| StylePicks payout path | To be verified | **OPEN** | — |

### 5.2.3 Functional advantage

Awin supports a `clickref` parameter that enables **Pin-level attribution**. Amazon does not (A.2 §12.2 records the limitation). This is a **functional** advantage, not a commercial one.

### 5.2.4 Candidate Merchants (illustrative, unverified)

| Merchant | Category | Commission | Cookie | Status |
|----------|----------|-----------|--------|--------|
| iDesign | Home Organization | 10% | 30 days | CANDIDATE |
| Lahome | Home Decor (rugs) | up to 20% | 60 days | CANDIDATE |
| Hernest | Furniture / Home Decor | up to 15% | 60 days | CANDIDATE |
| OJCommerce | Home Decor / Furniture | 5–10% (up to 30% select) | 14 days | CANDIDATE |

### 5.2.5 Activation status

**Blocked pending OI-A6-02.** Not activation-ready.

## 5.3 Tier 3 — Impact

| Attribute | Value | Status |
|-----------|-------|--------|
| Role | Scaling — large brands | — |
| Coverage | Global brands | CANDIDATE |
| Bolivia eligibility | To be verified | OPEN |
| Payout rail | To be verified | OPEN |
| Activation status | Deferred until Style Picks has audience + traffic + conversion history | — |

## 5.4 Tier 4 — FlexOffers

| Attribute | Value | Status |
|-----------|-------|--------|
| Role | Backup catalog | — |
| Coverage | Merchants not available in Awin | CANDIDATE |
| Payment terms | Net 60 standard | CANDIDATE |
| Bolivia eligibility | To be verified | OPEN |
| Payout rail | To be verified | OPEN |
| Activation status | Secondary | — |

## 5.5 Tier 5 — Direct Brand Programs

| Attribute | Value | Status |
|-----------|-------|--------|
| Role | Long-term commerce media property | — |
| Activation | After consistent conversion evidence exists | — |

---

# 6. Bolivia Operating Model

## 6.1 Publisher Eligibility

A provider accepts a Bolivian publisher when:

1. Its publisher terms do not require residency in a specific jurisdiction, **or**
2. Its publisher terms explicitly include Bolivia, **or**
3. It provides a documented path (legal entity, tax form) that Style Picks can satisfy.

**Current positions are recorded as OPEN in §5 and in the Open Items table.**

## 6.2 Payment Rails

### 6.2.1 Payoneer

| Attribute | Value | Status | Source |
|-----------|-------|--------|--------|
| Type | Multi-currency receiving account | CANDIDATE | (Payoneer documentation; section + date pending) |
| Awin supports Payoneer | Documented | **CANDIDATE** | Awin payment documentation (section + date pending) |
| Payoneer available to Bolivian publisher | To be verified | OPEN | — |
| StylePicks payout path (Awin) | To be verified | OPEN | — |
| Minimum payout | Typically $20 (per network) | CANDIDATE | — |
| Currency conversion | Network-specific (Awin: ~1.75%) | CANDIDATE | — |
| Settlement time | Typically 1–2 business days after payout release | CANDIDATE | — |

### 6.2.2 US Banking Infrastructure (Conditional)

| Attribute | Value | Status | Source |
|-----------|-------|--------|--------|
| Type | US receiving account | CANDIDATE | (to be sourced) |
| Function | Receives USD deposits only | CANDIDATE | (to be sourced) |
| Acceptance | Must be verified per provider | OPEN (OI-A6-04) | — |

> **Correction to prior informal guidance.** "Lead Bank + Payoneer works for most providers" is **not** an architectural fact. It is a hypothesis to be verified per provider.

### 6.2.3 Amazon Associates Payout for Bolivia (Decision Frame Input)

Amazon Associates US **may** pay by direct deposit only to certain countries, and **may** use alternatives (e.g., gift cards) outside them. Whether Bolivia falls under direct deposit or an alternative is **OI-A6-01**.

> **Why this matters for the Decision Frame.** If Amazon's payout rail for Bolivia is gift cards rather than cash, the value of Path 2 (reapply to Amazon) changes materially. This should be verified **before** the Decision Frame on 2026-10-12.

## 6.3 Operating Rule

> **Every provider activated by Style Picks must have a documented payment rail.** No provider is activated on the assumption that a rail will work.

---

# 7. Provider Decision Matrix

| Provider | Bolivia eligible? | Payout rail? | Home Decor merchants? | Attribution ≥ 24h? | Tier | Activation |
|----------|-------------------|--------------|------------------------|--------------------|------|-----------|
| Amazon Associates | OPEN | **OPEN (Decision Frame input)** | CANDIDATE | VERIFIED (24h / 89d) | 1 | **Active — DR-1 and DR-5 exceptions** |
| Awin | OPEN (OI-A6-02) | CANDIDATE (Payoneer) | CANDIDATE | CANDIDATE (30–60d) | 2 | Blocked pending OI-A6-02 |
| Impact | OPEN | OPEN | CANDIDATE | CANDIDATE | 3 | Deferred |
| FlexOffers | OPEN | OPEN | CANDIDATE | CANDIDATE | 4 | Secondary |
| Direct brands | Case by case | Case by case | Case by case | Case by case | 5 | Future |

---

# 8. Affiliate Provider Domain Model

## 8.1 Domain Entities

```
AffiliateProvider
    └── MerchantProgram
            └── ProductDestination   (conceptual tuple; the tuple itself is not persisted)
```

**Four conceptual levels:**

| Level | Entity | Represents |
|-------|--------|-----------|
| Network | `AffiliateProvider` | The affiliate network (Amazon, Awin, Impact, FlexOffers) |
| Merchant | `MerchantProgram` | A specific merchant within a network |
| Product Destination | `(MerchantProgram, product_destination)` tuple | The specific product + URL + tracking information |
| Product Record | *(existing)* A.4 I.1.2 | The Style Picks product record |

> **On persistence.** `ProductDestination` is a conceptual tuple, but it is carried by the persisted field `approved_destination_reference` on the Product Record. The `product_destination` component is the ASIN (or provider-specific product identifier) already recorded in the Product Record; the `MerchantProgram` component is the merchant reference. No new persisted record is required for the tuple itself.

## 8.2 AffiliateProvider (Network)

```
AffiliateProvider
    ├── provider_id           (unique, internal)
    ├── network               (Amazon / Awin / Impact / FlexOffers / Direct)
    ├── provider_name         (human-readable)
    ├── publisher_terms_ref   (link to verified terms)
    ├── terms_verified_at     (date)
    ├── default_payout_rail   (Payoneer / US bank / other)
    ├── payout_rail_ref       (link to verified rail)
    ├── status                (Active / Pending / Excluded / Deprecated)
    └── notes                 (free text)
```

## 8.3 MerchantProgram

```
MerchantProgram
    ├── merchant_id                 (unique, internal)
    ├── provider_id                 (FK → AffiliateProvider)
    ├── merchant_name               (human-readable)
    ├── category                    (Home Decor / Home Organization / Other)
    ├── market                      (US, default)
    ├── commission_model            (percent / flat / tiered)
    ├── commission_value            (numeric, if known)
    ├── attribution_window          (hours or days)
    ├── tracking_url_template       (network-specific template)
    ├── static_tracking_parameters  (structured; see below)
    ├── program_terms_ref           (link to verified merchant terms)
    ├── terms_verified_at           (date)
    ├── status                      (Active / Pending / Excluded / Deprecated)
    └── notes                       (free text)
```

### 8.3.1 Static Tracking Parameters

`static_tracking_parameters` holds the parts of the tracking configuration that **do not change per Pin**:

| Parameter | Example | Description |
|-----------|---------|-------------|
| `publisher_id` | Awin publisher ID | Constant across all Pins for this network |
| `category_tag_map` | `Home Decor → stylepicks-home-20` | Per-category Amazon associate tag; or equivalent per-network mapping |
| `network_defaults` | (network-specific) | Any other static parameter required by the network |

The **dynamic** part of the tracking configuration (per-Pin identifiers) belongs to the Content Asset and is defined in §8.4.

## 8.4 Tracking Reference (Content Asset Level)

The per-Pin tracking identifier(s) are carried by the **Content Asset**, not the Merchant Program. This is because per-Pin identifiers change with every Pin and cannot be declared at the merchant level.

The persisted schema (delegated to CP-006/A.4) uses a structured field:

```
tracking_reference
    ├── provider          (FK → AffiliateProvider)
    ├── identifier_type   (associate_tag / clickref / sub_id / …)
    └── identifier_value  (the actual value)
```

**A single Content Asset may carry more than one `tracking_reference`.** Example: Awin can use a `clickref` to identify the Pin, plus a `sub_id` to distinguish a campaign. Both are dynamic and both belong to the Content Asset.

> **What is not carried here.** The publisher ID is **static** and belongs to the Merchant Program (§8.3.1). It is not a `tracking_reference` on the Content Asset.

### 8.4.1 Provider Consistency Invariant (Proposed)

> **INV-3a (proposed).** For every `tracking_reference` on a Content Asset, `tracking_reference.provider` must equal the `AffiliateProvider` of the `MerchantProgram` referenced via the Content Asset's Product Record.

This invariant prevents two sources of truth for provider identity. **Filed under CP-006.**

## 8.5 Relationships to Existing Records

| Existing record | Field | New value domain |
|-----------------|-------|------------------|
| Product Record (A.4 I.1.2) | `approved_destination_reference` | Carries the `(MerchantProgram, product_destination)` tuple |
| Content Asset (A.4 I.1.6) | `affiliate_destination_url` | Derived from the Merchant Program's `tracking_url_template` + `static_tracking_parameters` + the Content Asset's `tracking_reference` |
| Content Asset (A.4 I.1.6) | `tracking_reference` (replaces `tracking_id`) | Structured per §8.4 |
| Compliance Record (A.4 I.1.8) | CD2 (generalized) | Evaluates the active provider's content rules (CP-007) |
| Compliance Record (A.4 I.1.8) | CD1 (generalized) | Evaluates the active provider's eligibility and survival rules (CP-007) |

## 8.6 Amazon as Both Network and Merchant

Amazon is the only provider in this document where the network and the merchant are the same entity.

- `AffiliateProvider.network = Amazon`
- `MerchantProgram.merchant_name = Amazon`
- `MerchantProgram.provider_id = AffiliateProvider(Amazon)`

No special-casing is required; the model accommodates it without modification.

## 8.7 Sole-Writer Requirement (A.4 INV-10)

| Record type | Sole writer | Rationale |
|-------------|-------------|-----------|
| `AffiliateProvider` | **C-12 (Compliance & Governance)** | C-12 is the sole authority for provider admission, verification, activation, suspension, and deactivation. Publisher terms, Bolivia eligibility, and payment rail are verified under CD1 (generalized in CP-007). |
| `MerchantProgram` | **C-02 (Product Discovery)** | Merchant registration is a discovery-time concern: the merchant is a source of product candidates. |

**This is filed as CP-008.**

---

# 9. Integration with A.4 Capability Contracts

## 9.1 Contract Extension

This document **extends** A.4 in four ways:

1. New record types: `AffiliateProvider`, `MerchantProgram` (CP-008).
2. Generalized destination: `approved_destination_reference` carries a `(MerchantProgram, product_destination)` tuple (CP-006).
3. Generalized tracking: `tracking_id` becomes `tracking_reference` (CP-006).
4. Generalized compliance domains: CD1 and CD2 become *Provider Eligibility & Survival* and *Provider Content Rules* (CP-007).

## 9.2 Required Change Proposals

| CP | Title | Affected sections | Classification | Status |
|----|-------|-------------------|----------------|--------|
| **CP-006** | Provider-independent destination model and tracking reference | A.2 §10.3; A.4 I.1.2, I.1.6; INV-3; new INV-3a | Contract extension | Proposed |
| **CP-007** | Provider eligibility and content rules (generalize CD1 and CD2) | A.4 I.1.8, C-12 | Contract extension | Proposed |
| **CP-008** | New record types + sole-writer assignment | A.4 Part I; INV-10 | Contract extension | Proposed |

## 9.3 CP-006 — Provider-independent destination model and tracking reference

**Divergence.** A.2 §10.3 defines the destination model as `Pin → Amazon product page (via affiliate link)`. A.4 INV-3 assumes the Amazon `tag` convention.

**Proposed resolution.**

1. Amend A.2 §10.3 to: `Pin → provider product page (via affiliate link)`, with Amazon as the initial provider.
2. Amend A.4 I.1.2 to admit a provider-qualified `approved_destination_reference` carrying a `(MerchantProgram, product_destination)` tuple.
3. Amend A.4 I.1.6 to replace `tracking_id` with `tracking_reference`.
4. Reword **INV-3**:

   > **INV-3 (revised).** The affiliate URL must be generated from the `tracking_url_template` and `static_tracking_parameters` of the referenced Merchant Program plus the `tracking_reference`(s) of the Content Asset. The tracking reference(s) embedded in the URL must match those carried in the Content Asset metadata.

5. Add **INV-3a** (Provider Consistency):

   > **INV-3a.** For every `tracking_reference` on a Content Asset, `tracking_reference.provider` must equal the `AffiliateProvider` of the `MerchantProgram` referenced via the Content Asset's Product Record.

**Classification.** Semantic generalization of the destination abstraction.

## 9.4 CP-007 — Provider eligibility and content rules

**Divergence.** A.4 C-12 defines **CD1 — Amazon Associates Eligibility & Survival** and **CD2 — Amazon Associates Content Rules** as Amazon-specific domains.

**Proposed resolution.** Generalize CD1 and CD2 to *Provider Eligibility & Survival* and *Provider Content Rules*, with Amazon as one instance. Withdraw the v1.0 `CD2-P` proposal.

**Impact.** C-12 gains two parameterized domains. No invariant changes.

## 9.5 CP-008 — New record types and sole-writer assignment

**Divergence.** A.4 Part I does not include `AffiliateProvider` or `MerchantProgram`. INV-10 requires exactly one sole writer per record type.

**Proposed resolution.** Add both to A.4 Part I.1, with sole writers as in §8.7.

**Impact.** A.4 Part I.1 gains two sections. C-12 and C-02 each gain one output.

---

# 10. Integration with A.5 Engineering Proposal

## 10.1 Adapter Pattern

A.5 §30 defines the adapter pattern. This document extends it:

```
Style Picks Core → Affiliate Provider Interface
                          ↓
        ┌─────────────┬─────────────┬─────────────┐
        ▼             ▼             ▼             ▼
   Amazon Adapter  Awin Adapter  Impact Adapter  Direct Adapter
```

## 10.2 Impact on Phase 0

**The FOM does not depend on this document.** Phase 0 (A.5 §32) uses Amazon as the sole provider.

## 10.3 Impact on Phase 5 (Publication & Lifecycle)

When a second provider is activated, Phase 5 must:

- extend the Publication Record to include a provider reference;
- extend the Compliance engine to evaluate the active provider's rules (CD1 and CD2, generalized);
- extend the destination derivation logic (C-05) to support provider-qualified references.

Deferred until the Decision Frame selects Path 2 or Path 3.

## 10.4 On `tracking_url_template`

`tracking_url_template` is the **default Merchant Program derivation mechanism**. Provider-specific destination construction may introduce additional parameters in Stage B. A.6 does not specify the URL-construction algorithm; it specifies the data the algorithm consumes.

---

# 11. Provider Activation Strategy

## 11.1 Activation Rules

A provider is activated when:

1. All hard constraints (§4.2) are VERIFIED.
2. Its terms are recorded as verified configuration (source + section + date).
3. Its adapter is defined in Stage B.

## 11.2 Activation Sequence

| Phase | Provider | When |
|-------|----------|------|
| **FOM** | Amazon | This cycle (DR-1 and DR-5 exceptions) |
| **Next cycle** | First verified alternative provider | After Decision Frame, if Path 2 or 3 is selected |
| **Growth** | Additional verified providers | After the first alternative produces conversion evidence |
| **Scale** | All verified tiers + Direct | After consistent conversion + audience |

## 11.3 Amazon Attribution Detail

Amazon Associates' default attribution window is **24 hours**. If the customer adds an item to their cart within those 24 hours, the attribution window extends to **89 days** for that item. Source: Amazon Associates Commission Income Statement, §"Qualifying Purchases", verified 2026-10-08.

## 11.4 Deactivation Rules

A provider is deactivated when:

- its terms change in a way that invalidates Style Picks' eligibility;
- its payout rail becomes unavailable;
- its merchants no longer cover the active categories;
- it is superseded by a better provider for the same function.

Deactivation is recorded. Existing Pins are re-linked to an active provider (per A.4 I.2.1, "Re-linked" event).

---

# 12. Excluded / Conditional Providers

## 12.1 Walmart Creator

| Attribute | Value |
|-----------|-------|
| Status | **Conditional — excluded pending verification** |
| Candidate reason | Requires US residency and a US bank account. |
| Verification | **OI-A6-06** |

## 12.2 Providers Requiring Jurisdiction-Specific Legal Entities

| Status | **Conditional** — excluded until the required entity can be formed |

## 12.3 Providers With No Documented Payment Rail

| Status | **Conditional** — excluded until a rail is documented |

---

# 13. Decision Rules

| Rule | Statement |
|------|-----------|
| **DR-1** | No provider is activated on an assumption. Every activation requires verified terms. **Exception:** Amazon is activated in the FOM as a recorded exception (see §5.1). |
| **DR-2** | The provider layer is provider-agnostic. No business function, capability, or contract may depend on a specific provider. |
| **DR-3** | Amazon is the initial provider but not a structural dependency. |
| **DR-4** | Awin is a **candidate**, not a commitment. Activation requires OI-A6-02 closure. |
| **DR-5** | Every provider must have a documented payment rail before activation. **Exception:** Amazon is activated in the FOM as a recorded exception, on the basis that the FOM does not attempt to generate or collect revenue. The payout rail (OI-A6-01) must be resolved before the next cycle. |
| **DR-6** | Providers failing a hard constraint are excluded until the constraint is satisfied. |
| **DR-7** | The FOM does not depend on this document. |
| **DR-8** | Commercial preferences (§4.3) never gate activation; they inform selection. |

---

# 14. Roadmap

```
This cycle (FOM)
    └── Amazon (DR-1 and DR-5 exceptions) — sole provider

Decision Frame (2026-10-12)
    ├── Path 1: extend survival clock → Amazon retained
    ├── Path 2: reapply → Amazon v2 (contingent on OI-A6-01)
    ├── Path 3: operate without Amazon → activate first verified alternative provider
    └── Path 4: redefine model → A.6 revised

Next cycle
    └── Activate first verified alternative provider
          ├── Awin, if OI-A6-02 closes and Payoneer rail is verified
          ├── Impact, if selected and verified
          └── FlexOffers / direct merchant, if required

Growth
    └── Additional verified providers

Scale
    └── All verified tiers + Direct
```

---

# 15. Risks

| Risk | Severity | Mitigation |
|------|----------|-----------|
| **Amazon payout rail for Bolivia is not cash** (OI-A6-01) | **High** | Verify before the Decision Frame on 2026-10-12. |
| Awin rejects publisher with no traffic history | Medium | Apply after the next cycle has produced content and at least one month of published Pins. |
| Merchant-level approval within Awin fails | Medium | Apply to multiple merchants; treat each as a separate approval. |
| Provider terms change between verification and activation | Medium | Record `terms_verified_at`; re-verify before activation. |
| Payment rail becomes unavailable | Medium | Maintain at least two verified rails where possible. |

---

# 16. What This Document Does Not Do

- It does not redefine A.1 through A.5.
- It does not commit to Awin, Impact, or any specific provider.
- It does not assume payment mechanics that have not been verified.
- It does not replace the Decision Frame (A.1 §18-A).
- It does not extend the FOM.
- It is not a new pipeline level. It is an annex to A.1, with CPs against A.2 and A.4.

> **On resilience.** The architecture is resilient: if Amazon's application lapses, Style Picks does not lapse with it. **Revenue is not yet resilient.** The two are distinct.

---

## Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** A.6 — Commercial Architecture (annex to A.1)

**Document ID:** A.6-AFFIL-STYP-001

**Version:** 1.4 — Editorial Cleanup (Baseline Final)

**Status:** **Baselined, closed for refinement.** Provider-specific eligibility facts remain OPEN verification inputs.

**Authorization:** This document extends Stage A. It derives from A.1 (Business Plan) and A.4 (Capability Contracts). CP-006, CP-007, CP-008 are proposed against A.2 and A.4 respectively.

**Blocking Dependencies for the FOM:** None.

**Blocking Dependencies for the Next Cycle:** OI-A6-02 (Awin eligibility from Bolivia).

**Decision Frame Input:** OI-A6-01 (Amazon payout rail for Bolivia).

**Language:** English

---

*End of Affiliate Provider Strategy — A.6-AFFIL-STYP-001 v1.4*

---

## Note on the FOM

> **This document does not change the FOM.**
>
> **What this document changes is the structural risk of the next cycle.** If Amazon's application lapses, Style Picks does not lapse with it — architecturally.
>
> **The Learning Record created at window close (A.5 §18) remains execution evidence.** A.6 defines the architecture; the Learning Record records what happened.
>
> **This version closes the A.6 refinement loop.** No further changes to A.6 until real-world evidence arrives: Awin's response, Amazon's payment configuration, and the Decision Frame outcome on 2026-10-12.

---

## Forward Note — Deferred Actions

The following actions are **deferred** and are not part of the FOM:

| # | Action | When |
|---|--------|------|
| 1 | Verify OI-A6-01 (Amazon payout rail for Bolivia) | Before 2026-10-12 |
| 2 | Decide all accumulated Change Proposals together: CP-004, CP-005 (from A.4 v1.1), and CP-006, CP-007, CP-008 (from A.6) | After the Decision Frame, in a single A.4 v1.2 |
| 3 | Activate a second provider (if Path 2 or Path 3 is selected) | Next cycle |

> **CP-006 through CP-008 only matter if a second provider is activated.** They do not block the FOM and do not require a decision this week.