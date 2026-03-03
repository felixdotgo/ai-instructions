**Ngôn ngữ:** [English](README.md) | [Tiếng Việt](README.vi.md)

# Kho Hướng Dẫn Copilot

Kho này chứa bộ file hướng dẫn Copilot theo kiến trúc phân lớp, giúp thực thi chính xác, dễ bảo trì và bao phủ đầy đủ SDLC.

## Các lớp hướng dẫn
- `.github/copilot-instructions.md`
	- Điểm vào toàn cục cho tất cả mô hình AI trong repository
	- Định nghĩa hành vi mặc định và điều hướng tới các lớp hướng dẫn
- `.github/instructions/core.copilot-instructions.md`
	- Hợp đồng hành vi đa ngôn ngữ
	- Các cổng SDLC (từ yêu cầu đến học sau sự cố)
	- Nền tảng clean code và nguyên tắc lập trình
	- Hợp đồng hoàn tất và báo cáo
- `.github/instructions/go.copilot-instructions.md`
	- Tiêu chuẩn triển khai dành riêng cho Go
- `.github/instructions/js.copilot-instructions.md`
	- Tiêu chuẩn triển khai dành riêng cho JavaScript/TypeScript
- `.github/instructions/php.copilot-instructions.md`
	- Tiêu chuẩn triển khai dành riêng cho Laravel/PHP
- `.github/instructions/system-design.copilot-instructions.md`
	- Quy tắc đầu ra cho tài liệu kiến trúc/system design
- `.github/instructions/project-space-template.copilot-instructions.md`
	- Mẫu placeholder để tùy chỉnh theo từng dự án
	- Placeholder cho SDLC, nguyên tắc code, bảo mật và vận hành
- `.github/skills/problem-decomposition/SKILL.md`
	- File skill cho AI agent để phân rã bài toán có cấu trúc
	- Hướng dẫn bổ trợ cho lập kế hoạch theo lát cắt triển khai và kiểm chứng
- `.github/skills/debugging-root-cause/SKILL.md`
	- File skill cho quy trình debug theo bằng chứng và cô lập nguyên nhân gốc
- `.github/skills/testing-verification/SKILL.md`
	- File skill cho chiến lược kiểm thử/xác minh theo mức rủi ro
- `.github/skills/clean-code-refactor/SKILL.md`
	- File skill cho refactor clean code theo từng bước an toàn
- `.github/skills/security-reliability/SKILL.md`
	- File skill cho tăng cường bảo mật và độ tin cậy vận hành
- `.github/skills/delivery-sdlc-execution/SKILL.md`
	- File skill cho thực thi đầu-cuối theo SDLC

## Mô hình ưu tiên (precedence)
Khi nhiều file cùng áp dụng, xử lý xung đột theo thứ tự sau:
1. chính sách an toàn của nền tảng/hệ thống
2. yêu cầu của người dùng
3. `.github/instructions/core.copilot-instructions.md`
4. overlay theo ngôn ngữ hoặc system design
5. file tùy chỉnh theo dự án (nếu có)

## Phạm vi bao phủ SDLC
Bộ hướng dẫn bao phủ rõ ràng:
- Yêu cầu và tiêu chí chấp nhận
- Phân tích và đánh giá tác động
- Thiết kế và đánh đổi
- Triển khai và chất lượng mã
- Xác minh và kiểm thử
- Sẵn sàng phát hành và rollback
- Vận hành và quan sát hệ thống
- Bảo trì và kế hoạch deprecation
- Ứng phó sự cố và học sau sự cố

## Quy tắc bảo trì
- Giữ quy tắc dùng chung trong `core.copilot-instructions.md`.
- Giữ các overlay mỏng và tập trung theo ngôn ngữ.
- Tránh lặp lại các khối chính sách giữa các overlay.
- Nếu thêm ngôn ngữ mới, tạo một overlay mỏng tham chiếu hành vi từ core.

## Cách dùng mẫu tùy chỉnh theo dự án
1. Sao chép `.github/instructions/project-space-template.copilot-instructions.md`.
2. Đổi tên bản sao thành file riêng cho dự án (ví dụ: `.github/instructions/my-project.copilot-instructions.md`).
3. Đặt `applyTo` đúng phạm vi dự án mong muốn.
4. Thay toàn bộ `{{PLACEHOLDER}}` bằng quy tắc cụ thể của dự án.
5. Giữ tiêu chuẩn dùng chung ở core; chỉ để phần khác biệt trong file dự án.
