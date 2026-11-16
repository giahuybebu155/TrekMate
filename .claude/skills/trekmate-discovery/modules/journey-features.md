# Module: Journey & Features

Chủ đề mô tả **người dùng đi qua những bước nào, và sản phẩm cần tính năng gì ở mỗi bước**, rồi chọn tính năng nào vào MVP.

## Mục tiêu

Nối persona và các khối giải pháp thành hành trình cụ thể, rút ra danh sách tính năng có truy vết, chấm điểm ưu tiên và chốt phạm vi MVP. Đây là đầu vào trực tiếp cho thiết kế màn hình (Giai đoạn 2) và đặc tả (Giai đoạn 3).

## Đầu vào

- `02-personas.md` (persona, JTBD, pain/gain) và `05-blueprint.md` (khối giải pháp, ranh giới miễn phí và trả phí).
- `01-problem.md`, `04-vision.md` để kiểm tra mức độ phù hợp.
- `sources/`: danh sách module và chức năng trong tài liệu dự án.
- `decision-log.md`: phạm vi MVP đã chốt, nền tảng, các quyết định tính năng.

## Đầu ra: `06-journey-features.md`

```markdown
---
topic: Journey & Features
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Journey & Features

## TL;DR
(≤ 5 dòng: số hành trình, số tính năng, MVP gồm gì, rủi ro phạm vi)

## 1. Hành trình người dùng

### J<n>: <tên hành trình> (persona P<n>, job JTBD-n)
| Giai đoạn | Trước chuyến đi | | Trong chuyến đi | Sau chuyến đi |
|---|---|---|---|---|
| Người dùng làm gì | | | | |
| Điểm chạm | | | | |
| Suy nghĩ / cảm xúc | | | | |
| Pain | PAIN-n | | | |
| Cơ hội | → F-Mn-nn | | | |

Cột giai đoạn có thể đổi theo sản phẩm; giữ thứ tự thời gian.

## 2. Danh sách tính năng
| ID | Tính năng | Module | Khối giải pháp | Phục vụ | Hành trình | Gói |
|---|---|---|---|---|---|---|
| F-M3-01 | | M3 | | JTBD-n, PAIN-n | J1 | Miễn phí / Trả phí |

Mỗi tính năng viết dưới dạng năng lực người dùng có được, không phải chi tiết giao diện.

## 3. Ưu tiên

### MoSCoW
| Nhóm | Tính năng | Lý do |
|---|---|---|
| Must | | Không có thì job cốt lõi của persona chính không hoàn thành |
| Should | | |
| Could | | |
| Won't (lần này) | | |

### RICE (cho các tính năng Should và Could)
| ID | Reach | Impact | Confidence | Effort | Điểm | Căn cứ |
|---|---|---|---|---|---|---|

Reach: số người dùng hoặc % persona bị ảnh hưởng trong một quý (ước lượng có căn cứ).
Impact: 3 lớn · 2 vừa · 1 nhỏ · 0,5 rất nhỏ. Confidence: 100% / 80% / 50%.
Effort: người-tuần. Điểm = Reach × Impact × Confidence ÷ Effort.

## 4. Phạm vi MVP
| Module | Trong MVP | Tính năng | Ghi chú |
|---|---|---|---|

**Ngoài MVP:** danh sách tính năng hoãn và lý do.
**Tiêu chí MVP thành công:** liên kết tới KPI trong Roadmap.

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Giai đoạn 2: hành trình J-n và tính năng MVP là căn cứ để lập danh sách màn hình và luồng UX.
- Giai đoạn 3: mỗi F-Mn-nn trong MVP trở thành một hoặc nhiều yêu cầu chức năng và user story.
- Roadmap: thứ tự Should/Could và tính năng ngoài MVP.
```

## Quy tắc

- **Truy vết bắt buộc:** mỗi tính năng gắn ít nhất một JTBD hoặc PAIN. Tính năng không gắn được là ứng viên bị bỏ.
- **Must chỉ dành cho tính năng thiếu thì job cốt lõi không hoàn thành.** Nếu nhóm Must quá một nửa danh sách, xem lại.
- **Phạm vi MVP đã chốt trong `decision-log.md` thắng điểm RICE.** Nếu RICE gợi ý khác, ghi `[PROP]` và đưa vào `discovery-gaps.md`; không tự đổi phạm vi.
- **Effort và Reach là ước lượng.** Ghi căn cứ; không có căn cứ thì Confidence tối đa 50%.
- Không viết user story, acceptance criteria hay màn hình ở đây.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Nếu chỉ phát hành được ba tính năng, đó là ba tính năng nào?
- Bước nào trong hành trình người dùng hay bỏ cuộc nhất?
- Tính năng nào chỉ hữu ích khi đã có nhiều người dùng hoặc nhiều dữ liệu?
- Nhóm có bao nhiêu người-tuần cho MVP?

## Viết V1

- Một hành trình cho mỗi persona ưu tiên; persona chính có hành trình đầy đủ nhất.
- Lấy tính năng từ danh sách chức năng trong nguồn, đặt lại ID theo `F-Mn-nn`, gắn JTBD/PAIN.
- MoSCoW cho toàn bộ; RICE chỉ cho Should và Could để tiết kiệm công.
- Phạm vi MVP theo `decision-log.md`. Ghi rõ tính năng nào của các module MVP bị hoãn.

## Kiểm tra trước khi xong

- [ ] Mỗi persona ưu tiên có ít nhất một hành trình.
- [ ] Mỗi tính năng có ID, module, JTBD/PAIN và hành trình.
- [ ] Mỗi pain quan trọng của persona chính có tính năng giải quyết hoặc được ghi là chưa giải quyết.
- [ ] Phạm vi MVP khớp `decision-log.md`.
- [ ] Gói miễn phí và trả phí khớp `05-blueprint.md`.
- [ ] RICE có căn cứ cho Reach và Effort.
