# Components Map

This document is **not a material for comparing or classifying** the elements that make up BOA Core.

What is done here is **to clarify "what question each exists to answer."**

---

## Overview: The 4 are "Checkpoints", not "Roles"

BOA / IDG / RP / RCA are not groups of roles for dividing tasks.

They are all designed as **"Checkpoints" that must be passed as the decision proceeds.**

- They do not exist simultaneously.
- They cannot be skipped.
- Their order cannot be swapped.

---

## BOA — Boundary-Oriented Architecture

**Question:
"From here on, is it okay for AI to decide?"**

BOA is the checkpoint that appears first.

What BOA does is not to evaluate the correctness of the decision.

- Is it the correct answer? ❌
- Is the accuracy sufficient? ❌
- Is it efficient? ❌

BOA looks at only one thing:

> **Has this decision entered meaning "Area" where it may be entrusted to AI?**

BOA defines **"the place where decision is allowed"**, not the "possibility of decision".

---

## IDG — Interface Determinability Gate

**Question:
"Is this input in a state where it can be decided now?"**

IDG appears only after passing BOA.

What IDG evaluates is not the performance or intelligence of the model.

- Accuracy ❌
- Amount of learning ❌
- Past track record ❌

What IDG looks at is:

> **Are inputs, context, and prerequisites complete?**

IDG returns one of the following:

- **Determinable** (Decision possible)
- **Indeterminable** (Decision impossible)

What determines here is that **Indeterminable is not an error.**

---

## RP — Resolution Protocol

**Question:
"How to treat this decision?"**

RP activates only when IDG returns "Determinable".

The role of RP is not to calculate the decision result.

What RP does is **to explicitly choose how to handle the decision.**

The result RP returns is always one of the following:

- **Resolve**
  Finalizes the decision and proceeds.

- **Reject**
  Discards the decision and does not adopt it.

- **Return**
  Returns the decision to a human or upstream design.

There is no option for RP to "remain silent".

---

## RCA — Responsibility Closure Architecture

**Question:
"Where does the responsibility for this decision remain?"**

RCA is the checkpoint that appears last.

RCA does not participate in the result of the decision itself.

What RCA does is:

> **Simply clarify whose responsibility this decision remains as.**

- Human?
- AI?
- Design?
- Organization?

By RCA, the decision does not "end", but comes to **"persist"**.

---

## Why All 4 Are Necessary

Without BOA,
AI intrudes into places where it should not decide.

Without IDG,
Indeterminability turns into failure in silence.

Without RP,
Decisions are finalized arbitrarily.

Without RCA,
Decisions vanish without belonging to anyone.

BOA Core **is established only when all of these are present.**

---

## What to Read Next

- How decisions flow and where they stop
  → `03_flow_of_decision.md`

- Meaning of indeterminable, stop, and unwind
  → `04_failure_and_stop.md`
