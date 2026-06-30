# EDSE Reference Architecture

**Weight**: Normative

## Purpose

Visual notation of the EDSE metamodel. This is one of three views of the same truth:

```
                    Metamodel
                  (formal truth)
                    /        \
                   /          \
      Conceptual Model     Reference Architecture
   (textual definition)     (visual notation)
```

## Conceptual Diagram

```
                    FOUNDATIONS
                         │
                         ▼
                 CONCEPTUAL MODEL
                         │
           ┌─────────────┴─────────────┐
           │                           │
           ▼                           ▼
      PRINCIPLES                   PROCESSES
           │                           │
           └─────────────┬─────────────┘
                         ▼
                   Evidence Package
                         │
                         ▼
               Candidate Decisions
                         │
                         ▼
                Accepted Decisions
                         │
                   ┌─────┴─────┐
                   ▼           ▼
            Operational   Technical
                   │           │
                   └─────┬─────┘
                         ▼
                  Architectural
                         │
                         ▼
                  ADR Document
                         │
                   ┌─────┴─────┐
                   ▼           ▼
             Implementation  Baseline Freeze
                   │           │
                   └─────┬─────┘
                         ▼
                   Health Report
                         │
                         ▼
               Governance Feedback
                         │
                         └────────► Next Iteration
```

## Layer Architecture

```
┌─────────────────────────────────────────────────────────┐
│                      TEMPLATES                           │
│              (Minimal structures)                        │
├─────────────────────────────────────────────────────────┤
│                      PATTERNS                            │
│              (Reusable scenarios)                        │
├─────────────────────────────────────────────────────────┤
│                      ARTIFACTS                           │
│              (Documentary representations)               │
├─────────────────────────────────────────────────────────┤
│                     PROCESSES                            │
│              (Behavior patterns)                         │
├─────────────────────────────────────────────────────────┤
│                     PRINCIPLES                           │
│              (Methodological rules)                      │
├─────────────────────────────────────────────────────────┤
│                   CONCEPTUAL MODEL                       │
│              (Entities and relationships)                │
├─────────────────────────────────────────────────────────┤
│                    FOUNDATIONS                            │
│              (Axioms that never change)                  │
└─────────────────────────────────────────────────────────┘

                    CONSTRAINTS
              (Invariant requirements)
```

## Dependency Rules

Each layer depends only on the layer below:

```
Templates → Patterns → Artifacts → Processes → Principles → Conceptual Model → Foundations
```

Never the reverse. Foundations never says "as defined in Processes".

## Weight Levels

| Level | Content | Change Rules |
|-------|---------|--------------|
| Normative | Foundations, Metamodel, Constraints, Conceptual Model, Reference Architecture | Governance approval required |
| Recommended | Principles, Processes, Patterns | Evidence from applications |
| Informative | Templates, Artifacts | Free evolution |

## Entity-Relationship Diagram

```
Research Question ──── operationalizes ────► Assessment Goal
        │                                           │
        │ originates                               │ collects
        ▼                                           ▼
    Finding ◄────────── supports ──────────── Evidence
        │
        │ feeds into
        ▼
Candidate Decision
        │
        │ accepted as
        ▼
    Decision ─────┬──── documents as ────► ADR Document
                  │
                  ├── implements ────► Implementation
                  │
                  ├── defers as ────► Technical Debt
                  │
                  └── freezes as ────► Baseline
                                          │
                                          │ generates
                                          ▼
                                    Health Report
                                          │
                                          │ feeds into
                                          ▼
                                  Research Question (new iteration)
```
