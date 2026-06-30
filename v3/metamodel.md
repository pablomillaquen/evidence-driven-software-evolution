# EDSE Metamodel

**Weight**: Normative

## Purpose

The formal definition of EDSE entities and relationships. This is the absolute center of EDSE. It describes what exists, not how it is used.

## Three Views

```
                    Metamodel
                  (formal truth)
                    /        \
                   /          \
      Conceptual Model     Reference Architecture
   (textual definition)     (visual notation)
```

- **Metamodel**: This document — formal definition
- **Conceptual Model**: `conceptual-model/` — textual explanation of each entity
- **Reference Architecture**: `reference-architecture.md` — visual notation

## Entities

### Research Question

**Attributes**:
- ID
- Question
- Motivation
- Success Condition

### Assessment Goal

**Attributes**:
- ID
- Description
- Value (independently valuable)

### Evidence

**Attributes**:
- ID
- Type (Audit / Test / Metric / Comparison / Regression)
- Source
- Content
- Date

### Finding

**Attributes**:
- ID
- Category
- Severity (Critical / High / Medium / Low)
- Confidence (High / Medium / Low)
- Description
- Impact

### Candidate Decision

**Attributes**:
- ID
- Priority (P1 / P2 / P3)
- Status (Pending / Accepted / Deferred / Rejected)
- Rationale

### Decision

**Attributes**:
- ID
- Type (Operational / Technical / Architectural)
- Status (Pending / Accepted / Deferred / Rejected)
- Justification
- Consequences

### ADR Document

**Attributes**:
- ID
- Context
- Decision
- Consequences
- Alternatives

### Baseline

**Attributes**:
- ID
- Snapshot
- Configuration
- Date

### Technical Debt

**Attributes**:
- ID
- Category
- Status (Open / Resolved)
- Description

### Health Report

**Attributes**:
- ID
- Dimensions
- Scores
- Recommendations

## Relationships

### Research Question → Assessment Goal

- **Relationship**: operationalizes
- **Cardinality**: 1:N
- **Description**: A Research Question generates one or more Assessment Goals

### Assessment Goal → Evidence

- **Relationship**: collects
- **Cardinality**: 1:N
- **Description**: An Assessment Goal collects one or more Evidence items

### Evidence → Finding

- **Relationship**: supports
- **Cardinality**: N:M
- **Description**: Evidence supports Findings; a Finding may be supported by multiple Evidence items

### Research Question → Finding

- **Relationship**: originates
- **Cardinality**: 1:N
- **Description**: A Research Question originates one or more Findings

### Finding → Candidate Decision

- **Relationship**: feeds into
- **Cardinality**: 1:N
- **Description**: A Finding feeds into one or more Candidate Decisions

### Candidate Decision → Decision

- **Relationship**: accepted as
- **Cardinality**: 1:1
- **Description**: A Candidate Decision is accepted as exactly one Decision

### Decision → ADR Document

- **Relationship**: documents as
- **Cardinality**: 1:0..1
- **Description**: An Architectural Decision is documented as an ADR Document

### Decision → Implementation

- **Relationship**: implements
- **Cardinality**: 1:0..N
- **Description**: A Decision may be implemented in one or more changes

### Decision → Technical Debt

- **Relationship**: defers as
- **Cardinality**: 1:0..N
- **Description**: A Decision may be deferred as Technical Debt

### Decision → Baseline

- **Relationship**: freezes as
- **Cardinality**: N:1
- **Description**: Decisions are frozen into a Baseline

### Baseline → Health Report

- **Relationship**: generates
- **Cardinality**: 1:1
- **Description**: A Baseline generates a Health Report

### Health Report → Research Question

- **Relationship**: feeds into
- **Cardinality**: 1:N
- **Description**: A Health Report feeds into new Research Questions

## States

### Finding States

```
Discovery → Classification → Research → Decision → Implementation → Validation → Closure
```

### Decision States

```
Pending → Accepted / Deferred / Rejected
```

### Baseline States

```
Proposed → Validated → Frozen
```

## Diagram

```
Research Question ──── operationalizes ────► Assessment Goal
        │                                           │
        │ originates                               │ collects
        ▼                                           ▼
    Finding ◄────────── supports ──────────── Evidence
        │
        │ feeds into
        ▼
Candidate Decision
        │
        │ accepted as
        ▼
    Decision ─────┬──── documents as ────► ADR Document
                  │
                  ├── implements ────► Implementation
                  │
                  ├── defers as ────► Technical Debt
                  │
                  └── freezes as ────► Baseline
                                          │
                                          │ generates
                                          ▼
                                    Health Report
                                          │
                                          │ feeds into
                                          ▼
                                  Research Question (new iteration)
```
