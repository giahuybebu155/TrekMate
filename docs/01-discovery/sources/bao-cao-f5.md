---
source: F5_BaoCao_final_v1.docx
kind: document
extracted: 2026-11-16
note: Trích nguyên văn Chương 1, mục 4.9 và 5.2–5.3 của báo cáo môn Quản trị dự án phần mềm. Phần MS Project, Delphi, chi phí bị lược bỏ vì không dùng cho Discovery. Bảng được chuyển sang dạng "cột | cột".
---

# Báo cáo F5 – trích đoạn dùng cho Discovery

## Chương 1 – Giới thiệu đề tài

GIỚI THIỆU VỀ ĐỀ TÀI VÀ CÔNG TÁC CHUẨN BỊ
Tên dự án
TrekMate – Ứng dụng web lên kế hoạch du lịch thông minh bằng AI
Mô tả dự án
Bối cảnh thị trường và Tính cấp thiết của đề tài
 TrekMate là một website dành cho những người tự sắp xếp chuyến đi của mình. Thay vì phải dùng nhiều công cụ riêng lẻ, họ có thể tìm điểm tham quan, xây dựng lịch trình từng ngày, theo dõi đường đi trên bản đồ, dự toán chi tiêu, rồi lưu lại và gửi cho bạn bè ngay trên một hệ thống. Chỉ cần khai báo điểm đến, thời lượng, mức ngân sách và sở thích, Gemini API sẽ đề xuất một lịch trình cụ thể; người dùng sau đó được tự điều chỉnh hoặc nhờ hệ thống làm lại.
Có hai vai trò sử dụng hệ thống: Người dùng (Traveler) thao tác với các chức năng lên kế hoạch, còn Quản trị viên (Admin) chịu trách nhiệm về dữ liệu địa điểm và tài khoản. Các chức năng được chia thành 11 module.
Các module và chức năng chính
Hệ thống được chia thành 11 module; Bảng 1.1 nêu chức năng và đối tượng sử dụng của từng module.
Bảng 1.1. Danh sách 11 module và chức năng chính
Mã | Module | Chức năng | Vai trò sử dụng
M1 | Tài khoản & Phân quyền | •     Đăng ký, đăng nhập (Firebase Authentication) •     Cập nhật thông tin cá nhân •     Khóa / mở khóa tài khoản •     Phân quyền theo vai trò | Người dùng; Admin
M2 | Khám phá địa điểm | •     Tìm kiếm và lọc địa điểm theo danh mục, ngân sách •     Xem chi tiết địa điểm (hình ảnh, mô tả, giờ mở cửa, giá tham khảo) | Người dùng
M3 | Lập kế hoạch bằng AI | •     Nhập tiêu chí chuyến đi •     Gemini sinh lịch trình theo ngày và  khung giờ •     Xem chi tiết kế hoạch, yêu cầu tạo lại •     Lưu kế hoạch vào tài khoản | Người dùng; Hệ thống (Gemini  API)
M4 | Đánh giá địa điểm | •     Xem đánh giá của địa điểm •     Viết đánh giá (số sao và nhận xét) •     Sửa / xóa đánh giá của mình | Người dùng
M5 | Quản trị địa điểm & Dashboard | •     Trang quản trị dành cho Admin •     Thêm, sửa, xóa địa điểm (POI) | Admin
M6 | Quản lý chi phí | •     Tự động ước tính chi phí theo hạng mục (di chuyển, ăn uống, lưu trú, vui chơi) •     Xem chi tiết chi phí chuyến đi •     Tùy chỉnh từng khoản chi | Người dùng
M7 | Quản lý lịch trình đã lưu | •     Xem lịch sử chuyến đi •     Chỉnh sửa lịch trình: thêm/bớt địa điểm, đổi thứ tự, đổi ngày | Người dùng
M8 | Bản đồ & Điều hướng | •     Hiển thị địa điểm và lịch trình trên bản đồ •     Tính tuyến đường, chọn phương tiện •     Dẫn đường thực tế theo vị trí hiện tại | Người dùng
M9 | Gợi ý khách sạn, nhà hàng & dịch vụ | •     Gợi ý theo phong cách du lịch và ngân sách •     Lưu lựa chọn dịch vụ vào kế hoạch | Người dùng; Hệ thống
M10 | Chia sẻ lịch trình | •     Chia sẻ lịch trình lên Facebook, Instagram | Người dùng
M11 | Thông báo & Nhắc nhở | •     Theo dõi thay đổi liên quan chuyến đi (thời tiết, giờ mở cửa) •     Gửi thông báo tự động (Cloud Functions) •     Tùy chỉnh loại thông báo nhận | Người dùng; Hệ thống
Đối tượng Người dùng Mục tiêu
Hệ thống được thiết kế hướng tới 2 nhóm đối tượng chính với các luồng trải nghiệm riêng biệt:
Nhóm Người dùng cuối (Travelers - Khách du lịch):
Là những cá nhân, gia đình hoặc nhóm bạn có nhu cầu đi du lịch tự túc.
Họ cần một công cụ đơn giản để tạo nhanh lịch trình, theo dõi chi phí nhóm, xem bản đồ di chuyển và chia sẻ kế hoạch cho những người đồng hành.
Nhóm Quản trị viên (System Administrators):
Đội ngũ vận hành hệ thống, chịu trách nhiệm cập nhật dữ liệu địa điểm (thêm, sửa, xóa), quản lý và khóa/mở khóa tài khoản người dùng, đảm bảo dữ liệu trên nền tảng chính xác và không vi phạm tiêu chuẩn cộng đồng.
Kiến trúc và Phân hệ Chức năng Cốt lõi
      Để giải quyết bài toán phân mảnh thông tin, ứng dụng được xây dựng với một kiến trúc module hóa, bao gồm các phân hệ chức năng tương hỗ lẫn nhau:
A. Phân hệ Dành cho Người dùng 
Module Tài khoản & Phân quyền (M1): Đăng ký, đăng nhập an toàn qua Firebase Authentication; cập nhật thông tin cá nhân. Các chuyến đi đã tạo được lưu theo tài khoản và xem lại trong phần lịch sử chuyến đi (M7).
Module Lập kế hoạch bằng AI (M3): Đây là "trái tim" của ứng dụng. Người dùng nhập các tham số: điểm đến, ngày đi – ngày về, ngân sách dự kiến (tiết kiệm/trung bình/cao cấp) và sở thích (nghỉ dưỡng, khám phá, ẩm thực, văn hóa). Gemini API trả về lịch trình chi tiết theo từng ngày, từng khung giờ; người dùng có thể yêu cầu tạo lại và lưu kế hoạch vào tài khoản.
Module Bản đồ & Điều hướng (M8): Tích hợp Google Maps Platform. Các điểm đến trong lịch trình được tự động ghim (pin) trên bản đồ; hệ thống tính tuyến đường, hiển thị khoảng cách và thời gian di chuyển dự kiến giữa các điểm theo phương tiện (đi bộ, xe máy, taxi) và hỗ trợ dẫn đường theo vị trí hiện tại.
Module Quản lý chi phí (M6): Tự động ước tính chi phí theo từng hạng mục của chuyến đi (di chuyển, ăn uống, lưu trú, vui chơi); người dùng xem chi tiết và tùy chỉnh từng khoản chi.
Module Chia sẻ lịch trình (M10): Chia sẻ lịch trình lên Facebook, Instagram để bạn đồng hành cùng xem kế hoạch trước giờ khởi hành.
B. Phân hệ Dành cho Quản trị viên (Admin Dashboard)
Quản trị địa điểm (M5 – POI Management): Thêm, sửa, xóa các điểm du lịch (Point of Interest); cập nhật giờ mở cửa, giá vé tham khảo, hình ảnh và danh mục.
Quản lý người dùng (M1): Khóa/mở khóa các tài khoản vi phạm chính sách và phân quyền theo vai trò (Người dùng, Admin).
Ứng dụng Trí tuệ Nhân tạo (AI)
Khác biệt lớn nhất của dự án so với các ứng dụng ghi chú thông thường là việc tích hợp Trí tuệ Nhân tạo, cụ thể là mô hình ngôn ngữ lớn Gemini, kết hợp với dữ liệu bản đồ từ Google Maps Platform:
Tạo lịch trình động bằng Prompt Engineering: Thay vì dùng các bộ lọc cứng nhắc và truy vấn cơ sở dữ liệu truyền thống, hệ thống chuyển yêu cầu của người dùng thành câu lệnh (prompt) gửi đến Gemini. AI đóng vai trò như một hướng dẫn viên bản địa, sắp xếp các điểm đến hợp lý về mặt thời gian (ví dụ: không gợi ý đi bảo tàng vào buổi tối mà gợi ý đi chợ đêm thay thế). Nếu người dùng chưa hài lòng với kế hoạch, họ có thể yêu cầu AI tạo lại lịch trình mới.
Thích ứng theo tiêu chí: Khi người dùng thay đổi ngân sách hoặc sở thích và tạo lại lịch trình, AI đề xuất các lựa chọn phù hợp hơn (quán ăn bình dân, xe buýt thay vì taxi) mà vẫn giữ trải nghiệm cốt lõi; kết hợp với gợi ý khách sạn, nhà hàng và dịch vụ theo phong cách du lịch (M9).
Danh sách chức năng của dự án
Yêu cầu chức năng
Người dùng kỳ vọng có một công cụ lập kế hoạch du lịch thật nhanh, dễ sử dụng và mang tính cá nhân hóa. Ứng dụng không chỉ hỗ trợ tìm kiếm điểm đến phù hợp mà còn phải đề xuất hành trình tối ưu, dự đoán chi phí và lưu lại các chuyến đi đã thực hiện. Mục tiêu tổng thể là mang đến một nền tảng du lịch thông minh, giúp họ chuẩn bị chuyến đi hiệu quả và tận hưởng trải nghiệm trọn vẹn hơn.
a) Đăng ký và đăng nhập
Người dùng mong muốn có thể tạo tài khoản một cách đơn giản thông qua email, số điện thoại hoặc liên kết với mạng xã hội để truy cập ứng dụng nhanh và thuận tiện.
Bên cạnh đó, việc đăng nhập cần bảo đảm an toàn, bảo mật và thao tác gọn nhẹ, giúp họ quản lý thông tin cá nhân cũng như đồng bộ dữ liệu chuyến đi trên nhiều thiết bị.
b) Gợi ý điểm đến và tìm kiếm thông minh
Hệ thống cần hỗ trợ tìm kiếm hoặc gợi ý các điểm du lịch phù hợp với sở thích, ngân sách, thời gian và mục đích chuyến đi.
Ngoài ra, mỗi điểm đến nên được trình bày đầy đủ thông tin như hình ảnh, đánh giá, khí hậu, lịch trình tham khảo và các hoạt động nổi bật để người dùng dễ hình dung trước khi lựa chọn.
c) Lập kế hoạch du lịch tự động bằng AI
Người dùng mong muốn nhận được một kế hoạch du lịch hoàn chỉnh bằng cách nhập vài thông tin cơ bản như điểm đến, số ngày, phong cách du lịch hoặc ngân sách. Trí tuệ nhân tạo cần tối ưu hóa hành trình và đề xuất lịch trình phù hợp.
Kế hoạch được tạo ra phải bao gồm danh sách địa điểm cần đến, thời gian gợi ý, khoảng cách di chuyển, khách sạn, nhà hàng và chi phí dự kiến để giúp họ tiết kiệm thời gian tìm hiểu và chuẩn bị.
d) Tính toán và theo dõi chi phí
Ứng dụng cần tự động ước tính tổng chi phí của chuyến đi, bao gồm di chuyển, ăn uống, lưu trú và vui chơi, nhằm hỗ trợ kiểm soát ngân sách hiệu quả hơn.
Bên cạnh đó, người dùng phải có khả năng tùy chỉnh các khoản chi theo lựa chọn cá nhân để hệ thống cập nhật lại kế hoạch cho phù hợp với nhu cầu hoặc mức thu nhập của họ.
e) Quản lý lịch trình và lưu trữ lịch sử chuyến đi
Hệ thống phải cho phép lưu lại các chuyến đi đã tạo và xem lại bất cứ khi nào cần, giúp người dùng tham khảo hoặc tái sử dụng cho những hành trình sau.
Ngoài ra, họ cần có khả năng chỉnh sửa lịch trình (thêm/bớt địa điểm, thay đổi ngày hoặc chỗ ở) để cá nhân hóa kế hoạch theo mong muốn riêng.
f) Tích hợp bản đồ và điều hướng
Người dùng muốn xem tuyến đường di chuyển trực tiếp trên bản đồ thông minh, bao gồm thời gian, quãng đường và phương tiện thích hợp, nhằm có cái nhìn trực quan về hành trình.
Khi chọn một địa điểm trong lịch trình, ứng dụng cần hiển thị dữ liệu chi tiết ngay trên bản đồ để thuận tiện cho việc chuẩn bị và điều hướng thực tế.
g) Chia sẻ, đánh giá và tương tác cộng đồng
Người dùng có nhu cầu chia sẻ lịch trình hoặc hình ảnh chuyến đi lên các nền tảng như Facebook hay Instagram để lưu giữ kỷ niệm và kết nối với bạn bè.
Họ cũng mong muốn đánh giá (số sao) và nhận xét về các địa điểm đã trải nghiệm, qua đó đóng góp cho cộng đồng và giúp ứng dụng cải thiện chất lượng đề xuất.
h) Thông báo và nhắc nhở
Hệ thống cần gửi thông báo về các thay đổi quan trọng liên quan đến chuyến đi, chẳng hạn như thời tiết xấu hoặc thay đổi giờ mở cửa của địa điểm.
Người dùng cần có quyền tùy chỉnh loại thông báo để tránh bị làm phiền nhưng vẫn đảm bảo nhận được các thông tin thiết yếu cho hành trình.
Yêu cầu phi chức năng
Hiệu suất: Yêu cầu về tốc độ tải trang, thời gian phản hồi (kể cả thời gian Gemini sinh lịch trình) và khả năng xử lý nhiều người dùng cùng lúc.
Bảo mật: Yêu cầu về tính an toàn, bảo mật thông tin người dùng (Firebase Authentication, Security Rules) và khả năng chống lại các cuộc tấn công mạng.
Độ tin cậy: Yêu cầu về độ ổn định, khả năng phục hồi khi có sự cố kỹ thuật.
Khả năng mở rộng: Có thể thêm mới tính năng và tăng khả năng xử lý tải mà không làm giảm hiệu suất.
Tương thích: Giao diện hiển thị tốt trên các trình duyệt phổ biến và các kích thước màn hình khác nhau (máy tính, máy tính bảng, điện thoại).
Thời gian làm dự án
Dự án được thực hiện trong 9 tuần, từ 21/08/2026 đến 23/10/2026, theo mô hình Thác nước gồm 5 giai đoạn nối tiếp nhau. Mỗi giai đoạn kết thúc bằng một mốc tiến độ (M1–M5). Bảng 1.6 tóm tắt nội dung và sản phẩm đầu ra của từng giai đoạn; lịch chi tiết của từng công việc được lập trên MS Project ở mục 3.2.
Giai đoạn 1: Khởi tạo, lập kế hoạch và phân tích yêu cầu (21/08 – 04/09/2026)
Đánh giá tính khả thi; khởi tạo Firebase, môi trường phát triển và tài khoản quản trị ban đầu.
Thu thập yêu cầu bằng khảo sát, phỏng vấn người du lịch tự túc; phân loại yêu cầu chức năng và phi chức năng, xác định mức ưu tiên của từng yêu cầu.
Hình 1.1. Đặc tả yêu cầu phần mềm (SRS)
Đặc tả use case và viết tài liệu Đặc tả yêu cầu phần mềm (SRS); lập kế hoạch dự án (WBS, ước lượng Delphi, lịch và chi phí) và trình giảng viên hướng dẫn phê duyệt (mốc M1).
Giai đoạn 2: Thiết kế hệ thống (07/09 – 11/09/2026)
Thiết kế kiến trúc hệ thống:
Kiến trúc Client – Firebase (BaaS): ứng dụng React làm việc trực tiếp với Firebase Authentication, Cloud Firestore và Cloud Functions; tích hợp Gemini API và Google Maps Platform.
Công nghệ sử dụng: React, TailwindCSS, Firebase, Gemini API, Google Maps Platform.
Định nghĩa các mô-đun chính, thành phần, và cách chúng tương tác.
Thiết kế chi tiết: cấu trúc dữ liệu Firestore và Security Rules, giao diện người dùng (UI/UX) trên Figma, luồng gọi Gemini API và Maps API.
Xây dựng sơ đồ kỹ thuật: Use Case Diagram, Sequence Diagram và sơ đồ cấu trúc dữ liệu Firestore; hoàn thành thiết kế (mốc M2).
Hình 1.2. Thiết kế hệ thống
Giai đoạn 3: Phát triển mã nguồn (14/09 – 02/10/2026)
Thiết lập môi trường phát triển:
Cài đặt React, TailwindCSS và Firebase CLI.
Thiết lập Git/GitHub để quản lý mã nguồn.
Cấu hình Firebase cho môi trường phát triển (dev) và môi trường chạy thật (production).
Phát triển mã nguồn:
Chia nhỏ hệ thống thành các mô-đun hoặc thành phần theo thiết kế.
Lập trình từng thành phần, bao gồm:
+ Phát triển giao diện người dùng (Frontend): Xây dựng UI theo prototype đã thiết kế
+ Phát triển xử lý phía server: cấu hình Firebase Authentication, Security Rules và viết Cloud Functions (gửi thông báo tự động, tính chi phí).
+ Tích hợp dịch vụ bên ngoài: Gemini API sinh lịch trình (Prompt Engineering) và Google Maps Platform (bản đồ, tuyến đường, dẫn đường).
Tích hợp các mô-đun hoặc thành phần để đảm bảo chúng hoạt động cùng nhau.
Quản lý mã nguồn và kiểm thử trong quá trình phát triển:
Đẩy mã nguồn lên GitHub, review code trước khi gộp nhánh.
Viết Unit Test song song với lập trình từng module; hoàn thành phát triển (mốc M3).
Giai đoạn 4: Kiểm thử hệ thống (05/10 – 16/10/2026)
Chuẩn bị môi trường kiểm thử:
Chuẩn bị môi trường kiểm thử trên Firebase, tách biệt với môi trường chạy thật.
Thiết lập dữ liệu kiểm thử (Test Data) để mô phỏng các tình huống thực tế.
Thực hiện kiểm thử: kiểm thử tích hợp (Gemini AI, bản đồ, chi phí), kiểm thử toàn luồng (end-to-end), kiểm tra hiệu năng và bảo mật cơ bản.
Ghi nhận, sửa lỗi và kiểm thử lại (re-test); tổng hợp báo cáo kết quả kiểm thử gồm số lượng lỗi, loại lỗi, mức độ nghiêm trọng và trạng thái xử lý (mốc M4).
Hình 1.3. Kiểm thử phần mềm
Giai đoạn 5: Triển khai và kết thúc (19/10 – 23/10/2026)
Triển khai hệ thống:
Triển khai ứng dụng React lên Firebase Hosting và gán tên miền.
Kiểm tra hoạt động của các chức năng, khả năng hiển thị giao diện, hiệu suất và tính bảo mật của hệ thống sau khi triển khai.
Kiểm tra dữ liệu trên Cloud Firestore, đảm bảo các thao tác thêm, sửa, xóa và truy xuất dữ liệu hoạt động chính xác.
Hướng dẫn người dùng sử dụng hệ thống, cung cấp tài liệu hướng dẫn và hỗ trợ trong giai đoạn đầu.
Hỗ trợ và bảo trì sau triển khai:
Theo dõi hoạt động của hệ thống để phát hiện và khắc phục các lỗi phát sinh.
Thu thập phản hồi từ người dùng nhằm đánh giá mức độ đáp ứng yêu cầu và xác định các chức năng cần cải thiện.
Cập nhật giao diện, điều chỉnh chức năng và tối ưu mã nguồn React dựa trên phản hồi thực tế.
Kiểm tra và cập nhật các quy tắc bảo mật Firebase, phân quyền truy cập dữ liệu và tối ưu hiệu suất khi cần thiết.
Tổng kết bài học kinh nghiệm, hoàn thiện báo cáo, slide bảo vệ và bàn giao mã nguồn cùng tài liệu kỹ thuật (mốc M5).
Hình 1.4. Bảo trì phần mềm
Nguồn lực dự án
Con người
Nhóm có 05 thành viên. Bảng 1.2 là bản tóm tắt phân công, phần chi tiết của từng người nằm ở mục 1.4.1.1 đến 1.4.1.5. 
Bảng 1.2. Tổng hợp phân công nhân sự
Thành viên | Vai trò | Số công việc | Khối lượng (giờ) | Người-ngày
Phạm Mai Gia Huy – 23IT.B081 | Project Manager (Trưởng dự án) | 34 | 299,2 | 37,40
Nguyễn Danh Linh – 23IT.B116 | Frontend / UI-UX Developer | 23 | 227,3 | 28,41
Nguyễn Đức Trọng – 23IT.B234 | Backend / Database Developer | 33 | 326,1 | 40,76
Phạm Viết Hưng – 23IT.B087 | AI / Integration Developer | 23 | 261,2 | 32,65
Phan Văn Nhật Hiếu – 24IT.B045 | Testing / Documentation | 14 | 243,4 | 30,43
Tổng |  | 127 | 1.357,2 | 169,65
1.4.1.1 Phạm Mai Gia Huy – 23IT.B081
Họ tên – MSSV | Phạm Mai Gia Huy – 23IT.B081
Vai trò | Project Manager (Trưởng dự án)
Công nghệ / kỹ năng | •  Quản lý dự án, lập kế hoạch và theo dõi tiến độ •  Viết đặc tả yêu cầu (SRS), phân tích nghiệp vụ •  Quản lý rủi ro, quản lý thay đổi phạm vi •  Git/GitHub, Trello
Module phụ trách | Điều phối toàn bộ 11 module; trực tiếp phụ trách đặc tả yêu cầu (SRS) và tài liệu quản trị dự án.
Nhiệm vụ | •  Xây dựng kế hoạch, giao việc, theo sát tiến độ và báo cáo giảng viên mỗi tuần. •  Thu thập, phân tích, đặc tả yêu cầu và khoanh vùng phạm vi 11 module. •  Kiểm soát rủi ro, thay đổi phạm vi và đánh giá mức đóng góp của các thành viên. •  Rút bài học kinh nghiệm và hoàn thiện báo cáo đồ án.
Khối lượng ước lượng | 34 công việc, 299,2 giờ (37,40 người-ngày)
1.4.1.2 Nguyễn Danh Linh – 23IT.B116
Họ tên – MSSV | Nguyễn Danh Linh – 23IT.B116
Vai trò | Frontend / UI-UX Developer
Công nghệ / kỹ năng | •  React, TailwindCSS, JavaScript •  Thiết kế giao diện trên Figma •  Responsive design, kéo thả, hiển thị dữ liệu
Module phụ trách | M2 Khám phá địa điểm; M4 Đánh giá địa điểm; M7 Quản lý lịch trình đã lưu; giao diện của M5 (trang quản trị), M6, M9, M11.
Nhiệm vụ | •  Chọn phong cách và bảng màu; thiết kế khoảng 15–18 màn hình bằng Figma. •  Dựng bố cục chung và trang quản trị cho Admin. •  Lập trình các màn hình tìm kiếm, chi tiết địa điểm, đánh giá, lịch sử chuyến đi và sửa lịch trình. •  Soạn slide và kịch bản demo cho buổi bảo vệ.
Khối lượng ước lượng | 23 công việc, 227,3 giờ (28,41 người-ngày)
1.4.1.3 Nguyễn Đức Trọng – 23IT.B234
Họ tên – MSSV | Nguyễn Đức Trọng – 23IT.B234
Vai trò | Backend / Database Developer
Công nghệ / kỹ năng | •  Firebase Authentication, Cloud Firestore, Security Rules •  Cloud Functions (Node.js) •  Thiết kế cơ sở dữ liệu NoSQL, phân quyền
Module phụ trách | M1 Tài khoản & Phân quyền; M5 Quản trị địa điểm (phần dữ liệu); M6 Quản lý chi phí (thuật toán ước tính); M11 Thông báo (gửi tự động); lưu kế hoạch của M3.
Nhiệm vụ | •  Khởi tạo Firebase, tạo tài khoản SuperAdmin và quy định quyền theo vai trò. •  Thiết kế cấu trúc Firestore cùng Security Rules. •  Lập trình đăng ký, cập nhật hồ sơ, khóa/mở khóa tài khoản, quản lý địa điểm, tính chi phí và gửi thông báo. •  Đưa bản production lên chạy; quản lý phiên bản và cấu hình các môi trường.
Khối lượng ước lượng | 33 công việc, 326,1 giờ (40,76 người-ngày)
1.4.1.4 Phạm Viết Hưng – 23IT.B087
Họ tên – MSSV | Phạm Viết Hưng – 23IT.B087
Vai trò | AI / Integration Developer
Công nghệ / kỹ năng | •  Gemini API, thiết kế prompt, xử lý kết quả JSON •  Google Maps Platform (Maps, Places, Directions) •  Tích hợp API ngoài, Geolocation
Module phụ trách | M3 Lập kế hoạch bằng AI; M8 Bản đồ & Điều hướng; M9 Gợi ý khách sạn, nhà hàng & dịch vụ; M10 Chia sẻ lịch trình; theo dõi sự kiện của M11.
Nhiệm vụ | •  Thiết kế kiến trúc và luồng kết nối với AI. •  Kết nối Gemini để sinh lịch trình, xử lý lỗi và giới hạn của API. •  Gắn bản đồ, tính tuyến đường và dẫn đường theo vị trí thực. •  Làm phần gợi ý dịch vụ, chia sẻ mạng xã hội và theo dõi sự kiện liên quan chuyến đi.
Khối lượng ước lượng | 23 công việc, 261,2 giờ (32,65 người-ngày)
1.4.1.5 Phan Văn Nhật Hiếu – 24IT.B045
Họ tên – MSSV | Phan Văn Nhật Hiếu – 24IT.B045
Vai trò | Testing / Documentation
Công nghệ / kỹ năng | •  Viết test plan, test case, unit test •  Kiểm thử tích hợp và end-to-end, kiểm tra hiệu năng, bảo mật cơ bản •  Soạn tài liệu kỹ thuật, báo cáo
Module phụ trách | Kiểm thử cho cả 11 module (đơn vị, tích hợp, end-to-end); kiểm tra hiệu năng và bảo mật; tài liệu và bàn giao.
Nhiệm vụ | •  Soạn test plan; viết và chạy unit test cho từng module. •  Kiểm thử phần tích hợp Gemini, bản đồ, chi phí và toàn bộ luồng end-to-end. •  Đo hiệu năng, kiểm tra bảo mật cơ bản và theo dõi lỗi sau phát hành. •  Bàn giao mã nguồn và tài liệu kỹ thuật.
Khối lượng ước lượng | 14 công việc, 243,4 giờ (30,43 người-ngày)
Cơ sở vật chất
1.4.2.1 Bảng Tổng Hợp Chi Phí Cơ Sở Vật Chất & Hạ Tầng Kỹ Thuật
Nhóm sử dụng laptop cá nhân và hạn mức miễn phí của các dịch vụ đám mây, nên chi phí cơ sở vật chất và dịch vụ chỉ gồm tiền tên miền (300.000 VNĐ). Firebase dùng gói Blaze (trả theo mức sử dụng) vì Cloud Functions không chạy trên gói Spark; với lượng truy cập của dự án, mức sử dụng nằm trong hạn mức miễn phí nên chi phí là 0 VNĐ.
                 Bảng 1.3. Chi phí cơ sở vật chất, phần mềm và dịch vụ dự kiến
STT | Hạng mục | Chi tiết | Chi phí dự kiến (VNĐ)
I. Thiết bị và không gian làm việc
1 | Máy tính cá nhân | 05 laptop của thành viên, không mua mới. | 0
2 | Không gian làm việc | Phòng tự học, thư viện của Trường; họp nhóm qua Google Meet. | 0
II. Dịch vụ đám mây và API
3 | Firebase (Authentication, Firestore, Hosting, Cloud Functions) | Gói Blaze (trả theo mức sử dụng), dùng trong hạn mức miễn phí; Cloud Functions không chạy trên gói Spark. | 0
4 | Gemini API | Gói miễn phí; giới hạn số lần gọi khi kiểm thử prompt. | 0
5 | Google Maps Platform | Maps, Places, Directions; dùng trong hạn mức miễn phí hàng tháng. | 0
III. Tên miền
6 | Tên miền | Đăng ký 01 năm cho bản chạy thật. | 300.000
IV. Công cụ phát triển
7 | VS Code, Git/GitHub, Figma (Education), Trello, Postman | Gói miễn phí. | 0
Tổng chi phí cơ sở vật chất và dịch vụ | 300.000
Tổng kinh phí dự án là 45.156.687 VNĐ (khoảng 45,2 triệu đồng). Chi phí nhân sự bằng số giờ của từng thành viên trong bảng Delphi nhân với đơn giá theo vai trò: 35.000 VNĐ/giờ cho quản lý dự án, 30.000 VNĐ/giờ cho lập trình viên và 24.000 VNĐ/giờ cho kiểm thử. Dự phòng bằng 10% chi phí trực tiếp. Cách tính chi tiết được trình bày ở mục 3.3.
Bảng 1.4. Tổng hợp kinh phí dự án
Khoản mục | Tỷ lệ | Chi phí dự kiến (VNĐ)
A. Chi phí nhân sự (quy đổi theo khối lượng giờ)
Phạm Mai Gia Huy (Project Manager) | 23,2% | 10.472.583
Nguyễn Danh Linh (Frontend / UI-UX Developer) | 15,1% | 6.818.500
Nguyễn Đức Trọng (Backend / Database Developer) | 21,7% | 9.782.500
Phạm Viết Hưng (AI / Integration Developer) | 17,4% | 7.835.750
Phan Văn Nhật Hiếu (Testing / Documentation) | 12,9% | 5.842.200
Cộng A – Nhân sự | 90,2% | 40.751.533
B. Cơ sở vật chất và dịch vụ (Bảng 1.3)
Cộng B – Cơ sở vật chất và dịch vụ | 0,7% | 300.000
C. Chi phí dự phòng
Dự phòng (10% chi phí trực tiếp) | 9,1% | 4.105.153
TỔNG KINH PHÍ DỰ ÁN (A + B + C) | 45.156.687
Ghi chú: tỷ lệ tính trên tổng kinh phí 45.156.687 VNĐ; chi tiết từng khoản ở mục 3.3.
1.4.2.2 Giải trình tính hợp lý & tối ưu chi phí
Tận dụng nguồn lực sẵn có:
Sử dụng laptop cá nhân của 5 thành viên, phòng tự học và thư viện của Trường; họp nhóm trực tuyến qua Google Meet, không phát sinh chi phí văn phòng và thiết bị.
Sử dụng hạn mức miễn phí của các dịch vụ đám mây:
Google Maps Platform có hạn mức sử dụng miễn phí hàng tháng, đủ cho việc hiển thị bản đồ, tìm địa điểm và tính tuyến đường trong thời gian phát triển và kiểm thử.
Firebase gói Blaze vẫn có hạn mức miễn phí cho Authentication, Firestore, Hosting và Cloud Functions; chỉ tính phí khi vượt hạn mức, nên với quy mô dữ liệu thử nghiệm chi phí là 0 VNĐ.
Gemini API dùng gói miễn phí; nhóm giới hạn số lần gọi khi kiểm thử prompt để không vượt hạn mức. Các công cụ VS Code, Git/GitHub, Figma, Trello đều dùng gói miễn phí.
Hạ tầng triển khai:
Ứng dụng được triển khai trên Firebase Hosting nên không cần thuê máy chủ riêng (VPS); chi phí duy nhất là đăng ký tên miền 300.000 VNĐ/năm.
Rủi ro phát sinh chi phí (ví dụ vượt hạn mức Gemini API hoặc Google Maps Platform, làm thêm giờ khi trễ tiến độ) được bù bằng khoản dự phòng 10% (4.105.153 VNĐ) do quản lý dự án nắm giữ.
Danh sách các bên liên quan
Nhận diện và quản lý các bên liên quan là yếu tố then chốt giúp dự án TrekMate – Hệ thống website lên kế hoạch du lịch thông minh đảm bảo đi đúng tiến độ, đáp ứng đúng yêu cầu kỹ thuật và mang lại giá trị thực tế cho người dùng. Danh sách các bên liên quan được chia thành 3 nhóm chính:
A. Nhóm Nội bộ Dự án (Internal Stakeholders)
Bên liên quan | Vai trò & Trách nhiệm chính | Mức độ ảnh hưởng / Quan tâm
Giảng viên hướng dẫn (ThS. Võ Văn Lường) | Định hướng về mặt chuyên môn và phương pháp luận quản trị dự án. Duyệt và phê duyệt các cột mốc quan trọng (SRS, System Design, Demo). Đánh giá chất lượng sản phẩm và tiến độ hoàn thành của nhóm. | Cao / Cao
Trưởng dự án (Project Manager) (Phạm Mai Gia Huy) | Lập kế hoạch, phân công công việc và theo dõi tiến độ trong suốt 9 tuần. Quản lý rủi ro, ngân sách và giải quyết các vấn đề phát sinh trong nhóm. Làm đầu mối giao tiếp chính với Giảng viên hướng dẫn. | Cao / Cao
Nhóm Phát triển (Dev / QA / UI-UX) (Nguyễn Danh Linh, Nguyễn Đức Trọng, Phan Văn Nhật Hiếu, Phạm Viết Hưng) | UI/UX & Frontend:  Thiết kế giao diện trên Figma, lập trình giao diện web bằng React và TailwindCSS. Backend & AI / Integration:  Thiết kế cơ sở dữ liệu Firestore, Security Rules, Cloud Functions; tích hợp Gemini API và Google Maps Platform. Testing / Documentation:  Xây dựng test case, kiểm thử chức năng, tích hợp, hiệu năng và viết tài liệu. | Cao / Cao
B. Nhóm Người dùng & Khách hàng (External Stakeholders - Users)
Bên liên quan | Vai trò & Nhu cầu thực tế | Mức độ ảnh hưởng / Quan tâm
Khách du lịch tự túc (Travelers) | Đối tượng:  Cá nhân, nhóm bạn, gia đình trẻ có nhu cầu đi du lịch tự chủ. Nhu cầu:  Tạo lịch trình nhanh bằng AI, tối ưu  quãng đường đi lại, quản lý ngân sách minh bạch và chia sẻ kế hoạch với bạn đồng hành. Đóng góp:  Cung cấp phản hồi (Feedback) ở giai đoạn thử nghiệm (Testing) để cải thiện UI/UX và logic của AI. | Trung bình / Cao
Đội ngũ Quản trị viên (Admins) | Đối tượng:  Ban quản trị vận hành ứng dụng TrekMate. Nhu cầu:  Trang quản trị trực quan để thêm, sửa, xóa điểm du lịch (POI) và quản lý, khóa/mở khóa tài khoản người dùng. | Cao / Trung bình
C. Nhóm Đối tác Dịch vụ & Hạ tầng (External Partners & Providers)
Bảng 1.5. Danh sách các bên liên quan
Bên liên quan | Dịch vụ cung cấp | Mức độ ảnh hưởng / Quan tâm
Google Cloud / AI Studio | Cung cấp Gemini API cho tính năng lập kế hoạch du lịch tự động. Cung cấp Google Maps Platform (Maps, Places, Directions) cho hiển thị bản đồ, tính tuyến đường  và dẫn đường. | Cao / Thấp
Nhà cung cấp hạ tầng (Firebase) và tên miền | Firebase:  xác thực người dùng (Authentication), cơ sở dữ liệu Cloud Firestore, Cloud Functions và Hosting cho website. Nhà đăng ký tên miền:  cung cấp tên miền cho bản chạy thật. | Trung bình / Thấp
Hội đồng Đánh giá Đồ án (Trường ĐH CNTT&TT Việt - Hàn) | Đánh giá tính thực tiễn, kiến trúc phần mềm, quy trình quản trị dự án và kết quả nghiệm thu cuối cùng của nhóm. | Cao / Cao
D. Ma trận Phân tích Bên liên quan (Power vs. Interest Grid)
Để quản lý hiệu quả các bên liên quan trong suốt 9 tuần dự án, nhóm áp dụng chiến lược ứng xử theo sơ đồ ma trận:
Quản lý chặt chẽ (High Power - High Interest): Giảng viên hướng dẫn, Trưởng dự án và Nhóm phát triển (Báo cáo tiến độ tuần, họp tiến độ hằng tuần).
Thỏa mãn nhu cầu (High Power - Low Interest): Hội đồng đánh giá đồ án, Các nhà cung cấp dịch vụ Cloud/API (Đảm bảo tuân thủ tiêu chuẩn kỹ thuật, hạn mức API).
Giữ kết nối & Cập nhật (Low Power - High Interest): Người dùng thử nghiệm (Travelers) (Gửi khảo sát người dùng, thu thập feedback nâng cấp tính năng).
Theo dõi (Low Power - Low Interest): Các đối tác tiềm năng khác.
Quy trình ứng dụng
Lý do lựa chọn mô hình Thác nước (Waterfall)
Nhóm chọn mô hình Thác nước (Waterfall) cho dự án TrekMate, trong đó các giai đoạn được thực hiện tuần tự: giai đoạn sau chỉ bắt đầu khi giai đoạn trước đã hoàn thành và được kiểm tra. Các lý do chính:
Yêu cầu rõ ràng và ổn định: Phạm vi 11 module đã được chốt trong tài liệu Scope v1.0 và WBS ngay từ đầu, ít khả năng thay đổi lớn trong 9 tuần.
Thời gian và ngân sách cố định: Dự án có hạn 9 tuần (21/08 – 23/10/2026) và ngân sách khoảng 45,2 triệu đồng; Waterfall cho phép lập lịch và dự toán chi phí cho toàn bộ dự án ngay từ giai đoạn lập kế hoạch.
Có mốc phê duyệt rõ ràng: Mỗi giai đoạn kết thúc bằng một mốc (M1–M5) với sản phẩm đầu ra cụ thể (SRS, tài liệu thiết kế, mã nguồn, báo cáo kiểm thử), thuận tiện cho giảng viên hướng dẫn duyệt và đánh giá.
Phù hợp với nhóm nhỏ, ít kinh nghiệm: Năm thành viên là sinh viên, chưa quen làm việc theo các vòng lặp ngắn của Agile/Scrum; quy trình tuần tự giúp phân công và theo dõi tiến độ đơn giản hơn.
Tài liệu đầy đủ: Mỗi giai đoạn đều tạo ra tài liệu, đáp ứng yêu cầu của môn học và thuận lợi cho việc bàn giao.
Phù hợp với cách lập kế hoạch bằng MS Project: Các giai đoạn nối tiếp nhau bằng quan hệ Finish-to-Start và mốc tiến độ, giúp xác định đường găng và theo dõi tiến độ so với kế hoạch gốc (baseline).
Hạn chế và cách khắc phục: Waterfall khó đáp ứng khi yêu cầu thay đổi muộn và lỗi thường được phát hiện ở cuối dự án. Nhóm giảm rủi ro bằng cách viết Unit Test song song khi phát triển và áp dụng quy trình kiểm soát thay đổi phạm vi (nhánh 5.1 của WBS).
Các giai đoạn triển khai chi tiết theo Mô hình Thác nước 
Toàn bộ quy trình phát triển dự án TrekMate gồm 5 giai đoạn chính kéo dài trong 9 tuần:
            Bảng 1.6. Các giai đoạn triển khai chi tiết theo Mô hình Thác nước
Giai đoạn | Thời gian | Nội dung công việc | Sản phẩm đầu ra
1. Khởi tạo, lập kế hoạch & phân tích yêu cầu | Tuần 1–2 (21/08 – 04/09/2026) | •      Đánh giá khả thi, thiết lập Firebase và môi trường phát triển. •      Thu thập nhu cầu thực tế về du lịch tự túc và việc ứng dụng AI. •      Xác định, phân loại yêu cầu chức năng (Functional) và phi chức năng (Non-functional); đặc tả use case. •      Lập kế hoạch dự án và thống nhất bài toán với Giảng viên hướng dẫn. | •      Tài liệu Đặc tả Yêu cầu Phần mềm (SRS). •      Kế hoạch dự án được phê duyệt.
2. Thiết kế hệ thống | Tuần 3 (07/09 – 11/09/2026) | •      Thiết kế kiến trúc Client + Firebase (BaaS) và luồng tích hợp Gemini AI, Maps API. •      Thiết kế cơ sở dữ liệu Firestore. •      Vẽ sơ đồ Use Case Diagram, Sequence Diagram. •      Xây dựng Wireframe và Prototype UI/UX trên Figma. | •      Tài liệu Thiết kế Hệ thống. •      Sơ đồ cấu trúc dữ liệu Firestore. •      Bản thiết kế UI/UX Figma.
3. Phát triển mã nguồn | Tuần 4–6 (14/09 – 02/10/2026) | •      Xây dựng 11 module bằng React + TailwindCSS. •      Cấu hình Firebase Authentication, Security Rules và Cloud Functions. •      Tích hợp Google Gemini AI (Prompt Engineering) và Google Maps API. •      Viết Unit Test song song trong quá trình phát triển. | •      Mã nguồn hoàn chỉnh trên GitHub. •      Bản chạy thử trên môi trường Staging.
4. Kiểm thử hệ thống | Tuần 7–8 (05/10 – 16/10/2026) | •      Kiểm thử tích hợp Gemini AI, bản đồ và chi phí. •      Kiểm thử toàn luồng (end-to-end). •      Kiểm tra hiệu năng và bảo mật cơ bản. •      Ghi nhận lỗi, sửa lỗi và kiểm thử lại (Re-test). | •      Bộ Kịch bản Kiểm thử (Test Cases). •      Báo cáo Kết quả Kiểm thử và danh sách lỗi đã xử lý.
5. Triển khai & kết thúc | Tuần 9 (19/10 – 23/10/2026) | •      Triển khai lên Firebase Hosting và gán tên miền. •      Theo dõi, vá lỗi sau triển khai. •      Tổng kết bài học kinh nghiệm. •      Hoàn thiện báo cáo, slide và bàn giao. | •      Website TrekMate hoạt động chính thức (Live Domain). •      Tài liệu hướng dẫn sử dụng. •      Báo cáo và slide bảo vệ đồ án.

## Mục 4.9 – Quản lý rủi ro

4.9 Quản lý rủi ro
Các rủi ro được nhận diện trong nhánh 5.3 Risk Management của WBS (5.3.1 Nhận diện rủi ro, 5.3.2 Đánh giá và xếp hạng, 5.3.3 Kế hoạch ứng phó) và được cập nhật trạng thái tại ngày 09/10/2026. Mức độ ảnh hưởng và xác suất được đánh giá theo ba mức: Cao, Trung bình, Thấp.
Bảng 4.11. Bảng quản lý rủi ro của dự án TrekMate
Mã | Rủi ro | Mức độ | Xác suất | Biện pháp ứng phó | Người phụ trách | Tình trạng 09/10
R1 | AI trả kết quả sai lệch hoặc không phù hợp (5.3.1.1) | Cao | Trung bình | Ràng buộc prompt trả về JSON theo mẫu; kiểm tra dữ liệu trước khi hiển thị; cho người dùng yêu cầu tạo lại | Phạm Viết Hưng | Đã xảy ra ở giai đoạn phát triển, đã xử lý
R2 | Quá tải hoặc vượt giới hạn Gemini API (5.3.1.2) | Cao | Trung bình | Lưu tạm kết quả, giới hạn số lần gọi, thử lại có độ trễ; dùng quỹ dự phòng nếu phải chuyển gói trả phí | Phạm Viết Hưng | Đang theo dõi
R3 | Trễ tiến độ do phụ thuộc giữa các  thành viên (5.3.1.3) | Trung bình | Cao | Họp tiến độ hằng tuần; điều chuyển việc cho thành  viên rảnh; giữ mốc cuối mỗi giai đoạn | Phạm Mai Gia Huy | Đang xảy ra ở giai đoạn kiểm  thử, đang điều chỉnh
R4 | Số lỗi phát hiện khi kiểm thử nhiều hơn dự kiến | Cao | Cao | Ưu tiên sửa lỗi mức cao; unit test song song từ giai đoạn phát triển; code review chéo | Nguyễn Đức Trọng | Đang xảy ra (3.2.5.5 kéo dài 1 ngày)
R5 | Thay đổi phạm vi chức năng | Trung bình | Trung bình | Mọi thay đổi ghi nhận và phê duyệt theo quy trình 5.1.1; chỉ nhận thay đổi nhỏ sau mốc M2 | Phạm Mai Gia Huy | Chưa xảy ra
R6 | Vượt hạn mức miễn phí của Firebase hoặc Google Maps | Trung bình | Thấp | Theo dõi lượng sử dụng; đặt cảnh báo ngân sách trên Google Cloud | Nguyễn Đức Trọng | Chưa xảy ra
R7 | Lộ dữ liệu do cấu hình Security Rules chưa chặt | Cao | Thấp | Kiểm tra quyền theo vai trò; kiểm tra bảo mật cơ bản (5.2.3.2) trước phát hành | Phan Văn Nhật Hiếu | Chưa đến thời điểm kiểm tra
R8 | Thành viên vắng mặt do ốm hoặc lịch thi | Trung bình | Trung bình | Mỗi module có người nắm thay; tài liệu và mã nguồn lưu trên GitHub | Phạm Mai Gia Huy | Chưa xảy ra
Hai rủi ro đã xảy ra (R1 và R4) là nguyên nhân trực tiếp của chi phí vượt ở nhánh Execute & Monitor. Rủi ro R3 đang xảy ra ở giai đoạn kiểm thử và được xử lý bằng việc điều chuyển nhân lực như trình bày ở mục 4.5 và 4.8. Các rủi ro còn lại chưa xảy ra và tiếp tục được theo dõi trong các buổi họp tiến độ hằng tuần.

## Mục 5.2–5.3 – Hạn chế và hướng phát triển

5.2 Hạn chế
Bên cạnh các kết quả đạt được, dự án vẫn còn một số hạn chế:
Phân công công việc chưa đồng đều. Một số thành viên bị dồn việc vào cùng một giai đoạn: Phạm Mai Gia Huy phải làm tới 195% công suất ở giai đoạn khởi tạo và lập kế hoạch, Phan Văn Nhật Hiếu tới 155% ở giai đoạn kiểm thử, do toàn bộ việc kiểm thử giao cho một người.
Ước lượng thời gian còn lạc quan. Lịch dự án dùng giá trị WA nên thời gian dự trữ mỏng. Một số công việc vượt ước lượng đáng kể, như tích hợp Gemini AI (vượt 25%) và thiết kế giao diện trên Figma (vượt 15%), làm dự án chậm nhẹ ở giai đoạn kiểm thử.
Phương pháp Delphi chỉ thực hiện một vòng. Nhóm chưa tổ chức các vòng thảo luận tiếp theo để thu hẹp chênh lệch giữa ước lượng của các thành viên.
Số liệu theo dõi tiến độ ở Chương 4 là số liệu giả lập, dùng để minh họa việc điều hành bằng MS Project, chưa phải số đo từ quá trình thực hiện thực tế.
Kinh nghiệm sử dụng công cụ còn hạn chế. Một số thành viên chưa quen MS Project và việc xây dựng WBS; nhóm chỉ có MS Project bản dùng thử nên thời gian thao tác bị giới hạn.
Sản phẩm mới dừng ở phiên bản web, chưa có ứng dụng di động, nên trải nghiệm khi dùng trong lúc đi du lịch chưa thuận tiện.
Sắp xếp thời gian học tập và làm việc nhóm đôi lúc chưa hợp lý, ảnh hưởng đến tiến độ chung.
5.3 Hướng phát triển
Trong tương lai, nhóm mong muốn tiếp tục hoàn thiện và phát triển dự án TrekMate để ứng dụng có thể đáp ứng tốt hơn nhu cầu của người dùng.
Một số hướng phát triển dự kiến bao gồm:
Phát triển ứng dụng trên điện thoại: Xây dựng phiên bản mobile trên Android và iOS để người dùng dễ dàng lập kế hoạch và theo dõi lịch trình khi đi du lịch.
Tích hợp chức năng đặt phòng: Cho phép người dùng tìm kiếm và đặt khách sạn, homestay trực tiếp trên hệ thống.
Tích hợp thanh toán trực tuyến: Hỗ trợ thanh toán khi đặt phòng hoặc sử dụng các dịch vụ du lịch.
Cải thiện chức năng AI: Nâng cao khả năng gợi ý lịch trình phù hợp với sở thích, thời gian và ngân sách của từng người dùng.
Hoàn thiện giao diện và hiệu suất: Cải thiện trải nghiệm người dùng, tốc độ xử lý và tính ổn định của hệ thống.
Ngoài ra, nhóm cũng mong muốn áp dụng những kiến thức đã học về quản trị dự án để lập kế hoạch và quản lý công việc hiệu quả hơn trong các dự án tiếp theo.
