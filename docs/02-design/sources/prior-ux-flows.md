# Luồng UX (UX Flows): TrekMate

> Giai đoạn 2/5 · Trạng thái: 🟡 Chờ duyệt · Mã màn hình: xem [`screens.md`](screens.md)
> Sơ đồ viết bằng Mermaid (GitHub hiển thị trực tiếp).

## F1 – Tạo chuyến đi bằng AI (luồng chính)

```mermaid
flowchart TD
  A[S01 Trang chủ / S09 Chuyến đi] -->|Bấm Tạo chuyến đi| B{Đã đăng nhập?}
  B -- Chưa --> L[S02 Đăng nhập] -->|next=/trips/new| C
  B -- Rồi --> C[S05 Bước 1: Điểm đến, ngày, số người]
  C --> D[Bước 2: Ngân sách] --> E[Bước 3: Sở thích, nhịp độ, phương tiện] --> F[Bước 4: Xác nhận]
  F -->|Tạo lịch trình| Q{Còn lượt AI hôm nay?}
  Q -- Hết --> QX[Thông báo hết lượt + giờ reset]
  Q -- Còn --> G[S06 Đang tạo]
  G --> H{Kết quả}
  H -- Thành công --> I[S07 Chi tiết chuyến đi: trạng thái Bản nháp]
  H -- Lỗi / quá 30s --> GX[Thông báo lỗi + Thử lại] --> G
  I --> J{Người dùng}
  J -->|Lưu chuyến đi| K[Trạng thái Đã lưu → S09]
  J -->|Tạo lại ngày này| G
  J -->|Chỉnh sửa| S8[S08 Chỉnh sửa] -->|Lưu thay đổi| I
```

**Quy tắc:**
- Kết quả AI được lưu ngay thành `trip` với `status = "draft"` để không mất khi reload; người dùng bấm "Lưu chuyến đi" thì chuyển `status = "saved"`. Bản nháp quá 7 ngày không mở sẽ bị xoá tự động (Cloud Function định kỳ).
- "Tạo lại ngày này" chỉ gửi dữ liệu của ngày đó + danh sách POI đã dùng ở các ngày khác (để AI không lặp lại POI).

## F2 – Đăng ký / đăng nhập

```mermaid
flowchart LR
  A[S02] --> B{Phương thức}
  B -- Google --> G[Popup Google] --> P
  B -- Email --> V{Dữ liệu hợp lệ?}
  V -- Không --> VE[Lỗi dưới field] --> A
  V -- Có --> R[Firebase Auth] --> RE{Kết quả}
  RE -- Email tồn tại / sai mật khẩu --> RX[Thông báo lỗi] --> A
  RE -- OK --> P{Lần đầu?}
  P -- Có --> U[Tạo users/uid: role=user, status=active] --> N[Chuyển đến next]
  P -- Không --> S{status = locked?}
  S -- Có --> SX[Đăng xuất + thông báo tài khoản bị khoá]
  S -- Không --> N
```

## F3 – Khám phá → thêm vào chuyến đi

```mermaid
flowchart LR
  A[S03 Khám phá] -->|Lọc/tìm| A
  A --> B[S04 Chi tiết POI] -->|Thêm vào chuyến đi| C{Đã đăng nhập?}
  C -- Chưa --> L[S02] --> B
  C -- Rồi --> D[Sheet: chọn chuyến đi cùng điểm đến + ngày]
  D -->|Chưa có chuyến đi| E[Tạo chuyến đi trống cho điểm đến này] --> F
  D -->|Chọn ngày| F[Thêm vào cuối ngày + toast 'Đã thêm' + link mở chuyến đi]
```

## F4 – Chỉnh sửa lịch trình

Mở S08 → kéo thả / Lên-Xuống / Chuyển ngày / Đổi giờ / Xoá / + Thêm địa điểm → hệ thống **tính lại tạm thời** chi phí và cảnh báo trùng giờ ngay trên client → "Lưu thay đổi" → ghi Firestore (một lần ghi cho cả chuyến đi) → quay lại S07 + toast. "Huỷ" hoặc rời trang khi có thay đổi → xác nhận bỏ thay đổi.

## F5 – Admin thêm POI

```mermaid
flowchart LR
  A[A02 Danh sách POI] -->|Thêm| B[A03 Form]
  B -->|Tìm trên Google Places| C[Cloud Function gọi Places API] --> D[Tự điền tên, địa chỉ, toạ độ, giờ mở cửa, ảnh]
  D --> E[Admin bổ sung danh mục, mức giá, thời lượng, mô tả]
  E --> F{Hợp lệ?}
  F -- Không --> B
  F -- Có --> G{Lưu nháp hay Xuất bản}
  G --> H[A02 + toast]
```
Trùng `googlePlaceId` với POI đã có → cảnh báo, gợi ý mở POI cũ.

## F6 – Admin khoá/mở khoá người dùng (theo Scope1 §2.2)

A05 → chọn người dùng → Khoá/Mở khoá → hộp thoại xác nhận (nhập lý do khi khoá) → Cloud Function: cập nhật `users/{uid}.status`, đặt custom claim, thu hồi refresh token, ghi `auditLogs` → toast thành công. Lỗi: người dùng không tồn tại → quay lại danh sách; lỗi cập nhật → "Thử lại".

## F7 – Chia sẻ (Sau MVP)

S07 → Chia sẻ → bật "Cho phép xem bằng link" → tạo `shareId` → Web Share API (mobile) hoặc sao chép link (desktop). Người nhận mở `/s/:shareId` (S10) không cần đăng nhập → có thể "Sao chép vào tài khoản của tôi" (cần đăng nhập).

## Điều hướng tổng thể

- **Mobile – BottomNav:** Khám phá (S03) · Chuyến đi (S09) · **Tạo** (S05) · Thông báo (S12, sau MVP; MVP ẩn) · Tài khoản (S13).
- **Desktop – TopBar:** Logo → S01 · Khám phá · Chuyến đi của tôi · nút accent "Tạo chuyến đi" · avatar (menu: Tài khoản, Admin nếu có quyền, Đăng xuất).
- **Admin:** sidebar riêng, route `/admin/*` được bảo vệ bằng role guard (client) + custom claim (Security Rules).
