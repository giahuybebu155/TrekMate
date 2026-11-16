# Module: Market

Chủ đề mô tả **người dùng đang có lựa chọn nào khác**, thị trường lớn đến đâu và chỗ trống sản phẩm có thể chiếm.

## Mục tiêu

Cho thấy sản phẩm cạnh tranh với ai (kể cả cách tự xoay xở không cần sản phẩm nào), đối thủ làm tốt và chưa tốt điều gì đối với các persona ưu tiên, và có tín hiệu thị trường nào đủ tin cậy. Đây là căn cứ để Vision chọn điểm khác biệt.

## Đầu vào

- `01-problem.md`, `02-personas.md` (hoặc ngữ cảnh tương đương trong `sources/`).
- Đối thủ hoặc công cụ đã được nhắc tới trong `sources/`.
- `decision-log.md`: thị trường mục tiêu, nền tảng.
- **Web search** cho thông tin đối thủ và số liệu thị trường. Đây là việc agent tự làm, không hỏi Product Owner.

## Đầu ra: `03-market.md`

```markdown
---
topic: Market
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Market

## TL;DR
(≤ 5 dòng: đối thủ đáng chú ý nhất, chỗ trống chính, độ tin cậy tổng)

## Đối thủ đã quét
| Tên | Loại | Họ làm gì (1–2 câu) | Điểm mạnh với persona của ta | Điểm yếu với persona của ta | Nguồn | Ngày xem |
|---|---|---|---|---|---|---|
| | trực tiếp / gián tiếp / thay thế | | | | link | dd/mm/yyyy |

Loại: **trực tiếp** (cùng giải quyết vấn đề bằng sản phẩm tương tự), **gián tiếp** (sản phẩm khác nhưng người dùng dùng thay), **thay thế** (cách làm không cần sản phẩm chuyên biệt).

## Cách người dùng đang tự xoay xở (bổ sung)
| Cách làm | Persona | Ưu điểm | Thiếu ở đâu | Nguồn |
|---|---|---|---|---|

## Tín hiệu thị trường
Chỉ ghi số liệu có nguồn web truy cập được. Thiếu thì để [TBD] kèm cách tìm.
| Chỉ số | Giá trị | Phạm vi / năm | Nguồn | Tin cậy |
|---|---|---|---|---|

## Chỗ trống
Những điều persona ưu tiên cần mà các lựa chọn hiện có làm chưa tốt. Mỗi điểm gắn PS-n hoặc JTBD-n và có thẻ nguồn.

## So sánh sâu (tuỳ chọn ở V1)
Bảng tính năng chi tiết, SWOT, mô hình giá. Chỉ thêm khi Product Owner yêu cầu hoặc khi Vision cần.

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Vision: chỗ trống nào là ứng viên cho điểm khác biệt.
- Blueprint: mô hình giá và kênh của đối thủ để tham khảo mô hình kinh doanh.
- Giai đoạn 2: đối thủ nào có trải nghiệm đáng học hoặc nên tránh.
```

## Quy tắc nghiên cứu

- **Chỉ đối thủ có tên thật**, có trang sản phẩm hoặc nguồn đáng tin. Mỗi dòng có link và ngày xem.
- Ưu tiên **nguồn gốc** (trang sản phẩm, trang giá, kho ứng dụng, thông cáo chính thức) hơn bài tổng hợp. Bài xếp hạng do chính một đối thủ viết thì ghi rõ là có xung đột lợi ích.
- Đánh giá điểm mạnh và điểm yếu **từ góc nhìn persona của dự án**, không phải đánh giá chung chung.
- Không chép mô tả quảng cáo của đối thủ; viết lại ngắn bằng lời của mình.
- Số liệu thị trường (quy mô, tăng trưởng, số người dùng) phải ghi năm. Số cũ hơn 24 tháng thì ghi là cần kiểm tra lại.
- Không bịa số người dùng, doanh thu hay xếp hạng.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Nhóm đã từng dùng sản phẩm nào, và vì sao bỏ?
- Ứng dụng nào trong nước đang được persona ưu tiên dùng nhiều nhất?
- Đối thủ nào bạn coi là chuẩn để so sánh khi bảo vệ đồ án?

Phần lớn câu trả lời ở đây tìm được trên web. Chỉ hỏi Product Owner những gì chỉ họ biết.

## Viết V1

- Quét nhanh **2–3 đối thủ có tên thật**, ưu tiên ít nhất một đối thủ trong nước nếu thị trường mục tiêu là trong nước. Mỗi đối thủ có mô tả, link và ngày xem.
- Cách tự xoay xở là phần bổ sung; ghi 2–3 cách nếu nguồn có nhắc.
- Tín hiệu thị trường: 1–3 số liệu có nguồn là đủ, hoặc `[TBD]`.
- So sánh sâu để sau.

## Kiểm tra trước khi xong

- [ ] Mỗi đối thủ có link nguồn và ngày xem.
- [ ] Điểm mạnh và điểm yếu được đánh giá theo persona của dự án.
- [ ] Mỗi chỗ trống gắn với PS-n hoặc JTBD-n.
- [ ] Không có số liệu thiếu nguồn hoặc thiếu năm.
- [ ] Phạm vi đối thủ khớp thị trường mục tiêu trong `decision-log.md`.
