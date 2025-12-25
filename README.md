# BOA — Boundary-Oriented Architecture

BOA (Boundary-Oriented Architecture) is an architecture core
for separating **Fact**, **Meaning**, and **Responsibility**
by explicitly declaring boundaries.

This repository is **not a software library**.
It is a **design authority** intended to be read by humans and LLMs.

---

## Start Here

The authoritative definition of BOA is:

→ **`boa_core.yaml`**

If you are confused, paste this file into your LLM.

---

## What BOA Is

- A way to prevent silent meaning drift
- A way to keep responsibility human-owned
- A way to design systems assuming AI (including Personal AI) exists

BOA assumes:
- Facts are immutable
- Meanings are contextual
- Responsibility cannot be automated

---

## What BOA Is Not

BOA does NOT:
- Define business logic
- Replace human judgment
- Automate responsibility
- Guarantee correctness or optimization

---

## Structure

```text
boa_core.yaml        # Immutable core (Single Source of Truth)
bindings/            # Domain-specific boundary bindings
examples/            # Minimal examples showing boundary behavior
