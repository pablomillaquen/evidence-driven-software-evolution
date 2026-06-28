# Finding Template

## H-XXX: [Title]

**Severity**: HIGH / MEDIUM / LOW
**Category**: Functional / Architecture / Performance / Security / Documentation / Compliance / Technical Debt / Regression / Usability
**Discovered**: [Date]
**Phase**: [Which phase found it]
**Status**: OPEN

---

### Lifecycle

```
OPEN → INVESTIGATING → DECISION → IMPLEMENTED → VALIDATED → CLOSED
```

| State | When |
|-------|------|
| **OPEN** | Problem identified, not yet investigated |
| **INVESTIGATING** | Research in progress |
| **DECISION** | Decision made, awaiting implementation |
| **IMPLEMENTED** | Code changed, awaiting validation |
| **VALIDATED** | Regression passed, awaiting closure |
| **CLOSED** | Finding fully resolved |

### Resolution Types

| Type | When to Use | Result |
|------|-------------|--------|
| **FIXED** | Problem resolved in this SPEC | Finding → CLOSED |
| **DEFERRED** | Problem documented for future SPEC | Finding → CLOSED + Technical Debt created |
| **DOCUMENTED** | Problem noted, no action needed | Finding → CLOSED |

---

### Description

[What was found. Be specific and factual.]

### Impact

[What it means for the system. Quantify if possible.]

### Evidence

**Evidence Level**: E0 / E1 / E2 / E3 / E4 / E5
**Evidence**: [Links to proof: code inspection, API output, metrics]

---

### Research Questions

- [ ] PI-XXX: [Question that needs investigation]

### Resolution

**Decision**: [FIX / DEFER / DOCUMENT]
**Justification**: [Why this decision, with evidence]
**Related**: D-XXX, ADR-XXX

### Path

**Path**: [Implementation / Documentation]

If Implementation:
- [ ] Tasks created
- [ ] Implementation complete
- [ ] Regression passed
- [ ] Evidence recorded

If Documentation:
- [ ] Technical Debt documented
- [ ] Future SPEC suggested

---

**Status**: OPEN → INVESTIGATING
**Closed**: [Date]
**Closed by**: [Who/what validated]
