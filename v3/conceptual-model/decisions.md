# Conceptual Model — Decisions

**Weight**: Normative

## Entity

**Decision**: An accepted choice with justification and consequences.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | D-XXX format |
| Type | enum | Operational / Technical / Architectural |
| Status | enum | Pending / Accepted / Deferred / Rejected |
| Justification | string | Why this decision |
| Consequences | string | What this means going forward |

## Types

### Operational
Process changes, workflow adjustments.
Documentation: Decision record.

### Technical
Library choices, implementation approaches.
Documentation: Decision record.

### Architectural
System-wide design choices.
Documentation: ADR Document.

## Relationships

- **basedOn** → Candidate Decision (1:1)
- **documentsAs** → ADR Document (1:0..1)
- **implementsAs** → Implementation (1:0..N)
- **defersAs** → Technical Debt (1:0..N)
- **freezesAs** → Baseline (N:1)

## States

```
Pending → Accepted / Deferred / Rejected
```

## Rules

- Every Decision MUST originate from a Candidate Decision
- Every Architectural Decision MUST have an ADR Document
- Every Decision MUST reference its justification
