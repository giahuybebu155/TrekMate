# Module: Vision

Chủ đề nói **sản phẩm muốn trở thành gì, cho ai, và khác biệt ở đâu**. Đây là la bàn để Blueprint, Journey & Features và Roadmap không đi lệch.

## Mục tiêu

Gói Problem, Personas và Market thành một hướng đi rõ ràng: tầm nhìn dài hạn, câu tuyên bố sản phẩm, định vị so với lựa chọn khác, điểm khác biệt độc nhất (USP) và cách tiếp cận người dùng đầu tiên. Vision chọn hướng; nó không liệt kê tính năng.

## Đầu vào

- `01-problem.md`, `02-personas.md`, `03-market.md` (hoặc ngữ cảnh tương đương trong `sources/`).
- `docs/00-process/po-answers.md`: mục tiêu dài hạn, mong muốn của Product Owner.
- `decision-log.md`: thị trường, nền tảng, phạm vi MVP, cam kết miễn phí hoặc thu phí.

## Đầu ra: `04-vision.md`

```markdown
---
topic: Vision
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Vision

## TL;DR
(≤ 5 dòng: tầm nhìn một câu, persona chính, điểm khác biệt, độ tin cậy)

## Tầm nhìn
Một câu: thế giới sẽ khác thế nào sau 3 năm nếu sản phẩm thành công.
Kèm 2–3 dòng giải thích và thẻ nguồn.

## Sứ mệnh
Sản phẩm làm gì mỗi ngày để tiến tới tầm nhìn.

## Product Statement
Dành cho **[persona chính]**
đang **[job / vấn đề quan trọng nhất]**,
**[tên sản phẩm]** là **[loại sản phẩm]**
giúp **[lợi ích chính]**.
Khác với **[lựa chọn thay thế chính]**,
sản phẩm của chúng tôi **[điểm khác biệt chính]**.

## Định vị
| Tiêu chí người dùng quan tâm | Sản phẩm của ta | Đối thủ A | Đối thủ B | Tự xoay xở |
|---|---|---|---|---|
Chọn 3–5 tiêu chí rút từ JTBD và pain của persona ưu tiên.

## USP
Một điểm khác biệt mà đối thủ trong `03-market.md` chưa làm tốt, gắn với chỗ trống cụ thể
và một hoặc nhiều PS-n. Nêu vì sao khó sao chép.

## Nguyên tắc sản phẩm
3–5 nguyên tắc dùng để quyết định khi có tranh cãi.
Ví dụ dạng: "Ưu tiên X hơn Y" (một nguyên tắc có đánh đổi rõ ràng).

## Tiếp cận người dùng đầu tiên (Go-to-Market sơ bộ)
| Kênh | Persona | Vì sao | Chi phí | Nguồn |
|---|---|---|---|---|
Chỉ những kênh khả thi với nguồn lực hiện có.

## Thành công trông như thế nào
- Câu người dùng sẽ nói sau lần dùng đầu tiên (định tính).
- 1–3 kết quả đo được, chi tiết hoá trong Roadmap.

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Blueprint: product statement và nguyên tắc sản phẩm là ràng buộc khi thiết kế giải pháp và mô hình kinh doanh.
- Roadmap: tầm nhìn và tiêu chí thành công để chọn chỉ số.
- Giai đoạn 2: giọng điệu và tính cách thương hiệu rút từ sứ mệnh và nguyên tắc.
```

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Trong 3 năm tới, sản phẩm muốn có người dùng thật lâu dài, hay chủ yếu để chứng minh năng lực?
- Câu bạn muốn người dùng nói sau lần dùng đầu tiên là gì?
- Nếu chỉ được giữ một điểm khác biệt, đó là điểm nào?
- Điều gì sản phẩm sẽ **không bao giờ** làm, dù người dùng yêu cầu?
- Ai là người dùng đầu tiên, và bạn gặp họ ở đâu?

## Viết V1

- Viết tầm nhìn và product statement ngay từ nguồn hiện có, kể cả khi Product Owner chưa trả lời câu hỏi về mục tiêu dài hạn. Gắn `[INF]` hoặc `[PROP]`, độ tin cậy `thấp`, và trỏ tới gap tương ứng.
- Nếu có hai hướng định vị đều hợp lý, ghi cả hai dưới dạng `[PROP]` kèm đánh đổi, rồi đưa lựa chọn vào `discovery-gaps.md`. Không tự chọn thay Product Owner.
- USP phải dựa trên chỗ trống trong `03-market.md`. Nếu Market chưa có, ghi USP là giả định.
- Go-to-Market sơ bộ: 1–3 kênh là đủ.

## Kiểm tra trước khi xong

- [ ] Product statement nhắc đúng persona chính và vấn đề trong Problem.
- [ ] USP gắn với ít nhất một chỗ trống trong Market và một PS-n.
- [ ] Không có tính năng cụ thể trong tầm nhìn hoặc sứ mệnh.
- [ ] Mỗi nguyên tắc sản phẩm có một đánh đổi rõ ràng.
- [ ] Không mâu thuẫn với `decision-log.md` (thị trường, nền tảng, miễn phí hay thu phí).
- [ ] Phần còn phụ thuộc vào câu trả lời của Product Owner có trỏ tới G-n.
