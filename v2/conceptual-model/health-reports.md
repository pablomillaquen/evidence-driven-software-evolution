# Conceptual Model — Health Reports

**Weight**: Normative

## Entity

**Health Report**: Summary of technology health dimensions.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | HR-XXX format |
| Dimensions | object | 5 health dimensions |
| Scores | object | Scores per dimension |
| Recommendations | list | Action items |

## Relationships

- **generatedFrom** → Baseline (1:1)
- **feedsInto** → Research Question (1:N)

## Health Dimensions

| Dimension | Description |
|-----------|-------------|
| Dependency Health | Package currency and maintenance |
| Security Posture | Vulnerability status |
| Code Quality | Patterns and anti-patterns |
| Testing Maturity | Coverage and reliability |
| Documentation Coverage | Completeness |

## Scoring

| Score | Status | Action |
|-------|--------|--------|
| 90-100 | Excellent | Maintain |
| 70-89 | Good | Monitor |
| 50-69 | Fair | Plan improvements |
| 30-49 | Poor | Prioritize fixes |
| 0-29 | Critical | Immediate action |

## Governance Feedback

When a dimension scores below 70, it automatically generates Research Questions for the next SPEC.
