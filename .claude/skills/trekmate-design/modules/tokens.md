# Module: Tokens

Chủ đề định nghĩa **giá trị thiết kế nền tảng**: màu, chữ, khoảng cách, bo góc, bóng, chuyển động, breakpoint. Đầu ra là hai file luôn khớp nhau: `DESIGN.md` (người đọc) và `design-tokens.json` (máy đọc).

## Mục tiêu

Một hệ token đủ nhỏ để nhất quán, đủ đầy để dựng mọi màn hình MVP mà không cần giá trị cứng. Agent code ở giai đoạn sau ánh xạ thẳng token sang Tailwind và CSS variables.

## Đầu vào

- `01-direction.md`.
- `sources/prior-DESIGN.md`, `sources/prior-design-tokens.json` (nếu có).
- `decision-log.md`: stack giao diện (ví dụ Tailwind + shadcn/ui), nền tảng, chế độ sáng/tối.

## Đầu ra

### `DESIGN.md`
```markdown
---
topic: Tokens
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# DESIGN.md

## TL;DR

## 1. Màu
### Bảng màu gốc        (tên, hex, dùng cho)
### Token ngữ nghĩa     (token, giá trị sáng, giá trị tối nếu có, dùng cho)
### Kiểm tra tương phản (cặp chữ/nền, tỷ lệ tính được, đạt/không đạt)
### Màu dữ liệu         (ví dụ màu theo ngày trên bản đồ; luôn kèm nhãn chữ hoặc số)

## 2. Chữ               (font, fallback, thang cỡ chữ: token, size/line-height, weight, dùng cho)
## 3. Khoảng cách & bố cục (thang spacing, lề, container, breakpoint, vùng chạm)
## 4. Bo góc, viền, bóng, lớp (z-index)
## 5. Chuyển động        (thời lượng, easing, quy tắc reduced-motion)
## 6. Icon              (bộ icon, cỡ, nét)
## 7. Ánh xạ sang code   (CSS variables, cấu hình Tailwind, quy ước đặt tên)

## Bàn giao
```

### `design-tokens.json`
Định dạng theo W3C Design Tokens (`$value`, `$description`). Nhóm: `color` (gốc), `semantic.light`, `semantic.dark` (nếu có), `font`, `space`, `radius`, `shadow`, `breakpoint`, `layout`, `motion`, `zIndex`. Token ngữ nghĩa tham chiếu token gốc bằng `{color.forest.600}`.

## Quy tắc

- Bắt đầu từ token gốc trong bản nháp cũ nếu vẫn hợp với Direction; chỉ đổi khi có lý do và ghi lại.
- Mỗi cặp chữ/nền dùng trong component phải có dòng trong bảng kiểm tra tương phản, **tính bằng công thức WCAG** (có thể chạy script nhỏ). Không đạt thì đổi màu hoặc cấm cặp đó và ghi rõ.
- Thang chữ tối đa 8 bậc; thang spacing theo bội số 4.
- Token ngữ nghĩa đặt tên theo vai trò (`primary`, `destructive`, `ai-surface`), không theo màu (`green`).
- Giá trị trong hai file phải giống hệt nhau. Sau khi sửa, so khớp từng token.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Có cần chế độ tối ở MVP không?
- Font có hỗ trợ đầy đủ dấu tiếng Việt không?
- Màu nhấn dùng cho hành động nào: chỉ một nút chính mỗi màn, hay cả trạng thái?

## Viết V1

- Lấy nguyên token từ bản nháp cũ nếu khớp Direction và nền tảng hiện tại.
- Chạy kiểm tra tương phản và ghi kết quả.
- Chỉ token cần cho màn hình MVP; token "để dành" ghi nhưng đánh dấu.

## Kiểm tra trước khi xong

- [ ] `DESIGN.md` và `design-tokens.json` khớp từng giá trị.
- [ ] Mọi cặp chữ/nền dùng thật có kết quả tương phản tính được và đạt AA.
- [ ] Không có token đặt tên theo màu ở lớp ngữ nghĩa.
- [ ] Font hỗ trợ tiếng Việt và có fallback.
- [ ] Phần ánh xạ sang code đủ để cấu hình Tailwind/CSS variables.
