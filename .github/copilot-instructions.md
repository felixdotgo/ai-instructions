# AI Instructions

## Precedence
Platform policies > User request > Core protocol > Language overlay > Project-specific

Conflict → follow higher precedence; state assumptions.

## Communication
- Default: **Vietnamese**; English only on explicit request
- Code artifacts (identifiers, comments, tests, errors): **always English**
- Clarify ambiguities before implementing; ask minimum questions needed

## Skills
Reusable skill guides in `.claude/skills/`:
- `problem-decomposition` — broad/ambiguous tasks, multi-file, multi-phase
- `debugging-root-cause` — bugs, regressions, flaky tests, incidents
- `testing-verification` — verification after non-trivial changes
- `clean-code-refactor` — tech debt, readability, maintainability
- `security-reliability` — trust boundaries, data handling, stability
- `delivery-sdlc-execution` — multi-gate delivery with release + ops handoff
