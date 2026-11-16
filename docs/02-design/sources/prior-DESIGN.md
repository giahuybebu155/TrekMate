# DESIGN.md: TrekMate Design System

> Giai đoạn 2/5 · Trạng thái: 🟡 Chờ duyệt · Cập nhật: 14/11/2026
> File này là **nguồn sự thật về giao diện**. AI coding agent KHÔNG được tự chọn màu, font, khoảng cách hay bo góc ngoài các token dưới đây.
> Token máy đọc: [`design-tokens.json`](design-tokens.json) · Màn hình: [`screens.md`](screens.md) · Luồng UX: [`ux-flows.md`](ux-flows.md)

---

## 1. Định hướng thị giác (Visual direction)

**Từ khoá:** *Tươi trẻ · Nhiều ảnh · Rừng & nắng · Đáng tin · Dễ dùng một tay.*

- **Ảnh điểm đến là nhân vật chính.** Card, hero và trang chi tiết dùng ảnh full-bleed. Chữ đặt trên ảnh luôn có lớp gradient tối (`overlay`) để đủ tương phản.
- **Xanh lá rừng (primary)** là màu của thương hiệu và của điều hướng, trạng thái "đã chọn". **Vàng nắng (accent)** chỉ dùng cho **một hành động nổi bật nhất mỗi màn hình** (ví dụ "Tạo chuyến đi bằng AI") và cho điểm nhấn AI.
- **Hình khối mềm:** bo góc lớn (card 16px, nút 12px, chip tròn), đổ bóng nhẹ. Không dùng viền đậm.
- **Tin cậy:** dữ liệu "đã xác minh" và "AI đề xuất" phải phân biệt được ngay bằng nhãn (badge). Không được trình bày nội dung AI như sự thật.
- **Mobile-first:** thiết kế ở 375px trước, mở rộng lên tablet và desktop. Hành động chính nằm trong vùng ngón cái (thanh dưới cùng / nút dính đáy).

**Không làm (anti-patterns):** gradient tím–xanh kiểu "AI template"; emoji thay icon; quá 2 màu nhấn trong một màn hình; chữ trắng trên ảnh mà không có overlay; card lồng card; chữ nhỏ hơn 12px.

## 2. Màu sắc (Color)

### 2.1 Bảng màu gốc

| Token | Hex | Dùng cho |
|---|---|---|
| `forest-50` | `#EEF7F1` | Nền vùng chọn, nền badge xanh |
| `forest-100` | `#D5EDDE` | Hover nhẹ, nền chip đã chọn |
| `forest-200` | `#A9D9BC` | Viền focus phụ |
| `forest-300` | `#74BF94` | Icon phụ, đường tuyến bản đồ (ngày lẻ) |
| `forest-400` | `#43A06D` | — |
| `forest-500` | `#2A8456` | Đường tuyến bản đồ chính |
| `forest-600` | `#1F6F4A` | **Primary**: nút chính, link, tab active |
| `forest-700` | `#185A3C` | Hover của primary |
| `forest-800` | `#13462F` | Pressed, tiêu đề trên nền sáng |
| `forest-900` | `#0D3221` | Chữ đậm trên nền vàng |
| `sun-50` | `#FFF8E6` | Nền khối AI, nền cảnh báo nhẹ |
| `sun-100` | `#FEEDC0` | Nền badge AI |
| `sun-300` | `#F9CF63` | Viền khối AI |
| `sun-400` | `#F5B82E` | **Accent**: CTA nổi bật, ngôi sao đánh giá |
| `sun-500` | `#E09E12` | Hover accent |
| `sun-700` | `#8A5D00` | Chữ trên nền `sun-50/100` |
| `stone-0` | `#FFFFFF` | Nền card |
| `stone-50` | `#F7F8F6` | Nền trang |
| `stone-100` | `#EEF0EC` | Nền input, skeleton |
| `stone-200` | `#DDE1DB` | Viền mặc định |
| `stone-400` | `#9AA39B` | Placeholder, icon tắt |
| `stone-600` | `#5B665E` | Chữ phụ |
| `stone-900` | `#1A2620` | Chữ chính |
| `red-600` | `#C8372D` | Lỗi, xoá |
| `red-50` | `#FDEDEC` | Nền lỗi |
| `blue-600` | `#2563C9` | Thông tin, trạng thái "đang di chuyển" |
| `blue-50` | `#EAF1FC` | Nền thông tin |

### 2.2 Token ngữ nghĩa (semantic), dùng các token này trong code

| Semantic token | Light | (Dark, để dành) |
|---|---|---|
| `--background` | `stone-50` | `#0F1712` |
| `--surface` (card) | `stone-0` | `#16211A` |
| `--foreground` | `stone-900` | `#E8EEE9` |
| `--muted-foreground` | `stone-600` | `#9DAAA0` |
| `--border` | `stone-200` | `#2A3830` |
| `--primary` / `--primary-foreground` | `forest-600` / `#FFFFFF` | `forest-400` / `#0D3221` |
| `--accent` / `--accent-foreground` | `sun-400` / `forest-900` | `sun-400` / `forest-900` |
| `--ai-surface` / `--ai-border` | `sun-50` / `sun-300` | `#2A2412` / `#6B5418` |
| `--success` | `forest-600` | `forest-400` |
| `--destructive` | `red-600` | `#F0675E` |
| `--info` | `blue-600` | `#6EA0F0` |
| `--ring` (focus) | `forest-600` | `forest-300` |

**Quy tắc tương phản (WCAG 2.2 AA):** chữ thường ≥ 4.5:1, chữ lớn/icon ≥ 3:1. Đã kiểm: trắng trên `forest-600` ≈ 6.1:1 ✅; `forest-900` trên `sun-400` ≈ 7.9:1 ✅; `stone-600` trên `stone-50` ≈ 5.6:1 ✅; marker ngày (chữ trắng) đều ≥ 5.1:1 ✅; **trắng trên `sun-400` ≈ 1.8:1 ❌, cấm dùng**; `stone-400` (2.6:1) chỉ dùng cho placeholder và icon trang trí, không dùng cho chữ mang thông tin.

### 2.3 Màu theo ngày trên bản đồ (phân biệt các ngày trong lịch trình)
Ngày 1 `#1F6F4A` · Ngày 2 `#2563C9` · Ngày 3 `#C2410C` · Ngày 4 `#7C3AED` · Ngày 5 `#0E7490` · Ngày 6+ lặp lại. Luôn kèm số thứ tự trên marker, không phân biệt chỉ bằng màu.

## 3. Chữ (Typography)

- **Font:** `Be Vietnam Pro` (Google Fonts, hỗ trợ dấu tiếng Việt đầy đủ), các weight 400/500/600/700. Fallback: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.
- Số liệu (giá, giờ, khoảng cách): `font-variant-numeric: tabular-nums`.
- Không dùng chữ IN HOA cho câu dài; chỉ dùng cho overline ≤ 3 từ.

| Token | Size / Line-height | Weight | Dùng cho |
|---|---|---|---|
| `display` | 36/44 (mobile 30/38) | 700 | Hero trang chủ |
| `h1` | 28/36 (mobile 24/32) | 700 | Tiêu đề trang |
| `h2` | 22/30 | 600 | Tiêu đề section, tên ngày |
| `h3` | 18/26 | 600 | Tiêu đề card |
| `body-lg` | 16/24 | 400 | Nội dung chính (mặc định trên mobile) |
| `body` | 14/22 | 400 | Nội dung phụ, bảng |
| `label` | 14/20 | 500 | Nhãn form, nút |
| `caption` | 12/16 | 500 | Badge, metadata (giờ, khoảng cách) |

Input trên mobile tối thiểu 16px để iOS Safari không tự zoom.

## 4. Khoảng cách, lưới & kích thước

- **Thang spacing (4pt):** `0, 1=4, 2=8, 3=12, 4=16, 5=20, 6=24, 8=32, 10=40, 12=48, 16=64` (px), trùng với thang mặc định của Tailwind.
- **Lề trang:** mobile 16px · tablet 24px · desktop 32px. Container tối đa **1200px**; nội dung đọc (form, chi tiết) tối đa **720px**.
- **Breakpoints:** `sm 640` · `md 768` · `lg 1024` · `xl 1280`.
- **Vùng chạm tối thiểu 44×44px.** Khoảng cách giữa hai vùng chạm ≥ 8px.
- **Bố cục trang chi tiết chuyến đi:** mobile là tab (Lịch trình | Bản đồ | Chi phí); từ `lg` trở lên chia 2 cột: danh sách 5/12 bên trái, bản đồ 7/12 dính (sticky) bên phải.

## 5. Bo góc, viền, đổ bóng, lớp (z-index)

| Token | Giá trị | Dùng cho |
|---|---|---|
| `radius-sm` | 8px | Input, badge vuông |
| `radius-md` | 12px | Nút, dropdown |
| `radius-lg` | 16px | Card, sheet |
| `radius-xl` | 24px | Hero, modal lớn |
| `radius-full` | 9999px | Chip, avatar, FAB |
| `shadow-sm` | `0 1px 2px rgba(16,40,28,.06)` | Card tĩnh |
| `shadow-md` | `0 4px 12px rgba(16,40,28,.08)` | Card hover, dropdown |
| `shadow-lg` | `0 12px 32px rgba(16,40,28,.12)` | Modal, bottom sheet |
| `overlay` | `linear-gradient(180deg, rgba(0,0,0,0) 40%, rgba(0,0,0,.65) 100%)` | Chữ trên ảnh |

z-index: `base 0 · sticky 10 · header 20 · dropdown 30 · sheet 40 · modal 50 · toast 60`.

## 6. Chuyển động (Motion)

- Thời lượng: `fast 120ms` (hover, nhấn) · `base 200ms` (mở/đóng, tab) · `slow 320ms` (sheet, chuyển trang).
- Easing: `ease-out` cho xuất hiện, `ease-in` cho biến mất; sheet/modal dùng `cubic-bezier(.2,.8,.2,1)`.
- Thư viện: `motion` (Motion for React), chỉ dùng cho sheet, reorder danh sách và chuyển trang. Hover dùng CSS transition.
- **Tôn trọng `prefers-reduced-motion`:** tắt mọi animation dịch chuyển, chỉ giữ fade.
- Loading AI: skeleton theo đúng hình dạng nội dung + 3 thông điệp tiến trình xoay vòng (xem `screens.md` S07). Không dùng spinner trơn quá 1 giây.

## 7. Icon & hình ảnh

- **Icon:** chỉ dùng `lucide-react`, stroke 1.75, kích thước 16/20/24. Không trộn bộ icon khác.
- **Icon danh mục POI (cố định):**

| Danh mục | Key | Icon lucide |
|---|---|---|
| Tham quan | `sightseeing` | `Landmark` |
| Thiên nhiên | `nature` | `Mountain` |
| Biển | `beach` | `Waves` |
| Ăn uống | `food` | `UtensilsCrossed` |
| Cà phê | `cafe` | `Coffee` |
| Lưu trú | `stay` | `BedDouble` |
| Mua sắm / chợ | `shopping` | `ShoppingBag` |
| Văn hoá / tâm linh | `culture` | `Church` |
| Vui chơi / về đêm | `nightlife` | `Sparkles` |

- **Ảnh:** tỷ lệ cố định: card 4:3, hero 16:9 (mobile 4:5), avatar 1:1. Luôn có `alt` mô tả. Dùng `loading="lazy"` trừ ảnh hero. Ảnh lỗi thì hiện placeholder màu `forest-50` + icon danh mục.
- Nguồn ảnh: ảnh POI do Admin tải lên (Firebase Storage) hoặc Google Places Photos (phải hiển thị attribution theo điều khoản Google).

## 8. Component (dựa trên shadcn/ui)

Dùng shadcn/ui làm nền, tuỳ biến bằng token ở trên. **Không cài thêm thư viện UI khác** (MUI, Ant, Chakra…).

| Component | Biến thể (variants) | Ghi chú |
|---|---|---|
| `Button` | `primary` · `accent` · `secondary` (viền) · `ghost` · `destructive`; size `sm 36` · `md 44` · `lg 52` | Mỗi màn hình tối đa **1** nút `accent`. Trạng thái loading: spinner nhỏ + giữ chiều rộng |
| `Input`, `Textarea`, `Select`, `Combobox` | default · error · disabled | Nhãn luôn hiển thị phía trên (không dùng placeholder thay nhãn). Lỗi hiện dưới field bằng `caption` màu destructive |
| `Chip` (toggle) | default · selected | Chọn sở thích, danh mục, mức ngân sách |
| `SegmentedControl` | — | Ngân sách: Tiết kiệm / Trung bình / Cao cấp; nhịp độ: Thư thả / Vừa phải / Dày đặc |
| `DestinationCard` | default · compact | Ảnh 4:3 + tên + vùng + "x địa điểm" |
| `PoiCard` | default · compact · in-itinerary | Ảnh, tên, danh mục, giá tham khảo, rating, `VerifiedBadge` |
| `ItineraryItem` | default · editing (có tay kéo) · current (chế độ Hôm nay) | Giờ bắt đầu–kết thúc, tên POI, thời lượng, chi phí ước tính, ghi chú AI; giữa 2 item có `TravelSegment` |
| `TravelSegment` | walk · motorbike · car/taxi · bus | Icon phương tiện + khoảng cách + thời gian |
| `DayHeader` | — | "Ngày 1 · T7, 21/12" + màu ngày + tổng chi phí ngày + nút "Tạo lại ngày này" |
| `CostSummary` | full · compact | Tổng, theo hạng mục (di chuyển/ăn uống/lưu trú/vui chơi), **mỗi người** |
| `Badge` | `verified` (xanh) · `ai` (vàng, icon `Sparkles`) · `unverified` (xám viền, "Chưa xác minh") · status | — |
| `AiNotice` | — | Khối nền `--ai-surface`: "Lịch trình do AI đề xuất, hãy kiểm tra giờ mở cửa trước khi đi" |
| `MapView` | full · embedded | Marker đánh số theo màu ngày; marker đang chọn to hơn + popup `PoiCard compact` |
| `BottomNav` (mobile) | — | Khám phá · Chuyến đi · **Tạo (accent, ở giữa)** · Thông báo · Tài khoản |
| `TopBar` (desktop) | — | Logo, menu, nút "Tạo chuyến đi", avatar |
| `Sheet` (mobile) / `Dialog` (desktop) | — | Viết đánh giá, chỉnh item, chọn POI để thêm |
| `EmptyState` | — | Minh hoạ nhỏ + 1 câu + 1 nút hành động |
| `Skeleton`, `Toast` (sonner), `Tabs`, `DropdownMenu`, `Avatar`, `RatingStars`, `Pagination` | — | — |
| Admin: `DataTable` | — | Tìm kiếm, lọc, sắp xếp, phân trang, chọn nhiều |

### Trạng thái bắt buộc cho mọi màn hình có dữ liệu
`loading` (skeleton) · `empty` (EmptyState) · `error` (thông điệp + nút Thử lại) · `success`. Nút có `hover`, `focus-visible` (ring 2px `--ring`, offset 2px), `active`, `disabled`, `loading`.

## 9. Giọng văn (UX writing)

- Xưng hô **"bạn"**, câu ngắn, chủ động, thân thiện nhưng không suồng sã. Không dùng tiếng lóng.
- Nút là **động từ + đối tượng**: "Tạo lịch trình", "Lưu chuyến đi", "Thêm địa điểm". Không dùng "OK", "Submit".
- Lỗi theo công thức **chuyện gì xảy ra + làm gì tiếp**: "Không tạo được lịch trình lúc này. Vui lòng thử lại sau ít phút."
- Định dạng: tiền `1.250.000 ₫` (`Intl.NumberFormat('vi-VN', {style:'currency', currency:'VND'})`); ngày `T7, 21/12/2026`; giờ `08:30`; khoảng cách `1,2 km`; thời gian `25 phút`.
- Toàn bộ chuỗi giao diện đặt trong file i18n `vi.json` (chuẩn bị cho tiếng Anh sau này), không viết cứng trong component.

## 10. Khả năng truy cập (Accessibility), checklist cho mọi PR

- [ ] Điều hướng đầy đủ bằng bàn phím, thứ tự focus hợp lý, `focus-visible` rõ ràng.
- [ ] Mọi ảnh có `alt`; icon-only button có `aria-label`.
- [ ] Form: `label` gắn với input; lỗi liên kết bằng `aria-describedby`.
- [ ] Không truyền đạt thông tin chỉ bằng màu (marker có số, badge có chữ).
- [ ] Danh sách kéo thả có phương án thay thế bằng nút "Lên/Xuống".
- [ ] Kiểm bằng axe-core: 0 lỗi mức serious/critical.

## 11. Ngân sách hiệu năng (Performance budget)

LCP ≤ 2,5s (4G) · INP ≤ 200ms · CLS ≤ 0,1 · JS ban đầu ≤ 200KB gzip (route-level code splitting; Google Maps JS chỉ tải khi mở bản đồ) · ảnh WebP, có `width/height`.

## 12. Ánh xạ sang Tailwind/shadcn (để AI làm theo)

- Khai báo semantic token dưới dạng CSS variables trong `src/styles/globals.css` (định dạng HSL theo quy ước shadcn), rồi map trong `tailwind.config` → `colors.primary = 'hsl(var(--primary))'`…
- Bảng màu gốc (`forest-*`, `sun-*`, `stone-*`) chỉ được dùng **bên trong** file token; component chỉ dùng class ngữ nghĩa (`bg-primary`, `text-muted-foreground`, `border-border`…).
- `borderRadius`: `sm 8 / md 12 / lg 16 / xl 24`. `fontFamily.sans = ['"Be Vietnam Pro"', ...fallback]`.
