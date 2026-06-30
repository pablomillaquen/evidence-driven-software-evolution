# Baseline Template

## Release Baseline — vX.Y.Z-[status]

**Version**: vX.Y.Z-[status]
**Date**: [Date]
**Status**: Frozen
**SPEC Type**: [Validation / Stabilization / Refactoring / etc.]

---

## Functional State

### What Works

| Feature | Status | Evidence Level | Evidence |
|---------|--------|----------------|----------|
| [Feature 1] | ✅ Working | E3 | [Test results] |
| [Feature 2] | ✅ Working | E3 | [Test results] |

### What's Deferred

| Feature | Finding ID | Reason | Future SPEC |
|---------|------------|--------|-------------|
| [Feature 3] | H-XXX | [Why deferred] | SPEC-XXX |

---

## Regression

| Metric | Value |
|--------|-------|
| PASS | [N] |
| FAIL | [N] (pre-existing: [list]) |
| New Regressions | 0 |

### Test Results

```
[Full test output or summary]
```

---

## Performance (if measured)

| Metric | Value | Evidence Level |
|--------|-------|----------------|
| Average Response Time | [X]s | E4 |
| Average Queries | [N] | E4 |
| Peak Memory | [N] KB | E4 |
| Endpoints Measured | [N] | E4 |

---

## Findings Summary

| Category | Open | Fixed | Deferred | Documented |
|----------|------|-------|----------|------------|
| Functional | 0 | [N] | [N] | [N] |
| Architecture | 0 | [N] | [N] | [N] |
| Performance | 0 | [N] | [N] | [N] |
| Security | 0 | [N] | [N] | [N] |
| **Total** | **0** | **[N]** | **[N]** | **[N]** |

---

## Technical Debt

| Debt | Finding ID | Priority | Impact | Future SPEC |
|------|------------|----------|--------|-------------|
| [Debt 1] | H-XXX | High/Medium/Low | [Impact] | SPEC-XXX |

---

## Architecture

### ADRs Created

| ADR | Decision | Confidence | Evidence Level |
|-----|----------|------------|----------------|
| ADR-001 | [Decision] | [Level] | [E1-E5] |

### Documentation Generated

| Document | Location |
|----------|----------|
| [Doc 1] | `docs/architecture/[doc1].md` |

---

## Metrics

### Engineering Metrics

| Metric | Value |
|--------|-------|
| Traceability Completeness | [X]% |
| Regression Coverage | [X]% |
| Evidence Coverage | [X]% |
| Evidence Level Average | E[X] |
| Finding Closure Rate | [X]% |
| Technical Debt Ratio | [X]% |

### Project Metrics

| Metric | Value |
|--------|-------|
| SPEC Completion | [X]% |
| Baseline Stability | [N] releases |
| Duration | [X] days |
| Tasks Completed | [N] |
| Scope Changes | [N] |
| Commits | [N] |
| Files Modified | [N] |

---

## Freeze Information

**Frozen**: [Date]
**Frozen by**: [Who/what process]
**Git Tag**: `vX.Y.Z-[status]`
**Commit**: [Hash]

---

## Next Baseline

**Next SPEC**: SPEC-XXX — [Name]
**Type**: [SPEC Type]
**Expected Start**: [Date]
**Dependencies**: [What must be true]

---

*This baseline was created as part of [SPEC name] closure.*
*It becomes the foundation for the next evolution cycle.*
