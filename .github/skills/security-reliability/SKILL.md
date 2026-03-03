---
name: security-reliability
description: Guide for integrating security and reliability checks into implementation and review. Use this when changes touch trust boundaries, data handling, or operational stability.
---

# Security Reliability Skill

Use this skill to reduce security and runtime risks through structured threat and failure analysis.

## When to Activate
- External input handling changes.
- AuthN/AuthZ, secrets, or sensitive data are involved.
- High-impact operational paths are modified.

## Required Inputs
- Data flow and trust boundaries.
- Access control rules and threat assumptions.
- Availability/reliability expectations.

## Procedure
1. Identify assets, entry points, and trust boundaries.
2. Enumerate plausible threats and failure modes.
3. Validate controls: input validation, authorization, safe defaults.
4. Add safeguards: timeouts, retries, circuit-breaking, idempotency as needed.
5. Ensure observability: logs/metrics/traces/alerts for new risks.
6. Verify with targeted security and reliability checks.

## Decision Rules
- Prefer least privilege and explicit authorization.
- Prefer fail-safe behavior over silent corruption.
- Prefer measurable mitigations with monitoring coverage.

## Anti-Patterns
- Logging secrets or sensitive payloads.
- Assuming trusted input without validation.
- Ignoring partial failure and retry behavior.

## Output Template
1. Risk Surface
2. Threats/Failure Modes
3. Mitigations Implemented
4. Verification
5. Monitoring/Runbook Notes
