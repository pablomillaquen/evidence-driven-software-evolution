# EDSE Governance

## Purpose

Rules for governing EDSE itself. This document applies EDSE to EDSE.

## Governance Rules

### Rule 1: Classification

Every new addition to EDSE must be classified as one of these types:

- Foundation
- Conceptual Model Entity
- Principle
- Process
- Artifact
- Pattern
- Template

### Rule 2: Validation

If a concept cannot be clearly classified in one of these categories, it must not be incorporated yet. It must first be validated through new applications of EDSE.

### Rule 3: Evidence

Every new addition must have emerged in at least one real application of EDSE before being considered part of the Core.

### Rule 4: Evolution

EDSE may grow by adding:
- New processes
- New artifacts
- New patterns
- New principles

Without modifying Conceptual Model or Foundations.

### Rule 5: Metamodel Changes

**Modifications to the Metamodel require evidence obtained from multiple independent applications of EDSE. No change to the conceptual core may be introduced solely by design preference.**

This rule ensures EDSE applies to itself: the methodology evolves based on evidence, not continuous redesign.

## Version Strategy

| Version | Strategy |
|---------|----------|
| EDSE v2.0 | Freeze conceptual architecture. Only minor corrections. |
| EDSE v2.x | Validate through real applications. Collect evidence. |
| EDSE v3.0 | Only if evidence justifies. Changes to metamodel. |

## Validation Criteria

EDSE v2.0 should be considered stable when it can describe, without modifications, at least three distinct projects:

1. SIGES API (Laravel) — ✅ Validated
2. SIGES Web Client (Angular) — ✅ Validated
3. Third project (TBD) — Pending
