# Module: Personas

Chủ đề mô tả **ai** gặp các vấn đề trong Problem, họ cần làm việc gì (job), điều gì cản trở (pain) và điều gì họ mong (gain).

## Mục tiêu

Tạo một nhóm nhỏ persona đủ khác nhau để dẫn dắt thiết kế và ưu tiên tính năng. Mỗi persona phải truy được về ít nhất một vấn đề `PS-n`. Persona là công cụ ra quyết định, không phải tiểu sử.

## Đầu vào

- `01-problem.md` (nếu có) hoặc ngữ cảnh tương đương trong `sources/`.
- Các persona hoặc nhóm người dùng đã được nêu trong nguồn và trong `docs/00-process/po-answers.md`.
- `decision-log.md`: persona nào được ưu tiên, phạm vi thị trường.
- Kết quả phỏng vấn hoặc khảo sát thật nếu có.

## Đầu ra: `02-personas.md`

```markdown
---
topic: Personas
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Personas

## TL;DR
(≤ 5 dòng: số persona, persona ưu tiên, job quan trọng nhất, độ tin cậy tổng)

## Tổng quan
| ID | Tên gọi | Mô tả một dòng | Vấn đề chính | Ưu tiên | Tin cậy |
|---|---|---|---|---|---|
| P1 | | | PS-1, PS-3 | chính | thấp |

## P<n>: <tên gọi>

**Chân dung:** tuổi, nghề nghiệp, hoàn cảnh đi du lịch. Chỉ giữ chi tiết ảnh hưởng tới quyết định sản phẩm.
**Bối cảnh sử dụng:** khi nào, ở đâu, trên thiết bị nào họ sẽ dùng sản phẩm.
**Hành vi hiện tại:** họ đang lên kế hoạch thế nào, dùng công cụ gì.

### Jobs To Be Done
| ID | Khi… | tôi muốn… | để… | Loại | Quan trọng |
|---|---|---|---|---|---|
| JTBD-1 | (tình huống) | (việc cần làm) | (kết quả mong đợi) | chức năng | cao |

Loại: chức năng, cảm xúc, hoặc xã hội.

### Pains & Gains
| ID | Loại | Mô tả | Gắn với | Mức độ | Nguồn |
|---|---|---|---|---|---|
| PAIN-1 | pain | | JTBD-1 | cao | [STK: …] |
| GAIN-1 | gain | | JTBD-1 | trung bình | [INF: …] |

### Empathy map
| Nói | Nghĩ | Làm | Cảm thấy |
|---|---|---|---|
| | | | |

**Thành công với họ là:** một câu đo được hoặc quan sát được.

## Người không phải đối tượng
Các nhóm người dùng chủ động không phục vụ ở giai đoạn này, kèm lý do.

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Market: persona nào dùng để đánh giá đối thủ.
- Journey & Features: mỗi persona ưu tiên cần một hành trình.
- Giai đoạn 2: bối cảnh sử dụng, thiết bị và cảm xúc để quyết định bố cục và giọng văn.
- Giai đoạn 3: JTBD-n là căn cứ để viết user story.
```

## Cách viết Job

Dùng dạng **"Khi [tình huống], tôi muốn [việc], để [kết quả]"** (quyết định đã ghi trong `decision-log.md`).

- **Tình huống** cụ thể: "Khi còn hai tuần nữa là đến chuyến đi 3 ngày với nhóm bạn", không phải "khi đi du lịch".
- **Việc cần làm** là việc người dùng muốn xong, không nhắc tính năng: "chốt được lịch trình cả nhóm đồng ý", không phải "dùng AI tạo lịch trình".
- **Kết quả** là điều họ thực sự quan tâm: "để không ai phải lo và ai cũng biết mình góp bao nhiêu".
- Một job chỉ có một việc. Nếu câu có "và" giữa hai việc thì tách thành hai job.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Ai trong nhóm là người lên kế hoạch, và ai chỉ đi theo?
- Họ dùng điện thoại hay máy tính khi lên kế hoạch, và khi đang đi?
- Điều gì khiến họ bỏ một công cụ lập kế hoạch giữa chừng?
- Ngân sách được quyết định trước hay sau khi chọn điểm đến?
- Thứ gì họ sẵn sàng trả tiền, thứ gì nhất định phải miễn phí?

## Viết V1

- 2–4 persona là đủ. Nếu nguồn đã nêu persona ưu tiên thì dùng đúng các persona đó.
- Mỗi persona 2–4 job, 3–6 pain/gain. Xếp theo mức quan trọng.
- Không có phỏng vấn thật: vẫn viết persona, gắn `[STK]` cho phần lấy từ lời PO, `[INF]` cho phần suy luận, đặt độ tin cậy `thấp` và ghi giả định `A-n`.
- Không bịa tên thật, trích dẫn hay số liệu khảo sát. Tên gọi persona chỉ là nhãn để dễ nhớ.

## Kiểm tra trước khi xong

- [ ] Mỗi persona gắn với ít nhất một `PS-n`; mỗi `PS-n` có ít nhất một persona.
- [ ] Các persona khác nhau ở điểm ảnh hưởng tới sản phẩm (mục tiêu, ngân sách, bối cảnh), không chỉ khác tuổi.
- [ ] Mọi job theo đúng dạng "Khi… tôi muốn… để…" và không nhắc tính năng.
- [ ] Mỗi pain/gain gắn với một job và có thẻ nguồn.
- [ ] Persona ưu tiên khớp với `decision-log.md`.
- [ ] Không có trích dẫn hay số liệu khảo sát bịa ra.
