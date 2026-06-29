# Conceptual Model — Assessment Goals

**Weight**: Normative

## Entity

**Assessment Goal**: A concrete, independently valuable objective that operationalizes a Research Question.

See: `metamodel.md` for formal definition.

## Attributes

| Attribute | Type | Values |
|-----------|------|--------|
| ID | string | AG-XXX format |
| Description | string | What this goal achieves |
| Value | string | Why it is independently valuable |

## Relationships

- **operationalizes** → Research Question (N:1)
- **collects** → Evidence (1:N)

## Purpose

Assessment Goals replace User Stories when no functional user exists. They operationalize Research Questions into concrete investigation objectives.

## Rules

- Each Assessment Goal must be independently valuable
- Assessment Goals drive Evidence collection
