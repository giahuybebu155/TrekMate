---
topic: Roadmap
status: draft
sources: [prior-research, bao-cao-f5, po-answers]
updated: 2026-11-21
---

# Roadmap

## TL;DR
Ba nhịp **Now (MVP) → Next → Later**. Now = M1–M5, M7 + comment + share/chi phí lát cắt. North Star: **số chuyến được lưu và chia sẻ mỗi tuần**. Lịch 9 tuần Waterfall trong báo cáo (08–10/2026) **không còn dùng** — [DEC: D8] Agile sprint 1 tuần; G-1 sẽ quyết độ dài Later. Tin cậy tiến độ: **thấp** (chưa có hạn bảo vệ mới).

## 1. Lộ trình theo kết quả

| Giai đoạn | Mục tiêu (kết quả cho người dùng) | Tính năng / module | Điều kiện để chuyển tiếp | Thời gian dự kiến |
|---|---|---|---|---|
| **Now – MVP** | P1 tạo được lịch AI kiểm chứng, biết tiền/người, gửi link; P2 xem/lọc điểm và đánh giá; Admin seed POI | F-M1-01/02/04, F-M2-*, F-M3-01…06, F-M4-*, F-M5-*, F-M7-01/02/03, F-M10-01 | KPI-1 có chuyến thật được chia sẻ trên bản demo; KPI-3 ≥ 90% điểm verified trong lịch mẫu; seed Q5 xong | Nhiều sprint 1 tuần `[TBD]` theo lịch đồ án mới. Báo cáo cũ 9 tuần đã qua mốc 23/10/2026 [DOC: bao-cao-f5] |
| **Next** | Trong chuyến: xem đường và được nhắc khi kế hoạch lệch; tiền theo hạng mục | F-M8-01, F-M11-01, F-M6-01 | PS-5 bắt đầu được giải; p95 generate vẫn đạt KPI-4 | Sau khi Now được PO duyệt demo |
| **Later** | Gợi ý KS/NH; Premium (nới AI, xuất PDF…); i18n EN; cộng tác sửa; Splitwise | F-M9-01, ranh giới Premium G-7, F-M10-02 tuỳ chọn | G-1 nếu là sản phẩm sống mới đầu tư kênh + trả phí | Phụ thuộc G-1 |

Thứ tự Now tôn trọng phụ thuộc Blueprint: **M5 seed → M3 generate → M7 lưu/sửa → F-M10-01 share**; M1 song song; M2/M4 có thể sau trái tim nhưng vẫn trong Now vì D0.3.

## 2. Phụ thuộc & rủi ro tiến độ

| Phụ thuộc | Ảnh hưởng tới | Phải xong trước | Rủi ro | Cách giảm |
|---|---|---|---|---|
| Firebase project + Auth + Rules emulator | M1, M7, comment | Coding M3 lưu chuyến | R7 | CI emulator |
| Seed 8 điểm × 20–40 POI [DEC: Q5] | Chất lượng B3 | Demo AI cho user | R9 | F-M5-02 Places fill; làm sprint 1–2 |
| Gemini qua Cloud Functions + schema Zod | F-M3-02 | Mọi demo trái tim | R1, R2 | Mock schema trong test; rate limit |
| Chốt G-6 | F-M7-03 | Merge comment | Làm sai public write | Mặc định A-4 đến khi PO trả lời |
| Google Maps billing | F-M5-02, Next M8 | — | R6 | Cache; trì hoãn M8 |
| G-1 tầm nhìn 3 năm | Later / Premium | Không chặn Now | Làm thừa GTM | Now vẫn đúng cho đồ án |

## 3. Hệ thống chỉ số

### North Star Metric

| Chỉ số | Định nghĩa | Vì sao chọn | Ngưỡng MVP |
|---|---|---|---|
| KPI-1 Số chuyến **lưu và có ít nhất 1 lượt mở link chia sẻ** / tuần | Đếm `trips` status saved có `shareOpenedAt` trong 7 ngày | Đo giá trị P1 (JTBD-1+3), không đếm pageview | `[PROP]` ≥ 10 chuyến/tuần trên môi trường demo nhóm lớp; khi có user ngoài: đặt lại |

### AARRR

| Giai đoạn | Chỉ số | Định nghĩa | Ngưỡng MVP | Cách đo |
|---|---|---|---|---|
| Acquisition | KPI-A1 Tài khoản mới / tuần | `users` tạo trong 7 ngày | `[PROP]` không bắt buộc cho đồ án; theo dõi | Firebase Auth |
| Activation | KPI-2 % user mới tạo được 1 lịch AI trong phiên đầu | Trong 24h sau signup, có 1 trip generated+saved | `[PROP]` ≥ 60% [DOC: prior-research §7] | Analytics sự kiện `trip_saved` |
| Retention | KPI-R1 % user mở lại app ≥ 1 lần trong 7 ngày sau chuyến | Quay lại xem lịch hoặc comment | `[PROP]` ≥ 20% — thấp vì A-UR | Auth lastLogin / trip open |
| Referral | KPI-Rf1 % chuyến có share link được mở bởi người khác | share unique viewer > 0 | `[PROP]` ≥ 40% chuyến saved | Đếm mở link |
| Revenue | Chưa có | Freemium chưa thu ở Now [DEC: D-BM] | — | Không đo tiền MVP; đo hạn lượt AI |

### KPI chất lượng

| ID | Chỉ số | Ngưỡng | Liên quan |
|---|---|---|---|
| KPI-3 | % điểm trong lịch generate là POI verified | `[PROP]` ≥ 90% [DOC: prior-research §7] | R1, D5; NFR GĐ3 |
| KPI-4 | p95 thời gian sinh lịch 3 ngày | `[PROP]` ≤ 15 giây | A-1; NFR |
| KPI-5 | Tỷ lệ Gemini lỗi schema sau 1 retry | `[PROP]` ≤ 5% | R1 |
| KPI-6 | Số lần gọi Gemini / chuyến lưu thành công (trung bình) | `[PROP]` ≤ 3 | R2 |
| KPI-7 | LCP trang chủ trên 4G | `[PROP]` ≤ 2,5 giây | [DOC: prior-research §7] |

### OKR quý đầu (tuỳ chọn)

**Objective:** Có bản demo P1 hoàn thành job cốt lõi trên 8 điểm seed.
- KR1: Seed đủ Q5 (8 điểm, 20–40 POI/điểm).
- KR2: 5 nhóm bạn (không chỉ thành viên team) lưu và mở được link.
- KR3: KPI-3 ≥ 90% trên 20 lịch test.

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-NS | North Star “lưu + chia sẻ” đúng giá trị P1 | Đổi sang “ngày đi thật” (khó đo) | Duyệt PO |
| G-1 | Later có thể rất ngắn nếu chỉ đồ án | Cắt Premium/GTM | Trả lời G-1 |

## Bàn giao
- Giai đoạn 3: Now = backlog sprint đầu; KPI-3…7 → NFR.
- Giai đoạn 5: North Star + AARRR để slide kết quả.
- Giai đoạn 2: performance budget bám KPI-4, KPI-7.
