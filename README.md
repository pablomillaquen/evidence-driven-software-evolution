# Evidence-Driven Software Evolution Methodology

**Version**: 1.0
**Status**: Specification
**Developed through**: SIGES Project (SPEC-001, SPEC-002)

---

> Every change must answer three questions:
>
> **Why?**
> **How do we know?**
> **Did it improve?**

---

## What Is This?

A methodology for evolving software systems with evidence, traceability, and architectural control. It governs **how to decide** what to do and **how to prove** it was done right.

Unlike process frameworks (Scrum, Kanban), this methodology focuses on **engineering decisions** — not project management.

## What This Is NOT

- Not Scrum, Kanban, or project management
- Not a software architecture (DDD, Clean Architecture)
- Not a testing framework (TDD, BDD)
- Not a coding standard

**It complements them.** It adds evidence-based governance to whatever process you use.

## When to Use

**Best suited for:**
- Legacy modernization
- Large refactoring
- Production hardening
- Technical debt reduction
- Compliance projects
- AI-assisted development
- Long-lived systems

**Probably unnecessary for:**
- Weekend hacks
- Throwaway prototypes
- Simple CRUD apps

---

## Core Principles

1. **Research Before Implementation** — Findings before fixes
2. **Evidence Over Intuition** — Confidence, not just code
3. **Architectural Guardrails** — Prove new patterns are needed
4. **Measure First** — Baselines before optimization
5. **Regression First** — Every change must prove nothing broke
6. **Baseline Freeze** — Verified states become foundations
7. **Complete Traceability** — Finding to release, fully linked

---

## The Engineering Evidence Cycle

```
Discover → Investigate → Decide → Implement → Validate → Freeze
```

Each cycle creates a **frozen baseline** — the foundation for the next evolution.

---

## The Two Layers

### Research Layer (Thinking)

```
Finding → Research Question → Evidence → Decision
```

### Engineering Layer (Doing)

```
SPEC → Tasks → Implementation → Regression → Release
```

**Every engineering action must be preceded by a research decision.**

---

## Quick Start

1. **Find something**: Code inspection, test failure, metric
2. **Create Finding**: Document what you found
3. **Research**: Gather evidence, ask questions
4. **Decide**: Fix, defer, or document
5. **Implement**: If fixing
6. **Validate**: Run regression
7. **Release**: Create new baseline

---

## Documentation Structure

| Document | Purpose |
|----------|---------|
| **README.md** | This file — introduction and overview |
| **SKILL.md** | Normative specification — rules, vocabulary, artifacts |
| **REFERENCE.md** | Examples, case studies, FAQ |
| **templates/** | Practical templates for all artifacts |

---

## Real-World Results

This methodology was validated through two specifications of the SIGES medical system:

- **85** functional scenarios validated
- **79** stabilization tasks completed
- **12** user stories across 4 phases
- **5** Architecture Decision Records
- **4** Mermaid architecture diagrams
- **34** PASS, **11** FAIL (all pre-existing)
- **100%** endpoints under 0.35s response time
- Complete traceability from finding to release

---

## Learn More

- **SKILL.md**: Complete normative specification
- **REFERENCE.md**: Real examples from SIGES project
- **templates/**: Ready-to-use templates

---

*Version 1.0 — Developed through evidence, not theory.*
