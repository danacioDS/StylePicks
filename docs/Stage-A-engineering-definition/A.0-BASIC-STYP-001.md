# A.0-BASIC-STYP-001 — Stage A: Basic Engineering

**Document ID:** A.0-BASIC-STYP-001

**Version:** 1.0 — Stage A Framing Baseline

**Status:** Stage A — Engineering Definition (Conceptual Level) — Baselined

**Project:** Style Picks — Content Commerce + Affiliate Commerce

**Engagement:** STYP-VALIDATION-2026

**Language:** English

**Document Type:** Stage A Framing Document

**Position:** Root framing document for the entire Stage A pipeline (A.1–A.5 + PH1)

---

## Change Log

| Version | Date | Change |
|---------|------|--------|
| **1.0** | Oct 8, 2026 | Initial A.0 framing document. Establishes Stage A as **Basic Engineering**, defines the pipeline, the document hierarchy, the cycle objective, the closing criteria, and the handoff to Stage B. Designed to precede A.1 and to be referenced by all Stage A documents. |

---

# 1. Purpose

This document defines **Stage A — Basic Engineering** for the Style Picks engagement.

It exists because the Stage A pipeline (A.1–A.5) was built **without a framing document**. Every document derived from a parent without a declared root. This document supplies that root.

A.0 does **not** add engineering content. It declares:

1. What Stage A is.
2. What Stage A is **not**.
3. Which documents constitute Stage A.
4. In what order they were produced and must be read.
5. What the current cycle attempts (the FOM) and what it defers.
6. When Stage A closes and how it hands off to Stage B.

> **A.0 is a framing document, not an engineering document.** If A.0 and any A.x document disagree, the A.x document governs the specific point; A.0 governs the reading order, the pipeline structure, and the closing criteria.

---

# 2. What Stage A Is

**Stage A is Basic Engineering.**

In the Style Picks delivery framework, engineering proceeds through four stages:

| Stage | Name | Question it answers | Deliverable |
|-------|------|---------------------|-------------|
| **A** | **Basic Engineering** | **What must the business do, and what must the system be able to do?** | Business intent, functions, capabilities, contracts, engineering proposal |
| B | System Architecture (HLD) | How is the system structured? | High-level design |
| C | Product Specification (Detailed Engineering) | How is each component specified? | Detailed specification |
| D | Implementation | How is the system built and delivered? | Working system |

Stage A produces **the conceptual engineering baseline**. It defines the problem space and the required behavior. It does **not** define the technical architecture, the code, or the deployment.

---

# 3. What Stage A Is Not

Stage A is **not**:

- a technical architecture;
- a software design;
- a data model in the implementation sense;
- a user interface specification;
- an implementation plan;
- a product roadmap.

Those belong to Stages B, C, and D.

Stage A documents may **reference** technical decisions (for example, the choice of Django in A.5 §39-A), but only as **committed defaults for the next stage**, not as Stage A content. The architecture itself is Stage B.

---

# 4. Stage A Pipeline

The Stage A pipeline consists of six documents plus this framing document:

```
A.0-BASIC-STYP-001   Stage A — Basic Engineering (this document)
        │
        ▼
A.1-BIZ-STYP-001     Business Plan and Commercial Validation
        │
        ▼
A.2-FUNC-STYP-001    Value Proposition Functional Specification
        │
        ▼
A.3-CAP-STYP-001     Business Capabilities Specification
        │
        ▼
A.4-CONTR-STYP-001   Capability Contracts Specification
        │
        ▼
A.5-ENG-STYP-001     Engineering Proposal
        │
        ▼
PH1-REG-STYP-001     Phase 1 Clarification & Open Items Register
        │
        ▼
STAGE-A-CONSOL-REPORT-STYP-001   Stage A Consolidation Report
```

## 4.1 Reading Order

| Order | Document | Role |
|-------|----------|------|
| 0 | **A.0** (this document) | Frames the stage |
| 1 | A.1 — Business Plan | Declares business intent and success criteria |
| 2 | A.2 — Functional Specification | Decomposes intent into eight business functions |
| 3 | A.3 — Capabilities Specification | Decomposes functions into twelve capabilities |
| 4 | A.4 — Capability Contracts | Formalizes each capability's contract |
| 5 | A.5 — Engineering Proposal | Proposes the system that implements the contracts |
| 6 | PH1 — Open Items Register | Cross-cutting register of unresolved external facts |
| 7 | Stage A Consolidation Report | Closes Stage A and authorizes Stage B |

## 4.2 Derivation

Each document derives from the one before it:

```
A.0  →  A.1  →  A.2  →  A.3  →  A.4  →  A.5
                                          │
                                          ▼
                                    Consolidation
                                          │
                                          ▼
                                       Stage B
```

**PH1 is cross-cutting.** It is not derived from any single document and is not a parent of any. It is referenced by all.

---

# 5. Stage A Objective

Stage A has **one engineering objective**:

> **Produce a conceptual baseline sufficient to authorize Stage B (System Architecture).**

That baseline is sufficient when:

1. The business intent is declared (A.1).
2. The business functions are declared (A.2).
3. The business capabilities are declared (A.3).
4. The contracts are formalized (A.4).
5. The engineering proposal is baselined (A.5).
6. All FOM-blocking Open Items are closed (PH1).
7. The consolidation report has audited the pipeline and authorized Stage B.

---

# 6. The Current Cycle — Traction Demonstration

Stage A was **not** produced in a commercial validation cycle. It was produced in a **traction demonstration cycle**, because the temporal window is 5 days (2026-10-07 to 2026-10-12).

## 6.1 What This Cycle Attempts

> **The First Operational Milestone (FOM): produce, validate, publish, and record one Pin end-to-end within the Style Picks internal system.**

The FOM is defined operationally in A.5 §46.

## 6.2 What This Cycle Does Not Attempt

- commercial validation;
- the survival floor (3 qualifying purchases);
- the success target (≥ 5 qualifying purchases);
- building the MVP;
- automating any capability beyond what the FOM requires.

## 6.3 Why

The Amazon Associates survival clock began on 2026-04-15 (OI-001). The deadline is 2026-10-12 (OI-002). The operational start is 2026-10-07. The remaining operating window is **5 days**.

A new Pinterest account cannot accumulate meaningful distribution in 5 days. Commercial validation in this window is arithmetically impossible. The FOM is achievable because it depends only on internal records, one external rule set (closed in PH1), and one manual publication.

> **Validation is deferred to the next cycle, per A.1 §18-A (Decision Frame at Window Close).**

---

# 7. Stage A Documents — Purpose Summary

| Document | Purpose | Version | Status |
|----------|---------|---------|--------|
| **A.0** | Frames Stage A as Basic Engineering; declares the pipeline and closing criteria | 1.0 | Baselined |
| **A.1** | Declares the business, the value proposition, the target, and the success criteria for this cycle and the next | 2.0 | Baselined |
| **A.2** | Declares the eight business functions required to deliver the value proposition | 1.3 | Baselined |
| **A.3** | Declares the twelve business capabilities that execute the functions | 1.3 | Baselined |
| **A.4** | Formalizes each capability's contract (data dictionary, state machines, invariants, error codes) | 1.1 | Baselined |
| **A.5** | Proposes the engineering system that implements the contracts | 1.4 | Baselined |
| **PH1** | Records Open Items and their closure evidence | 1.3 | Baselined |
| **Consolidation** | Audits the pipeline and authorizes Stage B | 1.1 | Pending |

---

# 8. Stage A Closing Criteria

Stage A closes when **all** of the following hold:

1. A.1 through A.5 are baselined.
2. PH1's FOM-blocking Open Items are closed.
3. The pipeline is internally consistent (no contradictions among A.1–A.5).
4. The Engineering Proposal is accepted.
5. The Stage A Consolidation Report is signed.

**Current status:**

| Criterion | Status |
|-----------|--------|
| A.1 baselined | ✅ v2.0 |
| A.2 baselined | ✅ v1.3 |
| A.3 baselined | ✅ v1.3 |
| A.4 baselined | ✅ v1.1 |
| A.5 baselined | ✅ v1.4 |
| FOM-blocking Open Items closed | ✅ OI-003, OI-005, OI-006, OI-007 |
| Internal consistency | ✅ (verified during reconciliation) |
| Consolidation Report | ⏳ Pending |

**Stage A is functionally closed.** The remaining step is the Consolidation Report, which formalizes the closure and authorizes Stage B.

---

# 9. Handoff to Stage B

Stage A hands off to Stage B (System Architecture — HLD).

Stage B must derive:

- the software architecture (modules, services, boundaries);
- the data architecture (storage, schemas, migrations);
- the model architecture (for the automation phases of the next cycle);
- the integration architecture (Pinterest, Amazon, AI providers);
- the deployment architecture (hosting, secrets, backups).

Stage B must **not** redefine:

- business functions (A.2);
- business capabilities (A.3);
- capability contracts (A.4);
- the FOM (A.5 §46);
- the Decision Frame (A.1 §18-A).

If Stage B needs to deviate from any contract, it returns a **Change Proposal** to A.4.

---

# 10. Stage A Is Not the MVP

A frequent confusion must be prevented:

| Concept | Definition | Stage |
|---------|------------|-------|
| **FOM** | One published Pin with a complete internal record trail | Stage A (this cycle) |
| **MVP** | The complete controlled path from Context to Performance, at Levels 1–2 of automation | Stages A–D (next cycle) |
| **Full system** | The private commerce operations platform described in A.5 §5 | Stages A–D (future) |

The FOM is a **subset** of the MVP, executed **manually**. The MVP is the target of the next cycle. The full system is the long-term target.

> **The survival clock binds to the FOM, not to the MVP or the full system.**

---

# 11. Two Clocks

Stage A distinguishes two time references:

| Clock | Definition | Date | Consequence |
|-------|------------|------|-------------|
| **Survival clock** | Amazon Associates account creation + 180 days | 2026-10-12 | If the survival floor is not reached, the account may lapse. |
| **Operating window** | The period in which Style Picks actually publishes content | 2026-10-07 to 2026-10-12 | This is the window in which the FOM must be achieved. |

The two clocks are **not the same**. Stage A is executed against the operating window; the Decision Frame at window close (A.1 §18-A) governs what happens after.

---

# 12. Stage A Principles

1. **Business first.** Functions precede capabilities precede contracts precede engineering.
2. **Contract first.** The engineering proposal does not redefine contracts; it implements them.
3. **Traceability by default.** Every record references its source.
4. **Human accountability.** Automation does not remove ownership.
5. **Evidence-based operation.** Claims trace to sources.
6. **Build time is scarce.** The Engineering Proposal caps build effort (A.5 §32-A).
7. **The FOM is the first deliverable.** No further document is required before execution.

---

# 13. What Comes After Stage A

```
Stage A — Basic Engineering        ✅ CLOSED (pending Consolidation Report)
        │
        ▼
Stage B — System Architecture      ⏳ Next
        │
        ▼
Stage C — Product Specification
        │
        ▼
Stage D — Implementation
```

**Immediate next actions (not documents):**

1. Produce the Stage A Consolidation Report.
2. Authorize Stage B.
3. **Execute the FOM**: verify external rules (closed in PH1), stand up Phase 0, publish the first Pin, log production time, open the Decision Frame.

> **The pipeline is internally consistent. The next action is execution, not further drafting.**

---

# 14. What A.0 Does Not Do

- It does not add engineering content.
- It does not redefine any A.x document.
- It does not replace PH1 or the Consolidation Report.
- It does not declare Stage A closed by itself; the Consolidation Report does that.
- It does not authorize Stage B by itself; the Consolidation Report does that.

A.0 is the **root framing document**. Its function is to be referenced by A.1–A.5 and by PH1 as the declared root of Stage A.

---

# 15. Document Integrity

> **A.0 is the root of the Stage A pipeline.** It declares the pipeline structure, the reading order, the closing criteria, and the handoff to Stage B. It is referenced by all Stage A documents.

If A.0 and any A.x document appear to conflict:

- On **engineering content** → the A.x document governs.
- On **pipeline structure, reading order, or closing criteria** → A.0 governs.

---

## Formal Sign-Off

**Prepared by:** Style Picks Editorial Owner

**Engagement:** STYP-VALIDATION-2026

**Stage:** A — Basic Engineering

**Level:** A.0 — Stage A Framing

**Document ID:** A.0-BASIC-STYP-001

**Version:** 1.0 — Stage A Framing Baseline

**Status:** **Baselined**

**Authorization:** This document is the root of the Stage A pipeline. A.1-BIZ-STYP-001 v2.0 is authorized to derive from it. The Stage A Consolidation Report is authorized to close Stage A and to authorize Stage B.

**Language:** English

---

*End of Stage A — Basic Engineering — A.0-BASIC-STYP-001 v1.0*

---

## Note on the Pipeline

> **This document was missing from the pipeline.** A.1 declared "Parent Documents: None (root document)" — but no document declared the **stage** to which A.1 belongs. A.0 supplies that declaration.
>
> A.1 remains the root of the **commercial and functional** chain. A.0 is the root of the **stage**. They are not in conflict; they operate at different levels.
>
> The pipeline is now complete in form: a framing document (A.0), five engineering documents (A.1–A.5), one cross-cutting register (PH1), and one closing report (Consolidation).