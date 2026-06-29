# EDSE — Vocabulary

## Primary Entities

| Entity | Definition |
|--------|------------|
| **Research Question** | A guiding question that frames investigation scope |
| **Assessment Goal** | A concrete, independently valuable objective that operationalizes a Research Question |
| **Evidence** | Objective data supporting findings and decisions |
| **Finding** | An identified observation with severity and confidence |
| **Candidate Decision** | An intermediate step between evidence and acceptance |
| **Decision** | An accepted choice with justification and consequences |
| **ADR Document** | Documented representation of an Architectural Decision |
| **Baseline** | A frozen reference point for future comparison |
| **Technical Debt** | Deferred work traced back to a Decision |
| **Health Report** | Summary of technology health dimensions |

## Severity Levels

| Level | Definition |
|-------|------------|
| **Critical** | Blocks further progress or creates immediate risk |
| **High** | Significant impact on quality or maintainability |
| **Medium** | Moderate impact, can be deferred |
| **Low** | Minor impact, nice-to-have improvement |

## Confidence Levels

| Level | Definition |
|-------|------------|
| **High** | Strong evidence, clear link to Research Question |
| **Medium** | Moderate evidence, reasonable inference |
| **Low** | Weak evidence, requires further investigation |

## Decision Types

| Type | Scope | Documentation |
|------|-------|---------------|
| **Operational** | Process changes, workflow adjustments | Decision record |
| **Technical** | Library choices, implementation approaches | Decision record |
| **Architectural** | System-wide design choices | ADR Document |

## Artifact Weight Levels

| Level | Content | Change Rules |
|-------|---------|--------------|
| **Normative** | Foundations, Metamodel, Constraints, Conceptual Model | Governance approval required |
| **Recommended** | Principles, Processes, Patterns | Evidence from applications |
| **Informative** | Templates, Artifacts | Free evolution |
