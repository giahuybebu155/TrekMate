# TrekMate – Ứng dụng web lên kế hoạch du lịch thông minh bằng AI

TrekMate giúp người Việt đi du lịch tự túc trong nước tạo lịch trình theo ngày bằng AI (Gemini), xem tuyến đường trên bản đồ (Google Maps), ước tính chi phí và chia sẻ kế hoạch cho bạn đồng hành.

Repository chứa tài liệu theo từng giai đoạn để AI coding agent (Claude Code) đọc và code chính xác, sau đó là mã nguồn.

## Giai đoạn

| # | Giai đoạn | Thư mục | Skill | Trạng thái |
|---|---|---|---|---|
| 1 | Product Discovery | [`docs/01-discovery`](docs/01-discovery) | `trekmate-discovery` | 🟡 Đang xây skill |
| 2 | Design System & Prototype | — | (chưa có) | ⚪ Chưa bắt đầu |
| 3 | Product Requirements | — | (chưa có) | ⚪ Chưa bắt đầu |
| 4 | Code | — | — | ⚪ Chưa bắt đầu |
| 5 | Present & QA | — | — | ⚪ Chưa bắt đầu |

Mỗi giai đoạn có một skill trong `.claude/skills/`. Giai đoạn sau đọc đầu ra của giai đoạn trước, không đọc skill của nó.

- Quy ước tài liệu: [`docs/00-process/conventions.md`](docs/00-process/conventions.md)
- Quyết định đã duyệt: [`docs/00-process/decision-log.md`](docs/00-process/decision-log.md)

## Stack (đã chốt)

React + Vite + TypeScript · TailwindCSS + shadcn/ui · Firebase (Authentication, Cloud Firestore, Cloud Functions, Hosting) · Gemini API · Google Maps Platform.

## Git

- `main`: chỉ chứa tài liệu đã duyệt và code chạy được.
- Nhánh tài liệu `docs/<nội-dung>`, nhánh code `feat/<story-id>-<tên-ngắn>`. Merge qua Pull Request.
- Commit theo Conventional Commits: `docs:`, `feat:`, `fix:`, `test:`, `chore:`.

## Nhóm phát triển

| Thành viên | Vai trò |
|---|---|
| Phạm Mai Gia Huy | Project Manager / Product Owner |
| Nguyễn Danh Linh | Frontend / UI-UX |
| Nguyễn Đức Trọng | Backend / Database (Firebase) |
| Phạm Viết Hưng | AI / Integration (Gemini, Maps) |
| Phan Văn Nhật Hiếu | Testing / Documentation |
