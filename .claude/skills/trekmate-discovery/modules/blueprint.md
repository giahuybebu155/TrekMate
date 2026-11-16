# Module: Solution Blueprint + Business Model

Chủ đề mô tả **giải pháp tổng thể và cách nó tạo ra, trao và giữ giá trị**. Business Model thuộc module này vì dùng chung phân tích giá trị và thương mại. Nó có trang riêng trên showcase nhưng không có tài liệu nghiên cứu riêng.

## Mục tiêu

Biến Vision thành một bản thiết kế giải pháp ở mức sản phẩm: giải pháp gồm những khối nào, mỗi khối giải quyết job hoặc pain nào, phụ thuộc vào công nghệ hay đối tác nào, và sản phẩm sống bằng gì. Đây là cầu nối giữa "vì sao" (Problem, Vision) và "làm gì trước" (Journey & Features, Roadmap).

## Đầu vào

- `01-problem.md` đến `04-vision.md` (hoặc ngữ cảnh tương đương).
- `sources/`: mô tả module, kiến trúc, stack, chi phí hạ tầng trong tài liệu dự án.
- `decision-log.md`: stack, nguồn dữ liệu, mô hình kinh doanh, phạm vi MVP.

## Đầu ra: `05-blueprint.md`

```markdown
---
topic: Solution Blueprint
status: draft
sources: [...]
updated: dd/mm/yyyy
---

# Solution Blueprint & Business Model

## TL;DR
(≤ 5 dòng: giải pháp một câu, các khối chính, mô hình kinh doanh, rủi ro lớn nhất)

## 1. Giải pháp tổng thể
Mô tả giải pháp trong 3–5 câu, từ góc người dùng.

### Các khối giải pháp
| Khối | Làm gì | Job / Pain giải quyết | Module sản phẩm | Phụ thuộc bên ngoài |
|---|---|---|---|---|
| | | JTBD-n, PAIN-n | Mn | (API, dịch vụ, dữ liệu) |

### Luồng giá trị chính
Chuỗi bước từ khi người dùng có nhu cầu tới khi nhận được giá trị, ở mức khối (không phải màn hình).

## 2. Value Proposition Canvas
| Phía khách hàng (persona chính) | Phía sản phẩm |
|---|---|
| **Jobs:** JTBD-n | **Sản phẩm & dịch vụ:** các khối |
| **Pains:** PAIN-n | **Pain relievers:** khối nào giảm pain nào |
| **Gains:** GAIN-n | **Gain creators:** khối nào tạo gain nào |

**Độ khớp:** pain hoặc gain quan trọng nào chưa có khối giải quyết.

## 3. Product Canvas
| Mục | Nội dung |
|---|---|
| Tên sản phẩm | |
| Persona chính | |
| Vấn đề cốt lõi | PS-n |
| Giải pháp | |
| Điểm khác biệt | (từ Vision) |
| Chỉ số thành công | KPI-n (chi tiết ở Roadmap) |
| Ràng buộc | (nền tảng, ngân sách, thời gian, công nghệ) |
| Rủi ro lớn nhất | |

## 4. Business Model

### Lean Canvas
| Ô | Nội dung | Nguồn |
|---|---|---|
| Vấn đề | top 3 PS-n | |
| Phân khúc khách hàng | persona, người dùng sớm | |
| Giải pháp | top 3 khối | |
| Giá trị độc nhất | (từ Vision) | |
| Lợi thế khó sao chép | | |
| Kênh | (từ Vision – Go-to-Market) | |
| Dòng doanh thu | | |
| Cơ cấu chi phí | | |
| Chỉ số then chốt | | |

### Ranh giới gói miễn phí và trả phí
| Năng lực | Miễn phí | Trả phí | Lý do |
|---|---|---|---|
Chỉ áp dụng khi mô hình kinh doanh có nhiều gói. Năng lực giải quyết job cốt lõi của persona chính
mặc định thuộc gói miễn phí, trừ khi Product Owner quyết định khác.

### Chi phí vận hành
| Hạng mục | Cách tính | Ước tính | Nguồn |
|---|---|---|---|
Ghi rõ dịch vụ nào đang dùng gói miễn phí và ngưỡng phải trả tiền.

## 5. Rủi ro & phụ thuộc
| ID | Rủi ro | Khối bị ảnh hưởng | Cách giảm | Tin cậy |
|---|---|---|---|---|

## Giả định
| ID | Giả định | Nếu sai thì | Cách kiểm chứng |
|---|---|---|---|

## Bàn giao
- Journey & Features: các khối là nhóm tính năng; Value Proposition chỉ ra tính năng nào bắt buộc.
- Roadmap: ranh giới miễn phí và trả phí, rủi ro và phụ thuộc quyết định thứ tự phát hành.
- Giai đoạn 3: khối và phụ thuộc bên ngoài là đầu vào cho kiến trúc, data model và danh sách API.
```

## Câu hỏi gợi ý (chỉ để suy nghĩ, xem elicitation.md)

- Năng lực nào người dùng sẵn sàng trả tiền: AI không giới hạn lượt, lịch trình nhóm, xuất PDF, chế độ ngoại tuyến?
- Năng lực nào nhất định phải miễn phí để người dùng ở lại?
- Dịch vụ bên ngoài nào nếu ngừng hoặc tăng giá thì sản phẩm không chạy được?
- Ngưỡng chi phí hạ tầng hàng tháng mà nhóm chấp nhận được là bao nhiêu?
- Nguồn dữ liệu địa điểm có đủ tin cậy để làm lợi thế không?

## Viết V1

- Lấy khối giải pháp từ danh sách module trong nguồn, gom thành 4–7 khối theo giá trị cho người dùng, không theo kỹ thuật.
- Value Proposition chỉ cho **persona chính**. Persona khác để vòng sau.
- Business Model theo quyết định đã ghi trong `decision-log.md`. Nếu chưa có ranh giới gói, đề xuất `[PROP]` một phương án kèm lý do và đưa câu hỏi vào `discovery-gaps.md`.
- Chi phí vận hành: chỉ ghi số có nguồn (trang giá chính thức, kèm tháng/năm). Không có thì `[TBD]`.
- Không thiết kế màn hình, data model hay API ở đây. Chỉ nêu khối và phụ thuộc.

## Kiểm tra trước khi xong

- [ ] Mỗi khối giải pháp giải quyết ít nhất một JTBD hoặc PAIN của persona chính.
- [ ] Mọi pain quan trọng của persona chính đã có khối giải quyết, hoặc được ghi là chưa giải quyết.
- [ ] Mô hình kinh doanh khớp với `decision-log.md`.
- [ ] Job cốt lõi của persona chính nằm ở gói miễn phí, hoặc có quyết định ghi lại lý do.
- [ ] Mỗi phụ thuộc bên ngoài có rủi ro và cách giảm tương ứng.
- [ ] Không có số chi phí thiếu nguồn.
