---
name: delivery-sdlc-execution
description: Guide for executing software tasks end-to-end across SDLC gates. Use this when work requires planning, implementation, verification, release readiness, and operational handoff.
---

# Delivery SDLC Execution Skill

Use this skill to convert requests into completion-ready delivery across requirements, build, validation, release, and operations.

## When to Activate
- Multi-step implementation with quality and release expectations.
- Changes requiring coordination across code, tests, docs, and ops.
- Work with non-trivial rollout or rollback risk.

## Required Inputs
- Goals, constraints, and acceptance criteria.
- Affected components and dependencies.
- Deployment model and operational requirements.

## Procedure
1. Requirements: define objective, scope, acceptance criteria.
2. Analysis: map dependencies, compatibility, and risk.
3. Design: choose approach and document trade-offs.
4. Build: implement minimal, focused, reversible changes.
5. Verify: run targeted then broader checks.
6. Release: define rollout, rollback triggers, and readiness checks.
7. Operate: specify observability and ownership updates.
8. Maintain: capture docs/changelog and follow-up risk item.

## Decision Rules
- Keep scope aligned to requested outcome.
- Make assumptions explicit when unavoidable.
- Do not claim completion without validation evidence.

## Anti-Patterns
- Skipping SDLC gates for risky changes.
- Shipping without rollback or monitoring considerations.
- Treating documentation/operations as optional for impactful changes.

## Output Template
1. Scope and Acceptance
2. Implementation Summary
3. Verification Evidence
4. Release/Rollback Plan
5. Operations/Maintenance Notes
