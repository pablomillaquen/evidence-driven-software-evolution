# Conceptual Model — Findings

**Weight**: Normative

## Entity

**Finding**: An identified observation with severity and confidence.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | H-XXX format |
| Category | string | Domain classification |
| Severity | enum | Critical / High / Medium / Low |
| Confidence | enum | High / Medium / Low |
| Description | string | What was found |
| Impact | string | What it means for the system |

## States

```
Discovery → Classification → Research → Decision → Implementation → Validation → Closure
```

## Relationships

- **supportedBy** → Evidence (N:M)
- **originatesFrom** → Research Question (N:1)
- **leadsTo** → Candidate Decision (1:N)

## Severity Levels

| Level | Definition | Action |
|-------|------------|--------|
| Critical | Blocks further progress | Must address before proceeding |
| High | Significant impact | Should address soon |
| Medium | Moderate impact | Plan for near future |
| Low | Minor impact | Document for future reference |

## Confidence Levels

| Level | Definition | Implication |
|-------|------------|-------------|
| High | Strong evidence | Decision can proceed |
| Medium | Moderate evidence | May need additional evidence |
| Low | Weak evidence | Investigate before deciding |
