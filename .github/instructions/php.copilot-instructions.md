---
applyTo: "**/*.php"
description: "PHP Laravel Overlay - Principal Architect Protocol"
---

# PHP Laravel Overlay (Principal Architect)

## 1) Scope
- This file provides Laravel/PHP-specific implementation standards.
- Shared behavior, SDLC gates, and completion contract are defined in [core.copilot-instructions.md](core.copilot-instructions.md).

## 2) Laravel Architecture Rules
- Follow Laravel conventions and existing project structure.
- Keep controllers thin; place business logic in services/actions where complexity justifies it.
- Use Form Request classes for validation in non-trivial endpoints.
- Use API Resources for stable response contracts when building APIs.

## 3) Implementation Standards
- Use strict type hints for parameters and return values where supported.
- Prefer Eloquent and Query Builder with parameter binding; avoid raw SQL unless justified.
- Protect against mass assignment using `$fillable` or `$guarded`.
- Keep authorization explicit via Policies/Gates for protected actions.

## 4) Error Handling and Data Integrity
- Return appropriate HTTP status codes.
- Use transactions for multi-step write workflows.
- Catch exceptions only where recovery or translation is necessary.
- Do not leave debugging calls (`dd`, `dump`) in production paths.

## 5) Testing Rules
- Use Feature tests for endpoint behavior and authorization.
- Use Unit tests for isolated business logic.
- Cover happy path, validation failures, and authorization denial paths.
- Mock external dependencies at boundaries.

## 6) Security and Compliance Additions
- Validate all external inputs.
- Apply CSRF protection for state-changing web routes.
- Prevent XSS by default escaping in Blade unless explicitly sanitized.
- Avoid logging secrets and sensitive personal data.

## 7) Release and Operations Expectations
For risk-bearing changes, include:
- migration compatibility and data backfill notes
- rollout and rollback plan
- observability updates (logs/metrics/alerts)

## 8) Forbidden Laravel/PHP Patterns
- Business logic directly embedded in Blade views.
- Missing authorization checks on protected operations.
- Direct unparameterized SQL with user input.
- Calling `env()` outside configuration files.

## 9) Completion Notes for Laravel/PHP Tasks
In final output for implementation tasks include:
- changed file list
- validation executed
- remaining risk or assumptions
