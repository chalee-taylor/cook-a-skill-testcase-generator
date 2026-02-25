# Skill Card — Test Case Generator

---

## Tên Skill
**Test Case Generator**

Tự động sinh test case từ file spec/PRD/BRS, phủ đầy đủ Happy Path, Negative, Edge Case và Security — đầu ra sẵn sàng dùng ngay.

---

## Việc gì được automate

QC/Tester nộp file spec (`.md`) → Skill đọc spec, phân tích logic nghiệp vụ, phát hiện edge case, sinh bộ test case đầy đủ theo chuẩn định sẵn, kèm Traceability Matrix và Test Report Template.

---

## TRƯỚC: làm tay

| Bước | Mô tả |
|------|-------|
| 1 | QC tự đọc spec — dò từng dòng để hiểu nghiệp vụ |
| 2 | Tự nghĩ ra các kịch bản: happy path, lỗi, biên |
| 3 | Gõ tay từng test case vào sheet/doc |
| 4 | Review lại để kiểm tra bỏ sót |
| 5 | Chỉnh format cho đúng chuẩn team |

**Thời gian:** 2–4 giờ / feature (feature phức tạp có thể lên 6–8 giờ)

**Rủi ro:**
- Dễ bỏ sót edge case, security case
- Mỗi QC viết một format khác nhau → khó review
- Phụ thuộc kinh nghiệm cá nhân

---

## SAU: có skill

| Bước | Mô tả |
|------|-------|
| 1 | QC paste nội dung spec vào Claude |
| 2 | Skill phân tích tự động: flow, business rule, edge case, security |
| 3 | Nhận ngay bộ test case đầy đủ (Markdown / JSON / CSV) |
| 4 | QC review nhanh và chỉnh sửa nhỏ nếu cần |

**Thời gian:** 15–30 phút / feature (chủ yếu là review đầu ra)

**Lợi ích:**
- Phủ đủ 4 loại: Happy Path, Negative, Edge Case, Security
- Format chuẩn nhất quán toàn team
- Traceability Matrix tự động — biết rule nào chưa có TC
- Không bỏ sót nhờ Edge Case Checklist 8 nhóm

---

## Tool / AI đã dùng

| Tool | Vai trò |
|------|---------|
| **Claude (Anthropic)** | Model AI chính — đọc spec, suy luận, sinh test case |
| **Claude Code** | Môi trường viết và kiểm thử SKILL.md, SPEC.md |
| **Markdown** | Định dạng spec đầu vào và test case đầu ra |
| **Git / GitHub** | Quản lý version, review qua Pull Request |

---

## Limitation

- Spec mơ hồ, thiếu user flow hoặc business rule → skill báo lỗi `WARN-001`, không sinh output
- Chỉ xử lý **1 feature mỗi lần** — spec đa feature cần tách trước
- Không sinh automation script (Selenium, Playwright, Postman)
- Không tích hợp trực tiếp với Jira, TestRail, hay bug tracker
- Không thực thi test — chỉ sinh test case để QC chạy tay
- Kết quả phụ thuộc chất lượng spec: garbage in → garbage out

---

## Roadmap mở rộng

| Ưu tiên | Tính năng |
|---------|-----------|
| 🔴 Cao | Phát hiện điểm mơ hồ trong spec và gợi ý bổ sung trước khi sinh TC |
| 🔴 Cao | Export trực tiếp sang Jira / TestRail qua API |
| 🟡 Trung bình | Sinh automation test skeleton (Playwright / Pytest) từ TC đã có |
| 🟡 Trung bình | Xử lý batch nhiều feature cùng lúc |
| 🟢 Thấp | Sinh test report tự động sau khi QC điền kết quả |
| 🟢 Thấp | Hỗ trợ spec viết bằng nhiều ngôn ngữ (EN / VI / JP) |
