# Conceptual Model — Technical Debt

**Weight**: Normative

## Entity

**Technical Debt**: Deferred work traced back to a Decision.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | ATD-XXX format |
| Category | string | Domain classification |
| Status | enum | Open / Resolved |
| Description | string | What is deferred |

## Relationships

- **deferredFrom** → Decision (N:1)

## Rules

- Every Technical Debt MUST trace back to a Decision
- Technical Debt must include rationale for deferral
- Technical Debt should reference future SPEC for resolution

## Management

Technical Debt is tracked in `docs/platform/accepted-technical-debt.md`.

Each entry includes:
- ID
- Category
- Rationale for deferral
- Traceability to future SPEC
- Status
