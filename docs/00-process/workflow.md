# Quy trình làm việc với AI: TrekMate

## 1. Nguyên tắc

1. **Docs trước, code sau.** AI chỉ code những gì đã có trong tài liệu được duyệt. Thiếu thông tin thì AI phải hỏi, không được tự bịa.
2. **Một nguồn sự thật.** Mỗi khái niệm chỉ được định nghĩa ở một file; các file khác dẫn link tới đó, không chép lại.
3. **Duyệt từng giai đoạn.** Giai đoạn N chỉ bắt đầu khi giai đoạn N-1 có trạng thái `✅ Đã duyệt` (Product Owner duyệt).
4. **Thay đổi có dấu vết.** Mọi thay đổi phạm vi/quyết định ghi vào `decision-log.md` và commit với tiền tố `docs:`.

## 2. Thứ tự đọc cho AI coding agent

```
CLAUDE.md
→ docs/01-research/research.md      (vì sao, cho ai)
→ docs/03-product/PRD.md             (làm gì)
→ docs/03-product/user-stories.md    (story của sprint hiện tại)
→ docs/02-design/DESIGN.md           (trông như thế nào)
→ docs/04-engineering/*              (làm thế nào)
```

## 3. Trạng thái tài liệu

| Nhãn | Ý nghĩa |
|---|---|
| ⚪ Chưa làm | Chưa có nội dung |
| 🟡 Chờ duyệt | Bản nháp, AI chưa được dùng để code |
| ✅ Đã duyệt | Được dùng làm căn cứ để code |
| 🔁 Cần cập nhật | Có thay đổi ở giai đoạn sau làm file này lỗi thời |

## 4. Nhánh Git & commit

- `main`: luôn ở trạng thái chạy được; tài liệu đã duyệt.
- `docs/<giai-doan>`: soạn tài liệu (ví dụ `docs/02-design`), merge bằng Pull Request.
- `feat/<story-id>-<ten-ngan>`: code theo user story (ví dụ `feat/US-M3-01-ai-generate`).
- Commit theo Conventional Commits: `docs:`, `feat:`, `fix:`, `test:`, `chore:`.

## 5. Nhịp sprint (sau khi GĐ1–3 được duyệt)

Sprint 1 tuần: Lập kế hoạch (thứ Hai) → AI code theo story → review PR + test → demo, retro (thứ Sáu). Backlog nằm ở `docs/03-product/backlog.md`.
