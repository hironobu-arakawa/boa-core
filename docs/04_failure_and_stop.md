# Failure, Stop, and Return

This document explains **how BOA Core handles "Failure" and "Stop".**

Failure here refers not to exception handling or error handling.

---

## What is "Failure" in This Design?

In BOA Core,
the failure to be avoided most is the following state:

> **Proceeding with a decision even though it cannot be decided.**

- Lacking information
- Broken context
- Changed prerequisites
- Ambiguous locus of responsibility

It is a "failure" in this design that a decision is made under these conditions.

---

## Stop is Not Abnormal

In BOA Core,
**Stop is a normal system**.

### Stop in BOA

- Boundary conditions not met
- Entered an area where decisions are not allowed

In this case,
the decision **is not started**.

This is neither rejection nor failure, but **termination as designed**.

---

## Return is a Responsible Action

Return returned by IDG or RP is not an abandonment of decision.

What Return means is:

- Cannot decide now
- Should not decide under these conditions
- Should return to human or design

This is an **explicit declaration of intent**.

Return is a regular route to "not hide indeterminability".

---

## Why "Silence" is Not Allowed

In BOA Core,
the following states are explicitly prohibited:

- Return nothing
- Implicitly regard as success
- Log failure but proceed

Silence makes it unclear whether a decision was made.

Unclear decisions **erase responsibility.**

Therefore, RP always has only one of the following:

```
RESOLVE | REJECT | RETURN
```

### Indeterminable is Not "Lack of Ability"

The reason IDG returns Indeterminable is not necessarily a lack of AI ability.

- Inputs are not complete
- Context is temporally broken
- Prerequisites differ from design time
- Responsibility boundary is unclear

These are problems that cannot be solved no matter how smart the model is.

BOA Core chooses a design that "does not try hard to solve" them.

## Why a Design That Stops is Necessary

Systems including AI tend to be evaluated for keeping moving.

However, in systems handling decisions,

- Moving fast
- Deciding a lot
- Automating

is less important than

> **Being able to stop correctly.**

BOA Core fixes this value as a structure.

## Relationship Between Responsibility and Stop

When a decision stops,
RCA leaves the following:

- Why it stopped
- Where it stopped
- Who stopped it (Human / AI / Design)

By this,
stopping becomes not a "failure" but material for the next decision.

## Summary

- Stop is not abnormal
- Return is a responsible decision
- Do not hide indeterminability
- Silence is not allowed
- **Being able to stop is safe**

BOA Core is **not a design for advancing decisions, but a design for not breaking decisions.**

## What to Read Next

How to make AI read this structure
→ [99_for_ai_readers.md](99_for_ai_readers.md)
