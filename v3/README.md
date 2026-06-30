# Evidence-Driven Software Evolution

**Version**: 2.0
**Status**: Architecture (Normative/Recommended/Informative)
**Developed through**: SIGES Project (SPEC-001 through SPEC-005)

---

> EDSE is a software engineering methodology built upon a conceptual language for describing and governing software evolution.

---

## What Is This?

A methodology for evolving software systems with evidence, traceability, and architectural control. It governs **how to decide** what to do and **how to prove** it was done right.

Unlike process frameworks (Scrum, Kanban), this methodology focuses on **engineering decisions** — not project management.

EDSE also possesses its own conceptual language defined in the Metamodel.

## What This Is NOT

- Not Scrum, Kanban, or project management
- Not a software architecture (DDD, Clean Architecture)
- Not a testing framework (TDD, BDD)
- Not a coding standard

**It complements them.** It adds evidence-based governance to whatever process you use.

## When to Use

**Best suited for:**
- Legacy modernization
- Large refactoring
- Production hardening
- Technical debt reduction
- Compliance projects
- AI-assisted development
- Long-lived systems

**Probably unnecessary for:**
- Weekend hacks
- Throwaway prototypes
- Simple CRUD apps

---

## Architecture

EDSE is organized in 7 layers:

```
Foundations → Conceptual Model → Principles → Processes → Artifacts → Patterns
                                                                        ↓
                                                                   Templates
```

The **Metamodel** is the formal definition of all entities and relationships. **Reference Architecture** is its visual notation.

## Weight Levels

| Level | Content | Change Rules |
|-------|---------|--------------|
| **Normative** | Foundations, Metamodel, Constraints, Conceptual Model | Governance approval required |
| **Recommended** | Principles, Processes, Patterns | Evidence from applications |
| **Informative** | Templates, Artifacts | Free evolution |

---

## Documentation Structure

```
v2/
├── foundations/              # Axioms that never change
├── metamodel.md             # Formal entity-relationship definition
├── conceptual-model/        # Entity documentation
├── constraints.md           # Invariant requirements
├── principles/              # Methodological rules
├── processes/               # Behavior patterns
├── artifacts/               # Documentary representations
├── patterns/                # Reusable scenarios
├── templates/               # Minimal structures
├── reference-architecture.md # Visual notation
└── governance.md            # Rules for EDSE itself
```

| Document | Purpose | Weight |
|----------|---------|--------|
| **SKILL.md** | Entry point — quick navigation | — |
| **metamodel.md** | Formal definition of entities and relationships | Normative |
| **constraints.md** | Invariant requirements (MUST rules) | Normative |
| **foundations/** | Philosophy, vocabulary, scope | Normative |
| **conceptual-model/** | Entity documentation | Normative |
| **principles/** | Methodological rules | Recommended |
| **processes/** | Assessment, Evolution, Validation, Governance, Baseline | Recommended |
| **patterns/** | GoF-style reusable scenarios | Recommended |
| **artifacts/** | Evidence Package, Release Report, etc. | Informative |
| **templates/** | Minimal structures | Informative |
| **governance.md** | Rules for EDSE itself | Normative |

---

## Quick Navigation

| I want to... | Go to |
|--------------|-------|
| Understand EDSE | `v2/foundations/` |
| See the metamodel | `v2/metamodel.md` |
| Learn the entities | `v2/conceptual-model/` |
| See the constraints | `v2/constraints.md` |
| See the principles | `v2/principles/` |
| See the processes | `v2/processes/` |
| Apply patterns | `v2/patterns/` |
| Use templates | `v2/templates/` |
| See the visual model | `v2/reference-architecture.md` |

---

## Real-World Results

EDSE was validated through five specifications of the SIGES medical system:

| SPEC | Type | Result |
|------|------|--------|
| SPEC-001 | Validation | 85/85 tests PASS |
| SPEC-002 | Stabilization | 79 tasks, 5 ADRs |
| SPEC-003 | Architectural Refactoring | 1086→166 lines |
| SPEC-004 | Dependency Modernization | 88 packages, -81% vulnerabilities |
| SPEC-005 | Frontend Assessment | 94 tasks, Evidence Package v1.0 |

**Total**: 38 Mermaid diagrams, 11 ADRs, complete traceability from finding to release.

---

## Governance

EDSE applies to itself:

> **Modifications to the Metamodel require evidence obtained from multiple independent applications of EDSE. No change to the conceptual core may be introduced solely by design preference.**

### Version Strategy

| Version | Strategy |
|---------|----------|
| EDSE v2.0 | Freeze conceptual architecture. Only minor corrections. |
| EDSE v2.x | Validate through real applications. Collect evidence. |
| EDSE v3.0 | Only if evidence justifies. Changes to metamodel. |

---

## Learn More

- **SKILL.md**: Entry point with quick navigation
- **v2/metamodel.md**: Formal definition of EDSE entities
- **v2/reference-architecture.md**: Visual notation
- **v2/governance.md**: Rules for EDSE itself

---

*Version 2.0 — A methodology with its own conceptual language.*
*Developed through evidence, not theory.*
