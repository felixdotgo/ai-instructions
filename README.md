**Languages:** [English](README.md) | [Tiếng Việt](README.vi.md)

# AI Instructions Repository

Layered instruction files for AI coding assistants (Claude + GitHub Copilot), designed for precise execution, token efficiency, and full SDLC coverage.

## Tool Support

| Tool | Entry Point | Skills |
|------|-------------|--------|
| **Claude** | `CLAUDE.md` | `.claude/skills/` |
| **Copilot** | `.github/copilot-instructions.md` | `.claude/skills/` |

Both tools share the same skills directory. Language overlays for Copilot use `applyTo` frontmatter for automatic file-type matching.

## Repository Structure

```
.
├── CLAUDE.md                                          # Claude entry point
├── .claude/
│   ├── skills/                                        # Shared skill guides (Claude + Copilot)
│   │   ├── problem-decomposition.md
│   │   ├── debugging-root-cause.md
│   │   ├── testing-verification.md
│   │   ├── clean-code-refactor.md
│   │   ├── security-reliability.md
│   │   └── delivery-sdlc-execution.md
│   └── instructions/                                  # Claude language overlays
│       ├── go.md
│       ├── js.md
│       ├── php.md
│       ├── system-design.md
│       └── project-space-template.md
└── .github/
    ├── copilot-instructions.md                        # Copilot global entry point
    └── instructions/                                  # Copilot language overlays (auto-applied)
        ├── core.instructions.md
        ├── go.instructions.md
        ├── js.instructions.md
        ├── php.instructions.md
        ├── system-design.instructions.md
        └── project-space-template.instructions.md
```

## Instruction Layers

### Shared (both tools)
- **Skills** (`.claude/skills/`) — reusable workflow guides for specialized tasks

### Claude (`CLAUDE.md`)
- Communication rules, token budget, SDLC gates, core engineering rules
- References `.claude/instructions/` for detailed language overlays

### Copilot (`.github/`)
- `copilot-instructions.md` — global entry: precedence model, language preference, skills reference
- `core.instructions.md` — cross-language contract: operating modes, token efficiency, SDLC gates, clean code, security, completion contract
- Language overlays — auto-applied by file type via `applyTo` frontmatter

## Skills Reference

| Skill | When to Use |
|-------|------------|
| `problem-decomposition` | Broad/ambiguous tasks spanning multiple files or phases |
| `debugging-root-cause` | Bugs, regressions, flaky tests, production incidents |
| `testing-verification` | Any non-trivial code/config change |
| `clean-code-refactor` | Technical debt, readability, maintainability improvements |
| `security-reliability` | Trust boundaries, data handling, operational stability |
| `delivery-sdlc-execution` | Multi-gate delivery with release and ops handoff |

## Precedence Model
Platform policies > User request > Core protocol > Language overlay > Project-specific

## SDLC Gates
**A**-Requirements → **B**-Analysis → **C**-Design → **D**-Build → **E**-Verify → **F**-Release → **G**-Ops → **H**-Maintain → **I**-Incident

## Project Customization

### For Copilot
1. Copy `.github/instructions/project-space-template.instructions.md`
2. Rename to `<project>.instructions.md`
3. Set `applyTo` to the project scope
4. Replace all `{{PLACEHOLDER}}` values

### For Claude
1. Copy `.claude/instructions/project-space-template.md`
2. Merge into project's `CLAUDE.md` or save as `.claude/instructions/project.md`
3. Replace all `{{PLACEHOLDER}}` values

## Maintenance Rules
- Shared rules belong in `core.instructions.md` (Copilot) or `CLAUDE.md` (Claude)
- Keep overlays thin and language-specific — no duplicating core rules
- New language: create a thin overlay referencing core behavior
- Skills are shared — update `.claude/skills/` only
