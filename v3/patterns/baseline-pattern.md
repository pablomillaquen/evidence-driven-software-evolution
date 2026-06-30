# Pattern — Baseline

**Weight**: Recommended

## Context

System state needs to be captured for future reference.

## Problem

How to create a reliable reference point for future evolution?

## Forces

- Must capture complete state
- Must be reproducible
- Must be verifiable
- Must not interfere with ongoing work

## Solution

1. Capture Current State
2. Validate Evidence Packages
3. Accept/Defer Candidate Decisions
4. Create Snapshot
5. Freeze Configuration
6. Reference Point Established

## Expected Outputs

- Baseline snapshot
- Configuration state
- Reference point

## Known Variations

- Technology Baseline
- Architecture Baseline
- Security Baseline
- Performance Baseline

## Anti-patterns

- Freezing incomplete evidence
- Not validating before freeze
- Missing configuration state
- Not creating snapshot
