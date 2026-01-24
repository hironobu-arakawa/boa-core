# Flow of Decision

This document illustrates the **order of decision progression** in BOA Core.

This does not show an algorithm.
It only clarifies **"conditions under which decision may proceed" and "conditions under which it must stop".**

---

## Overall Flow (Concept)

Decisions proceed only in the following order:

1. **BOA** (Boundary Check - Where?)
2. **RCA** (Responsibility Acceptance - Who?)
3. **RP**  (Resolution Certification - How to handle?)

This order cannot be changed.

---

## Pseudo-code Representation (Concept)

```pseudo
function decision_flow(input, context):

    // 1. Boundary check (BOA)
    // Is it within the boundary?
    if not BOA.allows(input, context):
        return STOP("Outside allowed boundary")

    // 2. Responsibility Assessment (RCA)
    // Does the agent accept responsibility?
    assessment = RCA.assess(input, context)

    if assessment.state == DENIED:
         return STOP("RCA denied responsibility: " + assessment.reason)
    
    if assessment.state == UNKNOWN:
         return ESCALATE("RCA cannot decide: " + assessment.reason)

    // Proceed only if assessment.state == ACCEPTED

    // 3. Resolution Protocol (RP)
    // Is the acceptance compliant with the protocol?
    resolution = RP.verify_and_promote(assessment)

    if resolution == PROMOTED_TO_RESOLUTION:
        return COMMIT_RESOLUTION(resolution)
    
    else:
        return ROUTE(resolution.routing_instruction)
```

---

## Meaning of Each Step (Important)

### 1. BOA — Boundary Check

```pseudo
if not BOA.allows(input, context):
    STOP
```

BOA is always evaluated first.
`STOP` here is not an error. It is a normal termination meaning "Do not start decision."

### 2. RCA — Responsibility Assessment

```pseudo
assessment = RCA.assess(input, context)
```

RCA indicates its **"intention as an agent"** regarding the input judgment case.

-   **ACCEPTED**: "I take responsibility (sign)."
-   **DENIED**: "I will not judge (reject)."
-   **UNKNOWN**: "I cannot decide (unknown)."

This is a more active step beyond mechanical determination.
Unless RCA nods yes, simple processing will absolutely not proceed.

### 3. RP — Resolution Protocol

```pseudo
resolution = RP.verify_and_promote(assessment)
```

RP inspects the **"legitimacy of the procedure"** for cases where RCA said "I accept (ACCEPTED)".

-   Is there a signature?
-   Are required items filled?
-   Is there authority?

If everything is proper, RP promotes this to **Resolution (Formal Solution)** and finalizes it.
Otherwise, it performs routing such as returning to human (Return).

---

## Invariants guarded by this flow

This structure has the following invariants:

-   Decision does not start without passing BOA.
-   **Decisions not accepted by RCA never reach RP.**
-   RP always returns an explicit result (Resolution or Routing).
-   Decisions belonging to no one cannot exist within the system.

---

## Note on Implementation (Important)

This pseudo-code is not an implementation example.
What is shown here is only:

> **The structure to prevent processing from proceeding while the locus of responsibility remains unclear.**

---

## What to read next

Reason for decision stop and its justification
→ [04_failure_and_stop.md](04_failure_and_stop.md)
