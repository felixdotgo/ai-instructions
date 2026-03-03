**Languages:** [English](README.md) | [Tiếng Việt](README.vi.md)

# Copilot Instructions Repository

This repository contains layered Copilot instruction files designed for precise execution, maintainable structure, and full SDLC coverage.

## Instruction Layers
- `.github/copilot-instructions.md`
	- Global entrypoint for all AI models in this repository
	- Defines default behavior and routes to layered instructions
- `.github/instructions/core.copilot-instructions.md`
	- Cross-language behavioral contract
	- SDLC lifecycle gates (requirements to incident learning)
	- clean code and programming principles baseline
	- completion and reporting contract
- `.github/instructions/go.copilot-instructions.md`
	- Go-specific implementation standards
- `.github/instructions/js.copilot-instructions.md`
	- JavaScript/TypeScript-specific implementation standards
- `.github/instructions/php.copilot-instructions.md`
	- Laravel/PHP-specific implementation standards
- `.github/instructions/system-design.copilot-instructions.md`
	- Architecture and system-design output rules
- `.github/instructions/project-space-template.copilot-instructions.md`
	- Placeholder template for project-specific customization
	- SDLC, coding principles, security, and operations placeholders
- `.github/skills/problem-decomposition/SKILL.md`
	- AI-agent skill file for structured problem decomposition
	- Complementary guidance for planning implementation slices and validation
- `.github/skills/debugging-root-cause/SKILL.md`
	- AI-agent skill file for debugging workflows and root-cause isolation
- `.github/skills/testing-verification/SKILL.md`
	- AI-agent skill file for risk-based testing and verification strategy
- `.github/skills/clean-code-refactor/SKILL.md`
	- AI-agent skill file for incremental clean-code refactoring
- `.github/skills/security-reliability/SKILL.md`
	- AI-agent skill file for security and reliability safeguards
- `.github/skills/delivery-sdlc-execution/SKILL.md`
	- AI-agent skill file for end-to-end SDLC execution

## Precedence Model
When multiple files apply, resolve conflicts in this order:
1. platform/system safety policies
2. user request requirements
3. `.github/instructions/core.copilot-instructions.md`
4. language or system-design overlays
5. project-specific custom instruction file (if present)

## SDLC Coverage Policy
The instruction set explicitly covers:
- Requirements and acceptance criteria
- Analysis and impact assessment
- Design and trade-offs
- Implementation and quality
- Verification and validation
- Release and rollback readiness
- Operations and observability
- Maintenance and deprecation planning
- Incident handling and postmortem learning

## Maintenance Rules
- Keep shared rules in `core.copilot-instructions.md`.
- Keep overlays thin and language-specific.
- Avoid duplicate policy blocks across overlays.
- If adding a new language, create a thin overlay that references core behavior.

## Project Customization Template Usage
1. Copy `.github/instructions/project-space-template.copilot-instructions.md`.
2. Rename copy to a project-specific file (example: `.github/instructions/my-project.copilot-instructions.md`).
3. Set `applyTo` to the project scope you want.
4. Replace all `{{PLACEHOLDER}}` values with project-specific rules.
5. Keep shared standards in core; keep project file focused on deltas.
