# BOA (Boundary-Oriented Architecture)

**BOA (Boundary-Oriented Architecture)** is a construction method for systems that **must sustain boundary-related decisions over the long term**.

BOA is applied **after architectural decisions have already been made**.
It transforms those decisions into system structure **without collapsing meaning (Meaning), responsibility (Responsibility), or human judgment (Judgment)**.

BOA does not decide "what should be built".
BOA defines "how to build" **without destroying decisions already made**.

---

## Position

BOA is positioned **between Decision and Implementation**.

- **VCDesign** defines *where judgment belongs*, and *what must not be fixed*
- **BOA** defines *how to build systems that maintain those boundaries*

Therefore, BOA is not philosophical but **methodological**.

---

## What is BOA

BOA is a construction method focused on:

- System structure that maintains boundaries
- **Explicit separation** of fact (Fact), meaning (Meaning), and responsibility (Responsibility)
- Viability under operational and organizational change
- Traceability of judgment ownership
- Safe integration of automation and AI

BOA is applied to systems where:

- Operations continue long after deployment
- Responsibility must be auditable
- Meaning may drift (drift) over time
- Automation must not inadvertently absorb judgment

---

## What BOA is NOT

BOA does **not** provide:

- Reference implementations
- Technology stacks
- Templates or blueprints
- Best practices
- Product recommendations

BOA does not optimize for speed or convenience.
BOA optimizes for **long-term correctness under change**.

---

## Core Separation

BOA enforces three strict separations:

### Fact
Immutable observations and records.

### Meaning
Contextual interpretation that may change over time.

### Responsibility
Human-owned judgment and its consequences.

These elements may interact,
but **must not collapse (conflate) with each other**.

---

## Positioning of AI

BOA is **AI-compatible**, not AI-driven.

AI **can**:

- Propose interpretations
- Generate hypotheses
- Surface inconsistencies
- Enumerate tradeoffs

AI **must not**:

- Make final decisions
- Own responsibility
- Overwrite facts
- Quietly escalate meaning to responsibility

All escalations require **explicit human resolution**.

---

### IDG: Interface Determinability Gate

In BOA,  
**capability (Capability) does not mean determinability (Determinability).**

Just because a system can infer a state does not mean  
it is permissible to use it in judgment.

BOA defines, as a boundary pattern to address this problem,  
**IDG (Interface Determinability Gate)**.

---

### Principles IDG Protects

- **Determinability over capability**  
  Unless a state can be determined deterministically  
  from an interface or authenticated sensing,  
  AI must not infer or assume it.

- **Explicit Detachment**  
  When determinability is not met,  
  AI must **explicitly detach** from decision support.

Expressions like "maybe", "probably", "usually"  
are explicitly prohibited in boundary design.

In IDG, silence is not failure.  
It is **a normal result of maintaining boundaries**.

---

### Position within BOA

IDG is  
one of the **boundary patterns (Boundary Pattern)** in BOA,

existing to:

- Not make judgments itself
- Only determine the conditions under which judgment is appropriate

([Reference: determinability_gate.yaml](./patterns/idg/determinability_gate.yaml))

---

## RP: Resolution Protocol

**Meaning (Meaning)** can escalate to **resolution (Resolution / Judgment)** only after passing through **RP (Resolution Protocol)**.

Resolution is not a meaningful computation result. It is a **structural interlock**.
It requires:

- **Structural check**: Has this escalation passed pre-judgment interlock?
- **Responsible actor**: Has a human explicitly accepted ownership?
- **Recorded action**: Is the act of judgment traceable?

Automation systems may propose *interpretation (Interpretation)*,
but must not auto-escalate it to *resolution (Resolution)* without passing through RP.

([Reference: BOA_RP_DEFINITION.yaml](./patterns/rp/BOA_RP_DEFINITION.yaml))

---

## When to Use BOA

BOA is used when:

- Implementing architecture derived from VCDesign
- Converting boundary decisions into permanent system structure
- Introducing automation or AI to operational systems
- Building systems that must maintain explainability over the long term

BOA is often recognized **after failure**:

- When responsibility becomes unclear
- When meaning drifts between teams
- When change makes the system brittle

In such cases, BOA helps **reconstruct where boundaries collapsed**.

---

## Relationship with VCDesign

VCDesign and BOA are intentionally separated.

- **VCDesign**
  Determines *what must be decided*, *where judgment belongs*

- **BOA**
  Determines *how to build systems that respect those decisions*

BOA does not override VCDesign.
BOA makes VCDesign **operationalizable**.

---

## Repository Scope

This repository contains:

- BOA's structural principles
- Construction rules that maintain boundaries
- Patterns derived from VCDesign decisions

It does **not** contain implementations.

Bindings, UI signals, and operational tools  
belong in **separate repositories**.

---

## Finally

If you are looking for:

- Which technologies to choose
- How to optimize performance
- How to automate decisions

BOA is **not the right tool**.

If you are trying to ensure that **decisions remain valid even as systems change**,
BOA is designed for that purpose.
