**Ngôn ngữ:** [English](README.md) | [Tiếng Việt](README.vi.md)

# AI Instructions Repository

Bộ file hướng dẫn phân lớp cho các AI coding assistant (Claude + GitHub Copilot), được thiết kế để thực thi chính xác, tối ưu token và bao phủ đầy đủ SDLC.

## Tool Support

| Công cụ | Entry Point | Skills |
|---------|------------|--------|
| **Claude** | `CLAUDE.md` | `.claude/skills/` |
| **Copilot** | `.github/copilot-instructions.md` | `.claude/skills/` |

Cả hai công cụ dùng chung thư mục skills. Language overlay cho Copilot sử dụng frontmatter `applyTo` để tự động khớp theo loại file.

## Repository Structure

```
.
├── CLAUDE.md                                          # Entry point cho Claude
├── .claude/
│   ├── skills/                                        # Skill dùng chung (Claude + Copilot)
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
│   └── instructions/                                  # Language overlay cho Claude
│       ├── go.md
│       ├── js.md
│       ├── php.md
│       ├── system-design.md
│       └── project-space-template.md
└── .github/
    ├── copilot-instructions.md                        # Global entry point cho Copilot
    └── instructions/                                  # Language overlay cho Copilot (tự động áp dụng)
        ├── core.instructions.md
        ├── go.instructions.md
        ├── js.instructions.md
        ├── php.instructions.md
        ├── system-design.instructions.md
        └── project-space-template.instructions.md
```

## Instruction Layers

### Dùng chung (cả hai công cụ)
- **Skills** (`.claude/skills/`) — hướng dẫn workflow tái sử dụng cho các tác vụ chuyên biệt

### Claude (`CLAUDE.md`)
- Communication rule, token budget, SDLC gates, core engineering rule
- Failure Escalation Protocol, Session Continuity, Documentation Discovery, Agent Orchestration
- Tham chiếu `.claude/instructions/` để biết chi tiết language overlay

### Copilot (`.github/`)
- `copilot-instructions.md` — global entry point: precedence model, ngôn ngữ mặc định, tham chiếu skills, failure escalation, session continuity, docs discovery
- `core.instructions.md` — cross-language contract: operating modes, token efficiency, SDLC gates, failure escalation protocol, documentation discovery, session continuity, clean code, security, completion contract
- Language overlay — tự động áp dụng theo loại file qua frontmatter `applyTo`

## Skills Reference

### Core Workflow Skills

| Skill | Khi nào dùng |
|-------|-------------|
| `problem-decomposition` | Tác vụ rộng/mơ hồ, đa file, đa giai đoạn |
| `debugging-root-cause` | Bug, regression, flaky test, production incident |
| `testing-verification` | Bất kỳ thay đổi code/config không tầm thường nào |
| `clean-code-refactor` | Tech debt, cải thiện readability và maintainability |
| `security-reliability` | Trust boundary, xử lý dữ liệu, operational stability |
| `delivery-sdlc-execution` | Multi-gate delivery với release và ops handoff |
| `code-review-pr` | Review PR/MR với severity level + actionable suggestion |
| `migration-upgrade` | Database migration, dependency upgrade, framework version bump |

### Self-Regulation Skills

| Skill | Khi nào dùng |
|-------|-------------|
| `failure-escalation` | Tự động kích hoạt khi implementation/debug; ngăn endless fix loop |
| `session-continuity` | Task dài, đa slice, sắp hết context budget |

### Knowledge & Discovery Skills

| Skill | Khi nào dùng |
|-------|-------------|
| `docs-discovery` | Tìm kiếm domain/project knowledge từ tài liệu |
| `domain-onboarding` | Lần đầu làm việc với dự án/domain mới; bootstrap domain knowledge |

### Collaboration & Operations Skills

| Skill | Khi nào dùng |
|-------|-------------|
| `agent-orchestration` | Task lớn với ≥3 subtree độc lập cần parallel execution |

## Key Protocols

### Failure Escalation (auto-active)
Tự động kích hoạt trong mọi task Implementation và debugging. Ngăn AI liên tục cố sửa lỗi theo cùng một cách.

| Cấp độ | Khi nào | Hành động |
|---------|---------|-----------|
| 1. Retry | Fix lần đầu thất bại | Phân tích, điều chỉnh, thử lại (tối đa 2 lần/approach) |
| 2. Re-analyze | 2 lần thất bại cùng approach | Dừng → phân tích root cause → chuyển approach mới |
| 3. Re-plan | 2 approach khác nhau đều thất bại | Dừng → chuyển Planning mode → phân tách lại bài toán |
| 4. Escalate | Re-plan vẫn thất bại | Dừng → báo cáo chi tiết → hỏi user |

### Session Continuity (auto-active cho large task)
Quản lý task dài vượt giới hạn session. Tự động checkpoint progress để resume liền mạch.

- Checkpoint vào `.claude/checkpoints/<task-slug>.md` sau mỗi slice hoàn thành
- Ở ~70% context budget: checkpoint + thông báo user
- Ở ~85% context budget: hoàn tất bước hiện tại, checkpoint, dừng an toàn
- Khi resume: đọc checkpoint → xác minh file state → tiếp tục từ slice tiếp theo

### Documentation Discovery
Fast documentation lookup khi dự án có thư mục `docs/`.

- **INDEX.md-first**: cheapest lookup path, single file read
- **Fallback**: filename scan → grep → deep search
- **Auto-maintenance**: đề xuất tạo/cập nhật `docs/INDEX.md`

### Agent Orchestration
Parallel execution cho large independent task.

- Phân tách task thành parallel-safe slice (non-overlapping file ownership) vs sequential slice (có dependency)
- Mỗi agent nhận self-contained context, độc lập (không truy cập parent conversation)
- Main thread phụ trách điều phối, conflict resolution, integration verification

### Domain Onboarding
Bootstrap domain knowledge nhanh cho dự án mới.

1. Rapid scan: README, cấu trúc thư mục, tech stack
2. Entity discovery: model/entity layer, migration, API route
3. Business rule extraction: validation, constant, authorization
4. Tạo domain skill file: `.claude/skills/domain-<project>.md`
5. User review và hoàn thiện

## Precedence Model
Platform policies > User request > Core protocol > Language overlay > Project-specific

## SDLC Gates
**A**-Requirements → **B**-Analysis → **C**-Design → **D**-Build → **E**-Verify → **F**-Release → **G**-Ops → **H**-Maintain → **I**-Incident

## Project Customization

### Cho Copilot
1. Sao chép `.github/instructions/project-space-template.instructions.md`
2. Đổi tên thành `<project>.instructions.md`
3. Đặt `applyTo` đúng phạm vi dự án
4. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

### Cho Claude
1. Sao chép `.claude/instructions/project-space-template.md`
2. Hợp nhất vào `CLAUDE.md` của dự án hoặc lưu thành `.claude/instructions/project.md`
3. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

### Domain Knowledge (any tool)
1. Kích hoạt skill `domain-onboarding` trong dự án mới
2. AI scan codebase và tạo draft `.claude/skills/domain-<name>.md`
3. Review và hoàn thiện domain skill đã tạo
4. Domain knowledge sẵn sàng cho mọi session sau đó

### Documentation Index
1. Nếu dự án có thư mục `docs/`, tạo `docs/INDEX.md` với topic→file mapping
2. AI sử dụng index này để fast documentation lookup
3. Index được auto-maintain khi docs thay đổi

## Maintenance Rules
- Shared rule thuộc về `core.instructions.md` (Copilot) hoặc `CLAUDE.md` (Claude)
- Giữ overlay mỏng và tập trung theo ngôn ngữ — không lặp lại core rule
- Thêm ngôn ngữ mới: tạo thin overlay tham chiếu core behavior
- Skills dùng chung — chỉ cập nhật trong `.claude/skills/`
- Self-regulation skill (`failure-escalation`, `session-continuity`) là always-on protocol, không cần kích hoạt thủ công
- Checkpoint file (`.claude/checkpoints/`) là ephemeral — không commit vào version control
- **Terminology preservation**: không bao giờ dịch technical term, tool name, proper noun hoặc domain term — giữ nguyên dạng gốc tiếng Anh trong mọi ngữ cảnh:
  - *Multilingual doc*: khi dịch tài liệu (ví dụ `README.md` → `README.vi.md`), chỉ dịch phần diễn giải xung quanh; giữ nguyên các term như skill, overlay, token, checkpoint, SDLC, rollback, migration, frontmatter
  - *Domain language (DDD)*: domain term chính là Ubiquitous Language — phải giữ nguyên trong code, tài liệu và giao tiếp. Dịch domain term (ví dụ "Invoice" → "Hóa đơn") phá vỡ sự thống nhất giữa code, doc và team, gây sai lệch hiểu biết chung
  - *Lý do*: tính nhất quán thuật ngữ đảm bảo độ chính xác, khả năng tìm kiếm và shared understanding xuyên suốt codebase và tài liệu