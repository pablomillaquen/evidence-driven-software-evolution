# Process — Validation

**Weight**: Recommended

## Purpose

Ensure changes do not break existing functionality.

## Flow

```
1. Run Tests
2. Compare to Baseline
3. Investigate Regressions
4. Register Findings
5. Update Evidence
```

## Entry Criteria

- Changes implemented
- Test suite available

## Exit Criteria

- All tests pass (or regressions documented)
- Evidence updated
- Findings registered (if any)

## When to Run

- After each user story (quick validation)
- After each phase (full regression)
- Before release (complete regression)
- When unexpected behavior (targeted regression)

## Rules

- Never merge with new regressions
- Flaky tests must be identified and documented
- Pre-existing failures are tracked separately
- Regression results are part of release evidence
