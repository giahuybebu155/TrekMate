# Danh sách màn hình & đặc tả: TrekMate

> Giai đoạn 2/5 · Trạng thái: 🟡 Chờ duyệt · Liên quan: [`DESIGN.md`](DESIGN.md), [`ux-flows.md`](ux-flows.md)
> Mỗi màn hình có: mã, route, module, quyền truy cập, mục đích, nội dung (theo thứ tự từ trên xuống), hành động, trạng thái. Mã màn hình (S.., A..) được dùng lại trong user stories ở GĐ3.

## Tổng quan

| Mã | Màn hình | Route | Module | Quyền | Sprint |
|---|---|---|---|---|---|
| S01 | Trang chủ | `/` | M2, M3 | Công khai | MVP |
| S02 | Đăng nhập / Đăng ký / Quên mật khẩu | `/login`, `/register`, `/forgot-password` | M1 | Khách | MVP |
| S03 | Khám phá điểm đến & địa điểm | `/explore`, `/explore/:destinationSlug` | M2 | Công khai | MVP |
| S04 | Chi tiết địa điểm (POI) | `/places/:poiId` | M2, M4 | Công khai (viết đánh giá cần đăng nhập) | MVP (đánh giá: Sau MVP) |
| S05 | Tạo chuyến đi bằng AI (wizard 4 bước) | `/trips/new` | M3 | Đăng nhập | MVP |
| S06 | Đang tạo lịch trình (AI loading) | `/trips/new` (bước chờ) | M3 | Đăng nhập | MVP |
| S07 | Chi tiết chuyến đi: Lịch trình · Bản đồ · Chi phí | `/trips/:tripId` | M3, M6, M7, M8 | Chủ chuyến | MVP (bản đồ/chi phí đầy đủ: Sau MVP) |
| S08 | Chỉnh sửa lịch trình | `/trips/:tripId?mode=edit` | M7 | Chủ chuyến | MVP |
| S09 | Chuyến đi của tôi | `/trips` | M7 | Đăng nhập | MVP |
| S10 | Trang chia sẻ công khai (chỉ xem) | `/s/:shareId` | M10 | Công khai | Sau MVP |
| S11 | Chế độ "Hôm nay" (trong chuyến) | `/trips/:tripId/today` | M8, M11 | Chủ chuyến | Sau MVP |
| S12 | Thông báo | `/notifications` | M11 | Đăng nhập | Sau MVP |
| S13 | Tài khoản & cài đặt | `/account` | M1, M11 | Đăng nhập | MVP (cài đặt thông báo: Sau MVP) |
| S14 | Gợi ý khách sạn / nhà hàng / dịch vụ | Sheet trong S07 | M9 | Chủ chuyến | Sau MVP |
| A01 | Admin – Tổng quan | `/admin` | M5 | Admin | MVP |
| A02 | Admin – Danh sách POI | `/admin/places` | M5 | Admin | MVP |
| A03 | Admin – Thêm/Sửa POI (import Google Places) | `/admin/places/new`, `/admin/places/:poiId` | M5 | Admin | MVP |
| A04 | Admin – Điểm đến | `/admin/destinations` | M5 | Admin | MVP |
| A05 | Admin – Người dùng | `/admin/users` | M1 | Admin | MVP |
| A06 | Admin – Kiểm duyệt đánh giá | `/admin/reviews` | M4 | Admin | Sau MVP |
| X01 | 404 / Không có quyền / Lỗi hệ thống | `*` | — | — | MVP |

> "MVP" = M1, M2, M3, M5, M7 (quyết định D0.3). Cột Sprint sẽ được chi tiết hoá trong `docs/03-product/backlog.md`.

---

## S01 – Trang chủ `/`
**Mục đích:** trong 5 giây người dùng hiểu TrekMate làm gì và bấm "Tạo chuyến đi bằng AI".
**Nội dung:**
1. Header: logo, (desktop) menu Khám phá · Chuyến đi của tôi, nút Đăng nhập / avatar.
2. Hero ảnh full-bleed (16:9, mobile 4:5) + overlay; `display`: "Lên lịch trình du lịch trong 1 phút"; mô tả 1 dòng; **ô nhập nhanh**: Điểm đến (combobox) + Số ngày (1–7) + nút **accent** "Tạo lịch trình" → chuyển sang S05 với dữ liệu đã điền.
3. "Điểm đến nổi bật": lưới `DestinationCard` (mobile cuộn ngang, desktop 4 cột).
4. "Cách TrekMate hoạt động": 3 bước có icon (Nhập nhu cầu → AI đề xuất → Chỉnh & chia sẻ).
5. "Chuyến đi gần đây của bạn" (nếu đã đăng nhập và có chuyến đi): 3 card.
6. Footer.

**Trạng thái:** chưa đăng nhập mà bấm Tạo → chuyển `/login?next=/trips/new...`.

## S02 – Đăng nhập / Đăng ký / Quên mật khẩu
**Nội dung (một cột, tối đa 400px):** logo · tiêu đề · nút "Tiếp tục với Google" (secondary) · đường kẻ "hoặc" · Email · Mật khẩu (có nút hiện/ẩn) · (Đăng ký: Họ tên, Nhập lại mật khẩu, checkbox đồng ý điều khoản) · nút primary · link chuyển qua lại giữa các form.
**Validate:** email đúng định dạng; mật khẩu ≥ 8 ký tự, có chữ và số; mật khẩu nhập lại phải khớp.
**Lỗi (theo Scope1 §2.1):** email sai định dạng · mật khẩu không khớp · email đã tồn tại · sai email/mật khẩu · tài khoản bị khoá ("Tài khoản của bạn đã bị tạm khoá. Liên hệ hỗ trợ.") · lỗi mạng.
**Sau khi thành công:** chuyển đến `next` hoặc `/`.

## S03 – Khám phá `/explore`, `/explore/:destinationSlug`
**Nội dung:**
1. Thanh tìm kiếm (từ khoá) dính trên cùng.
2. Không có `destinationSlug`: lưới điểm đến.
3. Có `destinationSlug`: hero nhỏ của điểm đến; hàng chip **danh mục** (9 danh mục ở DESIGN §7) + **ngân sách** (Tiết kiệm / Trung bình / Cao cấp) + sắp xếp (Phổ biến · Đánh giá cao · Giá thấp); danh sách `PoiCard` (mobile 1 cột, tablet 2, desktop 3); phân trang kiểu "Tải thêm" (20 mục/lần).
4. (desktop ≥ lg) Nút chuyển "Xem bản đồ" (để dành, sau MVP).

**Trạng thái:** loading = 6 skeleton card; empty = "Không tìm thấy địa điểm phù hợp. Thử bỏ bớt bộ lọc." + nút Xoá bộ lọc; error.
**Bộ lọc được phản ánh lên URL** (`?q=&cat=food,cafe&budget=low&sort=rating`) để có thể chia sẻ link và dùng nút Back.

## S04 – Chi tiết POI `/places/:poiId`
**Nội dung:** gallery ảnh (vuốt) · tên (h1) · danh mục + `VerifiedBadge` · rating trung bình + số đánh giá · khối thông tin: địa chỉ, giờ mở cửa (hôm nay nổi bật; "Đang mở cửa"/"Đã đóng cửa"), giá tham khảo theo mức ngân sách, thời lượng tham quan gợi ý · mô tả · bản đồ nhỏ (embedded) + nút "Chỉ đường" (mở Google Maps) · nút **primary** "Thêm vào chuyến đi" (mở sheet chọn chuyến đi và ngày) · danh sách đánh giá (sau MVP: nút "Viết đánh giá" → sheet với `RatingStars` 1–5 + nhận xét 10–1000 ký tự; sửa/xoá đánh giá của mình).
**Trạng thái:** POI bị ẩn/xoá → X01 "Địa điểm không còn khả dụng".

## S05 – Tạo chuyến đi bằng AI `/trips/new` (wizard)
Thanh tiến trình 4 bước ở trên; nút "Quay lại" / "Tiếp tục" dính đáy (mobile). Dữ liệu giữ trong state và trong query string để không mất khi reload.

| Bước | Trường | Kiểu & ràng buộc |
|---|---|---|
| 1. Điểm đến & thời gian | Điểm đến (bắt buộc) | Combobox từ `destinations` (chỉ những điểm đến đang mở) |
| | Ngày đi, ngày về (bắt buộc) | Date range; ngày đi ≥ hôm nay; **tối đa 7 ngày** |
| | Số người (bắt buộc) | Stepper 1–20, mặc định 2 |
| 2. Ngân sách | Mức ngân sách | SegmentedControl: Tiết kiệm / Trung bình / Cao cấp (mặc định Trung bình) |
| | Ngân sách tối đa/người (tuỳ chọn) | Số VNĐ, bước 50.000 |
| 3. Sở thích & nhịp độ | Sở thích (≥ 1) | Chip nhiều lựa chọn: Nghỉ dưỡng, Khám phá, Ẩm thực, Văn hoá, Thiên nhiên, Check-in sống ảo, Về đêm |
| | Nhịp độ | Thư thả (2–3 điểm/ngày) / Vừa phải (4–5) / Dày đặc (6+) |
| | Phương tiện chính | Đi bộ · Xe máy · Ô tô/taxi · Xe buýt |
| | Ghi chú thêm (tuỳ chọn) | Textarea ≤ 300 ký tự ("Có trẻ nhỏ", "Ăn chay"…) |
| 4. Xác nhận | Tóm tắt tất cả lựa chọn, có nút sửa từng phần | Nút **accent** "Tạo lịch trình" + dòng nhỏ "Còn x/10 lượt tạo hôm nay" |

## S06 – Đang tạo lịch trình (AI loading)
Skeleton đúng hình dạng S07 (DayHeader + 3 ItineraryItem) + thông điệp xoay vòng mỗi 3 giây: "Đang chọn địa điểm phù hợp…" → "Đang sắp xếp lộ trình hợp lý…" → "Đang ước tính chi phí…". Nút ghost "Huỷ".
**Lỗi:** quá 30 giây hoặc AI lỗi → "Không tạo được lịch trình lúc này." + nút "Thử lại" (không trừ lượt nếu lỗi do hệ thống). Hết lượt trong ngày → thông báo + giờ được reset.

## S07 – Chi tiết chuyến đi `/trips/:tripId`
**Header:** ảnh điểm đến + overlay · tên chuyến đi (sửa inline) · "21–23/12 · 3 ngày · 5 người · Trung bình" · nút: Chỉnh sửa (secondary), Chia sẻ (ghost, sau MVP), menu ⋯ (Nhân bản, Xoá).
`AiNotice` nếu chuyến đi do AI tạo.
**Mobile:** `Tabs` Lịch trình | Bản đồ | Chi phí. **Desktop ≥ lg:** cột trái Lịch trình + Chi phí, cột phải bản đồ sticky.
- **Lịch trình:** chọn ngày (chip ngang "N1 · T7 21/12"), mỗi ngày: `DayHeader` → chuỗi `ItineraryItem` xen `TravelSegment`. Item: giờ `08:00–09:30`, tên POI (link S04), danh mục, `VerifiedBadge` hoặc `Badge unverified`, chi phí ước tính/người, ghi chú AI (1–2 dòng, mở rộng được).
- **Bản đồ:** marker đánh số theo màu ngày, polyline tuyến từng ngày; chọn item ↔ highlight marker.
- **Chi phí:** `CostSummary`: tổng cả chuyến, **mỗi người**, theo hạng mục và theo ngày; chú thích "Chi phí ước tính, có thể thay đổi".
**Hành động trên ngày:** "Tạo lại ngày này" (gọi AI cho riêng ngày đó, xác nhận trước vì ghi đè).

## S08 – Chỉnh sửa lịch trình (`?mode=edit`)
Mỗi item có tay kéo (kéo thả trong ngày và sang ngày khác) + nút ⋯ (Lên, Xuống, Chuyển sang ngày…, Đổi giờ, Xoá). Cuối mỗi ngày: "+ Thêm địa điểm" → sheet tìm POI theo điểm đến của chuyến đi (dùng lại S03 dạng compact).
Thanh dính đáy: "Huỷ" (ghost) · "Lưu thay đổi" (primary). Rời trang khi chưa lưu → hộp thoại xác nhận.
**Ràng buộc:** giờ kết thúc > giờ bắt đầu; cảnh báo (không chặn) nếu trùng giờ hoặc ngoài giờ mở cửa.

## S09 – Chuyến đi của tôi `/trips`
Tabs: Sắp tới · Đã qua · Bản nháp. Lưới card chuyến đi (ảnh, tên, ngày, số người, tổng chi phí/người). Nút accent "Tạo chuyến đi".
**Empty:** "Bạn chưa có chuyến đi nào." + nút "Tạo chuyến đi đầu tiên".

## S10 – Trang chia sẻ `/s/:shareId` (Sau MVP)
Giống S07 nhưng chỉ xem, không có nút sửa; banner "Tạo chuyến đi của riêng bạn với TrekMate" + nút "Sao chép vào tài khoản của tôi". Có thẻ Open Graph (tiêu đề, ảnh điểm đến, mô tả "3 ngày ở Hội An · 1.250.000 ₫/người"). Chủ chuyến có thể tắt link bất kỳ lúc nào.

## S11 – Chế độ "Hôm nay" (Sau MVP)
Thẻ lớn "Điểm tiếp theo" (giờ, tên, khoảng cách từ vị trí hiện tại) + nút accent "Dẫn đường" (deep link Google Maps) · dòng thời gian của hôm nay · cảnh báo thời tiết (nếu có).

## S12 – Thông báo (Sau MVP)
Danh sách theo thời gian; loại: thời tiết xấu, POI thay đổi giờ mở cửa/đóng cửa, nhắc trước chuyến đi 1 ngày. Chưa đọc có chấm xanh; "Đánh dấu đã đọc tất cả".

## S13 – Tài khoản & cài đặt `/account`
Ảnh đại diện, họ tên, email (chỉ đọc), sở thích mặc định (dùng để điền sẵn S05) · (sau MVP) bật/tắt từng loại thông báo, kênh in-app/email · Đổi mật khẩu (nếu đăng ký bằng email) · Đăng xuất.

## S14 – Gợi ý dịch vụ (Sau MVP)
Sheet từ S07: tabs Lưu trú · Ăn uống · Dịch vụ, lọc theo mức ngân sách của chuyến đi; mỗi `PoiCard compact` có nút "Lưu vào kế hoạch" (chọn ngày/khung giờ).

## A01–A06 – Khu vực Admin `/admin/*`
**Bố cục:** sidebar trái (Tổng quan · Điểm đến · Địa điểm · Người dùng · Đánh giá) + nội dung; tối ưu desktop (≥ 1024px), trên mobile chỉ cần xem được.
- **A01 Tổng quan:** 4 thẻ số liệu (Người dùng, Chuyến đi tạo trong 7 ngày, POI đang hiển thị, Lượt gọi AI hôm nay/hạn mức) + danh sách POI thiếu ảnh/giờ mở cửa.
- **A02 Danh sách POI:** `DataTable` cột Ảnh · Tên · Điểm đến · Danh mục · Mức giá · Trạng thái (Hiển thị/Ẩn/Nháp) · Cập nhật lần cuối; lọc theo điểm đến, danh mục, trạng thái; hành động: Sửa, Ẩn/Hiện, Xoá (xác nhận).
- **A03 Form POI:** ô "Tìm trên Google Places" → chọn kết quả để **tự điền** tên, địa chỉ, toạ độ, giờ mở cửa, ảnh, `googlePlaceId`; Admin bổ sung: điểm đến, danh mục, mức ngân sách phù hợp, giá tham khảo (min–max VNĐ/người), thời lượng tham quan gợi ý (phút), khung giờ phù hợp (sáng/trưa/chiều/tối), mô tả, tags, trạng thái. Lưu nháp / Xuất bản.
- **A04 Điểm đến:** CRUD điểm đến (tên, slug, vùng, ảnh bìa, mô tả, toạ độ trung tâm, đang mở cho người dùng hay không).
- **A05 Người dùng:** bảng email, tên, vai trò, ngày tạo, trạng thái; hành động **Khoá/Mở khoá** (theo Scope1 §2.2: xác nhận → cập nhật → ghi log → toast thành công), đổi vai trò (chỉ SuperAdmin).
- **A06 Kiểm duyệt đánh giá (Sau MVP):** danh sách đánh giá bị báo cáo; Ẩn / Giữ lại.

## X01 – Trang lỗi
404 "Không tìm thấy trang" · 403 "Bạn không có quyền truy cập trang này" · 500 "Đã có lỗi xảy ra". Đều có nút "Về trang chủ".
