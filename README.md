# TrekMate – Ứng dụng web lên kế hoạch du lịch thông minh bằng AI

TrekMate giúp người Việt đi du lịch tự túc trong nước tạo lịch trình theo ngày bằng AI (Gemini), xem tuyến đường trên bản đồ (Google Maps), ước tính chi phí và chia sẻ kế hoạch cho bạn đồng hành.

Repository này chứa **toàn bộ tài liệu theo quy trình 5 giai đoạn**, viết để AI coding agent (Claude Code) đọc và code chính xác, sau đó là mã nguồn.

## Quy trình 5 giai đoạn

| # | Giai đoạn | Thư mục | Đầu ra chính | Trạng thái |
|---|---|---|---|---|
| 1 | Research & Discovery | [`docs/01-research`](docs/01-research) | Persona, journey, đối thủ, KPI, quyết định nền tảng | 🟡 Chờ duyệt |
| 2 | Design System & Prototype | [`docs/02-design`](docs/02-design) | `DESIGN.md`, design tokens, danh sách màn hình, luồng UX | ⚪ Chưa làm |
| 3 | Product Requirements | [`docs/03-product`](docs/03-product) | PRD, user stories + acceptance criteria, data model, Gemini contract, backlog | ⚪ Chưa làm |
| 4 | Vibe Code | [`docs/04-engineering`](docs/04-engineering) + `CLAUDE.md` + `.claude/` | Kiến trúc, quy ước code, skills, prompt từng sprint | ⚪ Chưa làm |
| 5 | Present Full Product | [`docs/05-delivery`](docs/05-delivery) | Test plan, Definition of Done, kịch bản demo, release notes | ⚪ Chưa làm |

Quy tắc chung của quy trình: xem [`docs/00-process/workflow.md`](docs/00-process/workflow.md).
Nhật ký quyết định: [`docs/00-process/decision-log.md`](docs/00-process/decision-log.md).

## Stack (đã chốt)

React + Vite + TypeScript · TailwindCSS + shadcn/ui · Firebase (Authentication, Cloud Firestore, Cloud Functions, Hosting) · Gemini API · Google Maps Platform (Maps JS, Places, Routes).

## Nhóm phát triển

| Thành viên | Vai trò |
|---|---|
| Phạm Mai Gia Huy | Project Manager / Product Owner |
| Nguyễn Danh Linh | Frontend / UI-UX |
| Nguyễn Đức Trọng | Backend / Database (Firebase) |
| Phạm Viết Hưng | AI / Integration (Gemini, Maps) |
| Phan Văn Nhật Hiếu | Testing / Documentation |

Tài liệu gốc của môn Quản trị dự án phần mềm (Scope, WBS, Delphi, MS Project) được dùng làm đầu vào cho giai đoạn 1.
