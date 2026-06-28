# Decision Template

## D-XXX: [Decision Title]

**Status**: ACCEPTED / DEFERRED / REJECTED
**Type**: OPERATIONAL / TECHNICAL / ARCHITECTURAL
**Confidence**: HIGH / MEDIUM / LOW
**Evidence Level**: E1 / E2 / E3 / E4 / E5
**Date**: [When decided]
**Context**: [What situation required this decision]

---

### Decision vs ADR

> **Every ADR is a Decision. Not every Decision deserves an ADR.**

| Criteria | Decision | ADR |
|----------|----------|-----|
| Scope | Operational or technical | Architectural |
| Impact | Localized | System-wide |
| Duration | May be temporary | Permanent reference |
| Documentation | This template | ADR template |

**When to create an ADR instead:**
- Decision affects system architecture
- Will be referenced by future work
- Needs to survive team changes
- Involves significant trade-offs

---

### Decision

[What was decided. Be clear and concise.]

### Justification

[Why this decision, with evidence. Reference findings and research questions.]

### Evidence

**Evidence Level**: E1 / E2 / E3 / E4 / E5
**Evidence**: [What proof supports this decision]

### Options Considered

| Option | Description | Pros | Cons | Verdict |
|--------|-------------|------|------|---------|
| A | [Description] | [Pros] | [Cons] | [Chosen/Rejected] |
| B | [Description] | [Pros] | [Cons] | [Chosen/Rejected] |

### Consequences

**Positive**:
- [Benefits]

**Negative**:
- [Trade-offs]

**Neutral**:
- [Things to be aware of]

### Related

- Finding: H-XXX
- Research: PI-XXX
- ADR: ADR-XXX (if architectural)
- Tasks: T001, T002, ...

### Implementation

- [ ] Tasks created
- [ ] Implementation complete
- [ ] Regression passed
- [ ] Evidence recorded
- [ ] Finding closed

---

**Implemented**: [Date]
**Validated**: [Date]
