# BOA (Boundary-Oriented Architecture)

**BOA (Boundary-Oriented Architecture)** is a construction method for systems that must
preserve **boundary decisions over time**.

BOA is applied **after architectural judgments have already been made**.
It translates those judgments into system structures **without collapsing meaning,
responsibility, or human judgment**.

BOA does not decide *what* should be built.  
It defines *how* to build **without breaking the decisions already made**.

---

## Positioning

BOA sits **between decision and implementation**.

- **VCDesign** defines *where judgment belongs* and *what must not be fixed*
- **BOA** defines *how to construct systems that preserve those boundaries*

BOA is therefore **methodological**, not philosophical.

---

## What BOA Is

BOA is a construction method that focuses on:

- Boundary-preserving system structures
- Explicit separation of **Fact**, **Meaning**, and **Responsibility**
- Survivability under operational and organizational change
- Traceable ownership of judgment
- Safe integration of automation and AI

BOA applies to systems where:

- operation continues long after deployment
- responsibility must remain auditable
- meaning may drift over time
- automation must not silently absorb judgment

---

## What BOA Is Not

BOA does **not** provide:

- reference implementations
- technology stacks
- templates or blueprints
- best practices
- product recommendations

BOA does not optimize for speed or convenience.  
It optimizes for **long-term correctness under change**.

---

## Core Separation

BOA enforces a strict separation between:

### Fact
Immutable observations and records.

### Meaning
Contextual interpretation that may change over time.

### Responsibility
Human-owned judgment and consequence.

These elements may interact,  
but **must not collapse into each other**.

---

## AI Positioning

BOA is **AI-compatible**, not AI-driven.

AI **may**:

- propose interpretations
- generate hypotheses
- surface inconsistencies
- enumerate trade-offs

AI **must not**:

- make final decisions
- own responsibility
- overwrite facts
- silently promote meaning into responsibility

All promotions require **explicit human resolution**.

---

## IDG: Determinability Guardrail

In BOA, capability does not imply determinability.
Just because a system *can* infer a state does not mean it *should*.

BOA enforces the **IDG (Interface Determinability Gate)** pattern:

- **Determinability over Capability**:
  If a state cannot be deterministically asserted from the interface or certified sensing,
  AI must not infer or assume it.
- **Explicit Detachment**:
  In such cases, the system must **detach** from decision support.
  "Likely", "Probably", or "Usually" are explicitly disallowed.

Silence in IDG is not a failure. It is a **boundary-preserving outcome**.

([Reference: BOA_IDG_DEFINITION.yaml](./BOA_IDG_DEFINITION.yaml))

---

## RP: Resolution Protocol

**Meaning** may only be promoted to **Resolution** (Judgment) through the **RP (Resolution Protocol)**.

Resolution is not a meaningful calculation; it is a **structural interlock**.
It requires:

- **Structural Check**: Does this promotion pass the pre-decision interlock?
- **Responsible Actor**: Is a human explicitly accepting ownership?
- **Recorded Act**: Is the act of judgment traceable?

Automated systems may propose *Interpretation*,
but they must never auto-upgrade it to *Resolution* without passing RP.

([Reference: BOA_RP_DEFINITION.yaml](./BOA_RP_DEFINITION.yaml))

---

## When to Use BOA

BOA is used when:

- implementing architectures derived from VCDesign
- translating boundary decisions into durable system structure
- introducing automation or AI into operational systems
- building systems that must remain explainable over time

BOA is often recognized **after failure**:

- when responsibilities become unclear
- when meaning drifts across teams
- when systems become brittle under change

In such cases, BOA helps reconstruct **where boundaries collapsed**.

---

## Relationship to VCDesign

VCDesign and BOA are intentionally separated.

- **VCDesign**  
  Determines *what must be decided* and *where judgment belongs*

- **BOA**  
  Determines *how to construct systems that honor those decisions*

BOA does not override VCDesign.  
It **operationalizes** it.

---

## Repository Scope

This repository contains:

- BOA structural principles
- boundary-preserving construction rules
- patterns derived from VCDesign judgments

It does **not** contain implementations.

Bindings, UI signals, and operational tooling
belong to **separate repositories**.

---

## Final Note

If you are looking for:

- what technology to choose
- how to optimize performance
- how to automate decisions

BOA is **not** the right tool.

If you are trying to ensure that **decisions remain valid after systems change**,  
BOA is designed for that purpose.
