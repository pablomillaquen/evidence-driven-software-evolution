# Conceptual Model — Evidence

**Weight**: Normative

## Entity

**Evidence**: Objective data supporting findings and decisions.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | E-XXX format |
| Type | enum | Audit / Test / Metric / Comparison / Regression |
| Source | string | Where it came from |
| Content | string | What it contains |
| Date | date | When collected |

## Types

| Type | Purpose | Example |
|------|---------|---------|
| Audit | Document current state | "44 controllers, 0 with validation" |
| Test | Prove functionality works | curl output, test results |
| Metric | Quantified measurement | Response times, query counts |
| Comparison | Before/after proof | "Was 0.5s, now 0.2s" |
| Regression | Nothing broke | Test suite results |

## Relationships

- **supports** → Finding (M:N)
- **collectedBy** → Assessment Goal (N:1)

## Rules

- Every Finding MUST reference at least one Evidence
- Evidence is never deleted (audit trail)
- Evidence is stored in the SPEC's evidence directory
