# Evidence-Driven Software Evolution

A software engineering methodology built upon a conceptual language for describing software evolution.

## What is EDSE?

EDSE is a methodology that:
- Starts with findings, not fixes
- Requires evidence for every claim
- Preserves architectural integrity
- Measures before and after
- Validates with regression testing
- Maintains complete traceability

EDSE also possesses its own conceptual language defined in the Metamodel.

## Architecture

EDSE is organized in 7 layers:

```
Foundations → Conceptual Model → Principles → Processes → Artifacts → Patterns
                                                                        ↓
                                                                   Templates
```

The Metamodel is the formal definition of all entities and relationships. Reference Architecture is its visual notation.

## Weight Levels

| Level | Content | Change Rules |
|-------|---------|--------------|
| Normative | Foundations, Metamodel, Constraints, Conceptual Model | Governance approval required |
| Recommended | Principles, Processes, Patterns | Evidence from applications |
| Informative | Templates, Artifacts | Free evolution |

## Quick Navigation

| I want to... | Go to |
|--------------|-------|
| Understand EDSE | `v2/foundations/` |
| See the metamodel | `v2/metamodel.md` |
| Learn the entities | `v2/conceptual-model/` |
| See the constraints | `v2/constraints.md` |
| See the principles | `v2/principles/` |
| See the processes | `v2/processes/` |
| View deliverables | `v2/artifacts/` |
| Apply patterns | `v2/patterns/` |
| Use templates | `v2/templates/` |
| See the visual model | `v2/reference-architecture.md` |
| See governance rules | `v2/governance.md` |

## Versions

| Version | Status | Purpose |
|---------|--------|---------|
| `v1/` | Reference | Historical documentation |
| `v2/` | Current | Layered architecture |
