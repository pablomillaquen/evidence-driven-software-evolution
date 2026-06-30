# Conceptual Model — Research Questions

**Weight**: Normative

## Entity

**Research Question**: A guiding question that frames investigation scope.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | RQ-XXX format |
| Question | string | The research question |
| Motivation | string | Why this question matters |
| Success Condition | string | What success looks like |

## Relationships

- **generates** → Assessment Goal (1:N)
- **originates** → Finding (1:N)

## Rules

- Never skip research for non-trivial changes
- Research Questions drive Evidence collection
- Research Questions feed into next iteration via Health Reports
