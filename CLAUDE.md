# Claude Instructions

## Communication
- Default: **Vietnamese**; English only on explicit request
- Code artifacts (identifiers, comments, tests, errors): **always English**
- Clarify ambiguities before implementing; ask minimum questions needed
- Routine output: ≤6 bullets or ≤120 words; ≤4 sections; no cross-section duplication

## Token Efficiency
- Parallel-first: batch independent tool calls
- 1 primary skill per task; add others only if needed
- Stop after 2 confirming evidence points or 3 fruitless searches
- **Exception**: deep analysis, audits, safety/security/compliance may exceed budget

## Operating Modes
| Mode | Trigger | Output |
|------|---------|--------|
| Discovery | review/audit/diagnose | evidence-based findings |
| Planning | architecture/migration/strategy | plan + rationale |
| Implementation | build/fix/refactor | code + validation |
| Review | critique/QA/risk | findings + severity + remediation |

## SDLC Gates
**A**-Requirements → **B**-Analysis → **C**-Design → **D**-Build → **E**-Verify → **F**-Release → **G**-Ops → **H**-Maintain → **I**-Incident

Apply all relevant gates; skip only with explicit justification.

## Anti-Hallucination
Verify APIs, types, file paths before use — no invented packages, methods, routes, schema fields.
Uncertain → search workspace first → smallest safe assumption → document uncertainty.

## Clean Code
Single-purpose · explicit contracts · low coupling · precise domain-aligned naming · validate at trust boundaries · backward-compatible · errors handled immediately with context

## Security
- Validate/sanitize all external inputs; authorize at every trust boundary
- No secrets in logs or output; fail-safe defaults; least privilege
- **Go**: auth at service/handler; no logging secrets
- **JS/TS**: injection/XSS/IDOR protection; no secrets in client payloads
- **PHP**: CSRF on state-changing routes; Blade escaping; `env()` only in config

## Completion Contract
- **Implementation**: modified files + validation results + residual risk
- **Design**: architecture + trade-offs + assumptions
- **Review**: findings + severity + remediation
- **Doc Sync** (all modes): after any structural/behavioral change, check and update `README.md`, `README.vi.md`, and any related docs (e.g. `CHANGELOG`, ADRs, wiki pages) so code and documentation always reflect each other consistently

## Skills
For specialized workflows, load `.claude/skills/<name>.md`:

| Skill | Activate when |
|-------|--------------|
| `problem-decomposition` | Broad/ambiguous, multi-file, multi-phase tasks |
| `debugging-root-cause` | Bug, regression, flaky test, production incident |
| `testing-verification` | Any non-trivial code/config change |
| `clean-code-refactor` | Tech debt, readability, maintainability improvements |
| `security-reliability` | Trust boundaries, data handling, operational stability |
| `delivery-sdlc-execution` | Multi-gate delivery with release + ops handoff |

## Language Overlays
Detailed rules in `.claude/instructions/`: `go.md` · `js.md` · `php.md` · `system-design.md`
