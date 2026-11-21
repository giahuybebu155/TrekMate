---
topic: Personas
status: draft
sources: [prior-research, po-answers, bao-cao-f5]
updated: 2026-11-21
---

# Personas

## TL;DR
Ba persona ưu tiên theo PO: **P1 nhóm trưởng chia chi phí** (chính), **P2 sinh viên tiết kiệm**, **P3 dân văn phòng cuối tuần**. [DEC: D6] Job quan trọng nhất: chốt lịch nhóm + biết tiền/người trong thời gian ngắn. Tin cậy **thấp–trung bình** (A-UR). Không có trích dẫn user thật.

## Tổng quan

| ID | Tên gọi | Mô tả một dòng | Vấn đề chính | Ưu tiên | Tin cậy |
|---|---|---|---|---|---|
| P1 | Nhóm trưởng Minh | Sinh viên tổ chức chuyến nhóm, cần lịch + tiền/người + link chia sẻ | PS-1, PS-2, PS-3 | chính | trung bình |
| P2 | Lan đi tiết kiệm | Tự túc túi tiền thấp, cần phương án thật sự rẻ | PS-1, PS-2, PS-4 | phụ | thấp |
| P3 | Tuấn cuối tuần | Nhân viên ít thời gian, chuyến 2N1Đ | PS-1, PS-2, PS-5 | phụ | thấp |
| Admin | Vận hành POI | Không phải khách hàng; cần để AI có dữ liệu sạch | — | vận hành | cao (từ scope) |

## P1: Nhóm trưởng Minh

**Chân dung:** ~22 tuổi, sinh viên, thường tổ chức chuyến 3N2Đ trong nước cho 4–6 bạn, ngân sách khoảng 1,5–2 triệu/người (ví dụ minh họa, không phải số khảo sát). [DOC: prior-research §3] [INF: from D6]
**Bối cảnh sử dụng:** lên kế hoạch trên điện thoại (chiếm phần lớn thời gian) hoặc máy tính lúc tối; trong chuyến cũng mở điện thoại. [DEC: D7 (sửa lần 2)] [DOC: prior-research P1]
**Hành vi hiện tại:** bàn trên Zalo, đọc TikTok, Maps, tự chia tiền cuối chuyến.

### Jobs To Be Done

| ID | Khi… | tôi muốn… | để… | Loại | Quan trọng |
|---|---|---|---|---|---|
| JTBD-1 | Khi còn khoảng 1–2 tuần nữa là chuyến 3 ngày với nhóm bạn | chốt một lịch cả nhóm xem được | không phải tranh luận lại trên Zalo mỗi tối | chức năng | cao |
| JTBD-2 | Khi đã có lịch sơ bộ | biết trước mỗi người phải góp bao nhiêu | mọi người đồng ý đi mà không sợ “lỗ im lặng” | chức năng | cao |
| JTBD-3 | Khi gửi kế hoạch cho bạn chưa có tài khoản | họ mở được và hiểu lịch | không hướng dẫn cài app hay đăng ký | xã hội | cao |
| JTBD-8 | Khi chuyến đã diễn ra hoặc vừa về | nhóm để lại nhận xét trên chuyến đó | giữ kỷ niệm và góp ý cho lần sau | cảm xúc | trung bình |

### Pains & Gains

| ID | Loại | Mô tả | Gắn với | Mức độ | Nguồn |
|---|---|---|---|---|---|
| PAIN-1 | pain | Nhóm bàn loãng, mỗi người một ý, không có bản “chính thức” | JTBD-1 | cao | [DOC: prior-research P1] |
| PAIN-2 | pain | Cuối chuyến tính tiền rối, không ai nhớ đã chi gì | JTBD-2 | cao | [DOC: prior-research P1] |
| PAIN-3 | pain | Sợ AI đưa điểm không có thật rồi mất mặt với nhóm | JTBD-1 | cao | [INF: from PS-2] |
| GAIN-1 | gain | Có link để dán Zalo, bạn mở là thấy lịch | JTBD-3 | cao | [STK: PO, 14/11/2026] [DEC: Q3] |
| GAIN-2 | gain | Số tiền/người hiện rõ, chia đều | JTBD-2 | cao | [DEC: Q1] |
| GAIN-8 | gain | Bạn bè comment dưới chuyến, cảm giác chuyến “có thật” | JTBD-8 | trung bình | [STK: PO, 16/11/2026] |

### Empathy map

| Nói | Nghĩ | Làm | Cảm thấy |
|---|---|---|---|
| “Mọi người xem lịch này được không” | “Nếu sai điểm thì mình bị trách” | Soạn trên điện thoại, gửi screenshot | Hào hứng lúc đầu, mệt khi chốt |

**Thành công với họ là:** trong một buổi tối có lịch theo ngày, link mở không bắt buộc đăng nhập (xem), và hiện chi phí/người. [DOC: prior-research P1] Comment trên chuyến: **G-6** (ai được viết).

## P2: Lan đi tiết kiệm

**Chân dung:** ~20 tuổi, sinh viên, đi một mình hoặc 1 bạn, ngân sách thấp, thời gian linh hoạt. [DOC: prior-research P2]
**Bối cảnh sử dụng:** điện thoại; lọc điểm miễn phí/rẻ trước khi tin lịch AI.
**Hành vi hiện tại:** ưu tiên xe khách/xe máy, homestay, quán bình dân; nghi lịch “đẹp” trên mạng.

### Jobs To Be Done

| ID | Khi… | tôi muốn… | để… | Loại | Quan trọng |
|---|---|---|---|---|---|
| JTBD-4 | Khi túi tiền chỉ đủ mức tiết kiệm cho 2–3 ngày | thấy phương án điểm + ăn + đi lại thật sự rẻ | không bị lịch “trung bình” đội giá | chức năng | cao |
| JTBD-5 | Khi đang chọn quán/điểm | đọc đánh giá từ người đã đến | tránh bẫy giá và chỗ đông khách Tây | chức năng | trung bình |

### Pains & Gains

| ID | Loại | Mô tả | Gắn với | Mức độ | Nguồn |
|---|---|---|---|---|---|
| PAIN-4 | pain | Lịch trên mạng và AI generic đẩy về phương án đắt | JTBD-4 | cao | [DOC: prior-research P2] |
| PAIN-5 | pain | Không biết điểm nào miễn phí / giá rẻ đã được kiểm chứng | JTBD-4 | trung bình | [INF: from D4 D5] |
| GAIN-3 | gain | Mức “Tiết kiệm” cho ra xe khách, homestay, quán bình dân khác hẳn mức khác | JTBD-4 | cao | [DOC: prior-research P2] |
| GAIN-4 | gain | Sao + nhận xét trên địa điểm giúp chọn chỗ | JTBD-5 | trung bình | [DOC: bao-cao-f5 M4] |

### Empathy map

| Nói | Nghĩ | Làm | Cảm thấy |
|---|---|---|---|
| “Cái này chắc đắt” | “App này có dành cho sinh viên không” | Lọc giá, đọc review | Cảnh giác, vui khi thấy chỗ rẻ |

**Thành công với họ là:** chọn ngân sách Tiết kiệm ra lịch khác rõ rệt so với Trung bình/Cao cấp, có giá tham khảo. [DOC: prior-research P2]

## P3: Tuấn cuối tuần

**Chân dung:** ~29 tuổi, nhân viên văn phòng TP.HCM, chuyến 2N1Đ (Đà Lạt, Vũng Tàu…), ít giờ chuẩn bị. [DOC: prior-research P3]
**Bối cảnh sử dụng:** tạo lịch trên điện thoại lúc tối giữa tuần; ít đọc review dài.
**Hành vi hiện tại:** hay nhờ ChatGPT rồi tự rút cho vừa 2 ngày; ghét lịch chạy show.

### Jobs To Be Done

| ID | Khi… | tôi muốn… | để… | Loại | Quan trọng |
|---|---|---|---|---|---|
| JTBD-6 | Khi chỉ còn 1–2 tối trước chuyến cuối tuần | có lịch 2 ngày vừa sức trong vài phút | không phải đọc hàng chục review | chức năng | cao |
| JTBD-7 | Khi lịch đã có | chỉnh nhẹ (bớt điểm, đổi thứ tự) rồi lưu | cuối tuần được nghỉ, không chạy show | cảm xúc | cao |

### Pains & Gains

| ID | Loại | Mô tả | Gắn với | Mức độ | Nguồn |
|---|---|---|---|---|---|
| PAIN-6 | pain | Không có thời gian đối chiếu giờ mở cửa / mật độ lịch | JTBD-6 | cao | [DOC: prior-research P3] |
| PAIN-7 | pain | AI nhồi quá nhiều điểm trong một ngày | JTBD-7 | trung bình | [DOC: prior-research P3] |
| GAIN-5 | gain | Form ngắn, mặc định hợp lý, chờ có tiến trình | JTBD-6 | cao | [DOC: prior-research J1] |
| GAIN-6 | gain | Nhịp “thư giãn” được tôn trọng khi tạo lại một ngày | JTBD-7 | trung bình | [DOC: prior-research J1 bước 5] |

### Empathy map

| Nói | Nghĩ | Làm | Cảm thấy |
|---|---|---|---|
| “Chỉ cần lịch đủ đi là được” | “Đừng để mình phải nghiên cứu” | Generate rồi sửa vài điểm | Vội, muốn xong |

**Thành công với họ là:** một lịch 2N1Đ tạo được trong phiên đầu, sửa được, lưu được. [DOC: prior-research P3]

## Người không phải đối tượng
- Khách inbound cần visa/phrasebook/tour quốc tế — đó là chỗ Vie Travel AI nhắm mạnh. [DOC: web – english.vtv.vn, 01/2026]
- Gia đình nhiều thế hệ, tour công ty, đặt phòng/vé trong app.
- Admin là **vai trò vận hành**, không phải persona trả tiền; cần M5 để POI đủ cho D5.

## Giả định

| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|
| A-UR | Pain/job P1–P3 đúng dù chưa phỏng vấn | Đổi thứ tự ưu tiên persona | Phỏng vấn 3 nhóm đúng 3 persona |
| A-3 | Link chỉ xem đủ cho nhóm ở MVP | Phải làm cùng sửa (phức tạp quyền) | Hỏi P1 khi dùng prototype |
| A-DEVICE | Mobile-first phục vụ P1–P3 tốt hơn desktop-first | Đổi breakpoint GĐ2 | [DEC: D7 (sửa lần 2)] — đã chốt |

## Bàn giao
- Market: đánh giá đối thủ theo P1 (nhóm + tiền/người) và P2 (túi tiền Việt Nam).
- Journey & Features: J1 cho P1, J2 cho P2, J3 cho P3.
- Giai đoạn 2: thiết bị điện thoại; giọng tươi, đáng tin, không “luxury”.
- Giai đoạn 3: JTBD-1…8 → user story.
