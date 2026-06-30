# Evidence-Driven Software Evolution — v1.2 Roadmap

**Status**: In Progress
**Based on**: v1.0 review feedback + SPEC-004 learnings

---

## Completed Improvements (v1.1 + v1.2)

### 7. Health Report Model ✅

**Completed in**: SPEC-004 (Dependency Modernization)

The Health Report communicates **the current state of the system** to clients, management, or audits. While Evidence demonstrates **what was done**, the Health Report communicates **what the system looks like now**.

**Components**:
- Dimensions (primary information)
- Overall Assessment (visual summary)
- Gating Rules (minimum criteria)
- Baseline Comparison (before/after)
- Trend (historical comparison)

**Reusable Domains**: Dependency, Security, Architecture, Test, API, Documentation, Maintainability, Performance

### 8. Health Metrics Model ✅

**Completed in**: SPEC-004 (Dependency Modernization)

Health Metrics define calculation formulas for Health Dimensions, making Health Reports repeatable and comparable across SPECs.

**Document**: `docs/platform/health-metrics.md`

**Finding Types**: Security, Compatibility, Maintenance, Governance, Performance, Documentation

### 9. Accepted Technical Debt Model ✅

**Completed in**: SPEC-004 (Dependency Modernization)

Accepted Technical Debt is distinct from Deferred Debt. It represents **conscious decisions to accept risk** with documented justification and deadline.

**Structure**: Reason, Risk Acceptance, Deadline, Justification, Owner

### 10. Governance Feedback Model ✅

**Completed in**: SPEC-004 (Dependency Modernization)

The Health Report is not the end of the cycle. It is the **generator of the next iteration**. Governance Feedback closes the loop between system state and future investigation.

**The Complete EDSE Cycle**:
```
Question → Investigation → Findings → Decisions → Implementation → Evidence → Health Report → Governance Feedback → Next Question
```

**Rules**:
- Low dimensions (< 70) automatically generate Research Questions
- The cycle never truly ends — it evolves continuously

---

## Planned Improvements (v1.3+)

### 1. Evidence Strength

Current: Evidence Level (E0-E5)
Proposed: Evidence Level + Strength

```
Evidence Level: E0 | E1 | E2 | E3 | E4 | E5
Strength: Weak | Moderate | Strong
```

Example:
```
Performance: E4, Strong
(because measured across 25 endpoints, 3 executions, 2 environments)
```

**Rationale**: E4 obtained once is not the same as E4 repeated 20 times.

### 2. Confidence Decay

Current: Decision Confidence (High/Medium/Low)
Proposed: Confidence + Validation Date + Revalidation Status

```
Decision Confidence: High
Validated: 2026
Status: Validated | Needs Revalidation
```

**Rationale**: A decision from 4 years ago may not have the same weight.

### 3. Core Mode vs Full Mode

Current: All artifacts required
Proposed: Two adoption levels

**Core Mode** (minimum viable):
- Finding
- Decision
- Regression
- Basic traceability

**Full Mode** (complete methodology):
- ADRs
- Baseline
- Metrics
- Taxonomy
- Evidence Levels
- Health Reports
- Governance Feedback

**Rationale**: Small teams may perceive full methodology as heavy. Allow incremental adoption.

### 4. Architectural Decision Minimum Evidence

Proposed rule:
> No architectural decision can be taken with evidence lower than E3.

**Rationale**: Architecture decisions are long-lasting and high-impact.

### 5. Finding Statistics

With taxonomy in place, enable:
- Findings per category per release
- Categories generating most debt
- Trends over time

### 6. Tasks Generator Abstraction

Current: Tasks reference specific implementation details
Proposed: Tasks maintain abstraction until decisions are made

**Problems identified**:
- Tasks like "Create `SystemStatus.php`" assume research decisions
- Too much detail (naming specific controllers/files)
- Subtasks not consolidated (research + decision = one flow)
- Mix of tasks and acceptance criteria

**Proposed rules**:
- Tasks reference "selected strategy" not specific implementations
- Research + Decision + Acceptance = one task
- Acceptance criteria separated from tasks
- File paths only when implementation is certain

**Example**:
```
Before: T014 Create SystemStatus.php
After:  T014 Implement selected centralization strategy for status values
```

**Rationale**: Tasks should maintain abstraction level of spec.md until research produces decisions.

---

## Priority

1. ~~Health Report Model~~ ✅ (completed in SPEC-004)
2. ~~Health Metrics Model~~ ✅ (completed in SPEC-004)
3. ~~Accepted Technical Debt Model~~ ✅ (completed in SPEC-004)
4. ~~Governance Feedback Model~~ ✅ (completed in SPEC-004)
5. Evidence Strength (high value, moderate complexity)
6. Core Mode (high adoption value)
7. Confidence Decay (useful for long-lived projects)
8. Minimum Evidence Rules (consistency improvement)
9. Statistics (data-driven improvement)
10. Tasks Generator Abstraction

---

*These improvements are part of v1.2 evolution.*
*v1.0 is ready for release as-is.*
*v1.1 incorporates Health Report, Health Metrics, and Accepted Technical Debt from SPEC-004.*
*v1.2 incorporates Governance Feedback (complete cycle) from SPEC-004.*
