---
name: testing-verification
description: Guide for planning and executing layered verification after code changes. Use this when adding features, fixing bugs, or refactoring behavior.
---

# Testing Verification Skill

Use this skill to design efficient, risk-based validation that starts narrow and expands to confidence.

## When to Activate
- Any non-trivial code/config change.
- Behavioral changes requiring confidence before release.
- Refactors that may affect compatibility.

## Required Inputs
- Changed files and impacted behavior.
- Existing test structure and tools.
- Risk areas (security, data integrity, performance, compatibility).

## Procedure
1. Map change surface to required validations.
2. Run nearest targeted tests first.
3. Add/update tests for changed business behavior.
4. Run broader checks (type/lint/build/integration) as needed.
5. Confirm negative and edge cases.
6. Record unresolved risks if full validation is not feasible.

## Validation Layers
- Unit: local logic and edge conditions.
- Integration: boundary contracts and dependencies.
- End-to-end/smoke: user-critical paths.
- Non-functional (when relevant): performance, reliability, security.

## Decision Rules
- Prefer smallest test set that can falsify the change quickly.
- Expand coverage proportionally to risk and blast radius.
- Treat flaky tests as signals to investigate, not ignore.

## Anti-Patterns
- Running only full-suite tests without targeted checks.
- Skipping edge/error path verification.
- Merging changes with unacknowledged test gaps.

## Output Template
1. Change Surface
2. Tests Executed
3. Results
4. Gaps/Risks
5. Release Confidence
