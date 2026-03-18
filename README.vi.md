**Ngôn ngữ:** [English](README.md) | [Tiếng Việt](README.vi.md)

# Kho Hướng Dẫn AI

Bộ file hướng dẫn phân lớp cho các trợ lý AI (Claude + GitHub Copilot), được thiết kế để thực thi chính xác, tối ưu token và bao phủ đầy đủ SDLC.

## Hỗ trợ công cụ

| Công cụ | Điểm vào | Skills |
|---------|----------|--------|
| **Claude** | `CLAUDE.md` | `.claude/skills/` |
| **Copilot** | `.github/copilot-instructions.md` | `.claude/skills/` |

Cả hai công cụ dùng chung thư mục skills. Language overlay cho Copilot sử dụng frontmatter `applyTo` để tự động khớp theo loại file.

## Cấu trúc repository

```
.
├── CLAUDE.md                                          # Điểm vào cho Claude
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
    ├── copilot-instructions.md                        # Điểm vào toàn cục cho Copilot
    └── instructions/                                  # Language overlay cho Copilot (tự động áp dụng)
        ├── core.instructions.md
        ├── go.instructions.md
        ├── js.instructions.md
        ├── php.instructions.md
        ├── system-design.instructions.md
        └── project-space-template.instructions.md
```

## Các lớp hướng dẫn

### Dùng chung (cả hai công cụ)
- **Skills** (`.claude/skills/`) — hướng dẫn quy trình tái sử dụng cho các tác vụ chuyên biệt

### Claude (`CLAUDE.md`)
- Quy tắc giao tiếp, ngân sách token, SDLC gates, quy tắc kỹ thuật cốt lõi
- Failure Escalation Protocol, Session Continuity, Documentation Discovery, Agent Orchestration
- Tham chiếu `.claude/instructions/` để biết chi tiết theo ngôn ngữ

### Copilot (`.github/`)
- `copilot-instructions.md` — điểm vào toàn cục: mô hình ưu tiên, ngôn ngữ mặc định, tham chiếu skills
- `core.instructions.md` — hợp đồng đa ngôn ngữ: chế độ hoạt động, hiệu quả token, SDLC gates, failure escalation, docs discovery, session continuity, clean code, bảo mật, hợp đồng hoàn tất
- Language overlay — tự động áp dụng theo loại file qua frontmatter `applyTo`

## Danh sách Skills

### Skills cốt lõi — SDLC & Engineering

| Skill | Khi nào dùng |
|-------|-------------|
| `problem-decomposition` | Tác vụ rộng/mơ hồ, đa file, đa giai đoạn |
| `debugging-root-cause` | Bug, regression, flaky test, sự cố production |
| `testing-verification` | Bất kỳ thay đổi code/config không tầm thường nào |
| `clean-code-refactor` | Nợ kỹ thuật, cải thiện khả năng đọc và bảo trì |
| `security-reliability` | Ranh giới tin cậy, xử lý dữ liệu, ổn định vận hành |
| `delivery-sdlc-execution` | Delivery đa cổng với bàn giao release và ops |
| `code-review-pr` | Review PR/MR với mức độ nghiêm trọng + đề xuất cụ thể |
| `migration-upgrade` | Database migration, nâng cấp dependency/framework |

### Skills tự động hóa — Session & Workflow

| Skill | Khi nào dùng |
|-------|-------------|
| `failure-escalation` | Tự động kích hoạt khi implementation/debug; ngăn vòng lặp sửa lỗi vô hạn |
| `session-continuity` | Task dài, đa slice, sắp hết context budget |
| `docs-discovery` | Tìm kiếm domain/project knowledge từ tài liệu |
| `domain-onboarding` | Lần đầu làm việc với dự án/domain mới; bootstrap domain knowledge |
| `agent-orchestration` | Task lớn với ≥3 subtree độc lập cần thực thi song song |

## Các tính năng chính

### Failure Escalation Protocol
Tự động kích hoạt trong mọi task Implementation và debugging. Ngăn AI liên tục cố sửa lỗi theo cùng một cách.

| Cấp độ | Khi nào | Hành động |
|---------|---------|-----------|
| 1. Retry | Fix lần đầu thất bại | Phân tích, điều chỉnh, thử lại (tối đa 2 lần/approach) |
| 2. Re-analyze | 2 lần thất bại cùng approach | Dừng → phân tích root cause → chuyển approach mới |
| 3. Re-plan | 2 approach khác nhau đều thất bại | Dừng → chuyển Planning mode → phân tách lại bài toán |
| 4. Escalate | Re-plan vẫn thất bại | Dừng → báo cáo chi tiết → hỏi user |

### Session Continuity
Quản lý task dài vượt giới hạn session. Tự động checkpoint tiến độ để resume liền mạch.

- Checkpoint vào `.claude/checkpoints/<task-slug>.md` sau mỗi slice hoàn thành
- Ở ~70% context budget: checkpoint + thông báo user
- Ở ~85% context budget: hoàn tất bước hiện tại, checkpoint, dừng an toàn
- Khi resume: đọc checkpoint → xác minh file state → tiếp tục từ slice tiếp theo

### Documentation Discovery
Tìm tài liệu nhanh khi dự án có thư mục `docs/`.

- Ưu tiên đọc `docs/INDEX.md` trước (1 file read duy nhất)
- Nếu không có index: quét filename → grep keyword → đọc file khớp
- Tối đa 3 lần đọc document/request (tiết kiệm token)
- Tự động đề xuất tạo `docs/INDEX.md` khi `docs/` tồn tại nhưng chưa có index

### Agent Orchestration
Phân công task song song cho nhiều agent khi task đủ lớn.

- Phân tách task thành slice song song (không chia sẻ file) vs tuần tự (có phụ thuộc)
- Mỗi agent nhận context đầy đủ, độc lập (không truy cập hội thoại cha)
- Thread chính phụ trách điều phối, giải quyết conflict, verification tích hợp

### Domain Onboarding
Bootstrap domain knowledge nhanh cho dự án mới.

1. Quét tổng quan: README, cấu trúc thư mục, tech stack
2. Khám phá entity: model/entity layer, migrations, API routes
3. Trích xuất business rules: validation, constants, authorization
4. Tạo domain skill file: `.claude/skills/domain-<project>.md`
5. User review và hoàn thiện

## Mô hình ưu tiên
Platform policies > User request > Core protocol > Language overlay > Project-specific

## SDLC Gates
**A**-Requirements → **B**-Analysis → **C**-Design → **D**-Build → **E**-Verify → **F**-Release → **G**-Ops → **H**-Maintain → **I**-Incident

## Tùy chỉnh theo dự án

### Cho Copilot
1. Sao chép `.github/instructions/project-space-template.instructions.md`
2. Đổi tên thành `<project>.instructions.md`
3. Đặt `applyTo` đúng phạm vi dự án
4. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

### Cho Claude
1. Sao chép `.claude/instructions/project-space-template.md`
2. Hợp nhất vào `CLAUDE.md` của dự án hoặc lưu thành `.claude/instructions/project.md`
3. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

### Onboard domain mới nhanh
1. Chạy skill `domain-onboarding` trên codebase mới
2. AI tự scan và tạo draft `.claude/skills/domain-<project>.md`
3. User review, chỉnh sửa, hoàn thiện → done trong 1 session

## Quy tắc bảo trì
- Quy tắc dùng chung thuộc về `core.instructions.md` (Copilot) hoặc `CLAUDE.md` (Claude)
- Giữ overlay mỏng và tập trung theo ngôn ngữ — không lặp lại quy tắc core
- Thêm ngôn ngữ mới: tạo overlay mỏng tham chiếu hành vi từ core
- Skills dùng chung — chỉ cập nhật trong `.claude/skills/`
- Checkpoint files (`.claude/checkpoints/`) là ephemeral — không commit vào version control