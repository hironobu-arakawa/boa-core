# Interface Determinability Gate (IDG)
— BOA Boundary Pattern —

Interface Determinability Gate (IDG) is  
**a boundary pattern within Boundary-Oriented Architecture (BOA)**.

IDG defines  
a **Determinability gate** that determines whether  
**AI or automation is permitted to participate in decision-making**.

---

## Position within BOA

BOA is an architecture for organizing:

- Where boundaries should be placed
- What those boundaries protect
- What happens when boundaries are crossed

IDG is responsible for:

> **"At this boundary point, is AI permitted to participate in decision-making?"**

IDG does not make decisions.  
**It only determines whether the conditions for decision-making are appropriate**.

---

## Boundaries that IDG Handles

IDG directly handles two boundaries:

- **Primary Boundary: Responsibility**
- **Secondary Boundary: Interpretation**

To prevent AI from participating in decisions when these boundaries are ambiguous,  
IDG uses **Determinability** as its sole criterion.

---

## Determinability

Determinability in IDG means:

> **The ability to assert a state definitively using only  
> observable facts at the interface, or authenticated signals,  
> without physical assumptions or inferences.**

High capability or  
past heuristic experience  
does not serve as grounds for determinability.

---

## Basic Gate Operation

IDG performs only the following binary judgment:

- **Pass**
  - Determinability requirements are met
  - AI is permitted to participate in information presentation and decision support

- **Block (Detach)**
  - Determinability requirements are not met
  - AI refrains from decision support

This judgment is never made based on  
"probability" or "likelihood".

---

## AI Detachment (Silence) is a Design Outcome

In IDG,  
**AI's silence (Detachment) is not a failure.**

- Making judgment incapability explicit
- Returning the decision to humans
- With explainable reasoning for why

This state itself is  
**a designed outcome**.

---

## Option: Routing Annotations

In some environments:

- Evidence quality is mixed
- Input channel trust levels differ
- Review costs need to be stratified

IDG permits the attachment of **non-normative annotations**  
to gate outputs in such cases.

Examples:

- `source_method`
- `interaction_type`
- `evidence_ref`
- `quality_band`

These **do not alter the judgment result**.  
They are used only for routing decisions downstream (in RP, etc.).

---

## Relationship with Domain Profiles

IDG is a **domain-independent** boundary pattern.

In the `profiles/` directory,

- Factory
- Healthcare
- Finance
- Public Sector
- Personal AI

domain vocabularies are mapped to the **interface concepts**  
that IDG handles.

This maintains:

- Common core logic
- Consistent boundary judgment
- Separated specialization

---

## Relationship with VCDesign / RP

- **VCDesign**  
  Top-level philosophy and constitution treating judgment and responsibility as design subjects

- **BOA**  
  Architecture for organizing boundary placement and roles

- **IDG**  
  Gate pattern for determining "judgment feasibility" at boundary points

- **RP (Resolution Protocol)**  
  Procedure for formally returning to humans  
  those events determined by IDG to be non-determinable

IDG functions within BOA as  
**a structure for halting judgment**.

---

## Related Files

- Gate Definition  
  `patterns/idg/determinability_gate.yaml`

- Domain Profiles  
  `patterns/idg/profiles/`

- Schemas  
  `patterns/idg/schemas/`

---

## Key Points (For Designers)

- IDG does not judge
- IDG does not infer
- IDG does not optimize

IDG guarantees only one thing:

> **The conditions for judgment to be appropriate  
> are structurally protected.**

---

## The One-Line Principle

> **If something cannot be determined deterministically,  
> do not have AI imagine it.**
