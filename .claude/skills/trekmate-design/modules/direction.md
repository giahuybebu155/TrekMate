# Module: Direction

Chủ đề chọn **tính cách thị giác và giọng văn** của sản phẩm. Mọi quyết định về màu, chữ, hình khối và cách viết đều dựa vào đây.

## Mục tiêu

Chuyển persona và vision thành một định hướng có thể kiểm chứng: vài từ khoá tính cách, điều nên làm và không nên làm, tham chiếu thị giác và giọng văn. Đủ cụ thể để hai người thiết kế độc lập ra kết quả giống nhau về tinh thần.

## Đầu vào

- `docs/01-discovery/02-personas.md`, `04-vision.md` (persona, bối cảnh sử dụng, nguyên tắc sản phẩm, tính cách thương hiệu).
- Lựa chọn phong cách của Product Owner trong `docs/00-process/po-answers.md`.
- `sources/`: bản nháp cũ (`prior-DESIGN.md` §1 và §9), ảnh tham khảo.

## Đầu ra: `01-direction.md`

```markdown
---
topic: Direction
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Design Direction

## TL;DR
(≤ 5 dòng: 3–5 từ khoá, màu chủ đạo, cảm giác tổng thể)

## Từ khoá tính cách
| Từ khoá | Nghĩa là | Không có nghĩa là | Căn cứ |
|---|---|---|---|
| Tươi trẻ | | | [STK: PO …] / P1, P2 |

## Nên làm / Không nên làm
| Nên | Không nên |
|---|---|

## Tham chiếu thị giác
| Tham chiếu | Học điều gì | Không lấy điều gì | Nguồn |
|---|---|---|---|
Chỉ ghi sản phẩm hoặc trang có thật, kèm link.

## Hình ảnh và minh hoạ
Vai trò của ảnh, tỷ lệ khung, cách đặt chữ trên ảnh, icon.

## Giọng văn
- Xưng hô, độ trang trọng.
- Cách viết nút, tiêu đề, thông báo lỗi, empty state (mỗi loại 1–2 ví dụ).
- Định dạng số, tiền, ngày, giờ, khoảng cách.

## Nền tảng & mật độ
Kích thước thiết kế chính, breakpoint, mật độ thông tin, cách dùng một tay (nếu mobile-first).

## Bàn giao
- Tokens: từ khoá → lựa chọn màu, font, bo góc, bóng.
- Components, Screens: giọng văn và quy tắc hình ảnh.
```

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Người dùng nên cảm thấy gì trong 5 giây đầu tiên?
- Sản phẩm nào persona chính đang dùng hằng ngày, và họ quen với kiểu giao diện nào?
- Nếu phải chọn giữa "nhiều ảnh, cảm hứng" và "gọn, nhiều thông tin", chọn bên nào?

## Viết V1

- Dùng lựa chọn phong cách đã có trong `po-answers.md` và bản nháp cũ. Không hỏi lại điều đã chốt.
- 3–5 từ khoá, mỗi từ khoá gắn với persona hoặc nguyên tắc trong Vision.
- 2–3 tham chiếu thị giác có thật là đủ.

## Kiểm tra trước khi xong

- [ ] Mỗi từ khoá có "nghĩa là" và "không có nghĩa là".
- [ ] Từ khoá truy được về persona, Vision hoặc lựa chọn của PO.
- [ ] Giọng văn có ví dụ cho nút, lỗi và empty state.
- [ ] Nền tảng khớp `decision-log.md`.
