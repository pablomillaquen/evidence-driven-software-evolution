# Conceptual Model — Candidate Decisions

**Weight**: Normative

## Entity

**Candidate Decision**: An intermediate step between evidence and acceptance.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | CD-XXX format |
| Priority | enum | P1 (Must-decide) / P2 (Should-decide) / P3 (Could-decide) |
| Status | enum | Pending / Accepted / Deferred / Rejected |
| Rationale | string | Why this decision is proposed |

## Relationships

- **basedOn** → Finding (N:1)
- **requires** → Evidence (N:M)
- **acceptedAs** → Decision (1:1)

## Purpose

Prevent mixing observations with solutions. The baseline does NOT propose changes — it presents evidence and identifies decisions that should be made.

## Flow

```
Evidence → Findings → Candidate Decision Inputs → Candidate Decisions → Accepted Decisions
```

## Priority Levels

| Priority | Definition | Action |
|----------|------------|--------|
| P1 | Must-decide before proceeding | Decide now |
| P2 | Should-decide soon | Decide in this iteration |
| P3 | Could-decide later | Document for future |
