# Module: Roadmap

Chủ đề mô tả **sản phẩm phát hành theo thứ tự nào, và đo thành công bằng gì**.

## Mục tiêu

Biến phạm vi MVP và các tính năng hoãn thành lộ trình phát hành theo kết quả (không phải danh sách ngày tháng cho từng tính năng), kèm hệ thống chỉ số để biết mỗi bước có hiệu quả không. Roadmap ở Discovery là mức chiến lược; kế hoạch sprint chi tiết thuộc Giai đoạn 3.

## Đầu vào

- `04-vision.md` (tầm nhìn, tiêu chí thành công), `05-blueprint.md` (rủi ro, phụ thuộc, ranh giới gói), `06-journey-features.md` (MVP, ưu tiên).
- `sources/`: lịch dự án, mốc, nguồn lực trong tài liệu dự án.
- `decision-log.md`: phạm vi MVP, nhịp phát triển.

## Đầu ra: `07-roadmap.md`

```markdown
---
topic: Roadmap
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Roadmap

## TL;DR
(≤ 5 dòng: số giai đoạn phát hành, MVP xong khi nào, North Star, rủi ro tiến độ)

## 1. Lộ trình theo kết quả
| Giai đoạn | Mục tiêu (kết quả cho người dùng) | Tính năng / module | Điều kiện để chuyển tiếp | Thời gian dự kiến |
|---|---|---|---|---|
| Now – MVP | | F-Mn-nn… | KPI-n đạt ngưỡng | |
| Next | | | | |
| Later | | | | |

Thời gian dự kiến chỉ ghi khi có căn cứ (lịch dự án, nguồn lực). Không có thì ghi khoảng tương đối.

## 2. Phụ thuộc & rủi ro tiến độ
| Phụ thuộc | Ảnh hưởng tới | Phải xong trước | Rủi ro | Cách giảm |
|---|---|---|---|---|

## 3. Hệ thống chỉ số

### North Star Metric
Một chỉ số thể hiện giá trị người dùng nhận được, có định nghĩa đo chính xác.
| Chỉ số | Định nghĩa | Vì sao chọn | Ngưỡng MVP |
|---|---|---|---|

### AARRR
| Giai đoạn | Chỉ số | Định nghĩa | Ngưỡng MVP | Cách đo |
|---|---|---|---|---|
| Acquisition | | | | |
| Activation | | | | |
| Retention | | | | |
| Referral | | | | |
| Revenue | | | | |

### KPI chất lượng
| ID | Chỉ số | Ngưỡng | Liên quan |
|---|---|---|---|
| KPI-n | (hiệu năng, độ chính xác, chi phí vận hành…) | | NFR ở Giai đoạn 3 |

### OKR quý đầu (tuỳ chọn)
**Objective:** …
- KR1: … (đo được, có ngưỡng)

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Giai đoạn 3: giai đoạn Now là phạm vi backlog các sprint đầu; KPI chất lượng thành yêu cầu phi chức năng.
- Giai đoạn 5: North Star và AARRR là căn cứ báo cáo kết quả khi trình bày sản phẩm.
```

## Quy tắc

- **Theo kết quả, không theo tính năng:** mỗi giai đoạn trả lời "người dùng làm được gì mới", rồi mới liệt kê tính năng.
- **Now phải khớp phạm vi MVP** trong `06-journey-features.md` và `decision-log.md`.
- **Chỉ số phải đo được** với công cụ sẽ có. Mỗi chỉ số có định nghĩa (đếm cái gì, trong khoảng thời gian nào).
- **Ngưỡng là mục tiêu, không phải dữ kiện.** Gắn `[PROP]` cho ngưỡng agent đề xuất; chỉ thành `[DEC]` khi Product Owner duyệt.
- Không lập sprint, story hay ước lượng chi tiết ở đây.

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Có hạn chót cố định nào (bảo vệ đồ án, ra mắt) mà MVP phải kịp?
- Dấu hiệu nào cho thấy MVP đủ tốt để làm tiếp giai đoạn Next?
- Doanh thu có phải mục tiêu của năm đầu không, hay chỉ người dùng?
- Ai sẽ đo chỉ số, và bằng công cụ gì?

## Viết V1

- Ba giai đoạn Now / Next / Later là đủ.
- Now lấy nguyên phạm vi MVP. Next và Later lấy từ nhóm Should, Could và tính năng hoãn, theo điểm ưu tiên.
- North Star và 1 chỉ số cho mỗi bước AARRR. Revenue có thể là `Chưa có` nếu chưa thu tiền ở MVP, kèm lý do.
- Lấy KPI chất lượng có sẵn trong nguồn (hiệu năng, độ chính xác AI…) và gắn nguồn.

## Kiểm tra trước khi xong

- [ ] Now khớp phạm vi MVP.
- [ ] Mỗi giai đoạn có điều kiện chuyển tiếp đo được.
- [ ] North Star phản ánh giá trị người dùng, không phải chỉ số vanity (lượt xem, lượt tải).
- [ ] Mỗi chỉ số có định nghĩa và cách đo.
- [ ] Ngưỡng do agent đề xuất được gắn `[PROP]`.
- [ ] Phụ thuộc kỹ thuật trong `05-blueprint.md` được phản ánh trong thứ tự.
