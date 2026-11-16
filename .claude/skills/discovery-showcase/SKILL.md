---
name: discovery-showcase
description: Chuẩn trình bày kết quả Product Discovery thành một trang web showcase để nhóm, giảng viên hoặc stakeholder xem. Dùng khi skill trekmate-discovery cần trang showcase, hoặc khi người dùng nói "showcase discovery", "trình bày discovery", "làm trang tổng hợp giai đoạn 1".
---

# Discovery Showcase

Skill này là **chuẩn trình bày**: nó quyết định bố cục, giao diện, cách điều hướng và tương tác của trang showcase. Nội dung luôn lấy từ các file chủ đề trong `docs/01-discovery/`. Skill không nghiên cứu, không viết thêm kết luận và không đổi ý nghĩa của tài liệu.

## Khi nào dùng

- Sau khi `trekmate-discovery` có V1 cho các chủ đề, khi Product Owner muốn một trang để xem hoặc chia sẻ.
- Khi chủ đề được cập nhật: chỉ thay dữ liệu của trang tương ứng, giữ nguyên bố cục đã lưu.

## Đầu ra

Một trang web tự chứa (HTML, CSS và JS trong một file), xuất bản thành artifact hoặc lưu tại `docs/01-discovery/showcase/index.html` nếu Product Owner yêu cầu file.

## Cấu trúc trang

| Trang / mục | Nguồn | Nội dung chính |
|---|---|---|
| Tổng quan | `README.md` + TL;DR mọi chủ đề | Sản phẩm một câu, bảng độ phủ chủ đề, 3 khoảng trống lớn nhất |
| Problem | `01-problem.md` | Bảng PS-n, HMW |
| Personas | `02-personas.md` | Thẻ persona, JTBD, pain/gain |
| Market | `03-market.md` | Bảng đối thủ có link, chỗ trống |
| Vision | `04-vision.md` | Tầm nhìn, product statement, định vị, USP |
| Solution Blueprint | `05-blueprint.md` §1–3 | Khối giải pháp, Value Proposition, Product Canvas |
| Business Model | `05-blueprint.md` §4 | Lean Canvas, ranh giới miễn phí và trả phí, chi phí |
| Journey & Features | `06-journey-features.md` | Hành trình, tính năng, MVP |
| Roadmap | `07-roadmap.md` | Now / Next / Later, North Star, AARRR |
| Câu hỏi mở | `sources/discovery-gaps.md` | Hàng đợi câu hỏi theo mức ảnh hưởng |

Business Model có trang riêng nhưng dữ liệu lấy từ Blueprint; không tạo tài liệu riêng cho nó.

## Quy tắc trình bày

- **Giữ nguyên bố cục, giao diện, chuyển động, điều hướng và tương tác đã lưu.** Khi cập nhật, chỉ thay dữ liệu dự án.
- **Điều hướng:** thanh bên hoặc thanh tab cố định với 10 mục trên; mỗi mục một trang hoặc một vùng cuộn có neo.
- **Thẻ nguồn và độ tin cậy luôn hiển thị.** `[DOC]`, `[STK]`, `[INF]`, `[PROP]`, `[DEC]` thành nhãn nhỏ có màu khác nhau; độ tin cậy thấp có dấu nhận biết bằng chữ, không chỉ bằng màu.
- **"Chưa có"** hiển thị như một trạng thái rõ ràng kèm lý do và mã gap, không để trống.
- **Link nguồn** của đối thủ và số liệu thị trường mở được từ trang.
- **Không thêm dữ liệu:** không số liệu, trích dẫn, logo hay ảnh không có trong tài liệu. Ảnh minh hoạ chỉ là khối giữ chỗ có nhãn.
- **Chữ đọc được:** tương phản tối thiểu 4,5:1, cỡ chữ nội dung tối thiểu 14px, bảng rộng cuộn ngang trong khung riêng.
- Nếu dự án đã có design system được duyệt (Giai đoạn 2), dùng màu và font của nó; nếu chưa, dùng giao diện trung tính, một màu nhấn.

## Kiểm tra trước khi xuất bản

- [ ] Mọi mục trong bảng cấu trúc có dữ liệu hoặc trạng thái "Chưa có" kèm lý do.
- [ ] Nội dung khớp file nguồn, không có nhận định mới.
- [ ] Thẻ nguồn và độ tin cậy hiển thị đầy đủ.
- [ ] Link đối thủ hoạt động.
- [ ] Trang xem được trên màn hình máy tính và điện thoại.
