# Evidence-Driven Software Evolution

A methodology for evolving software systems with evidence, traceability, and architectural control. Designed for AI-assisted engineering projects where decisions must be justified, not assumed.

## When to Use

- Evolving an existing software system with controlled changes
- Stabilizing a codebase before adding new features
- Projects requiring audit trails and architectural decisions
- Any project where "why" matters as much as "what"

## Core Principles

### 1. Research Before Implementation

Never assume the solution. Every change starts with a finding, not a fix.

```
Finding (H)
    ↓
Research Question (PI)
    ↓
Evidence
    ↓
Decision (D)
    ↓
Implementation
    ↓
Validation
```

### 2. Evidence as Requirement

Every important claim must be backed by evidence. Not opinion. Not intuition. Not "it feels faster."

Evidence types:
- **Code inspection**: What the code actually does
- **API execution**: What the system actually returns
- **Metrics**: Quantified measurements before and after
- **Regression tests**: Proof that nothing broke

### 3. Architectural Guardrails

Before creating new components:
1. Evaluate existing architecture
2. Justify the need for change
3. Document the decision
4. Prefer the simplest path within existing patterns

Rule: "If a improvement can be made within the existing architecture, that alternative must be preferred."

### 4. Measure First

Before optimizing:
1. Measure current state
2. Establish baseline
3. Justify changes with data
4. Re-measure after changes

No optimization without measurement.

### 5. Regression First

Every change must demonstrate:
- No functionality broken
- Compatibility maintained
- Measurable improvement (if applicable)

### 6. Complete Traceability

```
Finding → Question → Decision → SPEC → Task → Commit → Evidence → Regression → Release
```

Every artifact links to the next. Nothing exists in isolation.

### 7. Reverse Traceability

Each finding must be traceable back to:
- The evidence that supports it
- The Research Question that originated it

```
Finding H-XXX
    ↓
Supported by
    Evidence E-XXX
    ↓
Originated from
    RQ-XXX
```

This enables auditing decisions back to evidence.

### 8. Knowledge Management

Each version generates:
- ADRs (Architecture Decision Records)
- Documentation
- Release Report
- Registered technical debt
- Updated roadmap

## Evidence Package

The primary deliverable of an EDSE investigation is the **Evidence Package** — a complete, reproducible investigation.

### Structure

```
evidence/
├── environment/
│   ├── project-metadata.json
│   └── environment-validation.md
├── architecture/
│   ├── module-inventory.md
│   ├── component-hierarchy.md
│   ├── routing-map.md
│   ├── service-layer.md
│   ├── state-management.md
│   └── architectural-patterns.md
├── technology/
│   ├── dependency-inventory.md
│   ├── outdated-packages.txt
│   ├── security-audit.txt
│   ├── health-classification.md
│   └── deprecated-packages.md
├── quality/
│   ├── code-patterns.md
│   ├── anti-patterns.md
│   ├── deprecated-practices.md
│   ├── findings.md
│   └── technical-debt-register.md
├── testing/
│   ├── test-execution-report.md
│   ├── coverage-analysis.md
│   ├── testing-gaps.md
│   └── smoke-test-results.md
├── performance/
│   ├── bundle-analysis.md
│   ├── load-times.md
│   ├── performance-characteristics.md
│   └── baseline-metrics.md
├── consolidated/
│   ├── findings-summary.md
│   ├── candidate-decision-inputs.md
│   ├── candidate-decisions.md
│   ├── decision-criteria.md
│   ├── priority-classification.md
│   └── reverse-traceability.md
├── baseline/
│   ├── baseline-snapshot.md
│   ├── package-lock.json
│   └── configuration-state.json
└── final.md
```

### Purpose

If someone asks "why did you modernize the frontend?", the answer is not "because the code was old" — it is the full chain: RQ → Evidence → Finding → Candidate Decision → Accepted Decision → Future SPEC.

## Specification Lifecycle

### Structure

A SPEC contains:

| Document | Purpose |
|----------|---------|
| `spec.md` | What and why (frozen during implementation) |
| `plan.md` | How (phases, tasks, traceability) |
| `research.md` | Research Protocol (questions, not conclusions) |
| `data-model.md` | Entities affected |
| `execution-guide.md` | Validation scenarios |
| `tasks.md` | Task list with status |
| `checklists/` | Quality gates |
| `evidence/` | Evidence Package |

### Phases

1. **Research**: Understand current state, identify findings
2. **Planning**: Define scope, phases, tasks
3. **Implementation**: One user story at a time, full cycle per US
4. **Validation**: Regression after each change
5. **Closure**: Final regression, release report, tag

### Frozen State

During implementation, `spec.md`, `plan.md`, `research.md`, and `tasks.md` are frozen. Unexpected behavior → register Finding, evaluate, defer if scope change.

## Research Protocol vs Research Report

### Research Protocol (Before Investigation)

Contains only:
- Research Question
- Motivation
- Investigation Strategy
- Evidence Required
- Success Condition

Does NOT contain:
- Findings
- Conclusions
- Decisions

### Research Report (After Investigation)

Contains:
- Findings with severity and confidence
- Evidence supporting findings
- Candidate decisions
- Accepted decisions

## Finding Model

### Format

```
## H-XXX: [Title]

**Severity**: HIGH / MEDIUM / LOW
**Confidence**: HIGH / MEDIUM / LOW
**Discovered**: [Date]
**Phase**: [Which phase found it]

### Description
[What was found]

### Impact
[What it means for the system]

### Resolution
[How it was addressed: FIXED / DEFERRED / DOCUMENTED]

### Evidence
[Links to proof]
```

### Confidence

Confidence indicates the strength of evidence:
- **High**: Strong evidence, clear link to Research Question
- **Medium**: Moderate evidence, reasonable inference
- **Low**: Weak evidence, requires further investigation

### Lifecycle

1. **Discovery**: Found during inspection or testing
2. **Classification**: Severity and confidence assessment
3. **Research**: Investigation if not obvious
4. **Decision**: Fix, defer, or document
5. **Implementation**: If fixing
6. **Validation**: Regression proof
7. **Closure**: Final status recorded

## Candidate Decisions

Candidate Decisions are an independent artifact between Evidence and Accepted Decisions.

### Purpose

Prevent mixing observations with solutions. The baseline does NOT propose changes — it presents evidence and identifies decisions that should be made.

### Flow

```
Evidence
    ↓
Findings
    ↓
Candidate Decision Inputs
    ↓
Candidate Decisions (P1, P2, P3)
    ↓
Accepted Decisions
    ↓
Baseline Freeze
```

### Format

```
## D-XXX: [Decision Title]

**Status**: PENDING / ACCEPTED / DEFERRED / REJECTED
**Priority**: P1 (Must-decide) / P2 (Should-decide) / P3 (Could-decide)
**Date**: [When decided]
**Context**: [What situation required this decision]

### Decision
[What was decided]

### Justification
[Why this decision, with evidence]

### Consequences
[What this means going forward]

### Related
- Finding: H-XXX
- Research: PI-XXX
- ADR: ADR-XXX (if architectural)
```

## Decision Preparation Phase

A standard phase in assessment SPECs that transforms findings into candidate decisions.

### Purpose

Prevents jumping from evidence directly to solutions. Ensures decisions are evidence-based and properly prioritized.

### Activities

1. Review all findings
2. Identify findings requiring decisions
3. Prepare candidate decision inputs
4. Classify decisions by priority
5. Document decision rationale

## Baseline Freeze

### Definition

Baseline Freeze captures the state of a system at a specific point in time, creating a reference point for all future evolution.

### Criteria

Before freezing, verify:
- [ ] All evidence packages are complete
- [ ] All findings are documented
- [ ] Consolidated Assessment Report is accurate
- [ ] All candidate decisions are accepted or deferred
- [ ] Baseline snapshot is created
- [ ] Configuration state is captured

### What is Frozen

- Evidence Package
- Findings with severity and confidence
- Candidate Decisions (accepted or deferred)
- Technology Health Report
- Baseline snapshot (package-lock.json, configuration-state.json)

### What is NOT Frozen

- Permanent documentation (separate deliverable)
- Implementation decisions (future SPECs)
- New features (future SPECs)

## Research Question Model

### When to Use

When a finding requires investigation before a decision can be made.

### Format

```
## PI-XXX: [Question]

**Finding**: H-XXX
**Context**: [Why this needs investigation]
**Options**: [What we considered]
**Evidence**: [What we found]
**Decision**: [What we chose and why]
```

### Rules

- Never skip research for non-trivial changes
- Always document options considered
- Decision must reference evidence
- Research feeds into ADRs when architectural

## Decision Model

### Format

```
## D-XXX: [Decision Title]

**Status**: ACCEPTED / DEFERRED / REJECTED
**Date**: [When decided]
**Context**: [What situation required this decision]

### Decision
[What was decided]

### Justification
[Why this decision, with evidence]

### Consequences
[What this means going forward]

### Related
- Finding: H-XXX
- Research: PI-XXX
- ADR: ADR-XXX (if architectural)
```

## Architecture Decision Records (ADR)

### When to Create

When a decision:
- Affects system architecture
- Will be referenced by future work
- Needs to survive team changes
- Involves trade-offs

### Format

```markdown
# ADR-XXX: [Title]

**Status**: Accepted
**Date**: [Date]
**Deciders**: [Who was involved]

## Context

[What is the issue that motivates this decision?]

## Decision

[What is the change being proposed or decided?]

## Consequences

### Positive
- [Benefits]

### Negative
- [Trade-offs]

### Neutral
- [Things to be aware of]

## Alternatives Considered

### [Option A]
[Description]
[Why not chosen]

### [Option B]
[Description]
[Why not chosen]
```

### Naming Convention

`docs/adr/NNN-short-title.md`

Examples:
- `001-authentication-strategy.md`
- `002-exception-handling.md`
- `003-logging-strategy.md`

## Evidence Model

### Directory Structure

```
evidence/
├── regression/           # Test results per phase
│   ├── baseline.md
│   ├── phase1-us01.md
│   └── final.md
├── phase1/              # Phase-specific evidence
│   ├── audit-before.md
│   └── audit-after.md
├── phase2/
│   └── ...
└── phase3/
    └── ...
```

### Evidence Types

| Type | Purpose | Example |
|------|---------|---------|
| Audit | Document current state | "44 controllers, 0 with validation" |
| Test | Prove functionality works | curl output, test results |
| Metric | Quantified measurement | Response times, query counts |
| Comparison | Before/after proof | "Was 0.5s, now 0.2s" |
| Regression | Nothing broke | Test suite results |

### Rules

1. Every finding must have evidence
2. Every decision must reference evidence
3. Evidence is stored in the SPEC's evidence directory
4. Evidence is never deleted (audit trail)

## Traceability Model

### Forward Traceability

```
Research Question
    ↓
Assessment Goal
    ↓
Evidence
    ↓
Finding
    ↓
Candidate Decision
    ↓
Accepted Decision
    ↓
Baseline Freeze
```

### Reverse Traceability

```
Finding H-XXX
    ↓
Supported by
    Evidence E-XXX
    ↓
Originated from
    RQ-XXX
```

### Tracking

In `tasks.md`:

```markdown
- [x] T001 Description — [US01] [Commit: abc123] [Evidence: path/to/file]
```

In `plan.md`:

```markdown
| US | Tasks | Commit | Evidence | Regression | Finding | Closed |
|----|-------|--------|----------|------------|---------|--------|
| US01 | T001-T005 | abc123 | evidence/... | 35 PASS | H-001 | ✅ |
```

## Regression Model

### When to Run

1. **After each user story**: Quick validation
2. **After each phase**: Full regression
3. **Before release**: Complete regression
4. **When unexpected behavior**: Targeted regression

### Process

```bash
# 1. Run tests
cd api && php artisan test  # (or equivalent)

# 2. Record results
# PASS / FAIL counts
# Compare to baseline

# 3. If new FAIL: investigate
# If H-xxx: register finding
# If regression: fix immediately

# 4. Update evidence
# evidence/regression/phaseX-usY.md
```

### Baseline

Always maintain a regression baseline:

| Version | PASS | FAIL | Notes |
|---------|------|------|-------|
| Pre-change | 35 | 10 | Baseline |
| Post-US01 | 35 | 10 | No change |
| Post-US02 | 36 | 9 | +1 PASS |

### Rules

- Never merge with new regressions
- Flaky tests must be identified and documented
- Pre-existing failures are tracked separately
- Regression results are part of release evidence

## Release Management

### Release Report Structure

```markdown
# Release Report — vX.Y.Z

**Version**: vX.Y.Z
**Date**: [Date]
**Status**: Released

## 1. Executive Summary
## 2. Objectives
## 3. Scope (Included / Not Included)
## 4. Work Completed (by phase)
## 5. Metrics (regression + performance)
## 6. Findings (closed + deferred)
## 7. Architectural Decisions (ADRs)
## 8. Architecture Assets (docs + diagrams)
## 9. Known Technical Debt
## 10. Risks
## 11. Lessons Learned
## 12. Next Roadmap
## 13. Release Approval
```

### Naming

`docs/releases/vX.Y.Z-[status].md`

Examples:
- `v1.0.0-validated.md`
- `v1.1.0-stabilized.md`

### Tagging

```bash
git tag -a vX.Y.Z-[status] -m "Release description"
```

## Documentation Architecture

### Required per SPEC

| Document | Location | Purpose |
|----------|----------|---------|
| SPEC documents | `specs/NNN-name/` | Specification |
| ADRs | `docs/adr/` | Architectural decisions |
| Architecture | `docs/architecture/` | System documentation |
| Release Reports | `docs/releases/` | Version history |
| Evidence | `specs/NNN-name/evidence/` | Proof artifacts |

### Mermaid Diagrams

Architecture docs should include:
- **Context diagram**: System boundaries
- **Component diagram**: Internal structure
- **ER diagram**: Data model
- **Deployment diagram**: Infrastructure

## Roadmap Evolution

### Process

1. **After each SPEC**: Review findings, update roadmap
2. **Identify orthogonal work**: Some specs can run in parallel
3. **Order by dependency**: Foundational work first
4. **Document rationale**: Why this order

### Example

```
SPEC-001 (Validation)
    ↓
SPEC-002 (Stabilization)
    ↓
├──────────────┐
▼              ▼
SPEC-011      SPEC-010
(Refactor)    (Security)
    │              │
    └──────┬───────┘
           ▼
    Future Evolution
```

## Anti-Patterns

### Don't

- ❌ Optimize without measuring
- ❌ Refactor without evidence of need
- ❌ Skip regression testing
- ❌ Make decisions based on opinion
- ❌ Create new patterns when existing ones work
- ❌ Forget to document why something was NOT done
- ❌ Mix Research Protocol with Research Report
- ❌ Jump from Evidence to Accepted Decisions (use Candidate Decisions)

### Do

- ✅ Measure before and after
- ✅ Document findings with evidence
- ✅ Run regression after every change
- ✅ Justify decisions with data
- ✅ Prefer existing architecture
- ✅ Record deferred work with rationale
- ✅ Separate Protocol from Report
- ✅ Use Candidate Decisions as intermediate step

## Quick Reference

### Finding → Decision Flow

```
Found something?
    ↓
Is it a problem? → No → Document and move on
    ↓ Yes
Can you fix it now? → No → Register Finding, defer
    ↓ Yes
Does it need research? → No → Implement, validate
    ↓ Yes
Create Research Question
    ↓
Gather Evidence
    ↓
Make Decision
    ↓
Implement
    ↓
Validate (regression)
    ↓
Close Finding
```

### Per-User-Story Cycle

```
1. Audit current state
2. Implement changes
3. Verify with tests/curl
4. Run regression
5. Record evidence
6. Register findings (if any)
7. Commit
8. Move to next US
```

---

*This methodology was developed through SPEC-001 and SPEC-002 of the SIGES project.*
*It was validated through SPEC-005 (Frontend Assessment) across two technological contexts.*
*It combines Software Engineering, Applied Research, and Architectural Governance.*
*Reusable across projects where evidence-based evolution is required.*
