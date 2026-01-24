# Overview: What This Architecture Is

BOA Core is **a set of structures for handling decision, responsibility, and stopping in systems involving AI without breaking them.**

This repository is not about "producing the correct answer."
**It exists to "correctly stop when a decision cannot be made."**

---

## This is Not a Framework

BOA / RCA / RP are not a layered architecture or framework in the general sense.

- They are not layers for dividing processing.
- They are not role assignments for organizing responsibilities.

They are all:

> **"Checkpoints" (Sekisho) that appear along the flow of decision.**

---

## The 3 Included Structures

This BOA Core includes the following three components:

- **BOA (Boundary-Oriented Architecture)**
  Declares the boundary where decisions are allowed.

- **RCA (Responsibility Closure Agent)**
  Takes responsibility for and completes the decision.

- **RP (Resolution Protocol)**
  Explicitly chooses to proceed, stop, or return the decision.

The important point is that **these do not exist simultaneously.**

---

## Basic Flow of Decision (Summary)

1. The system reaches **BOA**.
2. **RCA** performs an Assessment (Evaluation of willingness to take responsibility).
3. **RP** activates only if RCA indicates "Accepted".
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
