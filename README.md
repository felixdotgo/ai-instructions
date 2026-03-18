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
│   │   ├── delivery-sdlc-execution.md
│   │   ├── failure-escalation.md
│   │   ├── session-continuity.md
│   │   ├── docs-discovery.md
│   │   ├── domain-onboarding.md
│   │   ├── code-review-pr.md
│   │   ├── agent-orchestration.md
│   │   └── migration-upgrade.md
│   ├── checkpoints/                                   # Auto-generated task checkpoints (gitignored)
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
- Failure escalation protocol, session continuity, documentation discovery, agent orchestration
- References `.claude/instructions/` for detailed language overlays

### Copilot (`.github/`)
- `copilot-instructions.md` — global entry: precedence model, language preference, skills reference, failure escalation, session continuity, docs discovery
- `core.instructions.md` — cross-language contract: operating modes, token efficiency, SDLC gates, failure escalation protocol, documentation discovery, session continuity, clean code, security, completion contract
- Language overlays — auto-applied by file type via `applyTo` frontmatter

## Skills Reference

### Core Workflow Skills
| Skill | When to Use |
|-------|------------|
| `problem-decomposition` | Broad/ambiguous tasks spanning multiple files or phases |
| `debugging-root-cause` | Bugs, regressions, flaky tests, production incidents |
| `testing-verification` | Any non-trivial code/config change |
| `clean-code-refactor` | Technical debt, readability, maintainability improvements |
| `security-reliability` | Trust boundaries, data handling, operational stability |
| `delivery-sdlc-execution` | Multi-gate delivery with release and ops handoff |

### Self-Regulation Skills
| Skill | When to Use |
|-------|------------|
| `failure-escalation` | Auto-active during implementation; prevents endless fix loops (retry → re-analyze → re-plan → escalate to user) |
| `session-continuity` | Long tasks, multi-slice work, approaching context/time limits; auto-checkpoints to `.claude/checkpoints/` |

### Knowledge & Discovery Skills
| Skill | When to Use |
|-------|------------|
| `docs-discovery` | Finding project/domain knowledge from `docs/` directory; INDEX.md-first strategy |
| `domain-onboarding` | First time in new project/domain; bootstraps domain knowledge from codebase into a reusable domain skill file |

### Collaboration & Operations Skills
| Skill | When to Use |
|-------|------------|
| `code-review-pr` | Reviewing PRs/MRs with structured severity levels (🔴 blocker, 🟡 warning, 🟢 suggestion, 💭 question) |
| `agent-orchestration` | Large tasks with ≥3 independent subtrees that benefit from parallel agent execution |
| `migration-upgrade` | Database migrations, dependency upgrades, framework version bumps, data transformations |

## Key Protocols

### Failure Escalation (auto-active)
Prevents AI from endlessly retrying the same failing approach:
1. **Level 1 — Retry**: max 2 attempts per approach
2. **Level 2 — Re-analyze**: switch to `debugging-root-cause`, try alternative approach
3. **Level 3 — Re-plan**: switch to `problem-decomposition`, present new plan to user
4. **Level 4 — Escalate**: stop and report all attempts to user

### Session Continuity (auto-active for large tasks)
Prevents progress loss when hitting session/context limits:
- Auto-checkpoints to `.claude/checkpoints/` after each completed slice
- Budget-aware: warns at ~70%, stops safely at ~85% with resume instructions
- Seamless resume: reads checkpoint → verifies file state → continues

### Documentation Discovery
Fast documentation lookup when project has `docs/` directory:
- **INDEX.md-first**: cheapest lookup path, single file read
- **Fallback**: filename scan → grep → deep search
- **Auto-maintenance**: suggests creating/updating `docs/INDEX.md`

### Agent Orchestration
Parallel execution for large independent tasks:
- Decomposes work into parallel-safe slices with non-overlapping file ownership
- Each agent receives self-contained context
- Main thread handles integration verification

### Domain Onboarding
Rapid domain knowledge bootstrap for new projects:
- 5-phase scan: README → entities → business rules → skill generation → user review
- Outputs reusable `.claude/skills/domain-<name>.md` file
- Enables domain-specific AI guidance in all future sessions

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

### Domain Knowledge (any tool)
1. Activate `domain-onboarding` skill in a new project
2. AI scans codebase and generates `.claude/skills/domain-<name>.md`
3. Review and refine the generated domain skill
4. Domain knowledge is now available in all future sessions

### Documentation Index
1. If project has `docs/` directory, create `docs/INDEX.md` with topic→file mapping
2. AI will use this index for fast documentation lookup
3. Index is auto-maintained when docs change

## Maintenance Rules
- Shared rules belong in `core.instructions.md` (Copilot) or `CLAUDE.md` (Claude)
- Keep overlays thin and language-specific — no duplicating core rules
- New language: create a thin overlay referencing core behavior
- Skills are shared — update `.claude/skills/` only
- Self-regulation skills (`failure-escalation`, `session-continuity`) are always-on protocols, not manually activated