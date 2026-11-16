# Module: Components

Chủ đề định nghĩa **khối giao diện dùng lại**: tên, biến thể, trạng thái, nội dung và cách dùng. Component là ngôn ngữ chung giữa thiết kế và code.

## Mục tiêu

Một danh sách component đủ để dựng mọi màn hình MVP, mỗi component nói rõ dựa trên thành phần nào của thư viện UI đã chốt, có biến thể và trạng thái gì, dùng token nào và chứa nội dung gì. Agent code dựng component theo đúng mô tả, không tự chế.

## Đầu vào

- `DESIGN.md`, `design-tokens.json`.
- `docs/01-discovery/06-journey-features.md` (tính năng MVP cần hiển thị gì).
- `sources/prior-DESIGN.md` §8 (danh sách component cũ, nếu có).
- `decision-log.md`: thư viện UI (ví dụ shadcn/ui), thư viện icon.

## Đầu ra: `03-components.md`

```markdown
---
topic: Components
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Components

## TL;DR

## Tổng quan
| ID | Component | Dựa trên | Biến thể | Dùng ở màn hình | Trạng thái |
|---|---|---|---|---|---|
| C-Button | Button | shadcn `Button` | primary · accent · secondary · ghost · destructive; sm · md · lg | S01, S05… | MVP |

## C-<Tên>
- **Mục đích:** một câu.
- **Giải phẫu:** các phần bên trong (ảnh, tiêu đề, metadata, hành động).
- **Biến thể:** tên, khi nào dùng.
- **Trạng thái:** default, hover, focus-visible, active, disabled, loading; với component dữ liệu: loading, empty, error.
- **Token dùng:** màu, chữ, khoảng cách, bo góc.
- **Nội dung:** độ dài tối đa, cách cắt chữ, định dạng số/tiền/ngày.
- **Khả năng truy cập:** vai trò, nhãn, điều hướng bàn phím.
- **Không dùng khi:** …

## Mẫu bố cục (layout patterns)
Header, điều hướng, khung trang, danh sách, form nhiều bước, bottom sheet / dialog.

## Bàn giao
- Screens: danh sách component được phép dùng.
- Giai đoạn 3–4: tên component và props chính để tạo file component.
```

## Quy tắc

- Ưu tiên thành phần có sẵn của thư viện UI đã chốt; chỉ tạo component mới khi kết hợp nhiều thành phần cho một mục đích nghiệp vụ (ví dụ thẻ địa điểm, mục lịch trình).
- Không cài thêm thư viện UI khác.
- Mỗi component chỉ dùng token ngữ nghĩa.
- Quy tắc toàn cục ghi một lần (ví dụ "mỗi màn hình tối đa một nút accent").
- Component phục vụ tính năng sau MVP vẫn có thể ghi nhưng đánh dấu `Sau MVP`.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Nội dung nào lặp lại ở nhiều màn hình (thẻ địa điểm, thẻ chuyến đi, mục bình luận)?
- Danh sách có cần kéo thả, hay nút lên/xuống là đủ?
- Hộp thoại trên điện thoại nên là bottom sheet hay toàn màn hình?

## Viết V1

- Lấy danh sách component từ bản nháp cũ, bỏ những gì không còn trong MVP, thêm component cho tính năng mới vào MVP (ví dụ đánh giá địa điểm, bình luận chuyến đi).
- Component cơ bản (Button, Input…) chỉ cần bảng tổng quan và quy tắc; component nghiệp vụ cần mô tả đầy đủ.

## Kiểm tra trước khi xong

- [ ] Mỗi component được ít nhất một màn hình MVP dùng.
- [ ] Mỗi component nghiệp vụ có đủ trạng thái và mục khả năng truy cập.
- [ ] Không có giá trị màu, cỡ chữ hay khoảng cách ngoài token.
- [ ] Mọi component dựa trên thư viện UI đã chốt hoặc có lý do tạo mới.
