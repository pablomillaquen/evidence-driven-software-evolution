---
name: Evidence-Driven Software Evolution
description: A methodology for evolving software systems with evidence, traceability, and architectural control. Includes vocabulary, evidence levels, finding taxonomy, SPEC types, baseline management, and complete traceability model.
---

# Evidence-Driven Software Evolution — Normative Specification

**Version**: 1.2
**Status**: Specification
**Type**: Normative (rules must be followed)

---

## 1. Vocabulary

### 1.1 Core Terms

| Term | Definition |
|------|------------|
| **Finding** | Observed fact requiring investigation. An anomaly, issue, or opportunity identified through inspection, testing, or measurement. |
| **Research Question** | Question created to resolve uncertainty about a Finding. Bridges discovery and decision. |
| **Evidence** | Verifiable proof supporting a claim. Must be reproducible and traceable. |
| **Decision** | Chosen course of action supported by evidence. May or may not become an ADR. |
| **ADR** | Architecture Decision Record. A Decision that affects system architecture and will be referenced by future work. |
| **SPEC** | Specification. A structured document defining what will be done, why, and how it will be validated. |
| **Baseline** | Frozen, validated system state that becomes the foundation for future work. |
| **Regression** | Test execution proving that existing functionality remains intact after changes. |
| **Release** | Official closure of a SPEC, creating a new Baseline. |
| **Technical Debt** | Documented consequence of a deferred Finding. Not a Finding itself — it is born from one. |

### 1.2 Action Terms

| Term | Definition |
|------|------------|
| **Freeze** | Officially marking a Baseline as the reference state for future work. |
| **Stabilize** | Improving system quality without changing user-facing behavior. |
| **Validate** | Proving through evidence that a change achieved its intended effect without side effects. |
| **Defer** | Documenting a Finding for resolution in a future SPEC. |
| **Close** | Marking a Finding as fully resolved with evidence. |

---

## 2. Levels of Evidence

Evidence is classified into six levels, from least to most reliable:

| Level | Name | Description | Example |
|-------|------|-------------|---------|
| **E0** | Opinion | Subjective belief without data | "I think this is slow" |
| **E1** | Code Inspection | Reading code to understand behavior | "Controller has no validation" |
| **E2** | Static Analysis | Automated code analysis | PHPStan, ESLint results |
| **E3** | Automated Test | Test execution proving behavior | PHPUnit, Jest results |
| **E4** | Measured Metric | Quantified before/after comparison | "Response time: 0.3s → 0.1s" |
| **E5** | Production Observation | Real-world behavior monitoring | APM logs, error rates |

### Rules

1. **Minimum E1** for all Findings (must inspect code)
2. **Minimum E3** for all code changes (must have tests)
3. **E4 required** for performance claims
4. **E0 never qualifies** as evidence (opinion is not evidence)

### Decision Recording

Every Decision must record its Evidence Level:

```
**Evidence Level**: E3
**Evidence**: PHPUnit test results (34 PASS, 11 FAIL)
```

---

## 3. Finding Taxonomy

Findings are categorized by their nature:

| Category | Description | Examples |
|----------|-------------|----------|
| **Functional** | Behavior doesn't match expectations | Wrong status code, missing field |
| **Architecture** | Structural concerns | Fat controller, missing service |
| **Performance** | Speed, memory, or query issues | Slow response, N+1 query |
| **Security** | Vulnerability or exposure | Missing auth, stack trace leak |
| **Documentation** | Missing or incorrect docs | Undocumented endpoint |
| **Compliance** | Regulatory or standard gaps | Missing audit trail |
| **Technical Debt** | Suboptimal implementation | Code duplication, hardcoded values |
| **Regression** | Broken existing functionality | Test failure after change |
| **Usability** | User experience issues | Confusing error message |

### Rules

1. Every Finding must have a Category
2. Category affects severity assessment
3. Categories enable statistics and prioritization

---

## 4. Finding Lifecycle

### States

```
OPEN → INVESTIGATING → DECISION → IMPLEMENTED → VALIDATED → CLOSED
```

| State | Description | Entry Criteria |
|-------|-------------|----------------|
| **OPEN** | Problem identified | Finding created |
| **INVESTIGATING** | Research in progress | Research Question created |
| **DECISION** | Decision made | Decision documented with evidence |
| **IMPLEMENTED** | Code changed | Commit completed |
| **VALIDATED** | Regression passed | Tests pass, evidence recorded |
| **CLOSED** | Fully resolved | All validation complete |

### Resolution Types

| Type | When to Use | Result |
|------|-------------|--------|
| **FIXED** | Problem resolved in this SPEC | Finding → CLOSED |
| **DEFERRED** | Problem documented for future SPEC | Finding → CLOSED + Technical Debt created |
| **DOCUMENTED** | Problem noted, no action needed | Finding → CLOSED |

### Dual Path

Findings can follow two paths:

**Path A: Implementation**

```
Finding → Research → Decision → Implementation → Validation → CLOSED
```

**Path B: Documentation**

```
Finding → Research → Decision → No implementation → Document → CLOSED
```

Both paths are valid. Not every Finding requires code changes.

---

## 5. Technical Debt Model

### Birth

Technical Debt is born from a deferred Finding:

```
Finding (DEFERRED)
    ↓
Technical Debt Documented
    ↓
Registered in Baseline
    ↓
Tracked in Future SPEC
```

### Rules

1. Technical Debt never exists alone — it always traces to a Finding
2. Every Technical Debt entry must include:
   - Original Finding ID
   - Why it was deferred
   - Impact assessment
   - Suggested future SPEC
3. Technical Debt is reviewed at each Baseline creation

---

## 6. Decision Model

### Decision vs ADR

> **Every ADR is a Decision. Not every Decision deserves an ADR.**

| Criteria | Decision | ADR |
|----------|----------|-----|
| Scope | Operational or technical | Architectural |
| Impact | Localized | System-wide |
| Duration | May be temporary | Permanent reference |
| Documentation | Decision template | ADR template |

### Decision Confidence

| Level | Criteria |
|-------|----------|
| **High** | Multiple evidence sources, clear metrics, no ambiguity |
| **Medium** | Single evidence source, reasonable confidence |
| **Low** | Limited evidence, assumptions made, needs future validation |

### Decision Recording

```
## D-XXX: [Title]

**Status**: ACCEPTED / DEFERRED / REJECTED
**Type**: OPERATIONAL / TECHNICAL / ARCHITECTURAL
**Confidence**: HIGH / MEDIUM / LOW
**Evidence Level**: E1 / E2 / E3 / E4 / E5
**Date**: [Date]
```

---

## 7. SPEC Model

### SPEC Types

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

### SPEC Structure

| Document | Required | Purpose |
|----------|----------|---------|
| `spec.md` | Yes | What and why (frozen during implementation) |
| `plan.md` | Yes | How (phases, tasks, traceability) |
| `research.md` | Yes | Decisions with justification |
| `data-model.md` | Conditional | Entities affected (if schema changes) |
| `quickstart.md` | Yes | Validation scenarios |
| `tasks.md` | Yes | Task list with status |
| `checklists/` | Yes | Quality gates |
| `evidence/` | Yes | All proof artifacts |

### SPEC Lifecycle

```
Draft → Research → Planning → Implementation → Validation → Closure
```

### Frozen State

During implementation, `spec.md`, `plan.md`, `research.md`, and `tasks.md` are frozen. Unexpected behavior → register Finding, evaluate, defer if scope change.

---

## 8. Baseline Model

### Components

| Component | Required | Description |
|-----------|----------|-------------|
| Version | Yes | Semantic version with status tag |
| Regression | Yes | Test results (PASS/FAIL) |
| Functional State | Yes | What works and how |
| Performance | Conditional | Metrics if measured |
| Technical Debt | Yes | What was deferred |
| ADRs | Yes | Architectural decisions made |
| Documentation | Yes | What was generated |

### Freeze Cycle

```
Validated Baseline
    ↓
Freeze (tag version)
    ↓
New SPEC (starts from frozen baseline)
    ↓
Implementation
    ↓
Regression (verify no breakage)
    ↓
Release Report
    ↓
New Frozen Baseline
```

### Rules

1. Every Baseline must have a Git tag
2. Every Baseline must include regression results
3. Every Baseline must list Technical Debt
4. Baselines are immutable once frozen

---

## 9. Traceability Model

### Chain

```
US → Decision → Task → Commit → Evidence → Regression → Finding → CLOSED
```

### Required Links

| From | To | Required |
|------|----|----------|
| Finding | Research Question | Yes (if investigated) |
| Research Question | Decision | Yes |
| Decision | ADR | If architectural |
| Decision | Tasks | Yes (if implemented) |
| Tasks | Commit | Yes |
| Commit | Evidence | Yes |
| Evidence | Regression | Yes |
| Regression | Finding | If new Finding discovered |

### Tracking Format

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

---

## 10. Regression Model

### When to Run

1. **After each user story**: Quick validation
2. **After each phase**: Full regression
3. **Before release**: Complete regression
4. **When unexpected behavior**: Targeted regression

### Baseline Comparison

Always compare to previous Baseline:

| Version | PASS | FAIL | Notes |
|---------|------|------|-------|
| Pre-change | 35 | 10 | Baseline |
| Post-US01 | 35 | 10 | No change |
| Post-US02 | 36 | 9 | +1 PASS |

### Rules

1. Never merge with new regressions
2. Flaky tests must be identified and documented
3. Pre-existing failures are tracked separately
4. Regression results are part of Baseline

---

## 11. Release Model

### Release Report

The Release Report officially closes a SPEC and creates a new Baseline.

```
SPEC → Tasks → Evidence → Regression → Release Report → Frozen Baseline
```

### Required Sections

| Section | Required |
|---------|----------|
| Executive Summary | Yes |
| Objectives | Yes |
| Scope | Yes |
| Work Completed | Yes |
| Metrics | Yes |
| Findings | Yes |
| ADRs | Yes |
| Technical Debt | Yes |
| Baseline | Yes |

### Tagging

```bash
git tag -a vX.Y.Z-[status] -m "Release description"
```

---

## 12. Metrics

### Engineering Metrics

| Metric | Description |
|--------|-------------|
| Traceability Completeness | % of changes with full traceability chain |
| Regression Coverage | % of features covered by regression tests |
| Evidence Coverage | % of decisions backed by evidence (min E1) |
| Evidence Level Average | Average evidence level across decisions |
| Finding Closure Rate | % of Findings resolved (not deferred) |
| Technical Debt Ratio | Deferred Findings / Total Findings |

### Project Metrics

| Metric | Description |
|--------|-------------|
| SPEC Completion | % of SPECs completed successfully |
| Baseline Stability | Consecutive releases without regression |
| Duration | Time from SPEC start to Baseline |
| Tasks Completed | Total tasks implemented |
| Scope Changes | Findings that changed SPEC scope |
| Commits | Total commits in SPEC |
| Files Modified | Total files changed |

### Rules

1. Metrics are recorded at each Baseline
2. Metrics are compared between Baselines
3. Trends are more important than absolute values

---

## 13. Documentation Architecture

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

---

## 14. Health Report Model

### Purpose

The Health Report communicates **the current state of the system** to clients, management, or audits. While Evidence demonstrates **what was done**, the Health Report communicates **what the system looks like now**.

### Health Report as EDSE Artifact

**Name**: System Health Artifact (or Operational Health Report)

**Reusable Domains**:
- Dependency Health
- Security Health
- Architecture Health
- Test Health
- API Health
- Documentation Health
- Maintainability Health
- Performance Health

### Health Report Structure

| Component | Required | Description |
|-----------|----------|-------------|
| **Dimensions** | Yes | Individual assessments per domain (primary information) |
| **Overall Assessment** | Yes | Visual summary of dimensions |
| **Gating Rules** | Yes | Minimum criteria that override numeric assessment |
| **Baseline Comparison** | Yes | Before/after metrics |
| **Trend** | Conditional | Historical comparison across versions |
| **Accepted Debt** | Yes | Documented technical debt with justification |

### Health Dimensions

Each Health Report contains dimension indicators:

| Dimension | Weight | Description |
|-----------|--------|-------------|
| Security | 35% | Vulnerability status |
| Regression Stability | 25% | Test baseline maintenance |
| Compatibility | 20% | Dependency compatibility |
| Freshness | 10% | Dependency currency |
| Maintainability | 10% | Code quality indicators |

### Gating Rules

Gating rules override numeric assessment:

```
IF Critical CVE exists THEN Overall Status = "At Risk"
IF regression ≠ baseline THEN Overall Status = "At Risk"
```

This prevents high scores from masking critical issues.

### Rules

1. Every Health Report must have Dimensions
2. Every Health Report must have Gating Rules
3. Every Health Report must include Baseline Comparison
4. Dimensions are the primary information; Overall Assessment is summary
5. Health Reports are repeatable across SPECs (same formulas)

---

## 15. Health Metrics Model

### Purpose

Health Metrics define calculation formulas for Health Dimensions, making Health Reports repeatable and comparable across SPECs.

### Document Location

`docs/platform/health-metrics.md` (permanent, reusable across SPECs)

### Metric Structure

```markdown
## Security Dimension

**Formula**: 
- 100 = 0 Critical + 0 High CVEs
- 90 = 0 Critical + 1 High CVE
- 70 = 1 Critical CVE
- 50 = 2+ Critical CVEs

**Weight**: 35%
```

### Finding Types for Health Reports

| Type | Description | Examples |
|------|-------------|----------|
| **Security** | Vulnerability findings | CVE, missing auth |
| **Compatibility** | Breaking changes | API changes, deprecations |
| **Maintenance** | Unmaintained packages | Abandoned dependencies |
| **Governance** | Process gaps | Missing reviews, deferred debt |
| **Performance** | Speed/regression | Response time degradation |
| **Documentation** | Missing docs | Undocumented changes |

### Rules

1. Metrics must be defined before generating Health Reports
2. Metrics must be documented in `health-metrics.md`
3. Same metrics must be used across SPECs for comparability
4. Finding Types enable aggregate analysis across Health Reports

---

## 16. Accepted Technical Debt Model

### Purpose

Accepted Technical Debt is distinct from Deferred Debt. It represents **conscious decisions to accept risk** with documented justification and deadline.

### Distinction

| Concept | When Created | Purpose |
|---------|--------------|---------|
| **Deferred Debt** | Finding deferred to future SPEC | Will be resolved later |
| **Accepted Debt** | Decision to accept risk | Will NOT be resolved unless conditions change |

### Accepted Debt Structure

```markdown
## ATD-XXX: [Package Name]

**Reason**: Why the update is deferred
**Risk Acceptance**: What risk is accepted
**Deadline**: When this debt must be revisited
**Justification**: Business/technical justification
**Owner**: Who accepted this debt
```

### Example

```markdown
## ATD-001: dompdf/dompdf

**Reason**: Updating to v2.x breaks Laravel integration
**Risk Acceptance**: PDF generation may have rendering differences
**Deadline**: Q4 2026 (before Laravel 12 upgrade)
**Justification**: Current version works; upgrade not critical for operations
**Owner**: Tech Lead
```

### Rules

1. Accepted Debt must have a Deadline
2. Accepted Debt must have a Justification
3. Accepted Debt must have an Owner
4. Accepted Debt is reviewed at each Baseline creation
5. Accepted Debt appears in Health Reports

---

## 17. Governance Feedback Model

### Purpose

The Health Report is not the end of the cycle. It is the **generator of the next iteration**. Governance Feedback closes the loop between system state and future investigation.

### The Complete EDSE Cycle

```
Question
    ↓
Investigation
    ↓
Findings
    ↓
Decisions
    ↓
Implementation
    ↓
Evidence
    ↓
Health Report (State of the System)
    ↓
Governance Feedback (New Questions)
    ↓
Next Iteration
```

### How Governance Feedback Works

1. **Health Report identifies weakness** (e.g., Maintainability = 58)
2. **New Research Question born** (e.g., "Why is maintainability low?")
3. **New Finding registered** (e.g., H-031: Maintainability below threshold)
4. **New SPEC created** (e.g., SPEC-009: Maintainability improvement)
5. **Cycle repeats**

### Example Flow

```
Health Report: Maintainability = 58
    ↓
PI-031: Why is maintainability low?
    ↓
H-031: Controllers exceed complexity threshold
    ↓
D-031: Extract services from controllers
    ↓
SPEC-009: Controller decomposition
    ↓
Evidence: Reduced complexity
    ↓
Health Report: Maintainability = 82
    ↓
Governance Feedback: Continue monitoring
```

### Rules

1. Every Health Report must be reviewed for Governance Feedback
2. Low dimensions (< 70) automatically generate Research Questions
3. Governance Feedback is documented in `research.md`
4. The cycle never truly ends — it evolves continuously

---

## 18. Anti-Patterns

### Never

- ❌ Optimize without measuring (violates Measure First)
- ❌ Refactor without evidence of need (violates Evidence Over Intuition)
- ❌ Skip regression testing (violates Regression First)
- ❌ Make decisions based on E0 evidence (violates Evidence Levels)
- ❌ Create new patterns when existing ones work (violates Guardrails)
- ❌ Forget to document why something was NOT done (violates Traceability)
- ❌ Allow Technical Debt without a Finding (violates Debt Model)
- ❌ Generate Health Report without Gating Rules (violates Health Report Model)
- ❌ Accept Technical Debt without Deadline (violates Accepted Debt Model)
- ❌ Use different Health Metrics across SPECs (violates comparability)
- ❌ Treat Health Report as final deliverable (violates Governance Feedback)

### Always

- ✅ Measure before and after (E4 required for performance)
- ✅ Document Findings with evidence (min E1)
- ✅ Run regression after every change
- ✅ Justify decisions with data
- ✅ Prefer existing architecture
- ✅ Record deferred work with rationale
- ✅ Link every artifact in the traceability chain
- ✅ Include Gating Rules in Health Reports
- ✅ Document Accepted Technical Debt with justification
- ✅ Use consistent Health Metrics across SPECs
- ✅ Generate new Research Questions from Health Report weaknesses

---

## 19. Quick Reference

### The Three Questions

```
Why?            → Finding + Research + Decision
How do we know? → Evidence + Metrics (min E1)
Did it improve? → Regression + Comparison + Health Report
```

### The Complete EDSE Cycle

```
Question → Investigation → Findings → Decisions → Implementation → Evidence → Health Report → Governance Feedback → Next Question
```

### Engineering Evidence Cycle

```
Discover → Investigate → Decide → Implement → Validate → Report → Feedback
```

### Baseline Freeze

```
Baseline → Freeze → SPEC → Evidence → Regression → Health Report → Governance Feedback → Release → Freeze → Next SPEC
```

### Finding Resolution Flow

```
Found something?
    ↓
Is it a problem? → No → Document and move on
    ↓ Yes
Does it need research? → No → Decide directly
    ↓ Yes
Create Research Question
    ↓
Gather Evidence (min E1)
    ↓
Make Decision (record Confidence)
    ↓
Implement? → Yes → Code → Validate → CLOSED
    ↓ No
Document → Create Technical Debt → CLOSED
```

---

*Version 1.2 — Normative Specification*
*This document defines the rules that must be followed when applying the methodology.*
*Changes in v1.1: Added Health Report Model, Health Metrics Model, Accepted Technical Debt Model.*
*Changes in v1.2: Added Governance Feedback Model (complete cycle).*
