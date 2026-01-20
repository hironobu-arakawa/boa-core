# Overview: What This Architecture Is

BOA Core is **a set of structures for handling decision, responsibility, and stopping in systems involving AI without breaking them.**

This repository is not about "producing the correct answer."
**It exists to "correctly stop when a decision cannot be made."**

---

## This is Not a Framework

BOA / IDG / RP / RCA are not a layered architecture or framework in the general sense.

- They are not layers for dividing processing.
- They are not role assignments for organizing responsibilities.

They are all:

> **"Checkpoints" (Sekisho) that appear along the flow of decision.**

---

## The 4 Included Structures

This BOA Core includes the following four components:

- **BOA (Boundary-Oriented Architecture)**
  Declares the boundary where decisions are allowed.

- **IDG (Interface Determinability Gate)**
  Evaluates whether the state is determinable.

- **RP (Resolution Protocol)**
  Explicitly chooses to proceed, stop, or return the decision.

- **RCA (Responsibility Closure Architecture)**
  Closes and retains the responsibility of the decision.

The important point is that **these do not exist simultaneously.**

---

## Basic Flow of Decision (Summary)

1. The system reaches **BOA**.
2. Advances to **IDG** only if boundary conditions are met.
3. **RP** activates only if IDG indicates "Determinable".
4. RP always returns one of the following:
   - **Resolve** (Decide)
   - **Reject** (Discard)
   - **Return** (Return to human or upstream)
5. **RCA** closes the responsibility for this decision.

---

## What This Design Prioritizes Most

This structure prioritizes neither success rate nor speed.

- Do not leave indeterminability ambiguous.
- Do not eliminate the option to "Stop".
- Leave room for humans to intervene.

BOA Core is **not a design for automating decisions, but a design for protecting decisions from breaking.**

---

## What to Read Next

- Roles and questions of each component
  → `02_components_map.md`

- Reasons for decision stops and their legitimacy
  → `04_failure_and_stop.md`
