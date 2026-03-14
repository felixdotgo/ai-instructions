---
name: delivery-sdlc-execution
description: Guide for executing software tasks end-to-end across SDLC gates. Use this when work requires planning, implementation, verification, release readiness, and operational handoff.
---

# Delivery SDLC Execution Skill

End-to-end delivery across SDLC gates (follows core protocol gates A-I).

## When to Activate
- Multi-step implementation with quality and release expectations.
- Changes requiring coordination across code, tests, docs, and ops.
- Non-trivial rollout or rollback risk.

## Procedure
1. **Scope**: define objective, acceptance criteria, constraints.
2. **Analyze + Design**: map dependencies/risk, choose approach, document trade-offs.
3. **Build**: minimal, focused, reversible changes.
4. **Verify**: targeted checks first → broader checks.
5. **Release + Operate**: rollout/rollback plan, observability, ownership updates, docs/changelog.

## Decision Rules
- Scope aligned to requested outcome.
- Assumptions explicit when unavoidable.
- No completion without validation evidence.

## Anti-Patterns
- Skipping gates for risky changes.
- Shipping without rollback or monitoring.
- Treating docs/ops as optional for impactful changes.

## Output Template
Scope → Implementation → Verification → Release/Risk.
