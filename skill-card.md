# Skill Card (1 trang) — testcase-generator

| Mục | Nội dung |
|---|---|
| Tên Skill | `testcase-generator` (v1.1.0) |
| Việc gì được automate | Tự động chuyển `spec_content` (PRD/BRS/User Story) thành bộ test case chuẩn gồm Happy Path, Negative, Edge Case, Security; có Intelligence Scan Report, Traceability Matrix, và hỗ trợ output `markdown/json/csv`. |
| TRƯỚC: làm tay | QC đọc spec thủ công, tự suy luận flow + business rule, tự viết từng TC, rồi tự rà soát thiếu sót/format. Thời gian thường **2–4 giờ/feature** (có thể **6–8 giờ** với feature phức tạp). |
| SAU: có skill | Skill tự validate input/spec, parse rule/flow, quét rủi ro, sinh TC theo coverage (`basic/standard/full`) và xuất định dạng mong muốn; QC chủ yếu review/chỉnh nhẹ. Thời gian còn **15–30 phút/feature**. |

| Mục | Nội dung |
|---|---|
| Tool/AI đã dùng | Claude/Claude Code (phân tích và sinh TC), Markdown/JSON/CSV (định dạng output), Git/GitHub (quản lý version & review). |
| Limitation | Nếu spec thiếu chất lượng (không có flow hoặc business rule/validation), skill dừng với `WARN-001`; chỉ tạo test case (không execute test); chưa push trực tiếp Jira/TestRail mặc định; spec nhiều feature nên tách nhỏ để kết quả rõ hơn. |
| Roadmap mở rộng | (1) Phát hiện mơ hồ trong spec và gợi ý sửa trước khi sinh TC; (2) Export/integration Jira-TestRail qua API; (3) Sinh skeleton automation từ TC (Playwright/Pytest); (4) Batch nhiều feature; (5) Tối ưu template đa ngôn ngữ. |
