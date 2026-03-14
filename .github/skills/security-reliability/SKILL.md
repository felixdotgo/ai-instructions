---
name: security-reliability
description: Guide for integrating security and reliability checks into implementation and review. Use this when changes touch trust boundaries, data handling, or operational stability.
---

# Security Reliability Skill

Reduce security and runtime risks through structured threat and failure analysis.

## When to Activate
- External input handling changes.
- AuthN/AuthZ, secrets, or sensitive data involved.
- High-impact operational paths modified.

## Procedure
1. Identify assets, entry points, and trust boundaries.
2. Enumerate plausible threats and failure modes.
3. Validate controls: input validation, authorization, safe defaults.
4. Add safeguards: timeouts, retries, circuit-breaking, idempotency as needed.
5. Ensure observability for new risks.
6. Verify with targeted security and reliability checks.

## Decision Rules
- Least privilege and explicit authorization.
- Fail-safe over silent corruption.
- Measurable mitigations with monitoring coverage.

## Anti-Patterns
- Logging secrets or sensitive payloads.
- Assuming trusted input without validation.
- Ignoring partial failure and retry behavior.

## Output Template
Risk Surface → Mitigation → Verification → Monitoring Notes.
