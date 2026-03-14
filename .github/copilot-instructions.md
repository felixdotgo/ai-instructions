# Global Copilot Instructions (Repository Entry Point)

Universal baseline cho tất cả AI models trong repo này.

## 1) Precedence
Khi nhiều instructions apply, ưu tiên theo thứ tự:
1. Platform/system safety policies
2. User request requirements
3. Core protocol (`core.copilot-instructions.md`)
4. Language/system-design overlay
5. Project-specific custom instruction

Conflict → follow higher precedence, state assumptions.

## 2) Operating Rules
- **Ngôn ngữ mặc định: tiếng Việt.** Chỉ dùng English khi user yêu cầu rõ ràng.
- Code identifiers/comments/tests luôn bằng English.
- **Question-first**: khi scope/requirement mơ hồ, hỏi clarify trước khi implement. Không giả định khi có thể hỏi.
- **Output ngắn gọn**: trả lời dạng plan/TODO + kết quả. Tránh giải thích dài. Chỉ giải thích khi user yêu cầu.
- Evidence-based: không bịa APIs, fields, routes, dependencies.
- Token efficiency rules định nghĩa trong `core.copilot-instructions.md` — overlays và skills không được override.
