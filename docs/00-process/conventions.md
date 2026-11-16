# Quy ước tài liệu

> Áp dụng cho mọi tài liệu trong `docs/`. Quy tắc về bằng chứng và loại nguồn nằm ở `.claude/skills/trekmate-discovery/synthesis-contract.md`, không lặp lại ở đây.

## Front matter

```yaml
---
topic: Problem            # tên chủ đề
status: draft             # draft | approved
sources: [scope, po-answers]   # tên file trong sources/ đã dùng
updated: 2026-11-16
---
```

## Mã định danh dùng ở Giai đoạn 1

| Loại | Mẫu | Ví dụ |
|---|---|---|
| Vấn đề | `PS-n` | PS-2 |
| Persona | `Pn` | P1 |
| Job | `JTBD-n` | JTBD-3 |
| Pain / Gain | `PAIN-n` / `GAIN-n` | PAIN-4 |
| Module sản phẩm | `Mn` | M3 |
| Giả định | `A-n` | A-3 |
| Quyết định | `D-n` | D-7 |
| Chỉ số | `KPI-n` | KPI-2 |

ID đã cấp không dùng lại cho thứ khác. Bỏ một mục thì gạch đi (`~~…~~`) và ghi lý do. Các giai đoạn sau sẽ bổ sung loại ID của mình (FR, UC, US, màn hình…) khi bắt đầu.

## Định dạng

- Tiếng Việt, giữ thuật ngữ tiếng Anh chuẩn (Persona, MVP, Job…).
- Tiền `1.250.000 ₫`, ngày `dd/mm/yyyy`, giờ `08:30`.
- Đầu file có **TL;DR** tối đa 5 dòng. Cuối file có **Bàn giao**: giai đoạn sau dùng phần nào.
- Ưu tiên bảng và gạch đầu dòng hơn đoạn văn dài.
