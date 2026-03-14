---
name: problem-decomposition
description: Guide for breaking complex software tasks into execution-ready slices. Use this when requests are broad, ambiguous, or span multiple files/phases.
---

# Problem Decomposition Skill

Convert broad/ambiguous requests into execution-ready slices.

## When to Activate
- Request spans multiple files, components, or lifecycle stages.
- Both implementation and quality gates required.
- Constraints present (security, compliance, compatibility, timeline).
- Task underspecified — assumptions must be explicit.

Skip for trivial one-step edits unless user requests decomposition.

## Procedure

### 1) Normalize the Request
- Rewrite into one clear objective sentence.
- Extract hard constraints and non-goals.
- Convert vague wording into testable acceptance criteria.

### 2) Map Impact Surface
- Identify touched modules, interfaces, data contracts, docs.
- Mark coupling risks and external dependencies.

### 3) Slice by Value and Risk
- Thin vertical slices with user-visible progress.
- Sequence by dependency order and risk reduction.
- Each slice independently verifiable.

### 4) Execution Contract per Slice
- Change target (files/components)
- Expected behavior change
- Acceptance checks
- Failure/rollback note if applicable

### 5) Verification Strategy
- Narrow checks closest to change first → broader checks.
- Record untestable areas as residual risk.

### 6) Assumptions and Open Questions
- State only assumptions required to proceed.
- Separate assumptions from facts.
- Flag questions affecting architecture/security/data integrity.

## Decision Rules
- Smallest viable slice over broad refactor.
- Explicit contracts over inferred behavior.
- Reversible changes for risky areas.
- User-value-first ordering when trade-offs are equal.

## Failure Handling
If blocked: identify missing artifact → propose safe default → continue with constrained scope and labeled uncertainty.

## Quality Bar
- Every slice has concrete outcome and validation method.
- Dependencies and ordering explicit.
- Scope boundaries prevent unrelated changes.
- Risks and assumptions visible and minimal.

## Anti-Patterns
- Giant single-step plans without checkpoints.
- Repeating user request without transformation.
- Hidden assumptions about APIs, schemas, environments.
- Validation deferred to end without per-slice checks.

## Output Template
Objective → Ordered Slices → Verification Plan → Assumptions/Risks.
Add Scope and Impacted Areas only when they materially change decisions.
