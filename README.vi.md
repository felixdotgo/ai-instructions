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
│   │   └── delivery-sdlc-execution.md
│   └── instructions/                                  # Language overlay cho Claude
│       ├── go.md
│       ├── js.md
│       ├── php.md
│       ├── system-design.md
│       └── project-space-template.md
└── .github/
    ├── copilot-instructions.md                        # Điểm vào toàn cục cho Copilot
    └── instructions/                                  # Language overlay cho Copilot (tự động áp dụng)
        ├── core.copilot-instructions.md
        ├── go.copilot-instructions.md
        ├── js.copilot-instructions.md
        ├── php.copilot-instructions.md
        ├── system-design.copilot-instructions.md
        └── project-space-template.copilot-instructions.md
```

## Các lớp hướng dẫn

### Dùng chung (cả hai công cụ)
- **Skills** (`.claude/skills/`) — hướng dẫn quy trình tái sử dụng cho các tác vụ chuyên biệt

### Claude (`CLAUDE.md`)
- Quy tắc giao tiếp, ngân sách token, SDLC gates, quy tắc kỹ thuật cốt lõi
- Tham chiếu `.claude/instructions/` để biết chi tiết theo ngôn ngữ

### Copilot (`.github/`)
- `copilot-instructions.md` — điểm vào toàn cục: mô hình ưu tiên, ngôn ngữ mặc định, tham chiếu skills
- `core.copilot-instructions.md` — hợp đồng đa ngôn ngữ: chế độ hoạt động, hiệu quả token, SDLC gates, clean code, bảo mật, hợp đồng hoàn tất
- Language overlay — tự động áp dụng theo loại file qua frontmatter `applyTo`

## Danh sách Skills

| Skill | Khi nào dùng |
|-------|-------------|
| `problem-decomposition` | Tác vụ rộng/mơ hồ, đa file, đa giai đoạn |
| `debugging-root-cause` | Bug, regression, flaky test, sự cố production |
| `testing-verification` | Bất kỳ thay đổi code/config không tầm thường nào |
| `clean-code-refactor` | Nợ kỹ thuật, cải thiện khả năng đọc và bảo trì |
| `security-reliability` | Ranh giới tin cậy, xử lý dữ liệu, ổn định vận hành |
| `delivery-sdlc-execution` | Delivery đa cổng với bàn giao release và ops |

## Mô hình ưu tiên
Platform policies > User request > Core protocol > Language overlay > Project-specific

## SDLC Gates
**A**-Requirements → **B**-Analysis → **C**-Design → **D**-Build → **E**-Verify → **F**-Release → **G**-Ops → **H**-Maintain → **I**-Incident

## Tùy chỉnh theo dự án

### Cho Copilot
1. Sao chép `.github/instructions/project-space-template.copilot-instructions.md`
2. Đổi tên thành `<project>.copilot-instructions.md`
3. Đặt `applyTo` đúng phạm vi dự án
4. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

### Cho Claude
1. Sao chép `.claude/instructions/project-space-template.md`
2. Hợp nhất vào `CLAUDE.md` của dự án hoặc lưu thành `.claude/instructions/project.md`
3. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc của dự án

## Quy tắc bảo trì
- Quy tắc dùng chung thuộc về `core.copilot-instructions.md` (Copilot) hoặc `CLAUDE.md` (Claude)
- Giữ overlay mỏng và tập trung theo ngôn ngữ — không lặp lại quy tắc core
- Thêm ngôn ngữ mới: tạo overlay mỏng tham chiếu hành vi từ core
- Skills dùng chung — chỉ cập nhật trong `.claude/skills/`
