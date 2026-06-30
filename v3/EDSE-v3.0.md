# EDSE Specification v3.0

**Version**: 3.0.0
**Date**: 2026-06-30
**Status**: Draft

## Introduction

EDSE (Evidence-Driven Software Evolution) is a methodology for incrementally evolving software systems. It separates discovery, research, design, and execution into distinct phases, each producing evidence-based artifacts.

## Core Concepts

### 1. Finding

An observation derived from evidence that identifies a problem or opportunity.

```
Observation → Evidence → Finding
```

**Properties**:
- Derived from evidence, not opinion
- Traceable to source data
- Classified by severity and confidence

### 2. Candidate Decision

A hypothesis for intervention that addresses a Finding.

```
Finding → Candidate Decision
```

**Properties**:
- Defines the business objective
- Remains stable throughout implementation
- Does not specify technical solution
- Can evolve based on research evidence

### 3. Implementation Research

The process of finding the best strategy to implement a Candidate Decision.

```
Candidate Decision → Research Questions → Evidence → Alternatives → Strategy
```

**Research Types**:
- **Assessment Research**: Discovers Findings and Candidate Decisions
- **Evolution Research**: Finds implementation strategy for accepted decisions

### 4. Implementation Strategy

The selected approach for implementing a Candidate Decision.

```
Research → Strategy Selection → Implementation Strategy
```

**Properties**:
- Selected from alternatives based on evidence
- Can be rejected if evidence warrants
- Documents rejected alternatives
- Justified with comparison matrix

### 5. Design

The technical specification of the selected Implementation Strategy.

```
Implementation Strategy → Design Specification
```

**Properties**:
- Does not explore alternatives (that's Research)
- Specifies exact implementation
- Defines scope, validations, risks
- Produces technical specifications

### 6. Execution Cycle

The repeatable pattern for implementing a Candidate Decision.

```
Implement → Validate → Produce Evidence → Decision Gate
```

**Properties**:
- Same pattern for every Candidate Decision
- Produces formal evidence artifacts
- Requires Decision Gate approval to proceed
- Independent of technology or domain

### 7. Evidence Gate

A formal checkpoint that requires evidence to proceed.

```
Evidence Gate Criteria → Evidence Review → Gate Decision (PASS/FAIL)
```

**Properties**:
- Blocking: cannot proceed without PASS
- Based on evidence, not opinion
- Documents gate criteria and results
- Can reject if evidence insufficient

### 8. Release Baseline

The immutable reference point after successful implementation.

```
All Evidence Gates PASS → Release Baseline Established
```

**Properties**:
- Frozen state of the system
- Reference for future regression validation
- Documents version, changes, and evidence
- Never modified after creation

## Metamodel

```
Business Objective
        │
        ▼
    Finding
        │
        ▼
Candidate Decision
        │
        ▼
Implementation Research
        │
        ▼
Implementation Strategy
        │
        ▼
    Design
        │
        ▼
Execution Cycle
 ├── Implement
 ├── Validate
 ├── Produce Evidence
 └── Evidence Gate
        │
        ▼
Release Baseline
```

## Process Flow

### Phase 1: Assessment

**Purpose**: Discover problems and opportunities

**Input**: System observation, user feedback, evidence

**Output**: Findings and Candidate Decisions

```
Observation → Evidence → Finding → Candidate Decision
```

### Phase 2: Implementation Research

**Purpose**: Find the best strategy for each Candidate Decision

**Input**: Accepted Candidate Decisions

**Output**: Implementation Strategies

```
Candidate Decision → Research Questions → Evidence → Alternatives → Strategy
```

### Phase 3: Design

**Purpose**: Specify the technical implementation

**Input**: Implementation Strategies

**Output**: Technical Specifications

```
Implementation Strategy → Design Specification
```

### Phase 4: Execution

**Purpose**: Implement, validate, and document

**Input**: Design Specifications

**Output**: Evidence, Release Baseline

```
Design → Execution Cycle → Evidence Gate → Release Baseline
```

## Evidence Types

### Transformation Evidence

Proves that the objective was achieved.

**Examples**:
- Implementation Report (what was changed)
- Compilation output
- Test results

### Preservation Evidence

Proves that functional equivalence was maintained.

**Examples**:
- Regression Report (test comparison)
- Smoke test results
- Console inspection

### Health Evidence

Proves that system health was maintained or improved.

**Examples**:
- Health Report (metrics)
- Performance comparison
- Dependency analysis

## Document Responsibilities

| Document | Responsibility |
|----------|----------------|
| **Assessment** | Discover problems |
| **Candidate Decisions** | Define desired intervention |
| **Research** | Find best strategy |
| **Design** | Specify exact solution |
| **Tasks** | Organize execution |
| **Reports** | Demonstrate outcomes |
| **Baseline** | Freeze new state |

## Scalability

### Single Decision SPEC

```
SPEC
 └── Candidate Decision
      └── Research → Design → Execution → Baseline
```

### Multiple Decision SPEC

```
SPEC
 ├── Candidate Decision D-001
 │    └── Research → Design → Execution → Gate
 ├── Candidate Decision D-002
 │    └── Research → Design → Execution → Gate
 └── Candidate Decision D-003
      └── Research → Design → Execution → Gate
      ↓
Release Baseline
```

## Key Principles

1. **Candidate Decisions are hypotheses** — they can evolve based on evidence
2. **Research refines decisions** — implementation strategy may differ from original assumption
3. **Evidence Gates are blocking** — cannot proceed without evidence
4. **Design specifies, Research discovers** — no overlap
5. **Execution Cycle is repeatable** — same pattern for every decision
6. **Baselines are immutable** — never modified after creation

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v1.0.0 | 2026-06-24 | Initial methodology |
| v2.0.0 | 2026-06-27 | Metamodel formalization |
| v3.0.0 | 2026-06-30 | Execution Cycle, Implementation Strategy, Evidence Gates |
