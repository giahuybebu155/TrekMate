# Module: Screens

Chủ đề lập **danh sách màn hình và đặc tả nội dung từng màn**. Đây là đầu vào chính để viết use case và user story ở Giai đoạn 3.

## Mục tiêu

Mỗi tính năng MVP có chỗ hiển thị, mỗi màn hình có route, quyền truy cập, nội dung từ trên xuống, hành động, trạng thái và chữ quan trọng viết sẵn. Đủ để vẽ prototype và viết user story mà không phải đoán.

## Đầu vào

- `docs/01-discovery/06-journey-features.md` (tính năng `F-Mn-nn`, phạm vi MVP), `02-personas.md` (bối cảnh sử dụng).
- `03-components.md`, `01-direction.md` (giọng văn).
- `sources/prior-screens.md` (nếu có).
- `decision-log.md`: phạm vi MVP, vai trò người dùng, nền tảng.

## Đầu ra: `04-screens.md`

```markdown
---
topic: Screens
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Screens

## TL;DR

## Tổng quan
| ID | Màn hình | Route | Module | Tính năng | Quyền | Phạm vi |
|---|---|---|---|---|---|---|
| S01 | | `/` | M2, M3 | F-M3-01 | Công khai | MVP |

Phạm vi: `MVP` hoặc `Sau MVP`.

## S<nn>: <Tên màn hình>
- **Mục đích:** người dùng đến đây để làm gì (gắn JTBD-n).
- **Vào từ / đi tới:** màn hình hoặc luồng liên quan.
- **Nội dung (từ trên xuống):** từng khối, component dùng (C-…), dữ liệu hiển thị.
- **Hành động:** nút/link, kết quả khi bấm.
- **Trạng thái:** loading · empty · error · success (mô tả, kèm chữ nguyên văn cho empty và error).
- **Ràng buộc nhập liệu:** trường, kiểu, bắt buộc, giới hạn (nếu có form).
- **Bố cục theo breakpoint:** khác biệt giữa kích thước chính và kích thước khác.
- **Chữ quan trọng:** tiêu đề, nút chính, thông báo.

## Màn hình hệ thống
404, không có quyền, lỗi hệ thống.

## Bàn giao
- Flows: màn hình tham gia luồng nào.
- Prototype: danh sách màn MVP cần dựng.
- Giai đoạn 3: mỗi màn hình MVP là căn cứ cho use case, user story và acceptance criteria.
```

## Quy tắc

- Mỗi tính năng MVP có ít nhất một màn hình; mỗi màn hình gắn ít nhất một tính năng.
- Màn hình quản trị dùng tiền tố `A`, màn hình người dùng dùng `S`. Giữ ID từ bản nháp cũ nếu màn hình vẫn tồn tại; không dùng lại ID cho màn khác.
- Chữ người dùng thấy: viết theo giọng văn trong `01-direction.md`.
- Ràng buộc nhập liệu ghi ở mức người dùng thấy (ví dụ "tối đa 7 ngày"); kiểu dữ liệu lưu trữ để Giai đoạn 3.
- Không mô tả màu, khoảng cách cụ thể; chỉ tham chiếu component và token.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Người dùng chưa đăng nhập được xem những màn nào?
- Bình luận và đánh giá hiển thị ở đâu, ai được viết, ai được xoá?
- Màn nào cần dùng được khi đang đi ngoài đường, một tay?

## Viết V1

- Bắt đầu từ `prior-screens.md`, cập nhật cột Phạm vi theo MVP hiện tại, thêm màn cho tính năng mới vào MVP.
- Màn MVP: đặc tả đầy đủ. Màn sau MVP: chỉ một dòng trong bảng tổng quan.

## Kiểm tra trước khi xong

- [ ] Mọi tính năng MVP có màn hình; mọi màn hình MVP có tính năng.
- [ ] Mỗi màn MVP có đủ bốn trạng thái và chữ cho empty, error.
- [ ] Mỗi màn có quyền truy cập rõ ràng.
- [ ] Chỉ dùng component có trong `03-components.md`, hoặc ghi rõ component mới cần thêm.
- [ ] Phạm vi khớp `decision-log.md`.
