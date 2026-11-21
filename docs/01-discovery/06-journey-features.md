---
topic: Journey & Features
status: draft
sources: [prior-research, bao-cao-f5, scope, po-answers]
updated: 2026-11-21
---

# Journey & Features

## TL;DR
Ba hành trình cho P1 P2 P3. MVP theo [DEC: D0.3 (sửa)]: **M1, M2, M3, M4, M5, M7** + **comment chuyến** + lát cắt **chi phí/người** và **link chia sẻ**. Ngoài MVP: M6 đầy đủ, M8, M9, M10 đầy đủ MXH, M11. Rủi ro phạm vi: comment (G-6) và seed POI (R9).

## 1. Hành trình người dùng

### J1: Chốt chuyến nhóm bằng AI (P1, JTBD-1, JTBD-2, JTBD-3)

| Giai đoạn | Trước chuyến đi | Trong chuyến đi | Sau chuyến đi |
|---|---|---|---|
| Người dùng làm gì | Đăng nhập → form AI (điểm, ngày, số người, ngân sách, sở thích) → chờ → xem lịch ngày → sửa/tạo lại → thấy tiền/người → lưu → gửi link Zalo | Mở lịch đã lưu trên điện thoại; sửa tay nếu đổi kế hoạch | Mở chuyến; đọc/ghi comment (G-6) |
| Điểm chạm | Form AI, kết quả theo ngày, link share | Danh sách giờ + điểm (không dẫn đường M8) | Trang chuyến + comment |
| Suy nghĩ / cảm xúc | Hào hứng; sốt nếu chờ lâu (A-1) | Cần lịch “Hôm nay” đơn giản | Muốn nhóm nói gì đó |
| Pain | PAIN-1, PAIN-3 | PS-5 chưa giải bằng thông báo | PAIN-2 đã giảm nếu đã thấy tiền/người từ trước |
| Cơ hội | → F-M3-01…06, F-M10-01 | → F-M7-02 | → F-M7-03 |

### J2: Tìm điểm rẻ và đánh giá (P2, JTBD-4, JTBD-5)

| Giai đoạn | Trước chuyến đi | Trong chuyến đi | Sau chuyến đi |
|---|---|---|---|
| Người dùng làm gì | Tìm/lọc POI theo danh mục và mức ngân sách; xem giá tham khảo; thêm vào chuyến hoặc generate mức Tiết kiệm | Xem chi tiết điểm đang tới | Viết sao + nhận xét (M4) |
| Điểm chạm | Khám phá, chi tiết POI | Chi tiết POI | Form đánh giá |
| Suy nghĩ / cảm xúc | Cảnh giác “có thật rẻ không” | Đối chiếu giá | Muốn đóng góp |
| Pain | PAIN-4, PAIN-5 | — | — |
| Cơ hội | → F-M2-01, F-M2-02, F-M3-02 | → F-M2-02 | → F-M4-02 |

### J3: Lịch cuối tuần vài phút (P3, JTBD-6, JTBD-7)

| Giai đoạn | Trước chuyến đi | Trong chuyến đi | Sau chuyến đi |
|---|---|---|---|
| Người dùng làm gì | Form ngắn, mặc định 2N1Đ, nhịp thư giãn → generate → bớt điểm, đổi thứ tự → lưu | Xem lịch | Ít dùng comment hơn P1 |
| Điểm chạm | Form, kết quả, M7 sửa | M7 | — |
| Suy nghĩ / cảm xúc | Vội; bỏ nếu form dài hoặc chờ không báo | Muốn ít điểm | — |
| Pain | PAIN-6, PAIN-7 | — | — |
| Cơ hội | → F-M3-01, F-M3-04, F-M7-02 | → F-M7-01 | — |

Hành trình Admin (vận hành, không phải persona): đăng nhập Admin → CRUD POI (Places điền sẵn) → xuất bản/ẩn. → F-M5-01, F-M5-02, F-M1-04.

## 2. Danh sách tính năng

| ID | Tính năng | Module | Khối | Phục vụ | Hành trình | Gói |
|---|---|---|---|---|---|---|
| F-M1-01 | Đăng ký tài khoản email/mật khẩu | M1 | B1 | điều kiện job | J1–J3 | Miễn phí |
| F-M1-02 | Đăng nhập email và Google | M1 | B1 | [DEC: Q2] | J1–J3 | Miễn phí |
| F-M1-03 | Cập nhật hồ sơ cá nhân | M1 | B1 | — phụ | — | Miễn phí |
| F-M1-04 | Admin khóa/mở khóa user | M1 | B1 | vận hành, G-6 | Admin | — |
| F-M2-01 | Tìm và lọc địa điểm theo danh mục, ngân sách | M2 | B2 | JTBD-4, JTBD-5, PAIN-4 | J2 | Miễn phí |
| F-M2-02 | Xem chi tiết POI (ảnh, giờ, giá tham khảo) | M2 | B2 | JTBD-5 | J2 | Miễn phí |
| F-M3-01 | Nhập tiêu chí chuyến (điểm, ngày, số người, ngân sách, sở thích, nhịp) | M3 | B3 | JTBD-1, JTBD-6 | J1, J3 | Miễn phí |
| F-M3-02 | Sinh lịch theo ngày từ POI ứng viên; nhãn verified/unverified | M3 | B3 | JTBD-1, PAIN-3, PS-2 | J1, J3 | Miễn phí (hạn lượt) |
| F-M3-03 | Xem lịch theo ngày/khung giờ | M3 | B3 | JTBD-1 | J1, J3 | Miễn phí |
| F-M3-04 | Tạo lại cả chuyến hoặc một ngày | M3 | B3 | JTBD-7, PAIN-7 | J1, J3 | Miễn phí (hạn lượt) |
| F-M3-05 | Lưu kế hoạch vào tài khoản | M3 | B5 | JTBD-1 | J1, J3 | Miễn phí |
| F-M3-06 | Hiển thị tổng chi phí ước tính và chi phí/người (chia đều) | M3 | B4 | JTBD-2, PAIN-2 [DEC: Q1] | J1 | Miễn phí |
| F-M4-01 | Xem đánh giá của địa điểm | M4 | B7 | JTBD-5 | J2 | Miễn phí |
| F-M4-02 | Viết / sửa / xóa đánh giá của mình (sao + nhận xét) | M4 | B7 | JTBD-5 [DEC: D0.3 (sửa)] | J2 | Miễn phí |
| F-M5-01 | Admin thêm/sửa/xóa/ẩn POI | M5 | B9 | R9, D4 | Admin | — |
| F-M5-02 | Admin tìm Places để tự điền POI | M5 | B9 | R9 [DEC: D4] | Admin | — |
| F-M7-01 | Xem lịch sử chuyến đã lưu | M7 | B5 | JTBD-7 | J1, J3 | Miễn phí |
| F-M7-02 | Sửa lịch: thêm/bớt điểm, đổi thứ tự, đổi ngày | M7 | B5 | JTBD-7 | J1, J3 | Miễn phí |
| F-M7-03 | Comment dưới chuyến đi | M7 | B8 | JTBD-8 [DEC: D0.3 (sửa)] | J1 | Miễn phí; quyền **G-6** |
| F-M10-01 | Tạo link chỉ xem + nút Share (Web Share), OG khi dán chat | M10* | B6 | JTBD-3 [DEC: Q3] | J1 | Miễn phí |
| F-M6-01 | Ước tính chi phí theo hạng mục + sửa từng dòng | M6 | — | JTBD-2 mở rộng | — | Sau MVP / ứng viên Premium |
| F-M8-01 | Ghim lịch trên bản đồ, tuyến, dẫn đường | M8 | — | PS-5, đi trong chuyến | — | Sau MVP |
| F-M9-01 | Gợi ý KS/NH/dịch vụ theo ngân sách | M9 | — | JTBD-4 mở rộng | — | Sau MVP |
| F-M10-02 | Chia sẻ ảnh thẻ Instagram/Facebook chuyên biệt | M10 | — | — | — | Won't MVP [DEC: Q3] |
| F-M11-01 | Thông báo thời tiết / giờ mở cửa (in-app + email) | M11 | — | PS-5 [DEC: Q4] | — | Sau MVP |

\*F-M10-01 là **lát cắt** M10 nằm trong MVP dù module M10 đầy đủ xếp sau. [DEC: Q3] vs [DEC: D0.3 (sửa)] — Q3 thắng cho lát cắt này vì PO đã chốt cách chia sẻ.

## 3. Ưu tiên

### MoSCoW

| Nhóm | Tính năng | Lý do |
|---|---|---|
| Must | F-M1-01, F-M1-02, F-M3-01, F-M3-02, F-M3-03, F-M3-05, F-M3-06, F-M5-01, F-M7-01, F-M7-02, F-M10-01 | Không có thì JTBD-1/2/3 của P1 không hoàn thành; không có M5 thì D5 sụp |
| Should | F-M2-01, F-M2-02, F-M3-04, F-M4-01, F-M4-02, F-M5-02, F-M7-03, F-M1-04 | Nằm trong phạm vi MVP đã chốt; thiếu thì demo kém nhưng job cốt lõi vẫn chạy được. Comment là Should vì G-6 chưa chốt quyền |
| Could | F-M1-03 | Hồ sơ không chặn job |
| Won't (lần này) | F-M6-01, F-M8-01, F-M9-01, F-M10-02, F-M11-01 | [DEC: D0.3 (sửa)] |

Must không quá nửa số dòng MVP nếu đếm Should M2/M4/comment là phần “có trong D0.3 nhưng không block JTBD-1”.

### RICE (Should và Could)

Reach = % persona bị ảnh hưởng trong quý đầu (ước, Confidence ≤ 50% vì A-UR). Impact: 3 lớn · 2 vừa · 1 nhỏ. Effort: người-tuần, team 5 + AI `[INF]`.

| ID | Reach | Impact | Confidence | Effort | Điểm | Căn cứ |
|---|---|---|---|---|---|---|
| F-M3-04 | 80 | 3 | 50% | 1 | 120 | P1 P3 hay không ưng bản 1 [DOC: J1] |
| F-M2-01 + F-M2-02 | 50 | 2 | 50% | 2 | 25 | P2; P1 có thể chỉ dùng AI |
| F-M4-02 | 40 | 2 | 50% | 1.5 | 27 | [DEC: D0.3] M4; cần user đã đi |
| F-M7-03 | 60 | 2 | 50% | 1 | 60 | PO yêu cầu MVP; G-6 có thể tăng Effort |
| F-M5-02 | 10 (Admin) | 3 | 80% | 1 | 24 | Giảm R9 rõ |
| F-M1-04 | 10 | 2 | 80% | 0.5 | 32 | Spam/comment |
| F-M1-03 | 30 | 0.5 | 50% | 0.5 | 15 | Could |

Phạm vi MVP **không đổi theo RICE**. [DEC: D0.3 (sửa)] thắng. RICE chỉ để sắp sprint trong GĐ3.

## 4. Phạm vi MVP

| Module | Trong MVP | Tính năng | Ghi chú |
|---|---|---|---|
| M1 | Có | F-M1-01, 02, 04; 03 Could | Q2 Email+Google |
| M2 | Có | F-M2-01, 02 | Should |
| M3 | Có | F-M3-01…06 | Trái tim |
| M4 | Có | F-M4-01, 02 | [DEC: D0.3 (sửa)] |
| M5 | Có | F-M5-01, 02 | Seed trước khi mở AI cho user |
| M6 | Lát cắt | F-M3-06 only | Không F-M6-01 |
| M7 | Có | F-M7-01, 02, 03 | F-M7-03 = comment |
| M8 | Không | — | Next |
| M9 | Không | — | Next |
| M10 | Lát cắt | F-M10-01 | Không F-M10-02 |
| M11 | Không | — | Next; cách thức khi làm: Q4 |

**Ngoài MVP:** F-M6-01, F-M8-01, F-M9-01, F-M10-02, F-M11-01; cộng tác sửa realtime; Splitwise.

**Tiêu chí MVP thành công:** KPI-1, KPI-2, KPI-3 trong `07-roadmap.md` (ngưỡng `[PROP]`).

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-3 | Link chỉ xem đủ, chưa cần đồng sửa | Thêm quyền editor | Prototype J1 với nhóm 5 người |
| A-4 | Comment: chỉ user đăng nhập (G-6a) | Đổi F-M7-03 + Rules | Trả lời G-6 |
| A-1 | Chờ generate ≤ 15s chấp nhận được nếu có skeleton | Cần lịch mẫu | Đo p95 |

## Bàn giao
- Giai đoạn 2: J1–J3 + cột MVP → danh sách màn Snn; Admin → Ann. Không vẽ màn M8/M11 trừ ghi chú “sau”.
- Giai đoạn 3: mỗi F-M*-** Must/Should MVP → FR/US.
- Roadmap: Now = bảng §4; Next = M8 + M11 (PS-5) rồi M6/M9.
