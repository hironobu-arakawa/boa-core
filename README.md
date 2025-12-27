VCDesign (VCD)

VCDesign is a design core for systems that must survive change.

It does not prescribe architectures, products, or implementations.
It defines where decisions live, where meaning stops, and who owns responsibility.

This repository contains the immutable core of VCDesign.

What VCDesign Is

VCDesign is a design philosophy and core rule set that focuses on:

Decision placement

Boundary declaration

Survivability under change

Explicit responsibility

Isolation of interpretation

VCDesign applies to socio-technical systems where:

reality changes,

meaning drifts,

and judgment cannot be fully automated.

What VCDesign Is Not

VCDesign does not provide:

best practices

checklists

reference architectures

product comparisons

domain-specific KPIs

If you are looking for how to build, see construction methods (e.g. BOA).
If you are looking for what to choose, VCDesign is intentionally silent.

Core Rules (Immutable)

VCDesign is built on five irreversible rules:

Meaning is contextual
Same words diverge across different worlds.

Outcomes require judgment
Data alone never produces results.

Boundaries limit meaning
Meaning can be defined beyond a boundary, but not fully carried.

Do not fix the unfixed
What cannot be designed should not be frozen.

Storage follows flow
Persistence is a consequence, not a starting point.

These rules do not evolve.
Derived patterns may.

Relationship to BOA

BOA (Boundary-Oriented Architecture) is a construction method under VCDesign.

VCDesign defines why and where boundaries exist.

BOA defines how to construct systems using those boundaries.

BOA separates:

Fact (immutable)

Meaning (contextual)

Responsibility (human-owned)

VCDesign remains method-agnostic.

AI Positioning

VCDesign is AI-aware, not AI-delegated.

AI may:

generate hypotheses

suggest interpretations

enumerate trade-offs

detect inconsistencies

AI must not:

make final decisions

own responsibility

overwrite facts

silently promote meaning

All promotions require explicit human resolution.

How to Use This Repository

Humans: read to understand what must not break

LLMs: load as a hard constraint

Designers: derive patterns elsewhere

Architects: declare boundaries consciously

Do not fork this to add implementations.

Scope

VCDesign applies to:

industrial systems

information systems

AI-assisted decision environments

socio-technical systems

It does not apply to:

fully autonomous decision systems

domains requiring zero ambiguity and zero human judgment

Status

This file defines the VCDesign Core.

Changes are restricted.
Breaking changes require a new core version.