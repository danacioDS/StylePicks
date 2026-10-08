# PH1-REG-STYP-001 v1.3 — Registro de Open Items (Corregido)

**Document ID:** PH1-REG-STYP-001

**Version:** 1.3 — Open Items Closure (Traction Demonstration Reconciled, Audit-Hardened)

**Status:** Stage A — Engineering Definition (Conceptual Level) — Baselined

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Document Type:** Open Items Register

**Scope:** Cross-cutting. This register is referenced by A.1–A.5. It is not a parent or child of any of them.

---

**Brand:** Style Picks
**Target Market:** United States
**Initial Channel:** Pinterest
**Monetization:** Amazon Associates
**StoreID:** `stylepicks05-20`
**Tracking IDs (per category):** `stylepicks-home-20` (Home Decor), `stylepicks-org-20` (Home Organization)
**Amazon Associates Account Created:** 2026-04-15
**Amazon Associates Deadline:** 2026-10-12
**Operating Window:** 2026-10-07 to 2026-10-12 (5 days)
**Actual Objective:** First Operational Milestone (FOM)
**Deferred Objective:** Commercial validation — next cycle

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| 1.0 | Oct 7, 2026 | Initial register; OI-001 through OI-008 defined. |
| 1.1 | Oct 8, 2026 | Header normalized; OI-001 and OI-002 closed. |
| 1.2 | Oct 8, 2026 | OI-003, OI-005, OI-006, OI-007 closed. |
| **1.3** | Oct 8, 2026 | **Audit hardening.** (1) **Priority reclassification recorded explicitly** (see §2.1): OI-003, OI-005, OI-006, OI-007 moved from *Defaultable* to *Blocking* — this change is now documented, per §8. (2) **§3 redefined:** "FOM-blocking" now means *required to publish a contract-compliant Pin*, not *required for account survival*. OI-003 is reclassified as **Decision Frame input**, not FOM-blocking. (3) **Tracking ID convention enforced:** the register now lists both per-category tracking IDs (`stylepicks-home-20`, `stylepicks-org-20`) and the StoreID. The link format uses the per-category tracking ID, not the StoreID (see OI-007). (4) **OI-005 source corrected:** the U.S. Associates Program documents are now cited instead of the EU IP Licence. (5) **OI-006, OI-007 split** into *Amazon requirement* vs. *StylePicks operational rule*. (6) **OI-005 image path reclassified:** the stock-context-only route is documented as insufficient under A.2 §10.6 and A.4 CP-004; the permitted routes are enumerated. (7) **Parenthood removed:** this register is now declared a cross-cutting reference, not a parent of A.1–A.5. (8) **FOM-blocking table added** (§3.1) to make the blocking set unambiguous. |

---

# 1. Purpose

This register is the **authoritative source of Open Items** for the Style Picks Stage A pipeline. Every document in Stage A references it. Any closure recorded here propagates by reference.

The register:

1. Tracks unresolved external facts that could invalidate a document if assumed incorrectly.
2. Records verification evidence for each closed item (source, date, exact rule).
3. Distinguishes **FOM-blocking** items from **Decision Frame inputs** and **next-cycle items**.

---

# 2. Open Items — Status Summary

| # | Open Item | Priority | Owner | Status |
|---|-----------|----------|-------|--------|
| **OI-001** | Amazon Associates account creation date | **Blocking** | Editorial Owner | **CLOSED — 2026-04-15** |
| **OI-002** | Amazon Associates deadline | **Blocking** | Editorial Owner | **CLOSED — 2026-10-12** |
| OI-003 | Qualifying-sales rule | Decision Frame input | Editorial Owner | **CLOSED — 2026-10-08** |
| OI-004 | Creators API access requirements | Next-cycle | Editorial Owner | **OPEN — non-blocking** |
| **OI-005** | Image and price display rules | **Blocking** | Editorial Owner | **CLOSED — 2026-10-08** |
| **OI-006** | Required disclosure wording | **Blocking** | Editorial Owner | **CLOSED — 2026-10-08** |
| **OI-007** | Link-format rules | **Blocking** | Editorial Owner | **CLOSED — 2026-10-08** |
| OI-008 | Evidence Source Policy | Next-cycle | Editorial Owner | **OPEN — non-blocking** |

## 2.1 Priority Reclassification (Recorded)

> **Change from v1.1 to v1.2, recorded here per §8.**

In v1.1, OI-003, OI-005, OI-006, and OI-007 were classified *Defaultable*. In v1.2 they were treated as *Blocking* without an explicit change-log entry. v1.3 corrects this:

| OI | v1.1 | v1.2 (implicit) | v1.3 (recorded) | Reason |
|----|------|-----------------|-----------------|--------|
| OI-003 | Defaultable | Blocking | **Decision Frame input** | Does not gate publication; informs the post-window decision. |
| OI-005 | Defaultable | Blocking | **Blocking** | Determines whether the Pin's image use is compliant. |
| OI-006 | Defaultable | Blocking | **Blocking** | Determines whether the Pin's disclosure is compliant. |
| OI-007 | Defaultable | Blocking | **Blocking** | Determines whether the Pin's link is compliant. |

---

# 3. FOM-Blocking Definition (Corrected)

> **An Open Item is FOM-blocking if a contract-compliant Pin cannot be published without its closure.**

This is narrower than the v1.2 definition. The FOM does **not** attempt account survival (A.1 v2.0 §17-A). Therefore, items that affect survival but not publication are not FOM-blocking.

## 3.1 FOM-Blocking Set

| OI | Blocks publication? | Blocks survival? | Classification |
|----|---------------------|------------------|----------------|
| OI-003 | No | Yes | Decision Frame input |
| OI-005 | **Yes** (image/price compliance) | No | **FOM-blocking** |
| OI-006 | **Yes** (disclosure compliance) | No | **FOM-blocking** |
| OI-007 | **Yes** (link compliance) | No | **FOM-blocking** |

**Consequence:** OI-003's closure is required for the Decision Frame (§18-A of A.1), not for publication.

---

# 4. Closure Records

Each record distinguishes **Amazon requirement** (external, binding) from **StylePicks operational rule** (internal decision).

---

## OI-001 — Amazon Associates Account Creation Date

| Field | Value |
|-------|-------|
| **Question** | When was the Style Picks Amazon Associates account created? |
| **Answer** | 2026-04-15 |
| **Source** | Style Picks Amazon Associates account dashboard |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED** |
| **Implication** | Survival clock began 2026-04-15. Not the operational start (2026-10-07). |

---

## OI-002 — Amazon Associates Deadline

| Field | Value |
|-------|-------|
| **Question** | What is the survival deadline? |
| **Answer** | 2026-10-12 (creation + 180 days) |
| **Source** | Amazon Associates Operating Agreement, Commission Income Statement |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED** |
| **Implication** | Operating window = 5 days. Validation is not achievable; the FOM is. |

---

## OI-003 — Qualifying-Sales Rule

| Field | Value |
|-------|-------|
| **Question** | What is the qualifying-sales rule? |
| **Answer** | Amazon requires **at least 3 qualifying sales within 180 days** of account creation. Once reached, the Associates team reviews the application for final approval. |
| **Source** | Amazon Associates Commission Income Statement (U.S.) |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED — Decision Frame input** |
| **Implication for FOM** | Does not gate publication. Informs the post-window decision (A.1 v2.0 §18-A). |
| **Implication for Decision Frame** | If the account lapses, Path 2 (reapply) starts from zero: the StoreID and current tracking IDs become invalid. This connects to CP-005 (inactive tracking ID error code). |

---

## OI-004 — Creators API Access Requirements

| Field | Value |
|-------|-------|
| **Question** | What are the current Creators API access requirements? |
| **Answer** | **Not yet verified.** Historically requires recent qualifying sales. |
| **Source** | Pending |
| **Status** | **OPEN — next-cycle** |
| **Implication** | FOM uses fully manual mode (A.5 §37-A). No API required. |

---

## OI-005 — Image and Price Display Rules

| Field | Value |
|-------|-------|
| **Question** | What are the rules for using Amazon images and displaying prices? |
| **Amazon requirement (images)** | Product Advertising Content consisting of an image may not be stored or cached. A link to the image may be stored for up to 24 hours. IP notices may not be altered, obscured, or made illegible. |
| **Amazon requirement (prices)** | Prices and availability may be displayed only if (a) Amazon serves the link containing that data, or (b) the data is obtained via the Creators API under its license. Scraping is not permitted. |
| **Source** | Amazon Associates Program Policies (U.S.); Amazon Associates Program IP Licence (U.S.); Amazon Associates Operating Agreement |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED** |
| **StylePicks operational rule** | The FOM does **not** use the Amazon product image stored locally, and does **not** display prices. |

### 4.1 Image Path for the FOM (Corrected)

The v1.2 conclusion — "use a stock context image, not the Amazon product image" — is **insufficient**. A.2-FUNC-STYP-001 §10.6 requires the product to be **visibly and accurately represented**, and prohibits stock imagery from depicting the product itself. A.4-CONTR-STYP-001 I.1.6 marks `product_image_reference` as **Required**.

**Permitted routes for the first Pin:**

| Route | Requirement | FOM-viable? |
|-------|-------------|-------------|
| **A. Original photography of the same product** | Operator owns or has access to the product | Yes, if available |
| **B. Manufacturer image with documented permission** | Permission recorded as an Imagery Evidence Record | Yes, if permission is obtained |
| **C. Amazon product image, served (not stored)** | Link to the Amazon image, ≤ 24h | Not practical for a published Pin |
| **D. Context-only Pin, product named in text** | Requires a new Change Proposal | Not currently permitted by A.2 §10.6 |

**FOM decision required:** the operator must choose Route A or B before publishing. Route D requires a CP and is a business decision, not a detail.

> **Note on CP-004:** v1.2 claimed CP-004 "supports" OI-005 closure. This was incorrect. CP-004 makes `contextual_image_reference` optional; it does **not** waive the requirement that `product_image_reference` be present and represent the product. The two operate at different levels.

---

## OI-006 — Required Disclosure Wording

| Field | Value |
|-------|-------|
| **Question** | What is the required affiliate disclosure statement? |
| **Amazon requirement** | *"As an Amazon Associate I earn from qualifying purchases."* Must appear **clearly and prominently** on the Site or wherever Amazon authorizes use of Program Content. |
| **Source** | Amazon Associates Program Operating Agreement (U.S.), Section 5 |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED** |
| **StylePicks operational rule** | Place the disclosure at the **beginning** of the Pin description. Pinterest truncates descriptions; "clearly and prominently" is not satisfied if the disclosure is hidden behind "see more". This rule also satisfies the independent FTC endorsement disclosure requirement (A.2 §13.3.6). |

**Note:** The v1.2 phrasing *"or any substantially similar statement previously allowed"* is removed. Only the exact wording verified above is used unless a future source explicitly permits an alternative.

---

## OI-007 — Link-Format Rules

| Field | Value |
|-------|-------|
| **Question** | How must the affiliate link be formatted? |
| **Amazon requirement** | Every Special Link must use the Associates ID assigned by Amazon. The Associates ID or "tag" must appear as a URL parameter. Amazon specifies the tag format as `XXXXX-##` or any other format Amazon may designate. Links must be accessed directly from the Site; bookmarks may not be incentivized. |
| **Source** | Amazon Associates Program Policies (U.S.), §2(a)-(b); Amazon Associates help documentation on simple text links |
| **Verification date** | 2026-10-08 |
| **Status** | **CLOSED** |
| **StylePicks operational rule** | Use the standard direct-link format with the **per-category tracking ID**, not the StoreID. |

### 4.2 Tracking ID Convention (Enforced)

A.1 §4, A.2 §12.6.1, A.3 §11.6, and A.4 (INV-3, INV-7) define **two per-category tracking IDs**:

| Tracking ID | Applied to |
|-------------|-----------|
| `stylepicks-home-20` | Home Decor |
| `stylepicks-org-20` | Home Organization |

**The StoreID `stylepicks05-20` is the account-level identifier, not the link-level tracking ID.** Using the StoreID in the link would break category attribution, which is the basis of Learn (A.2 §12.2).

**Operational link format for the FOM:**

```
https://www.amazon.com/dp/[ASIN]?tag=stylepicks-home-20
```

or, for Home Organization:

```
https://www.amazon.com/dp/[ASIN]?tag=stylepicks-org-20
```

**Action required before the first Pin:** create both per-category tracking IDs in the Associates account. If the exact names are unavailable, update the convention in A.1–A.4 rather than silently changing the register.

**Additional operational rule:** no URL shorteners, no third-party redirects. Amazon does not permit masking affiliate links.

---

## OI-008 — Evidence Source Policy

| Field | Value |
|-------|-------|
| **Question** | What is the formal Evidence Source Policy? |
| **Answer** | Not yet formalized. Interim rule: only the Amazon product page and the manufacturer's official site count as Verified (A.2 §9.6.2; A.3 §16.5). |
| **Status** | **OPEN — next-cycle** |
| **Implication** | FOM uses only Amazon product page data → Evidence Confidence = High. No blocker. |

---

# 5. Remaining Open Items

| # | Open Item | Deferred to | Gate |
|---|-----------|-------------|------|
| OI-004 | Creators API access requirements | Next cycle | C-02 programmatic mode |
| OI-008 | Evidence Source Policy | Next cycle | Evidence Confidence = Medium |

---

# 6. Change Proposals Affecting This Register

| CP | Title | Status | Effect |
|----|-------|--------|--------|
| CP-001 | Re-evaluation vs Revocation | Accepted 2026-10-08 | None |
| CP-002 | AI-Generated Contextual Imagery | Pending | Would expand imagery sources; not required for FOM |
| CP-003 | Review Cleared Sole-Writer | Accepted 2026-10-08 | None |
| CP-004 | Optional Contextual Image | Proposed | Makes `contextual_image_reference` optional; does **not** waive `product_image_reference` |
| CP-005 | Inactive Tracking ID Error Code | Proposed | Relevant if the Associates account lapses |

---

# 7. Actions Before the First Pin

1. **Create both per-category tracking IDs** in the Associates account (`stylepicks-home-20`, `stylepicks-org-20`). If unavailable, update A.1–A.4.
2. **Choose the image route** for the first Pin: original photography (A) or manufacturer image with permission (B). Record the imagery Evidence Record.
3. **Verify disclosure placement** in the Pin description (beginning of the description).
4. **Verify link format** uses the per-category tracking ID, no shorteners.
5. **Do not display prices.**

---

# 8. Register Integrity

> **This register is the single source of truth for Open Items. No document may declare an Open Item closed independently.**

Closures are never silent. Priority changes are never silent. Any change to an Open Item's status, priority, or classification is recorded in the Change Log and, where substantive, in a dedicated section.

---

## Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Engineering Definition (Conceptual Level)

**Level:** PH1 — Clarification & Open Items

**Document ID:** PH1-REG-STYP-001

**Version:** 1.3 — Open Items Closure (Traction Demonstration Reconciled, Audit-Hardened)

**Status:** **Baselined**

**Open Items Remaining:** OI-004, OI-008 — both next-cycle.

**Language:** English

---

*End of Phase 1 Clarification & Open Items Register — PH1-REG-STYP-001 v1.3*