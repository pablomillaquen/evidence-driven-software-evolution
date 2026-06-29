# Conceptual Model — Baselines

**Weight**: Normative

## Entity

**Baseline**: A frozen reference point for future comparison.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | BL-XXX format |
| Snapshot | object | System state capture |
| Configuration | object | Configuration state |
| Date | date | When frozen |

## States

```
Proposed → Validated → Frozen
```

## Relationships

- **freezes** → Decision (1:N)
- **generates** → Health Report (1:1)

## Freeze Criteria

Before freezing, verify:
- All evidence packages are complete
- All findings are documented
- All candidate decisions are accepted or deferred
- Baseline snapshot is created
- Configuration state is captured

## What is Frozen

- Evidence Package
- Findings with severity and confidence
- Candidate Decisions (accepted or deferred)
- Technology Health Report
- Baseline snapshot

## What is NOT Frozen

- Permanent documentation (separate deliverable)
- Implementation decisions (future SPECs)
- New features (future SPECs)
