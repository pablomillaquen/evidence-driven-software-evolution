# SPEC Template

# Feature Specification: [Title]

**Feature Branch**: `[branch-name]`
**Created**: [Date]
**Base**: [Previous version or "New project"]
**Status**: Draft / In Progress / Completed
**Type**: Validation / Stabilization / Refactoring / Architecture / Security / Migration / Compliance / Performance / Research

**Input**: [What triggered this SPEC]

---

## SPEC Types

| Type | Purpose | Expected Duration |
|------|---------|-------------------|
| **Validation** | Verify existing behavior | Short |
| **Stabilization** | Improve quality without behavior change | Medium |
| **Refactoring** | Restructure without behavior change | Medium |
| **Architecture** | Document or establish architectural patterns | Short |
| **Security** | Address vulnerabilities or compliance | Variable |
| **Migration** | Move between technologies or data | Long |
| **Compliance** | Meet regulatory requirements | Variable |
| **Performance** | Optimize measured metrics | Medium |
| **Research** | Investigate feasibility or options | Short |

---

## Context

### Current State

[Describe the current state of the system relevant to this SPEC]

### Problem Statement

[What problem or opportunity does this SPEC address]

### Goals

- [Goal 1]
- [Goal 2]
- [Goal 3]

### Non-Goals

- [What this SPEC explicitly does NOT address]

---

## Scope

### Included

- [Feature/change 1]
- [Feature/change 2]

### Not Included

- [Explicitly excluded 1]
- [Explicitly excluded 2]

---

## Research

### Findings

| ID | Category | Description | Severity | Status |
|----|----------|-------------|----------|--------|
| H-001 | [Category] | [Description] | HIGH | OPEN |

### Research Questions

| ID | Question | Status |
|----|----------|--------|
| PI-001 | [Question] | RESOLVED |

### Decisions

| ID | Decision | Type | Confidence | Evidence Level | Status |
|----|----------|------|------------|----------------|--------|
| D-001 | [Decision] | [Type] | [Level] | [E1-E5] | ACCEPTED |

---

## Data Model

### Entities Affected

| Entity | Changes |
|--------|---------|
| [Entity] | [What changes] |

### Schema Changes

[None / Description of changes]

---

## User Stories

### US01: [Title]

**As a** [role]
**I want** [goal]
**So that** [benefit]

**Validation Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

---

## Implementation Plan

### Phase 1: [Name]

| US | Tasks | Commit | Evidence | Regression | Finding | Closed |
|----|-------|--------|----------|------------|---------|--------|
| US01 | T001-T005 | - | - | - | - | - |

### Phase 2: [Name]

| US | Tasks | Commit | Evidence | Regression | Finding | Closed |
|----|-------|--------|----------|------------|---------|--------|
| US02 | T006-T010 | - | - | - | - | - |

---

## Quickstart

### Validation Scenarios

1. **Scenario 1**: [Description]
   - Steps: [Steps to execute]
   - Expected: [Expected result]

2. **Scenario 2**: [Description]
   - Steps: [Steps to execute]
   - Expected: [Expected result]

---

## Evidence Directory

```
evidence/
├── regression/
│   ├── baseline.md
│   └── final.md
├── phase1/
│   └── audit-before.md
└── phase2/
    └── ...
```

---

## Closure Checklist

- [ ] All user stories complete
- [ ] All findings CLOSED or DEFERRED
- [ ] Regression baseline maintained
- [ ] Evidence recorded (min E1)
- [ ] ADRs created (if applicable)
- [ ] Architecture docs updated (if applicable)
- [ ] Release Report created
- [ ] Baseline documented
- [ ] Version tagged
