# Elicitation: hỏi từ bằng chứng hiện có

Mục tiêu của việc hỏi là **thay đổi được phân tích**, không phải điền đủ biểu mẫu. Mỗi câu hỏi tốn sự chú ý của Product Owner; chỉ hỏi khi câu trả lời có giá trị hơn một bản nháp có nguồn.

## 1. Khi nào hỏi

Chỉ hỏi khi **cả ba** điều sau đều đúng:

1. **Chưa có câu trả lời.** Đã kiểm tra `sources/` (đặc biệt `po-answers.md`), `decision-log.md` và các file chủ đề hiện có.
2. **Câu trả lời có thể đổi kết luận.** Nếu mọi câu trả lời hợp lý đều dẫn tới cùng một bản nháp, đừng hỏi; ghi giả định `A-n` và viết tiếp.
3. **Không tự suy ra được một cách có trách nhiệm.** Nếu suy luận từ nguồn đủ chắc (`[INF]` mức tin cậy trung bình trở lên), dùng suy luận và để PO sửa khi duyệt.

Không hỏi để:
- Xác nhận điều đã có trong nguồn.
- Xin phép viết bản nháp. Cứ viết V1 trước (xem SKILL.md).
- Lấy thông tin mà web search tìm được (đối thủ, quy mô thị trường, giá dịch vụ). Tự tìm, ghi `[DOC: web – …]`.

## 2. Tìm câu hỏi từ đâu

Câu hỏi sinh ra từ dữ liệu, không từ danh sách cố định. Bốn nguồn sinh câu hỏi tốt:

| Tín hiệu | Ví dụ | Câu hỏi sinh ra |
|---|---|---|
| **Mâu thuẫn** giữa hai nguồn | Báo cáo ghi mô hình Waterfall, PO chọn sprint 1 tuần | Không cần hỏi nếu `decision-log` đã chốt; nếu chưa thì hỏi bên nào thắng |
| **Khoảng trống chặn kết luận** | Không có dữ liệu nguồn thu | "TrekMate có định thu tiền không, và bằng cách nào?" |
| **Giả định rủi ro cao** | V1 giả định người dùng chịu chờ 15 giây | "Có dữ liệu nào cho thấy người dùng chấp nhận chờ lâu như vậy không?" |
| **Lựa chọn hướng đi** mà agent không được tự quyết | Hai định vị khác nhau đều hợp lý | Đưa 2–3 phương án `[PROP]` kèm đánh đổi, hỏi PO chọn |

Câu hỏi mẫu trong mỗi module chỉ là gợi ý suy nghĩ. Không chép nguyên văn, không hỏi theo thứ tự trong module.

## 3. Cách viết một câu hỏi

- **Một câu hỏi, một quyết định.** Không gộp hai ý vào một câu.
- **Tự đứng được.** PO đọc riêng câu hỏi vẫn hiểu: nêu ngắn ngữ cảnh và vì sao nó quan trọng.
- **Có phương án khi có thể.** 2–4 lựa chọn cụ thể, đánh dấu phương án khuyến nghị và lý do. PO luôn được trả lời tự do.
- **Nói rõ hậu quả.** "Nếu chọn A thì Blueprint bỏ phần nguồn thu; nếu B thì cần thêm mục hoa hồng đặt phòng."
- **Không dẫn dắt.** Không viết câu hỏi để PO xác nhận đề xuất của agent.

Mẫu ghi trong `discovery-gaps.md`:

| # | Câu hỏi | Chủ đề bị ảnh hưởng | Vì sao quan trọng | Hỏi ngày |
|---|---|---|---|---|
| G-n | (câu hỏi, kèm phương án nếu có) | Vision, Blueprint | (kết luận nào sẽ đổi) | dd/mm/yyyy |

## 4. Bao nhiêu câu, khi nào gửi

- **Sau V1:** gửi tối đa **3 câu** có ảnh hưởng lớn nhất. Các câu còn lại vẫn nằm trong `discovery-gaps.md`, xếp theo mức ảnh hưởng.
- **Mỗi vòng sau:** tối đa 3 câu mới, chỉ những câu phát sinh từ câu trả lời trước hoặc từ mâu thuẫn mới.
- **Khi đang cập nhật một chủ đề:** chỉ hỏi câu thuộc chủ đề đó hoặc phụ thuộc trực tiếp.
- Nếu PO vắng mặt (chạy theo lịch, không ai trả lời), không chờ: viết tiếp với giả định rõ ràng và để câu hỏi trong hàng đợi.

## 5. Xử lý câu trả lời

1. Ghi nguyên ý vào `sources/po-answers.md` kèm ngày. Đây là `[STK]`.
2. Xoá câu hỏi khỏi mục "Đang chờ trả lời" trong `discovery-gaps.md`.
3. Nếu câu trả lời là một lựa chọn phạm vi hoặc hướng đi, đề xuất PO ghi vào `decision-log.md`. Chỉ sau khi ghi thì mới dùng thẻ `[DEC]`.
4. Sửa đúng các chủ đề bị ảnh hưởng, rồi chạy kiểm tra nhất quán của `synthesis-contract.md` §6.
5. Câu trả lời mơ hồ hoặc mâu thuẫn với quyết định cũ: không tự diễn giải. Hỏi lại một câu làm rõ, ngắn hơn câu cũ.

## 6. Khi PO không biết

"Chưa biết" là một câu trả lời hợp lệ. Khi đó:
- Ghi giả định `A-n` an toàn nhất cho MVP và cách kiểm chứng (khảo sát, thử nghiệm, số liệu sau ra mắt).
- Nếu khoảng trống có thể để lại, chuyển câu hỏi sang mục "Đã được PO chấp nhận để trống" kèm lý do.
