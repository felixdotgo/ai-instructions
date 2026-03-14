---
name: clean-code-refactor
description: Guide for safe, incremental refactoring that improves readability and maintainability without changing intended behavior. Use this for technical debt reduction and code quality improvements.
---

# Clean Code Refactor Skill

Behavior-preserving refactors with clear intent and low risk.

## When to Activate
- Code is hard to read, duplicate, overly coupled, or brittle.
- User requests cleanup, simplification, or maintainability improvement.
- New feature work exposes structural debt.

## Procedure
1. Define invariants (what must not change).
2. Identify highest-value refactor target.
3. Apply one focused step at a time — keep public contracts stable.
4. Re-run targeted tests after each logical step.
5. Document trade-offs and remaining debt.

## Decision Rules
- Prefer clarity over cleverness.
- Prefer incremental, reversible changes.
- Stop when readability and maintainability goals are met.

## Anti-Patterns
- Large rewrites with mixed concerns.
- Changing behavior under "refactor" label.
- Introducing abstractions without repeated use cases.

## Output Template
Goal → Changes → Verification → Residual Risk.
