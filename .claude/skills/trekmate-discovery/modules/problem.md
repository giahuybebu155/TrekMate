# Module: Problem

Chủ đề gốc của Discovery. Mọi chủ đề khác truy ngược về các vấn đề ở đây.

## Mục tiêu

Nêu rõ **vấn đề nào đáng giải quyết, của ai, nghiêm trọng đến đâu, và vì sao bây giờ**, tách bạch giữa điều có bằng chứng và điều mới là giả định. Đây là phần trả lời "vì sao sản phẩm nên tồn tại", không phải mô tả giải pháp.

## Đầu vào

- Mọi file trong `sources/`: mô tả dự án, scope, báo cáo, lời kể của PO, nghiên cứu cũ.
- `decision-log.md` để biết phạm vi đã chốt (thị trường, nền tảng…).
- Nếu đã có: `02-personas.md` và `03-market.md` để đối chiếu, nhưng không bắt buộc.

## Đầu ra: `01-problem.md`

```markdown
---
topic: Problem
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Problem

## TL;DR
(≤ 5 dòng: vấn đề chính, ai gặp, mức nghiêm trọng, độ tin cậy tổng)

## Bối cảnh
Tình huống hiện tại của người dùng khi chưa có sản phẩm: họ đang làm việc này thế nào,
dùng những công cụ gì, tốn bao nhiêu thời gian hoặc công sức. Mỗi nhận định có thẻ nguồn.

## Danh sách vấn đề

| ID | Vấn đề | Ai gặp | Tần suất | Mức nghiêm trọng | Bằng chứng | Tin cậy |
|---|---|---|---|---|---|---|
| PS-1 | (mô tả theo góc người dùng, không nhắc giải pháp) | P1, P2 | mỗi chuyến đi | cao | [DOC: …] [STK: …] | trung bình |

## Chi tiết từng vấn đề
### PS-n: <tên ngắn>
- **Tình huống:** khi nào vấn đề xảy ra.
- **Hậu quả:** người dùng mất gì (thời gian, tiền, cơ hội, cảm xúc).
- **Cách xoay xở hiện tại:** họ đang giải quyết tạm bằng gì, và cách đó thiếu ở đâu.
- **How might we:** một câu HMW mở ra hướng giải quyết, không chốt giải pháp.

## Vì sao bây giờ
Thay đổi nào (công nghệ, hành vi, thị trường) làm vấn đề này đáng giải quyết vào lúc này.
Ghi nguồn; nếu chỉ là suy luận thì dùng [INF].

## Vấn đề không giải quyết
Những vấn đề liên quan nhưng chủ động để ngoài phạm vi, kèm lý do.

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Personas: PS nào gắn với persona nào.
- Vision: PS nào là cốt lõi để đưa vào tuyên bố sản phẩm.
- Giai đoạn 3: PS-n là gốc truy vết cho yêu cầu chức năng.
```

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Lần gần nhất người dùng gặp vấn đề này là khi nào, và họ đã làm gì?
- Nếu không giải quyết, điều tệ nhất xảy ra là gì?
- Ai chịu thiệt nhiều nhất: người lên kế hoạch hay người đi cùng?
- Có ai đã trả tiền hoặc bỏ nhiều công sức để giải quyết vấn đề này chưa?
- Điều gì khiến vấn đề này cấp thiết hơn so với 2–3 năm trước?

## Viết V1

- Lấy vấn đề từ nguồn có sẵn (mô tả dự án, scope, lý do làm đề tài, nghiên cứu cũ). Gộp các vấn đề trùng nhau.
- 3–6 PS là đủ cho V1. Xếp theo mức nghiêm trọng × tần suất.
- Vấn đề chưa có dữ liệu người dùng thật vẫn được viết, gắn mức tin cậy `thấp` và giả định `A-n`.
- Mô tả vấn đề bằng ngôn ngữ của người dùng. Không viết "chưa có ứng dụng AI lập lịch trình" (đó là thiếu giải pháp, không phải vấn đề).

## Kiểm tra trước khi xong

- [ ] Không PS nào mô tả giải pháp hoặc tính năng.
- [ ] Mỗi PS có "Ai gặp", bằng chứng có thẻ nguồn và mức tin cậy.
- [ ] Mỗi PS có một câu HMW.
- [ ] Các PS không trùng nhau về bản chất.
- [ ] Không mâu thuẫn với `decision-log.md` (ví dụ phạm vi địa lý).
- [ ] Câu hỏi có ảnh hưởng lớn đã đưa vào `discovery-gaps.md`, không để trong file này.
