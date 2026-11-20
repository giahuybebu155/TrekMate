# Design Contract

Bổ sung cho `../_shared/synthesis-contract.md`, áp dụng cho mọi module của Giai đoạn 2. Mục đích: agent code ở giai đoạn sau dựng giao diện mà không phải đoán màu, khoảng cách, trạng thái hay nội dung chữ.

## 1. Truy vết

Mọi thứ trong thiết kế phải trả lời được "vì sao có nó":

| Đối tượng | ID | Phải truy về |
|---|---|---|
| Màn hình | `Snn` (người dùng), `Ann` (quản trị) | Ít nhất một tính năng `F-Mn-nn` trong `06-journey-features.md` |
| Luồng | `FLn` | Một hành trình `J-n` hoặc một tính năng MVP |
| Component | `C-<tên>` | Ít nhất một màn hình dùng nó |
| Token | tên token | Ít nhất một component hoặc quy tắc dùng nó |

Đối tượng không truy được là ứng viên bị bỏ. Màn hình phục vụ tính năng ngoài MVP được ghi nhưng đánh dấu `Sau MVP`.

## 2. Nguồn duy nhất của token

- `design-tokens.json` là **nguồn máy đọc duy nhất**; `DESIGN.md` giải thích và phải khớp từng giá trị.
- Component, màn hình và prototype chỉ dùng **token ngữ nghĩa** (ví dụ `primary`, `muted-foreground`), không dùng bảng màu gốc hay giá trị cứng.
- Đổi một token: sửa cả hai file trong cùng một lần, kiểm tra lại tương phản, ghi vào `decision-log.md` nếu là màu chủ đạo, font hoặc thang khoảng cách.

## 3. Khả năng truy cập (WCAG 2.2 AA)

- Tương phản chữ thường ≥ 4,5:1, chữ lớn và icon có nghĩa ≥ 3:1. **Tính bằng công thức**, ghi kết quả trong `DESIGN.md`; không ước lượng bằng mắt.
- Vùng chạm ≥ 44×44 px; input trên điện thoại cỡ chữ ≥ 16 px.
- Không truyền đạt thông tin chỉ bằng màu.
- Mọi control dùng phần tử thật (`button`, `a`, `input` có `label`); icon-only có `aria-label`; có `focus-visible` rõ ràng.
- Tôn trọng `prefers-reduced-motion`.

## 4. Trạng thái bắt buộc

Mọi màn hình có dữ liệu mô tả đủ bốn trạng thái: **loading** (skeleton), **empty**, **error** (thông điệp + hành động thử lại), **success**. Mọi control tương tác có: default, hover, focus-visible, active, disabled, loading (nếu có thao tác chờ).

## 5. Nội dung chữ

- Chữ người dùng thấy được viết **nguyên văn** trong `04-screens.md` cho các thông điệp quan trọng: tiêu đề, nút hành động chính, empty state, lỗi.
- Theo giọng văn trong `01-direction.md`. Lỗi viết theo công thức: chuyện gì xảy ra + người dùng làm gì tiếp.
- Định dạng số, tiền, ngày theo `docs/00-process/conventions.md`.

## 6. Nền tảng

Theo quyết định nền tảng trong `decision-log.md`. Thiết kế ở kích thước chính trước, rồi mô tả cách bố cục thay đổi ở các breakpoint khác. Không thiết kế riêng cho nền tảng ngoài phạm vi đã chốt.

## 7. Dữ liệu trong thiết kế

Prototype và ví dụ dùng **dữ liệu giả có nhãn rõ** (`[giá]`, `[Tên quán]`) hoặc dữ liệu lấy từ nguồn có thật. Không bịa giá, đánh giá, số liệu hay ảnh trông như thật. Ảnh dùng khối giữ chỗ có mô tả.
