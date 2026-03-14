---
name: debugging-root-cause
description: Guide for isolating root causes of defects with fast, evidence-based debugging. Use this when fixing bugs, regressions, flaky behavior, or production incidents.
---

# Debugging Root Cause Skill

Symptom → verified root cause → minimal fix → regression check.

## When to Activate
- Bug, regression, crash, or inconsistent behavior reported.
- Tests fail with unclear reason.
- Production-like environment errors.

## Procedure
1. Reproduce reliably with smallest possible case.
2. Capture evidence (error output, stack trace, inputs, environment).
3. Localize failure boundary (module, function, dependency, data path).
4. Build and test hypotheses one by one — change one variable at a time.
5. Identify root cause and contributing factors.
6. Implement minimal fix at source of defect.
7. Verify with targeted tests, then broader regression checks.

## Decision Rules
- Facts from repro/logs over assumptions.
- Fix root mechanism, not downstream symptoms.
- No success without regression verification.

## Anti-Patterns
- Patching without reproducible evidence.
- Mixing multiple speculative fixes in one step.
- Declaring success without regression verification.

## Output Template
Symptom → Root Cause → Fix → Verification → Residual Risk.
