# Module: Prototype

Chủ đề dựng **bản giao diện chạy được** cho các màn hình MVP, đặt trong repo để Product Owner bấm thử và agent code đọc trực tiếp.

## Mục tiêu

Một prototype tĩnh, dùng dữ liệu giả, đi được theo các luồng MVP chính, áp đúng token và component. Prototype kiểm chứng thiết kế trước khi code thật; nó không phải mã sản phẩm.

## Đầu vào

- `design-tokens.json`, `DESIGN.md`, `03-components.md`, `04-screens.md`, `05-flows.md`.
- `decision-log.md`: nền tảng, kích thước thiết kế chính.

## Đầu ra: `docs/02-design/prototype/`

```
prototype/
├── README.md          ← cách mở, danh sách màn đã dựng, luồng đi được, phần chưa làm
├── index.html         ← trang mục lục: link tới từng màn và từng luồng
├── tokens.css         ← CSS variables sinh từ design-tokens.json (không viết tay giá trị khác)
├── S01-home.html
├── S05-trip-new.html
└── …                  ← mỗi màn một file, tên theo ID màn hình
```

Mỗi file màn hình là HTML tự chứa (có thể dùng React qua CDN nếu cần trạng thái), chỉ dùng `tokens.css` cho màu, chữ, khoảng cách. Liên kết giữa các file theo `05-flows.md`.

## Quy tắc

- **Chỉ màn MVP.** Màn sau MVP không dựng.
- **Token là nguồn duy nhất:** `tokens.css` sinh từ `design-tokens.json`; không có hex, px cỡ chữ hay khoảng cách viết cứng trong file màn hình ngoài giá trị bố cục riêng của màn.
- **Trạng thái:** mỗi màn có cách xem các trạng thái loading, empty, error (ví dụ tham số `?state=empty` hoặc công tắc trên trang).
- **Dữ liệu giả có nhãn** (`[giá]`, `[Tên quán]`); không bịa số liệu trông như thật. Ảnh dùng khối giữ chỗ có mô tả.
- **Không gọi dịch vụ thật** (Firebase, Gemini, Maps). Bản đồ là khối giữ chỗ có marker giả.
- **Khả năng truy cập như sản phẩm thật:** phần tử `button`, `a`, `input` + `label`, `aria-label` cho icon, `focus-visible`.
- **Kích thước chính trước:** dựng đúng kích thước thiết kế chính trong `decision-log.md`, sau đó kiểm tra bố cục ở breakpoint khác.
- Không thêm thư viện ngoài React và font đã chốt.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Luồng nào cần bấm thử được trước nhất để Product Owner duyệt?
- Có cần chụp ảnh màn hình prototype cho báo cáo không?

## Viết V1

- Dựng luồng chính quan trọng nhất trước (thường là luồng tạo giá trị cốt lõi của persona chính), đủ các màn trong luồng đó.
- Sinh `tokens.css` từ `design-tokens.json` bằng script nhỏ, không chép tay.
- Ghi trong `prototype/README.md` những màn và luồng chưa dựng.

## Kiểm tra trước khi xong

- [ ] Mỗi màn đã dựng có trong `04-screens.md` và thuộc MVP.
- [ ] Đi được trọn luồng chính theo `05-flows.md`.
- [ ] `tokens.css` khớp `design-tokens.json`; không có giá trị màu viết cứng.
- [ ] Mỗi màn xem được các trạng thái loading, empty, error.
- [ ] Mở được bằng trình duyệt, không cần cài đặt, không gọi dịch vụ thật.
