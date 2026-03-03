---
name: clean-code-refactor
description: Guide for safe, incremental refactoring that improves readability and maintainability without changing intended behavior. Use this for technical debt reduction and code quality improvements.
---

# Clean Code Refactor Skill

Use this skill to perform behavior-preserving refactors with clear intent and low risk.

## When to Activate
- Code is hard to read, duplicate, overly coupled, or brittle.
- User requests cleanup, simplification, or maintainability improvement.
- New feature work exposes structural debt.

## Required Inputs
- Current implementation and pain points.
- Existing tests and expected behavior contracts.
- Scope boundaries and non-goals.

## Procedure
1. Define invariants (what must not change).
2. Identify highest-value refactor target.
3. Apply one focused refactor step at a time.
4. Keep public contracts stable unless explicitly approved.
5. Re-run targeted tests after each logical step.
6. Document trade-offs and remaining debt.

## Refactor Priorities
- Clarify naming and control flow.
- Reduce duplication with proven abstractions.
- Isolate side effects from domain logic.
- Simplify interfaces and boundaries.

## Decision Rules
- Prefer clarity over cleverness.
- Prefer incremental, reversible changes.
- Stop when readability and maintainability goals are met.

## Anti-Patterns
- Large rewrites with mixed concerns.
- Changing behavior under “refactor” label.
- Introducing abstractions without repeated use cases.

## Output Template
1. Refactor Goal
2. Invariants
3. Changes Applied
4. Verification
5. Remaining Debt
