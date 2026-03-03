---
name: debugging-root-cause
description: Guide for isolating root causes of defects with fast, evidence-based debugging. Use this when fixing bugs, regressions, flaky behavior, or production incidents.
---

# Debugging Root Cause Skill

Use this skill to drive bug investigation from symptom to verified root cause before implementing fixes.

## When to Activate
- User reports a bug, regression, crash, or inconsistent behavior.
- Tests fail and failure reason is unclear.
- Errors occur in production-like environments.

## Required Inputs
- Repro steps and observed behavior.
- Expected behavior.
- Recent changes, logs, and failing tests (if available).

## Procedure
1. Reproduce reliably with the smallest possible case.
2. Capture evidence (error output, stack trace, inputs, environment).
3. Localize failure boundary (module, function, dependency, data path).
4. Build and test hypotheses one by one.
5. Identify the root cause and contributing factors.
6. Implement minimal fix at source of defect.
7. Verify with targeted tests, then broader regression checks.

## Decision Rules
- Prefer facts from repro/logs over assumptions.
- Change one variable at a time during investigation.
- Fix the root mechanism, not only downstream symptoms.

## Anti-Patterns
- Patching without reproducible evidence.
- Mixing multiple speculative fixes in one step.
- Declaring success without regression verification.

## Output Template
1. Symptom
2. Repro
3. Root Cause
4. Fix
5. Verification
6. Residual Risk
