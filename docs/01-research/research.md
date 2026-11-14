# 01 – Research & Discovery: TrekMate

> Giai đoạn 1/5 · Trạng thái: **Bản nháp chờ duyệt** · Cập nhật: 14/11/2026
> Nguồn đầu vào: `F5_BaoCao_final_v1.docx`, `Scope1.docx`, `UpdateTrekMate_WBS.xlsx`, `TrekMate_Chuong4_DieuHanhDuAn_v2.docx` + khảo sát đối thủ trên web.
> Tài liệu này là **nguồn sự thật (source of truth)** cho các giai đoạn sau. AI coding agent phải đọc file này trước khi đọc PRD.

---

## 1. Tóm tắt sản phẩm (Product one-liner)

**TrekMate** là web app giúp người Việt đi du lịch tự túc **trong nước** tạo lịch trình theo ngày bằng AI (Gemini), xem tuyến đường trên bản đồ (Google Maps), ước tính chi phí và chia sẻ kế hoạch cho bạn đồng hành, tất cả trên một nơi.

**Vấn đề cốt lõi:** người đi tự túc phải ghép 4–6 công cụ (Google Maps, TikTok/Facebook review, Excel chi phí, Zalo nhóm, ChatGPT) để lên một chuyến đi. Thông tin phân mảnh, lịch trình AI chung chung hay “bịa” địa điểm, chi phí không minh bạch.

## 2. Quyết định đã chốt ở GĐ1

| # | Quyết định | Giá trị | Lý do |
|---|---|---|---|
| D1 | Phạm vi địa lý MVP | **Việt Nam** (điểm đến trong nước) | Dữ liệu POI kiểm soát được; tiền tệ VNĐ; UI tiếng Việt |
| D2 | Ngôn ngữ UI | Tiếng Việt (chuẩn bị sẵn i18n key để thêm EN sau) | Persona là người Việt |
| D3 | Tiền tệ | VNĐ, số nguyên, không thập phân | Đơn giản hóa tính chi phí |
| D4 | Nguồn POI | **Kết hợp**: Firestore (Admin quản lý) là nguồn chính; Google Places bổ sung ảnh, giờ mở cửa, toạ độ, rating | Admin kiểm soát chất lượng; Places giảm công nhập tay |
| D5 | AI grounding | Gemini **chỉ được chọn POI từ danh sách ứng viên** lấy trong DB; được phép đề xuất “điểm ngoài danh sách” nhưng phải gắn cờ `unverified` | Giảm rủi ro R1 (AI trả kết quả sai, bịa địa điểm) |
| D6 | Persona ưu tiên | P1 Nhóm bạn chia chi phí · P2 Sinh viên tiết kiệm · P3 Dân văn phòng đi cuối tuần | Theo lựa chọn của PO |
| D7 | Nền tảng | Web responsive, **mobile-first** (dùng khi đang đi) | Hạn chế 5.2 của báo cáo: chưa có app mobile |
| D8 | Phương pháp phát triển | Chuyển từ Waterfall (báo cáo môn học) sang **Agile/Scrum, sprint 1 tuần**, MVP trước | Phù hợp vibe-code với AI: vòng ngắn, kiểm thử liên tục |

## 3. Persona

### P1 – “Nhóm trưởng” Minh, 22 tuổi, sinh viên năm 4 (Đà Nẵng)
- **Bối cảnh:** tổ chức chuyến 3N2Đ Hội An – Huế cho nhóm 5 bạn, ngân sách ~1,5–2 triệu/người.
- **Mục tiêu:** có lịch trình hợp lý trong 10 phút; gửi link cho cả nhóm xem; biết tổng chi phí và **mỗi người phải góp bao nhiêu**.
- **Nỗi đau:** cả nhóm bàn trên Zalo rất loãng; mỗi người một ý; cuối chuyến tính tiền rối.
- **Hành vi:** dùng điện thoại 90%, đọc review TikTok, ưu tiên quán bình dân, đi xe máy.
- **Thành công khi:** link chia sẻ mở được không cần đăng nhập; chi phí hiển thị theo đầu người.

### P2 – Lan, 20 tuổi, sinh viên đi “du lịch bụi” tiết kiệm
- **Bối cảnh:** đi một mình hoặc đi cùng 1 bạn, ngân sách thấp, thời gian linh hoạt.
- **Mục tiêu:** tối đa điểm miễn phí/giá rẻ; biết đi xe buýt/xe máy đến đâu; tránh “bẫy giá” du lịch.
- **Nỗi đau:** lịch trình trên mạng thường dành cho ngân sách trung/cao cấp.
- **Thành công khi:** mức ngân sách “Tiết kiệm” thực sự cho ra phương án rẻ (quán bình dân, homestay/hostel, xe buýt).

### P3 – Anh Tuấn, 29 tuổi, nhân viên văn phòng (TP.HCM)
- **Bối cảnh:** đi cuối tuần 2N1Đ (Đà Lạt, Vũng Tàu), ít thời gian chuẩn bị.
- **Mục tiêu:** tạo kế hoạch trong vài phút, đặt chỗ ở tốt, lịch không quá dày.
- **Nỗi đau:** không có thời gian đọc nhiều review; ghét lịch trình chạy show.
- **Thành công khi:** AI tôn trọng nhịp độ “thư giãn”, giờ mở cửa đúng, có nhắc nhở thời tiết.

> **Admin (vai trò vận hành):** cần trang quản trị nhanh để thêm/sửa/xoá POI, đồng bộ dữ liệu từ Google Places, khoá tài khoản vi phạm, ẩn đánh giá spam.

## 4. User journey chính (Journey map rút gọn)

### J1 – Tạo chuyến đi bằng AI (P1, P3) – luồng “trái tim” của sản phẩm
| Bước | Người dùng làm | Hệ thống làm | Cảm xúc / rủi ro | Cơ hội thiết kế |
|---|---|---|---|---|
| 1 | Bấm “Tạo chuyến đi bằng AI” | Mở form nhiều bước | Hào hứng | Form ≤ 4 bước, có giá trị mặc định |
| 2 | Chọn điểm đến, ngày đi–về, số người, ngân sách (Tiết kiệm/Trung bình/Cao cấp), sở thích, nhịp độ | Validate; lấy POI ứng viên từ Firestore theo điểm đến | Lo nhập sai | Gợi ý điểm đến phổ biến; chip sở thích |
| 3 | Chờ AI | Gọi Cloud Function → Gemini (JSON schema) → validate | **Chờ lâu = bỏ** | Skeleton + thông điệp tiến trình; mục tiêu < 15 giây |
| 4 | Xem lịch trình theo ngày/khung giờ + bản đồ + tổng chi phí | Ghim POI lên bản đồ, tính chi phí | Kiểm tra độ tin cậy | Nhãn “Đã xác minh” / “AI đề xuất – chưa xác minh” |
| 5 | Chỉnh: kéo thả đổi thứ tự, thêm/bớt, “Tạo lại ngày này” | Cập nhật, tính lại chi phí và tuyến | Muốn kiểm soát | Tạo lại **một ngày** thay vì cả chuyến (tiết kiệm quota) |
| 6 | Lưu & chia sẻ link cho nhóm | Lưu `trips/{id}`, tạo link chia sẻ chỉ đọc | Tự hào | Link mở không cần đăng nhập; preview đẹp khi dán vào Zalo/Messenger |

### J2 – Khám phá & đánh giá địa điểm (P2)
Tìm kiếm → lọc theo danh mục/ngân sách → xem chi tiết (ảnh, giờ mở cửa, giá tham khảo, đánh giá) → “Thêm vào chuyến đi” → sau chuyến đi viết đánh giá.

### J3 – Trong chuyến đi (P1, P2)
Mở lịch trình hôm nay → xem điểm tiếp theo → “Dẫn đường” (mở Google Maps directions) → nhận thông báo thời tiết xấu/đóng cửa → ghi chi phí thực tế.

### J4 – Admin quản trị POI
Đăng nhập Admin → danh sách POI → thêm POI (tìm bằng Google Places để tự điền) → chỉnh giá tham khảo, danh mục, mức ngân sách → xuất bản/ẩn.

## 5. Khảo sát đối thủ (tóm tắt, 11/2026)

| Đối thủ | Điểm mạnh | Điểm yếu so với nhu cầu của persona TrekMate |
|---|---|---|
| **Mindtrip** | Lập kế hoạch qua chat trên bản đồ, dữ liệu POI rất lớn, đã có đặt vé máy bay | Thiên về thị trường quốc tế, không tối ưu cho ngân sách và cách đi của người Việt |
| **Layla** | Lịch trình kèm giá khách sạn trực tiếp, cảnh báo giá | Chủ yếu qua chat, ít chỉnh tay, không có cộng tác nhóm |
| **Wanderlog** | Lên kế hoạch nhóm trên bản đồ, cộng tác tốt | Phần AI nhẹ hơn các planner chuyên AI |
| **Vie Travel AI** (VN) | Song ngữ Việt–Anh, AI Trip Planner, cá nhân hoá | Đối thủ trực tiếp trong nước, cần theo dõi |
| **ChatGPT / Gemini app** | Linh hoạt, miễn phí | Không thành lịch trình dùng được ngay: không bản đồ, không lưu, dễ bịa thông tin |

**Định vị khác biệt của TrekMate (Positioning):**
1. **Cho người Việt đi trong nước, theo túi tiền**: 3 mức ngân sách ra phương án thật sự khác nhau (xe buýt/xe máy, quán bình dân, homestay).
2. **AI có kiểm chứng**: lịch trình được neo vào POI do Admin quản lý, gắn nhãn rõ điểm nào đã xác minh.
3. **Đi nhóm**: chia sẻ link chỉ đọc, chi phí theo đầu người (MVP); chia tiền chi tiết là tính năng sau MVP (xem câu hỏi mở Q1).
4. **Mobile-first, dùng được trong lúc đi**: chế độ “Hôm nay”, dẫn đường bằng một chạm.

## 6. Problem statements & “How might we”

| Mã | Problem statement | How might we… |
|---|---|---|
| PS1 | Người đi tự túc mất nhiều giờ ghép thông tin từ nhiều nguồn | …tạo lịch trình theo ngày dùng được ngay trong < 2 phút? |
| PS2 | Lịch trình AI hay bịa địa điểm, sai giờ mở cửa | …chỉ để AI chọn trong dữ liệu đã xác minh và cho thấy rõ độ tin cậy? |
| PS3 | Nhóm bạn khó thống nhất kế hoạch và chi phí | …giúp cả nhóm xem cùng một kế hoạch và biết mỗi người phải góp bao nhiêu? |
| PS4 | Người ngân sách thấp không tìm được phương án phù hợp | …để mức “Tiết kiệm” thực sự rẻ và minh bạch? |
| PS5 | Khi đang đi, thông tin thay đổi (mưa, đóng cửa) | …nhắc đúng lúc mà không làm phiền? |

## 7. Chỉ số thành công (North Star & KPI MVP)

- **North Star:** số chuyến đi được **lưu và chia sẻ** mỗi tuần.
- **Activation:** ≥ 60% người dùng mới tạo được 1 lịch trình AI trong phiên đầu.
- **Chất lượng AI:** ≥ 90% điểm trong lịch trình là POI đã xác minh; ≤ 5% phản hồi Gemini lỗi schema (sau retry).
- **Hiệu năng:** p95 thời gian sinh lịch trình ≤ 15 giây (3 ngày); LCP trang chủ ≤ 2,5 giây trên 4G.
- **Chi phí API:** ≤ 3 lần gọi Gemini cho mỗi chuyến đi lưu thành công (trung bình).

## 8. Ràng buộc & giả định (Constraints & Assumptions)

- **Ngân sách hạ tầng ≈ 0đ:** dùng hạn mức miễn phí của Firebase (gói Blaze vì cần Cloud Functions), Gemini và Google Maps; chỉ trả tiền tên miền (300.000đ/năm). → Phải có **cache, rate limit và budget alert** (R2, R6).
- **Gemini API key và Maps server key không bao giờ nằm ở client.** Mọi lời gọi Gemini/Places phía server đi qua Cloud Functions (R7).
- **Đội ngũ:** 5 sinh viên + AI coding agent (Claude Code). Mỗi module có “chủ sở hữu” theo phân công gốc (Huy-PM, Linh-FE, Trọng-BE, Hưng-AI, Hiếu-QA).
- **Giả định cần kiểm chứng:**
  - A1: Người dùng chấp nhận chờ 10–15 giây cho lịch trình AI nếu có hiển thị tiến trình.
  - A2: 150–300 POI cho 5–8 điểm đến phổ biến là đủ cho demo MVP.
  - A3: Link chia sẻ chỉ đọc đủ cho nhu cầu nhóm ở MVP (chưa cần cùng chỉnh sửa realtime).

## 9. Rủi ro sản phẩm (kế thừa Bảng 4.11 + bổ sung)

| Mã | Rủi ro | Biện pháp đưa vào thiết kế |
|---|---|---|
| R1 | AI trả kết quả sai, bịa địa điểm | JSON schema bắt buộc (responseSchema), validate bằng Zod, chỉ chọn POI theo `poiId`, retry 1 lần, nhãn `unverified` |
| R2 | Vượt quota Gemini | Rate limit theo user (ví dụ 10 lần/ngày), cache theo hash input, tạo lại theo từng ngày |
| R6 | Vượt hạn mức Maps/Firebase | Budget alert trên Google Cloud; cache kết quả Places vào Firestore; giới hạn số lần gọi Directions |
| R7 | Security Rules lỏng gây lộ dữ liệu | Rules theo vai trò + test bằng Firebase Emulator trong CI |
| R9 (mới) | Dữ liệu POI ít làm AI kém hữu ích | Seed POI cho 5–8 điểm đến trước Sprint 2; công cụ import từ Places cho Admin |

## 10. Câu hỏi mở (sẽ chốt ở GĐ3 – PRD)

- **Q1:** Persona P1 cần **chia chi phí theo người**. MVP chỉ hiển thị “chi phí/người” (chia đều), hay làm luôn ghi chi tiêu thực tế + ai trả bao nhiêu (kiểu Splitwise)? → ảnh hưởng phạm vi M6.
- **Q2:** Đăng nhập: chỉ Email/Password + Google, hay thêm số điện thoại (OTP tốn phí SMS)?
- **Q3:** Chia sẻ MXH (M10): chỉ link chia sẻ + nút Share của trình duyệt (Web Share API), hay cần ảnh thẻ lịch trình để đăng Instagram?
- **Q4:** Thông báo (M11): in-app + email, hay cần web push (FCM)?
- **Q5:** Danh sách 5–8 điểm đến seed ban đầu (gợi ý: Đà Nẵng, Hội An, Huế, Đà Lạt, Nha Trang, Phú Quốc, Hà Nội, Sa Pa).

## 11. Đầu ra chuyển sang GĐ2

- Persona và journey J1–J4 → danh sách màn hình và luồng UX.
- Định vị “trẻ, tiết kiệm, đáng tin, đi nhóm” → định hướng thị giác (visual direction) trong `DESIGN.md`.
- KPI hiệu năng → ngân sách hiệu năng (performance budget) trong design system.

---
**Nguồn tham khảo đối thủ:** unite.ai “Best AI Tools for Travel Planning” (08/2026); fast.io “Best AI Tools for Travel Planning in 2026”; lindy.ai “AI travel assistant”; VTV “Vie Travel AI officially launches” (01/2026).
