# Tasks Template

## Phase N: [Phase Name]

**Purpose**: [What this phase achieves]

### User Story N: [US Name]

**As a** [role]
**I want** [goal]
**So that** [benefit]

**Validation Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

**Preconditions**:
- [What must be true before starting]

---

#### Tasks

- [ ] T001 [Task description] — [US01] [Commit: abc123] [Evidence: path/to/file]
- [ ] T002 [Task description] — [US01] [Commit: abc123] [Evidence: path/to/file]
- [ ] T003 [Task description] — [US01] [Commit: abc123] [Evidence: path/to/file]

#### Findings

| ID | Description | Status |
|----|-------------|--------|
| H-001 | [Description] | CLOSED |

#### Evidence

| Type | File |
|------|------|
| Audit | `evidence/phaseN/audit-before.md` |
| Test | `evidence/regression/phaseN-usXX.md` |

---

## Dependencies & Execution Order

### Phase Dependencies

- **Phase 1**: No dependencies
- **Phase 2**: Depends on Phase 1
- **Phase N**: Depends on Phase N-1

### User Story Dependencies

- **US01**: Can start after Phase 1
- **US02**: Depends on US01
