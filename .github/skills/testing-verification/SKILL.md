---
name: testing-verification
description: Guide for planning and executing layered verification after code changes. Use this when adding features, fixing bugs, or refactoring behavior.
---

# Testing Verification Skill

Risk-based validation: start narrow, expand to confidence.

## When to Activate
- Any non-trivial code/config change.
- Behavioral changes requiring confidence before release.
- Refactors that may affect compatibility.

## Procedure
1. Map change surface to required validations.
2. Run nearest targeted tests first (unit → integration → e2e/smoke).
3. Add/update tests for changed business behavior.
4. Run broader checks (type/lint/build) as needed.
5. Confirm negative and edge cases.
6. Record unresolved risks if full validation is not feasible.

## Decision Rules
- Smallest test set that can falsify the change quickly.
- Expand coverage proportionally to risk and blast radius.
- Flaky tests are signals to investigate, not ignore.

## Anti-Patterns
- Running only full-suite without targeted checks.
- Skipping edge/error path verification.
- Merging with unacknowledged test gaps.

## Output Template
Change Surface → Tests Executed → Results → Gaps/Risks.
