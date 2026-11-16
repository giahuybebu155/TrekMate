---
source: Scope1.docx
kind: document
extracted: 2026-11-16
note: Trích nguyên văn tài liệu Scope v1.0. Bảng được chuyển sang dạng "cột | cột".
---

Ý tưởng: XÂY DỰNG ỨNG DỤNG WEB LÊN KẾ HOẠCH DU LỊCH THÔNG MINH
1. Scope:
Module | Actor chính | Mục đích
Quản lý tài khoản | User / Admin | Đăng ký, đăng nhập, quản lý trạng thái tài khoản
Tìm kiếm địa điểm | User | Tìm & lọc điểm đến du lịch
Lập kế hoạch bằng AI | User / Hệ thống AI | Sinh lịch trình tự động qua Gemini API
Đánh giá địa điểm | User | Xem, viết, sửa, xóa đánh giá
Quản lý dữ liệu du lịch (Admin) | Admin | Quản trị địa điểm & người dùng
2. Module: Quản lý tài khoản
2.1 Đăng ký tài khoản
Bước | Actor | Hành động
1 | User | Nhấn nút "Đăng ký"
2 | User | Nhập thông tin (email, mật khẩu...)
3 | Hệ thống | Kiểm tra dữ liệu hợp lệ (định dạng email, độ mạnh mật khẩu)
4 | Hệ thống | Kiểm tra email đã tồn tại chưa
5 | Hệ thống | Tạo tài khoản → thông báo thành công
Luồng lỗi (Alternative flow): email sai định dạng · mật khẩu không khớp · email đã tồn tại · lỗi hệ thống.
2.2 Quản lý người dùng (Admin – khóa/mở khóa tài khoản)
Bước | Actor | Hành động
1 | Admin | Truy cập trang quản trị (Dashboard) → "Quản lý người dùng"
2 | Hệ thống | Hiển thị danh sách user
3 | Admin | Chọn 1 user cụ thể
4 | Admin | Chọn hành động: Khóa hoặc Mở khóa
5 | Hệ thống | Yêu cầu xác nhận
6 | Admin | Xác nhận thao tác
7 | Hệ thống | Cập nhật trạng thái + ghi log hoạt động + thông báo thành công
Điều kiện tiên quyết: Admin đã đăng nhập & có quyền quản lý người dùngLuồng lỗi: user không tồn tại → báo lỗi, quay lại danh sách · lỗi cập nhật → thông báo thử lại
3. Module: Tìm kiếm địa điểm du lịch
Bước | Actor | Hành động
1 | User | Truy cập mục "Địa điểm" (đã đăng nhập)
2 | User | Nhập từ khóa hoặc chọn bộ lọc
3 | Hệ thống | Truy vấn dữ liệu địa điểm
4 | Hệ thống | Hiển thị kết quả tìm kiếm
Luồng lỗi: không tìm thấy kết quả phù hợp
4. Module: Lập kế hoạch du lịch bằng AI (điểm nhấn của đề tài)
Bước | Actor | Hành động
1 | User | Chọn "Tạo bằng AI"
2 | User | Nhập thông tin: ngày đi, ngân sách, sở thích, điểm đến dự kiến
3 | Hệ thống (Gemini AI) | Xử lý và sinh đề xuất lịch trình
4 | User | Xem kế hoạch được đề xuất
5 | User | Lưu kế hoạch (hoặc yêu cầu tạo lại)
Luồng lỗi: thiếu thông tin đầu vào → yêu cầu nhập lại · AI lỗi không tạo được → cho thử lại · user không đồng ý kế hoạch → AI đề xuất bản mới
5. Module: Đánh giá địa điểm
Bước | Actor | Hành động
1 | User | Chọn 1 địa điểm để xem chi tiết
2 | User | Chọn đánh giá (số sao + nhận xét)
3 | Hệ thống | Lưu đánh giá vào hệ thống
Lưu ý: nếu user thoát trước khi gửi → đánh giá không được lưu. 
6. Module: Quản lý dữ liệu du lịch (Admin)
Bước | Actor | Hành động
1 | Admin | Truy cập trang quản trị
2 | Admin | Chọn chức năng (thêm/sửa/xóa địa điểm)
3 | Admin | Nhập hoặc chỉnh sửa dữ liệu
4 | Hệ thống | Lưu thay đổi vào database
Luồng lỗi: nhập thiếu dữ liệu · lỗi hệ thống
