---
topic: Vision
status: draft
sources: [prior-research, po-answers, bao-cao-f5]
updated: 2026-11-21
---

# Vision

## TL;DR
TrekMate là web (mobile-first) để người Việt đi trong nước có **lịch AI kiểm chứng + chi phí/người + chia sẻ nhóm**. Persona chính: P1. USP: không bịa điểm vì neo POI Admin. Tầm nhìn 3 năm phụ thuộc **G-1** (đồ án vs sản phẩm sống) — bản dưới là `[PROP]`, tin cậy **thấp**.

## Tầm nhìn
**[PROP, G-1]** Sau 3 năm, nhóm bạn Việt Nam lên chuyến tự túc trong nước thì mở TrekMate trước, thay vì ghép Zalo + Maps + chatbot — vì lịch đáng tin và tiền/người hiện sẵn.

Giải thích: nếu G-1 chọn “chủ yếu đồ án”, tầm nhìn thu hẹp thành *bảo vệ được sản phẩm demo tin cậy trên 8 điểm đến seed*. Nếu chọn “người dùng thật lâu dài”, cùng một câu nhưng Roadmap Later phải có kênh tăng trưởng và Premium. [INF: from G-1 chưa trả lời + D-BM]

## Sứ mệnh
Mỗi ngày, giúp người đi tự túc biến tiêu chí chuyến đi (nơi, ngày, túi tiền, sở thích) thành **lịch theo ngày có thể sửa, lưu, chia sẻ**, với điểm lấy từ dữ liệu đã kiểm soát. [DOC: bao-cao-f5] [DEC: D5]

## Product Statement
Dành cho **[P1 – nhóm trưởng chuyến bạn bè]**
đang **[ghép nhiều nguồn và không tin lịch AI, khó chốt tiền/người — PS-1, PS-2, PS-3]**,
**TrekMate** là **website lên kế hoạch du lịch tự túc trong nước**
giúp **có lịch theo ngày dùng được, biết mỗi người góp bao nhiêu, gửi được cho nhóm**.
Khác với **[chatbot + Zalo, hoặc AI planner quốc tế]**,
sản phẩm **chỉ ghép điểm đã có trong dữ liệu Việt Nam (nhãn rõ điểm chưa xác minh) và tính chi phí/người ngay trên lịch**. [DEC: D1] [DEC: D5] [DEC: Q1]

## Định vị

| Tiêu chí người dùng quan tâm | TrekMate | Vie Travel AI | Wanderlog | Tự xoay xở (Zalo+Maps+ChatGPT) |
|---|---|---|---|---|
| Lịch AI theo ngày, tiếng Việt, đi trong nước | Trái tim sản phẩm | Có, app | AI phụ | Có text, không cấu trúc |
| Điểm không bịa (neo dữ liệu kiểm soát) | Bắt buộc D5 | Không rõ cơ chế Admin POI đồ án | User tự thêm điểm | Tự đối chiếu |
| Chi phí/người chia đều | MVP | Ngân sách chuyến (theo thông cáo) | Split bills mạnh | Excel sau chuyến |
| Mở link không cần cài app | Web + link xem [DEC: Q3] | App Store | Có web | Screenshot |
| Cộng tác sửa realtime | Không ở MVP (A-3) | Không phải USP đã thấy | Mạnh | Zalo |

## USP
**Lịch trình AI cho người Việt đi trong nước, chỉ chọn từ POI do Admin quản lý, gắn nhãn tin cậy, kèm chi phí/người để gửi nhóm.** Gắn chỗ trống 1+2 trong `03-market.md` và PS-2, PS-3.

Vì sao khó sao chép ngay: không phải mô hình ngôn ngữ, mà **bộ POI đã curate + quy tắc Gemini không được bịa id** + UX nhóm tối giản. Đối thủ lớn có data toàn cầu nhưng không làm lớp kiểm soát này cho 8 điểm đến Việt Nam. [DEC: D4] [DEC: D5]

Không lấy USP: đặt phòng, chatbot visa, cộng tác Google-Docs, dẫn đường turn-by-turn (M8 sau MVP).

## Nguyên tắc sản phẩm

1. **Đáng tin hơn “hay”** — thà ít điểm đã xác minh còn hơn lịch đẹp mà bịa. [DEC: D5]
2. **Job cốt lõi P1 nằm ở gói miễn phí** — tạo lịch, lưu, xem chi phí/người, chia sẻ. [DEC: D-BM] [INF: from synthesis-contract]
3. **Một lịch cho cả nhóm, không phải một cuộc chat** — form + kết quả theo ngày, chỉnh tay được. [DOC: prior-research J1]
4. **Mobile-first, dùng được khi dán Zalo** — không bắt app. [DEC: D7 (sửa lần 2)] [DEC: Q3]
5. **Chi phí hạ tầng tiến tới 0đ** — cache, rate limit, không nhét API key ra client. [DOC: prior-research §8]

## Tiếp cận người dùng đầu tiên (Go-to-Market sơ bộ)

| Kênh | Persona | Vì sao | Chi phí | Nguồn |
|---|---|---|---|---|
| Bạn cùng lớp / nhóm đi chung của thành viên | P1 | Đồ án, vòng đầu 0đ | 0đ | [INF: đội 5 sinh viên, bao-cao-f5] |
| Link chia sẻ có Open Graph khi dán Zalo/Messenger | P1 bạn đi cùng | Viral vòng gần | 0đ (Hosting) | [DEC: Q3] |
| Community sinh viên / group du lịch tự túc | P2 | Đúng túi tiền | thời gian | [PROP] |

Không chạy ads ở V1. Phụ thuộc G-1: nếu chỉ đồ án thì kênh 1+2 đủ.

## Thành công trông như thế nào
- **Định tính [PROP, G-3]:** “Lịch này dùng được luôn, không phải soi lại từng quán; nhóm mình biết phải góp bao nhiêu.” PO có thể thay câu này.
- **Đo được (chi tiết `07-roadmap.md`):** chuyến được lưu và chia sẻ; ≥ 60% user mới tạo được 1 lịch AI trong phiên đầu `[PROP]` từ prior-research.

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-V1 | USP “POI kiểm chứng + tiền/người” đủ khác Vie Travel | Phải đổi USP (ví dụ chỉ đồ án demo) | So feature khi demo cạnh nhau |
| G-1 | Tầm nhìn 3 năm chưa chốt | Roadmap Later có thể thừa/thiếu | Trả lời G-1 |

## Bàn giao
- Blueprint: statement + nguyên tắc 1–5 là ràng buộc; Freemium không khóa job P1.
- Roadmap: North Star = chuyến lưu và chia sẻ.
- Giai đoạn 2: tính cách “tươi, tiết kiệm, đáng tin, đi nhóm”; không luxury booking.
