# Evidence-Driven Software Evolution — Reference Guide

**Version**: 1.0
**Type**: Reference (examples, case studies, FAQ)

---

## 1. Real-World Example: SIGES Project

### 1.1 Context

SIGES is a Laravel 11 + Angular 17 medical equipment management system. The project used this methodology through two specifications:

- **SPEC-001**: Functional Validation
- **SPEC-002**: Product Stabilization

### 1.2 SPEC-001: Functional Validation

**Type**: Validation SPEC
**Duration**: 1 day
**Objective**: Validate all API endpoints against existing behavior

#### Findings

| ID | Category | Description | Resolution |
|----|----------|-------------|------------|
| H-001 | Functional | Missing authorization on endpoints | FIXED |
| H-002 | Architecture | Frontend-only role enforcement | FIXED |
| H-003 | Functional | Inconsistent HTTP responses | FIXED |
| H-004 | Functional | Missing validation | FIXED |

#### Evidence

```
Evidence Level: E3
Evidence: 85 functional tests (PHPUnit)
Result: 85 PASS, 0 FAIL
```

#### Baseline

```
Version: v1.0.0-validated
Regression: 85 PASS, 0 FAIL
Technical Debt: None
```

### 1.3 SPEC-002: Product Stabilization

**Type**: Stabilization SPEC
**Duration**: 1 day
**Objective**: Improve quality without changing user-facing behavior

#### Findings

| ID | Category | Description | Resolution | Evidence Level |
|----|----------|-------------|------------|----------------|
| H-015 | Security | HttpException stack trace exposure | FIXED | E3 |
| H-014 | Functional | DashboardNurseControllerTest flaky | DEFERRED | E3 |

#### Decisions

| ID | Decision | Type | Confidence | Evidence Level |
|----|----------|------|------------|----------------|
| D-001 | Backend is authentication authority | Architectural | High | E1 |
| D-002 | No caching until performance baseline proves need | Technical | High | E4 |
| D-003 | All consolidation deferred (guardrail) | Technical | High | E1 |

#### ADRs

| ADR | Decision |
|-----|----------|
| ADR-001 | Authentication Strategy |
| ADR-002 | Exception Handling |
| ADR-003 | Logging Strategy |
| ADR-004 | Validation Pattern |
| ADR-005 | Performance Strategy |

#### Baseline

```
Version: v1.1.0-stabilized
Regression: 34 PASS, 11 FAIL (all pre-existing)
Performance: All endpoints under 0.35s
Technical Debt: 6 items documented
```

---

## 2. Finding Examples

### 2.1 Finding with Implementation Path

```
## H-015: HttpException Stack Trace Exposure

**Severity**: HIGH
**Category**: Security
**Discovered**: 2026-06-27
**Phase**: US02
**Status**: CLOSED

### Description
Production exceptions exposed full stack traces to API consumers.

### Impact
Security risk: internal implementation details visible.

### Evidence
**Evidence Level**: E1
**Evidence**: Code inspection of api/bootstrap/app.php

### Resolution
**Decision**: Fix in this SPEC
**Confidence**: High
**Evidence Level**: E3

### Implementation
- [x] Updated exception handler
- [x] Added HttpException case
- [x] Regression passed (35 PASS)

### Validation
- [x] Regression: 35 PASS, 10 FAIL
- [x] Evidence: evidence/phase1/exception-handler/test-results.txt
```

### 2.2 Finding with Documentation Path

```
## H-014: DashboardNurseControllerTest Flaky

**Severity**: LOW
**Category**: Functional
**Discovered**: 2026-06-27
**Phase**: US01
**Status**: CLOSED

### Description
Test sometimes passes, sometimes fails. Non-deterministic behavior.

### Impact
Low: test reliability issue, not a system issue.

### Evidence
**Evidence Level**: E3
**Evidence**: Multiple test runs showing inconsistent results

### Resolution
**Decision**: Document and defer
**Confidence**: Medium
**Evidence Level**: E3

### Technical Debt Created
- **Impact**: Test reliability
- **Suggested SPEC**: SPEC-011 (Refactoring)
- **Priority**: Low
```

---

## 3. Decision Examples

### 3.1 Operational Decision

```
## D-XXX: Use Backward-Compatible Pagination

**Status**: ACCEPTED
**Type**: OPERATIONAL
**Confidence**: HIGH
**Evidence Level**: E4
**Date**: 2026-06-27

### Decision
Add pagination that behaves identically to current behavior when no page parameter is provided.

### Justification
Without `page` param, endpoints must return all records (current behavior). Changing this breaks Angular frontend.

### Evidence
**Evidence Level**: E4
**Evidence**: Backward compatibility test (curl output)

### Options Considered

| Option | Pros | Cons | Verdict |
|--------|------|------|---------|
| Add pagination | Performance improvement | Risk of breaking frontend | Chosen (with backward compat) |
| No change | No risk | No improvement | Rejected |
```

### 3.2 Architectural Decision (ADR)

```
# ADR-001: Authentication Strategy

**Status**: Accepted
**Type**: ARCHITECTURAL
**Date**: 2026-06-27

## Context
SIGES needs consistent authentication across all API endpoints.

## Decision
Backend is the authority for authentication. Frontend is evidence only.

## Consequences

### Positive
- Single source of truth
- Consistent behavior
- Audit trail

### Negative
- Frontend cannot override backend decisions

## Alternatives Considered

### Frontend authority
Rejected because: Frontend can be bypassed.

### Shared authority
Rejected because: Creates inconsistency.
```

---

## 4. Baseline Examples

### 4.1 Validation Baseline

```
# Release Baseline — v1.0.0-validated

**Version**: v1.0.0-validated
**Date**: 2026-06-27
**Status**: Frozen

## Functional State

| Feature | Status | Evidence |
|---------|--------|----------|
| Equipment CRUD | ✅ Working | E3 |
| Task Management | ✅ Working | E3 |
| User Authentication | ✅ Working | E3 |

## Regression

| Metric | Value |
|--------|-------|
| PASS | 85 |
| FAIL | 0 |
| New Regressions | 0 |

## Technical Debt
None

## ADRs
None

## Freeze Information
**Frozen**: 2026-06-27
**Git Tag**: `v1.0.0-validated`
**Commit**: abc123
```

### 4.2 Stabilization Baseline

```
# Release Baseline — v1.1.0-stabilized

**Version**: v1.1.0-stabilized
**Date**: 2026-06-27
**Status**: Frozen

## Functional State

| Feature | Status | Evidence |
|---------|--------|----------|
| All v1.0 features | ✅ Working | E3 |
| Exception handling | ✅ Improved | E3 |
| Validation | ✅ Improved | E3 |
| Logging | ✅ Added | E3 |

## Regression

| Metric | Value |
|--------|-------|
| PASS | 34 |
| FAIL | 11 (pre-existing) |
| New Regressions | 0 |

## Performance

| Metric | Value |
|--------|-------|
| Average Response Time | 0.218s |
| Endpoints Under 0.35s | 25/25 (100%) |

## Technical Debt

| Debt | Priority | Future SPEC |
|------|----------|-------------|
| DashboardController 1,088 lines | High | SPEC-011 |
| 1,442 lines duplication | Medium | SPEC-011 |
| Hardcoded constants | Medium | SPEC-011 |

## ADRs

| ADR | Decision |
|-----|----------|
| ADR-001 | Authentication Strategy |
| ADR-002 | Exception Handling |
| ADR-003 | Logging Strategy |
| ADR-004 | Validation Pattern |
| ADR-005 | Performance Strategy |

## Freeze Information
**Frozen**: 2026-06-27
**Git Tag**: `v1.1.0-stabilized`
**Commit**: d0317e3
```

---

## 5. Traceability Example

### Complete Chain

```
H-015 (Finding)
    ↓
PI-001 (Research Question): How should exceptions be handled?
    ↓
E1 (Evidence): Code inspection of exception handler
    ↓
D-002 (Decision): Add HttpException case
    ↓
US02 (SPEC): Exception Handling
    ↓
T010 (Task): Update exception handler
    ↓
abc123 (Commit): "US02: Update exception handler"
    ↓
E3 (Evidence): Test results (35 PASS)
    ↓
Regression: 35 PASS, 10 FAIL
    ↓
H-015 CLOSED
```

---

## 6. FAQ

### Q: When should I create an ADR instead of a regular Decision?

**A:** When the decision:
- Affects system architecture
- Will be referenced by future work
- Needs to survive team changes
- Involves significant trade-offs

If it's operational or technical with localized impact, use the Decision template.

### Q: What evidence level is required for a Finding?

**A:** Minimum E1 (code inspection). You must look at the code before documenting a Finding.

### Q: What evidence level is required for performance claims?

**A:** E4 (measured metric). You must measure before and after.

### Q: Can a Finding be closed without implementation?

**A:** Yes. If the decision is to document or defer, the Finding can be CLOSED with that resolution.

### Q: How is Technical Debt different from a Finding?

**A:** Technical Debt is born from a deferred Finding. It's the documented consequence, not the Finding itself.

### Q: What happens if regression fails?

**A:** You cannot proceed. Fix the regression first, then re-run regression.

### Q: How many evidence sources are required for a Decision?

**A:** Minimum one (E1). More sources increase Confidence level.

### Q: Can I skip the Research Layer?

**A:** Only for trivial changes. If there's any uncertainty, create a Research Question.

### Q: What's the difference between a SPEC and a task?

**A:** A SPEC defines what and why. Tasks define how. A SPEC contains many tasks.

### Q: When is a Baseline complete?

**A:** When:
- Regression passes (or pre-existing failures documented)
- All Findings are CLOSED or DEFERRED
- Release Report is created
- Git tag is created

---

## 7. Case Study: Performance Baseline

### Context

During SPEC-002, we needed to decide whether to optimize API performance.

### Research Layer

**Finding**: No performance baseline existed.

**Research Question**: Is the system fast enough?

**Evidence**: Measured 25 endpoints (E4)

**Decision**: No optimizations needed (all under 0.35s)

### Engineering Layer

**SPEC**: US11 (Performance Baseline)

**Tasks**: Measure all endpoints, document results

**Implementation**: Created performance baseline document

**Regression**: 35 PASS, 10 FAIL (no change)

**Release**: Documented in Release Report

### Result

- No code changes needed
- Evidence-based decision saved optimization effort
- Baseline established for future comparison

---

## 8. Case Study: Architectural Guardrail

### Context

During SPEC-002, we discovered significant code duplication (1,442 lines).

### Research Layer

**Finding**: 9 duplication patterns across 23 controllers.

**Research Question**: Should we consolidate now?

**Evidence**: Duplication analysis (E2)

**Decision**: Defer (guardrail: "If improvement can be made within existing architecture, prefer that")

### Engineering Layer

**SPEC**: US06 (Duplication Audit)

**Tasks**: Audit only, no implementation

**Implementation**: Documented findings

**Regression**: 35 PASS, 10 FAIL (no change)

**Release**: Technical Debt documented for SPEC-011

### Result

- No code changes
- Guardrail prevented premature refactoring
- Evidence supports future SPEC-011 work

---

*Version 1.0 — Reference Guide*
*This document provides examples, case studies, and answers to common questions.*
