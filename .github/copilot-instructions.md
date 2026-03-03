# Global Copilot Instructions (Repository Entry Point)

This file is the universal baseline for all AI models in this repository.

## 1) Purpose
- Provide one consistent instruction entrypoint for all tasks.
- Route specialized behavior to layered instruction files.
- Keep outputs precise, verifiable, and SDLC-aware.

## 2) Repository Instruction Map
- `.github/instructions/core.copilot-instructions.md`
  - Cross-language behavior, SDLC lifecycle gates, completion contract.
- `.github/instructions/go.copilot-instructions.md`
  - Go-specific coding standards.
- `.github/instructions/js.copilot-instructions.md`
  - JavaScript/TypeScript-specific coding standards.
- `.github/instructions/php.copilot-instructions.md`
  - Laravel/PHP-specific coding standards.
- `.github/instructions/system-design.copilot-instructions.md`
  - Architecture/system-design output constraints.
- `.github/instructions/project-space-template.copilot-instructions.md`
  - Placeholder template for project-specific customization.
- `.github/skills/problem-decomposition/SKILL.md`
  - AI-agent skill for execution-ready problem decomposition.
- `.github/skills/debugging-root-cause/SKILL.md`
  - AI-agent skill for evidence-based debugging and root-cause isolation.
- `.github/skills/testing-verification/SKILL.md`
  - AI-agent skill for layered verification and confidence building.
- `.github/skills/clean-code-refactor/SKILL.md`
  - AI-agent skill for safe, behavior-preserving refactoring.
- `.github/skills/security-reliability/SKILL.md`
  - AI-agent skill for trust-boundary security and reliability hardening.
- `.github/skills/delivery-sdlc-execution/SKILL.md`
  - AI-agent skill for end-to-end SDLC execution and handoff.

Skills are complementary guidance and do not override core precedence rules.

## 3) Precedence and Conflict Resolution
When multiple instructions apply, use this order:
1. Platform/system safety policies
2. User request requirements
3. `.github/instructions/core.copilot-instructions.md`
4. Relevant language/system-design overlay
5. Project-specific custom instruction (if created from template)

If rules conflict, follow higher precedence and state assumptions explicitly.

## 4) Default Operating Rules
- Match user response language unless user requests a different language.
- Keep code identifiers/comments/tests in English.
- Use evidence-based analysis; avoid inventing APIs, fields, routes, or dependencies.
- For implementation tasks, deliver concrete file changes and validation outcomes.
- For design/review tasks, deliver structured artifacts with assumptions and trade-offs.

## 5) SDLC Baseline
Every substantial task should account for:
- Requirements and acceptance criteria
- Analysis and impact
- Design decisions and trade-offs
- Build quality and error handling
- Verification and test coverage
- Release/rollback readiness
- Operations and observability
- Maintenance updates and incident learning

## 6) Completion Criteria
A task is complete when applicable artifacts are delivered:
- Changed files (or explicit no-change outcome)
- Validation/check results
- Assumptions/known limitations
- Next risk item when relevant
