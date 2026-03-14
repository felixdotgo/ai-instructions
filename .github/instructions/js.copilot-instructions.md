---
applyTo: "**/*.{js,jsx,ts,tsx,mjs,cjs}"
description: "JavaScript/TypeScript Overlay - Principal Architect Protocol"
---

# JavaScript/TypeScript Overlay (Principal Architect)

## 1) Scope
- This file provides JavaScript/TypeScript-specific implementation standards.
- Shared behavior, SDLC gates, and completion contract are defined in [core.copilot-instructions.md](core.copilot-instructions.md).

## 2) Type and API Design Rules
- Prefer precise static typing in TypeScript.
- Avoid `any`; use `unknown` plus type guards when necessary.
- Keep public APIs small, explicit, and backward-compatible by default.
- Validate external payloads at boundaries.

## 3) Implementation Standards
- Keep logic localized and avoid broad rewrites unless explicitly requested.
- Prefer language/runtime-native features before custom utility layers.
- In React code, prefer derived state over unnecessary effects.
- Avoid expensive operations in render paths.

## 4) Error Handling and Reliability
- Handle asynchronous failures explicitly.
- Propagate errors with context, not silent fallbacks.
- Define timeout/cancellation behavior for external calls where relevant.
- Avoid hidden side effects in shared utility functions.

## 5) Testing Rules
- If tests exist, add or update tests for modified business logic.
- Cover success, failure, and edge cases (`null`, `undefined`, empty structures).
- Assert external behavior and contracts, not implementation internals.

## 6) Forbidden JS/TS Patterns
- Type erasure (`any` everywhere) instead of typed boundaries.
- Silent promise rejection handling.
- Over-abstracted utility wrappers for simple language features.
- New dependencies without compatibility and necessity check.
