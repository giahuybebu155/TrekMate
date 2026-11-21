# Giai đoạn 1: Product Discovery

Tài liệu trong thư mục này được tạo và cập nhật bằng skill `trekmate-discovery` (`.claude/skills/trekmate-discovery/`). Giai đoạn 2 (Design) và Giai đoạn 3 (Requirements) đọc các file chủ đề dưới đây.

## Cách chạy

Trong Cursor hoặc Claude Code, tại thư mục repo:
- Chạy toàn bộ: "chạy discovery cho TrekMate" / "chạy giai đoạn 1".
- Cập nhật một chủ đề: "cập nhật persona", "cập nhật đối thủ", "cập nhật MVP scope"…

## Độ phủ chủ đề

| Chủ đề | File | Trạng thái | Mức tin cậy chính | Khoảng trống lớn nhất |
|---|---|---|---|---|
| Problem | `01-problem.md` | draft | trung bình | A-UR, G-3 |
| Personas | `02-personas.md` | draft | thấp–trung bình | A-UR |
| Market | `03-market.md` | draft | cao (đối thủ) / thấp (WTP) | willingness-to-pay |
| Vision | `04-vision.md` | draft | thấp | G-1, G-3 |
| Solution Blueprint + Business Model | `05-blueprint.md` | draft | cao (giải pháp) / thấp (thu phí) | G-7 |
| Journey & Features | `06-journey-features.md` | draft | trung bình | G-6 |
| Roadmap | `07-roadmap.md` | draft | thấp (tiến độ) | G-1, hạn đồ án |

Trạng thái: `Chưa có` · `draft` · `approved`. Bảng này được skill cập nhật sau mỗi lần chạy.

V1 ngày 21/11/2026. Đối chiếu cặp chủ đề: Problem↔Personas, Personas↔Journey, Market↔Vision, Vision↔Blueprint, Blueprint↔Roadmap, tất cả↔decision-log — không mâu thuẫn DEC; G-6/G-7 đánh dấu chỗ chưa chốt.

## Nguồn

| File | Loại | Nội dung |
|---|---|---|
| `sources/scope.md` | DOC | Scope v1.0 |
| `sources/bao-cao-f5.md` | DOC | Trích báo cáo môn Quản trị dự án phần mềm |
| `sources/prior-research.md` | INF / PROP | Bản tổng hợp Discovery trước đó (14/11/2026) |
| `../00-process/po-answers.md` | STK | Câu trả lời của Product Owner (mọi giai đoạn) |
| `sources/discovery-gaps.md` | — | Hàng đợi câu hỏi |
| `../00-process/decision-log.md` | DEC | Quyết định đã duyệt |
