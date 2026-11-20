# Giai đoạn 2: Design System & Prototype

Tài liệu trong thư mục này được tạo và cập nhật bằng skill `trekmate-design` (`.claude/skills/trekmate-design/`). Đầu vào là kết quả Giai đoạn 1 trong `docs/01-discovery/`. Giai đoạn 3 (Requirements) và agent code đọc các file dưới đây.

## Cách chạy

Trong Claude Code, tại thư mục repo:
- Chạy toàn bộ: "chạy design cho TrekMate". Nên chạy sau khi Giai đoạn 1 có ít nhất Personas, Vision và Journey & Features.
- Cập nhật một chủ đề: "cập nhật token màu", "cập nhật màn hình S07", "dựng prototype luồng tạo chuyến đi"…

## Độ phủ chủ đề

| Chủ đề | File | Trạng thái | Mức tin cậy chính | Khoảng trống lớn nhất |
|---|---|---|---|---|
| Direction | `01-direction.md` | Chưa có | — | — |
| Tokens | `DESIGN.md`, `design-tokens.json` | Chưa có | — | — |
| Components | `03-components.md` | Chưa có | — | — |
| Screens | `04-screens.md` | Chưa có | — | — |
| Flows | `05-flows.md` | Chưa có | — | — |
| Prototype | `prototype/` | Chưa có | — | — |

Trạng thái: `Chưa có` · `draft` · `approved`. Bảng này được skill cập nhật sau mỗi lần chạy.

## Nguồn

| File | Loại | Nội dung |
|---|---|---|
| `sources/prior-DESIGN.md` | PROP | Bản nháp design system mobile-first (14/11/2026): màu xanh lá rừng + vàng nắng, font Be Vietnam Pro, component |
| `sources/prior-design-tokens.json` | PROP | Token máy đọc của bản nháp trên |
| `sources/prior-screens.md` | PROP | Danh sách màn hình S01–S14, A01–A06 (phạm vi MVP theo quyết định cũ, cần cập nhật) |
| `sources/prior-ux-flows.md` | PROP | Luồng F1–F7 bằng Mermaid |
| `sources/design-gaps.md` | — | Hàng đợi câu hỏi của giai đoạn |
| `../01-discovery/` | — | Đầu ra Giai đoạn 1 |
| `../00-process/po-answers.md` | STK | Câu trả lời của Product Owner |
| `../00-process/decision-log.md` | DEC | Quyết định đã duyệt |

Lưu ý: các bản nháp `prior-*` được viết trước khi MVP thêm M4 và bình luận chuyến đi (D0.3 sửa, 16/11/2026), nên phạm vi màn hình trong đó cần cập nhật.
