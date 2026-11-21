---
topic: Problem
status: draft
sources: [scope, bao-cao-f5, prior-research, po-answers]
updated: 2026-11-21
---

# Problem

## TL;DR
Người Việt đi du lịch tự túc trong nước phải ghép nhiều công cụ để có một chuyến đi dùng được: tìm điểm, sắp ngày, ước chi phí, thống nhất với nhóm. [DOC: bao-cao-f5] Lịch trình từ chatbot dễ sai địa điểm và giờ; nhóm bạn khó chốt kế hoạch và tiền. [DOC: prior-research] Độ tin cậy tổng: **trung bình** vì chưa khảo sát user thật (A-UR, G-5 đã đóng).

## Bối cảnh
Người đi tự túc (cá nhân, nhóm bạn, gia đình) cần tìm điểm tham quan, dựng lịch từng ngày, xem đường, dự toán chi tiêu, rồi gửi cho bạn đồng hành. [DOC: bao-cao-f5 §Chương 1] Họ đang xoay xở bằng Google Maps, review TikTok/Facebook, bảng tính chi phí, nhóm Zalo và ChatGPT/Gemini chat. [DOC: prior-research §1] [INF: from DOC bao-cao-f5 + prior-research] Thông tin nằm rải, mỗi công cụ chỉ giải một mảnh; không có một nơi vừa lịch theo ngày, vừa chi phí/người, vừa chia sẻ. Phạm vi vấn đề ở MVP là **đi trong nước, VNĐ**. [DEC: D1] [DEC: D3]

Chưa có phỏng vấn hay khảo sát thật. [STK: PO, 16/11/2026] Mọi mức “tần suất / nghiêm trọng” dưới đây là suy luận từ tài liệu đồ án và lời PO, tối đa tin cậy trung bình (A-UR).

## Danh sách vấn đề

| ID | Vấn đề | Ai gặp | Tần suất | Mức nghiêm trọng | Bằng chứng | Tin cậy |
|---|---|---|---|---|---|---|
| PS-1 | Ghép nhiều nguồn mất giờ mới có lịch dùng được | P1, P2, P3 | mỗi chuyến đi | cao | [DOC: bao-cao-f5] [DOC: prior-research PS1] | trung bình |
| PS-2 | Lịch từ AI/chatbot bịa điểm, sai giờ, không kiểm chứng | P1, P2, P3 | mỗi lần nhờ AI | cao | [DOC: prior-research PS2] [INF: from R1] | trung bình |
| PS-3 | Nhóm khó thống nhất một kế hoạch và biết mỗi người góp bao nhiêu | P1 | mỗi chuyến nhóm | cao | [STK: PO, 14/11/2026] [DOC: prior-research PS3] | trung bình |
| PS-4 | Phương án trên mạng thường không khớp túi tiền thấp | P2 | mỗi chuyến tiết kiệm | cao | [DOC: prior-research PS4] [STK: PO – persona P2] | thấp |
| PS-5 | Khi đang đi, thông tin đổi (mưa, đóng cửa) mà kế hoạch không kịp cập nhật | P1, P2, P3 | trong chuyến | trung bình | [DOC: bao-cao-f5 mục h] [DOC: prior-research PS5] | thấp |

## Chi tiết từng vấn đề

### PS-1: Phân mảnh thông tin khi lên kế hoạch
- **Tình huống:** còn vài ngày đến vài tuần trước chuyến 2–4 ngày trong nước, người lên kế hoạch phải chọn điểm, sắp thứ tự, ước tiền.
- **Hậu quả:** mất nhiều giờ; lịch dở dang; bỏ sót giờ mở cửa hoặc khoảng cách; cảm giác “chưa sẵn sàng”.
- **Cách xoay xở hiện tại:** tab Maps + TikTok + Excel/Zalo. Thiếu một lịch theo ngày/khung giờ có thể lưu và mở lại. [DOC: prior-research §1]
- **How might we:** làm sao để có lịch trình theo ngày dùng được ngay mà không phải ghép 4–6 công cụ?

### PS-2: Không tin được lịch do AI viết
- **Tình huống:** nhờ ChatGPT/Gemini (hoặc app AI chung) “lên lịch 3 ngày Hội An”.
- **Hậu quả:** đến nơi mới biết quán đóng, điểm không tồn tại, hoặc quá xa; mất thời gian và tiền; mất niềm tin vào công cụ.
- **Cách xoay xở hiện tại:** tự đối chiếu lại Maps/review từng điểm — gần như làm lại từ đầu. [DOC: prior-research PS2, R1]
- **How might we:** làm sao để lịch do máy đề xuất chỉ dùng điểm kiểm chứng được, và người dùng thấy rõ điểm nào chưa chắc?

### PS-3: Nhóm không ngồi trên cùng một kế hoạch và một con số tiền
- **Tình huống:** một người (thường “nhóm trưởng”) soạn lịch; 4–5 bạn góp ý trên Zalo; cuối chuyến mới chia tiền.
- **Hậu quả:** bàn loãng, mỗi người một file; không biết trước phải góp bao nhiêu; căng thẳng sau chuyến. [DOC: prior-research P1]
- **Cách xoay xở hiện tại:** screenshot, Google Docs, chia tay bằng máy tính. Link xem chung và chi phí/người là phần MVP; chia hóa đơn chi tiết để sau. [DEC: Q1]
- **How might we:** làm sao để cả nhóm xem cùng một kế hoạch và biết mỗi người góp bao nhiêu trước khi đi?

### PS-4: Người túi tiền thấp không thấy phương án thật sự rẻ
- **Tình huống:** sinh viên/người trẻ chọn “tiết kiệm” nhưng blog và AI vẫn gợi ý quán/tour trung–cao cấp.
- **Hậu quả:** vượt ngân sách hoặc bỏ cuộc, nghĩ “công cụ này không dành cho mình”.
- **Cách xoay xở hiện tại:** hỏi bạn, lướt TikTok quán bình dân, tự lọc homestay/xe khách. [DOC: prior-research PS4]
- **How might we:** làm sao để mức ngân sách thấp cho ra phương án khác hẳn (xe khách/xe máy, quán bình dân, homestay) và thấy rõ tiền?

### PS-5: Kế hoạch “chết” khi thực tế đổi
- **Tình huống:** đang ở điểm đến, trời mưa, điểm đóng cửa, nhóm muốn đổi.
- **Hậu quả:** lịch trên giấy/ảnh screenshot không cập nhật; bỏ lỡ hoặc đi đường vòng.
- **Cách xoay xở hiện tại:** hỏi nhóm Zalo, mở Maps lại. Thông báo thời tiết/giờ mở cửa thuộc M11, **sau MVP**. [DEC: D0.3 (sửa)] [DOC: bao-cao-f5 mục h]
- **How might we:** làm sao nhắc đúng lúc khi kế hoạch không còn khớp thực tế, mà không làm phiền? *(HMW cho giai đoạn Next; MVP chỉ cần lịch sửa được tay.)*

## Vì sao bây giờ
- Du lịch nội địa Việt Nam lớn và đang tăng: **110 triệu lượt khách nội địa năm 2024**; năm 2025 ước **135,5 triệu lượt**. [DOC: web – vietnamtourism.gov.vn, 01/2025] [DOC: web – vietnamtourism.vn, 12/2025]
- LLM (Gemini) đủ rẻ/dễ gọi để sinh lịch JSON, nhưng rủi ro bịa điểm vẫn còn — cần neo vào dữ liệu do nhóm kiểm soát. [DEC: D5] [INF: from D5 + R1]
- Đối thủ AI trip planner quốc tế không tối ưu túi tiền và cách đi của người Việt; trong nước đã có Vie Travel AI (ra mắt 01/2026) — cửa sổ “làm gọn cho nhóm bạn Việt Nam” vẫn mở nếu TrekMate khác ở kiểm chứng POI + chi phí nhóm. [DOC: web – english.vtv.vn, 01/2026] Chi tiết đối thủ: `03-market.md`.

## Vấn đề không giải quyết
| Vấn đề | Lý do để ngoài |
|---|---|
| Đặt vé máy bay, khách sạn, tour trong app | Ngoài stack và MVP; M9 gợi ý dịch vụ sau MVP. [DEC: D0.3 (sửa)] |
| Du lịch nước ngoài, đa tiền tệ | [DEC: D1] [DEC: D3] |
| Chia hóa đơn kiểu Splitwise (ai trả món nào) | [DEC: Q1] — sau MVP |
| Cộng tác sửa lịch realtime nhiều người | Giả định A-3: link chỉ xem đủ cho MVP. [DOC: prior-research A3] |
| Thông báo thời tiết / đóng cửa chủ động | M11 sau MVP. [DEC: D0.3 (sửa)] |

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-UR | Mô tả pain của P1–P3 đúng hướng dù chưa phỏng vấn | Có thể sai persona/PS ưu tiên | Khảo sát 8–12 người đi tự túc trước khi khóa GĐ3 |
| A-1 | Người dùng chấp nhận chờ 10–15 giây nếu thấy tiến trình | Cần lịch mẫu/cache, không chỉ generate live | Đo thời gian bỏ form khi prototype |
| A-WAIT | PS-5 không chặn job cốt lõi ở MVP nếu lịch sửa tay được | Phải kéo M11 vào MVP | Xem GĐ2: user có đòi “Hôm nay / thời tiết” ngay demo không |

## Bàn giao
- Personas: PS-1→P1 P2 P3; PS-2→P1 P2 P3; PS-3→P1; PS-4→P2; PS-5→P1 P2 P3.
- Vision: cốt lõi là PS-1 + PS-2 + PS-3.
- Giai đoạn 3: PS-n là gốc truy vết cho yêu cầu chức năng.
- Câu người dùng nói sau chuyến đầu: **G-3** (chưa chốt).
