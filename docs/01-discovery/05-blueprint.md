---
topic: Solution Blueprint
status: draft
sources: [bao-cao-f5, scope, prior-research, po-answers]
updated: 2026-11-21
---

# Solution Blueprint & Business Model

## TL;DR
Web mobile-first: user nhập tiêu chí → Gemini **chỉ chọn POI trong DB** → lịch theo ngày sửa được → lưu, chia sẻ, chi phí/người, đánh giá điểm, comment chuyến. Admin curate POI. Freemium `[PROP]` ranh giới gói. Rủi ro lớn: AI bịa / hết quota / POI ít. Tin cậy giải pháp: **cao** (đã chốt stack). Tin cậy thương mại: **thấp**.

## 1. Giải pháp tổng thể
Người dùng mở website, đăng nhập, tạo chuyến bằng AI từ điểm đến – ngày – số người – mức ngân sách – sở thích. Hệ thống lấy ứng viên POI trong Firestore, gọi Gemini qua Cloud Functions, trả lịch theo ngày/khung giờ. User xem, tạo lại, sửa tay, thấy tổng tiền và tiền/người, lưu, gửi link xem. Có thể tìm điểm, viết đánh giá sao, comment dưới chuyến. Admin thêm/sửa/ẩn POI và khóa user. [DOC: bao-cao-f5] [DEC: D0.2] [DEC: D0.3 (sửa)] [DEC: D5] [DEC: D7 (sửa lần 2)]

Bản đồ turn-by-turn, chi phí hạng mục đầy đủ, gợi ý KS/NH, thông báo thời tiết: **sau MVP**. [DEC: D0.3 (sửa)]

### Các khối giải pháp

| Khối | Làm gì | Job / Pain giải quyết | Module sản phẩm | Phụ thuộc bên ngoài |
|---|---|---|---|---|
| B1 Tài khoản | Đăng ký/đăng nhập email+Google, hồ sơ, Admin khóa user | Điều kiện dùng các job; bảo vệ comment (G-6) | M1 | Firebase Auth |
| B2 Khám phá POI | Tìm, lọc, xem chi tiết điểm | JTBD-5, PAIN-5 | M2 | Firestore; Places bổ sung [DEC: D4] |
| B3 Lịch AI kiểm chứng | Sinh lịch từ POI ứng viên, nhãn verified/unverified, tạo lại | JTBD-1, JTBD-6, PAIN-3, PAIN-6 | M3 | Gemini API (server) |
| B4 Chi phí/người | Tổng ước tính + chia đều theo số người | JTBD-2, PAIN-2 | Lát cắt M6 trên M3/M7 | Giá tham khảo trong POI |
| B5 Lịch đã lưu & sửa tay | Lịch sử, thêm/bớt/đổi thứ tự/ngày | JTBD-7 | M7 | Firestore |
| B6 Chia sẻ xem | Link chỉ xem + Web Share + OG | JTBD-3, GAIN-1 | Lát cắt M10 [DEC: Q3] | Hosting |
| B7 Đánh giá địa điểm | Sao + nhận xét, sửa/xóa của mình | JTBD-5, GAIN-4 | M4 | Firestore |
| B8 Comment chuyến | Bình luận dưới chuyến đã lưu/chia sẻ | JTBD-8, GAIN-8 | M7 (tính năng mới) | Auth + Rules; **G-6** |
| B9 Vận hành POI | Admin CRUD POI, seed 8 điểm đến | PAIN-5, R9 | M5 | Google Places (điền sẵn) |

Khối sau MVP (không thiết kế sâu ở đây): Bản đồ & dẫn đường (M8), Chi phí chi tiết/tùy chỉnh (phần còn lại M6), Gợi ý KS/NH (M9), Thông báo (M11), cộng tác sửa realtime.

### Luồng giá trị chính
Nhu cầu chuyến đi → (B1) vào được hệ thống → (B3) nhận lịch kiểm chứng → (B4) thấy tiền/người → (B5) chỉnh cho vừa nhóm → (B6) gửi bạn → (B7/B8) đánh giá điểm / comment chuyến → (B9) Admin giữ POI đủ để B3 không rỗng.

## 2. Value Proposition Canvas

| Phía khách hàng (P1) | Phía sản phẩm |
|---|---|
| **Jobs:** JTBD-1, JTBD-2, JTBD-3 | **Sản phẩm & dịch vụ:** B3, B4, B5, B6 |
| **Pains:** PAIN-1, PAIN-2, PAIN-3 | **Pain relievers:** một lịch chính; tiền/người; POI + nhãn tin cậy |
| **Gains:** GAIN-1, GAIN-2 | **Gain creators:** link Zalo; số tiền chia đều |

**Độ khớp:** PAIN liên quan thời tiết/đóng cửa (PS-5) **chưa có khối MVP** — ghi nhận cho Next (M11/M8). Comment (JTBD-8) có B8 nhưng quyền ai viết còn **G-6**.

## 3. Product Canvas

| Mục | Nội dung |
|---|---|
| Tên sản phẩm | TrekMate |
| Persona chính | P1 |
| Vấn đề cốt lõi | PS-1, PS-2, PS-3 |
| Giải pháp | Lịch AI neo POI + chi phí/người + chia sẻ web |
| Điểm khác biệt | USP trong `04-vision.md` |
| Chỉ số thành công | KPI-1 North Star: chuyến lưu và chia sẻ / tuần (`07-roadmap.md`) |
| Ràng buộc | Web mobile-first; VN; VNĐ; stack D0.2; hạ tầng ~0đ; team 5 SV + coding agent |
| Rủi ro lớn nhất | R1 AI bịa / schema lỗi; R9 POI ít; R2 hết quota Gemini |

## 4. Business Model

### Lean Canvas

| Ô | Nội dung | Nguồn |
|---|---|---|
| Vấn đề | PS-1, PS-2, PS-3 | `01-problem.md` |
| Phân khúc khách hàng | P1 sớm (nhóm SV); P2 P3 mở rộng | [DEC: D6] |
| Giải pháp | B3, B4, B6 | |
| Giá trị độc nhất | Lịch AI kiểm chứng + tiền/người cho người Việt | `04-vision.md` |
| Lợi thế khó sao chép | Bộ POI curate 8 điểm + schema D5 (yếu nếu không seed) | [DEC: D4] [DEC: Q5] |
| Kênh | Bạn bè đội, link Zalo | `04-vision.md` |
| Dòng doanh thu | Freemium: Premium sau khi job cốt lõi miễn phí | [DEC: D-BM] |
| Cơ cấu chi phí | Firebase Blaze (Functions), Gemini, Maps, domain | [DOC: prior-research §8] |
| Chỉ số then chốt | Chuyến lưu+chia sẻ; % activation; % POI verified trong lịch | `07-roadmap.md` |

### Ranh giới gói miễn phí và trả phí

`[PROP]` — chưa có DEC chi tiết. Job cốt lõi P1 **ở Free**.

| Năng lực | Miễn phí | Trả phí (Premium) | Lý do |
|---|---|---|---|
| Tạo lịch AI | Có, **giới hạn lượt/ngày** (ví dụ 5–10) | Nới hạn / ưu tiên | Bảo vệ quota R2; job vẫn làm được |
| Lưu & sửa lịch | Có | — | JTBD-1, JTBD-7 |
| Chi phí/người chia đều | Có | — | JTBD-2 |
| Link chia sẻ chỉ xem | Có | — | JTBD-3 |
| Đánh giá POI + comment chuyến | Có | — | M4 + JTBD-8 trong MVP |
| Tạo lại theo ngày | Có, tính vào hạn mức | Không tính / hạn cao | [DOC: prior-research J1] |
| Chia hóa đơn chi tiết | Không (sau MVP) | Ứng viên Premium | [DEC: Q1] |
| Bản đồ dẫn đường, thông báo, M9 | Không ở MVP | Có thể gói sau | [DEC: D0.3 (sửa)] |
| Xuất PDF / bỏ branding | Không | `[PROP]` | Không cần cho job cốt lõi |

Câu hỏi ranh giới chi tiết: **G-7** (hàng đợi).

### Chi phí vận hành

| Hạng mục | Cách tính | Ước tính | Nguồn |
|---|---|---|---|
| Firebase Hosting, Auth, Firestore | Spark không đủ Functions; cần Blaze, dùng hạn mức miễn phí | `[TBD]` số USD/tháng khi có traffic; MVP demo thường trong free quota | [DOC: prior-research §8] — kiểm tra [firebase.google.com/pricing](https://firebase.google.com/pricing) lúc triển khai |
| Cloud Functions | Gọi Gemini/Places phía server | `[TBD]` theo số generate | R2, R7 |
| Gemini API | Một số model có free tier; model frontier trả phí | Free tier tồn tại cho một phần model (11/2026); không lấy giá $ bịa | [DOC: web – aistudio.google.com/docs/pricing, 11/2026](https://aistudio.google.com/docs/pricing) |
| Google Maps Platform | Maps JS / Places / Directions | `[TBD]`; cache Places vào Firestore | R6 |
| Tên miền | Năm | ~300.000 ₫/năm (số từ tài liệu cũ, cần check nhà đăng ký) | [DOC: prior-research §8] |

Không bịa ngưỡng quota Firebase/Maps. Trước sprint code: chép bảng giá chính thức vào đây.

## 5. Rủi ro & phụ thuộc

| ID | Rủi ro | Khối bị ảnh hưởng | Cách giảm | Tin cậy |
|---|---|---|---|---|
| R1 | AI bịa điểm, sai schema | B3 | JSON schema, Zod, chỉ `poiId` trong danh sách, retry, nhãn unverified | cao [DOC: prior-research] |
| R2 | Hết quota Gemini | B3 | Rate limit/user, cache hash input, tạo lại theo ngày, hạn Free | cao |
| R6 | Hết hạn mức Maps | B2, M8 sau | Cache Places; MVP hạn chế Maps JS | trung bình |
| R7 | Rules lỏng, lộ chuyến/comment | B5 B6 B8 | Rules theo role; emulator tests | cao |
| R9 | POI ít → lịch kém | B3 B9 | Seed 8 điểm, 20–40 POI/điểm trước khi demo AI | cao [DEC: Q5] |
| R-G6 | Comment spam / ẩn danh | B8 | Chờ G-6; mặc định A-4: phải đăng nhập | trung bình |

Gemini và Maps **key chỉ ở server**. [DOC: prior-research §8]

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-2 | 150–300 POI / 8 điểm đủ demo | Phải import Places nhiều hơn | Thử generate 3 điểm đến seed |
| A-4 | Comment yêu cầu đăng nhập (khuyến nghị G-6a) | Đổi Rules và luồng B8 | Trả lời G-6 |
| A-BM | User chấp nhận hạn lượt AI ở Free | Phải nới Free, rủi ro R2 | Đếm generate/user khi có bản thử |

## Bàn giao
- Journey & Features: B1–B9 = nhóm tính năng MVP; M8/M9/M11/M6 đầy đủ = Next.
- Roadmap: seed POI trước khi phụ thuộc B3; Freemium chưa thu tiền ở Now.
- Giai đoạn 3: phụ thuộc Auth, Functions, Gemini, Places, Rules.
- Giai đoạn 2: không thiết kế màn M8/M11 trừ chỗ “bàn giao sau”.
