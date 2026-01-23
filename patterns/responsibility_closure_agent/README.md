# RCA Pattern
Responsibility Closure Agent

---

## Role of This Directory

`patterns/rca` is a **set of patterns for defining "where, by whom, and under what conditions responsibility is accepted" in a machine-readable and operational form.**

The RCA (Responsibility Closure Agent) defined here deals with:

- Not about improving AI performance
- Not about raising decision accuracy

It deals with **the structure for "closing" decisions.**

---

## What is RCA (Briefly)

RCA is an entity that satisfies the following:

- **Signs** the result of the decision
- The scope that can be signed is **explicitly limited**
- **Stops** if it cannot sign

In other words, RCA is:

> **Not an "Advancing AI"**
> **But a "Stoppable AI (or Human)"**

---

## Why RCA is Necessary

With Generative AI:

- Trial and error became faster
- Changes became easier
- "GO" became lighter

On the other hand, the following are increasing:

- Changes where it is unknown who accepted them
- Decisions where responsibility cannot be identified later
- Results that proceeded "somehow"

To prevent this, RCA:

- **Converts decisions into signatures**
- **Fixes the locus of responsibility as a structure**
- **Rejects decisions that cannot be closed**

---

## Relationship with IDG (Important)

This directory is the **upper layer** of `patterns/idg`.

- **IDG (Interface Determinability Gate)**
  → Boundary determining "Is it okay to decide?"

- **RCA (Responsibility Closure Agent)**
  → Subject determining "Is it okay to accept?" and signing

The relationship is as follows:

```
[ Generator (Creating AI) ]
↓
[ IDG ]
(Determinable?)
↓
[ RCA ]
(Acceptable?)
↓
[ CCP Signature / Stop ]
```

**Models under IDG cannot cross IDG.**
RCA operates only assuming the result of IDG.

---

## Directory Structure

```
patterns/rca/
├── RCADelagtion.yaml
└── human_protocol.ja.md
```

### RCADelagtion.yaml
- **Constitution defining RCA in a machine-readable way**
- Includes scope, AST constraints, risk budget, signing authority
- Completely fixes "what can be done and what cannot make be done"

### human_protocol.ja.md
- Rules on **how humans operate RCA**
- Defines exception handling, idk-lamp lighting, stop conditions
- Document to eliminate emotions, customs, and dependent judgments

---

## What This Pattern Does Not Handle

The RCA pattern does not aim to:

- Make AI smarter
- Raise decision accuracy
- Make it produce the correct answer

It always deals only with:

> **"Who accepts responsibility for that decision?"**

---

## When to Use RCA

When you see the following signs, it is time for RCA:

- idk-lamp lights up frequently
- Revert has become "work"
- Reason for decision cannot be explained later
- "GO for now" has become normalized

---

## Summary in One Sentence

> **RCA is a pattern for pushing the undefined use world out to a world acceptable as use.**

---

## What to Read Next

1. `patterns/idg/README.ja.md`
2. `patterns/rca/human_protocol.ja.md`
3. VCDesign Narrative / idk-lamp Narrative

---

This pattern is not a finished form.
**The moment responsibility is accepted, the next uncertainty begins.**

RCA is placed to rotate that loop without breaking it.
