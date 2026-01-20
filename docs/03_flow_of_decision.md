# Flow of Decision

This document shows **the progression order of decisions** in BOA Core.

This is not an algorithm.
It only clarifies **"conditions under which a decision may proceed" and "conditions under which it stops"**.

---

## Overall Flow (Concept)

Decisions proceed only in the following order:

1. **BOA** (Boundary Check)
2. **IDG** (Determinability Check)
3. **RP** (Resolution Choice)
4. **RCA** (Responsibility Closure)

This order cannot be changed.

---

## Pseudo Code Representation (Concept)

```pseudo
function decision_flow(input, context):

    // 1. Boundary check
    if not BOA.allows(input, context):
        return STOP("Outside allowed boundary")

    // 2. Determinability check
    determinability = IDG.evaluate(input, context)

    if determinability == INDETERMINABLE:
        return RETURN("Cannot decide under current conditions")

    // 3. Resolution
    resolution = RP.resolve(input, context)

    if resolution == RESOLVE:
        outcome = apply_decision(input)

    else if resolution == REJECT:
        outcome = discard_decision(input)

    else if resolution == RETURN:
        return RETURN("Decision returned by protocol")

    // 4. Responsibility closure
    RCA.close(outcome, resolution, context)

    return outcome
```

---

## Meaning of Each Step (Important)

### 1. BOA — Boundary Check

```pseudo
if not BOA.allows(input, context):
    STOP
```

BOA is always evaluated first.

`STOP` here is not an error.
It is a normal termination meaning "Do not start decision".

BOA deals with the allowed area of the decision, not the correctness of the decision.

### 2. IDG — Determinability Check

```pseudo
if determinability == INDETERMINABLE:
    RETURN
```

Indeterminable is not a failure.
Indeterminable is a reason to "Return".

RP is not activated here.

Proceeding with a decision while IDG does not pass is a violation of design.

### 3. RP — Resolution

```pseudo
resolution = RP.resolve(...)
```

RP does not calculate the decision result.
What RP decides is "How to treat this decision".

The value RP can return is always one of the following:

**RESOLVE | REJECT | RETURN**

Silence, implication, and defaults do not exist.

### 4. RCA — Responsibility Closure

```pseudo
RCA.close(outcome, resolution, context)
```

RCA does not evaluate the success or quality of the decision.

What RCA does is to record:

- Whose responsibility is this decision?
- Which decision was made under what conditions?
- How far was automatic and from where was human?

## Invariants Protected by This Flow

This structure has the following invariants:

- Decision creates not start without passing BOA
- RP does not activate without passing IDG
- RP always returns an explicit result
- A decision not passing RCA "does not exist"

## Note for Implementation (Important)

This pseudo code is not an implementation example.

- Sync / Async is not specified
- Exception handling method is not specified
- Language / Framework is not assumed

What is shown here is only:

> **The flow that must be protected so that the decision does not break.**

## What to Read Next

Reasons why a decision stops, and its legitimacy
→ [04_failure_and_stop.md](04_failure_and_stop.md)
