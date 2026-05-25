# Intro2SE — Testing — YAG

---

## Mục lục

1. [Member Contribution Assessment](#1-member-contribution-assessment)
2. [Test Plan](#2-test-plan)
3. [Test Cases](#3-test-cases)
   - 3.1 [Danh sách Test Cases](#31-danh-sách-test-cases)
   - 3.2 [Test Case Specifications](#32-test-case-specifications)
     - TC-004: Register → JWT → Call Protected API
     - TC-005: Login Brute-Force Rate Limit
     - TC-014: VNPAY Checkout URL Generation
     - TC-015: VNPAY IPN Success → Premium Update
     - TC-023: WebSocket Autosave 5s Trigger
4. [AI Usage Declaration](#4-ai-usage-declaration)
5. [Presentation](#5-presentation)
6. [Reflective Report](#6-reflective-report)

---

## Objectives

Tài liệu này trình bày kế hoạch kiểm thử (Test Plan) và các đặc tả kiểm thử (Test Case Specifications) cho dự án **YAG** — nền tảng đọc và sáng tác truyện trực tuyến với tích hợp AI.

Tất cả các artifact dự án phải nhất quán và đồng bộ. Nếu tài liệu đề xuất được chỉnh sửa trong giai đoạn này, phiên bản mới phải được ghi lại. Đến cuối dự án, tất cả các phiên bản của mọi artifact cần được nộp để thể hiện sự phát triển của sản phẩm.

---

## 1. Member Contribution Assessment

### Phạm Hương Trà  **~20%**

> **Phụ trách:**  TC-001, TC-002, TC-003, TC-010, TC-011, Mục 4, Mục 6

**Bằng chứng công việc (Jira / Git):**

| Tên Task | Mô tả | Trạng thái |
|---|---|---|
| Write Test Plan | Soạn toàn bộ kế hoạch kiểm thử: phạm vi, kỹ thuật, đối tượng | Done |
| TC-001 Bcrypt Unit Test | Viết và chạy unit test hàm băm mật khẩu | Done |
| TC-002 VNPAY HMAC Unit Test | Viết unit test sinh chữ ký HMAC-SHA512 | Done |
| TC-003 pgvector Cosine Unit Test | Viết unit test độ chính xác cosine distance | Done |
| TC-010 AI Semantic Search E2E | Viết integration test tìm kiếm ngữ nghĩa AI | Done |
| TC-011 Miu AI Suggestion | Viết integration test gợi ý AI Miu Sidebar | Done |
| AI Usage Declaration | Tổng hợp khai báo sử dụng AI toàn nhóm | Done |
| Reflective Report | Tổng hợp báo cáo phản tư | Done |

*[Screenshot minh chứng: Jira board hiển thị Task Name, Assignee: Phạm Hương Trà, Status, Assigned Date, Completion Date]*

---

### Trần Gia Hiển  **~25%**

> **Phụ trách:** TC-004, TC-005, TC-006, TC-007, TC-008, TC-009, Mục 1 (phần cá nhân)

**Bằng chứng công việc (Jira / Git):**

| Tên Task | Mô tả | Trạng thái |
|---|---|---|
| TC-004 Register → JWT | Viết integration test luồng đăng ký → JWT → gọi API | Done |
| TC-005 Login Rate Limit | Viết security test brute-force đăng nhập | Done |
| TC-006 OTP Reset Flow | Viết integration test luồng reset mật khẩu OTP | Done |
| TC-007 Redis Cache Hit/Miss | Viết integration test cache chapter Redis | Done |
| TC-008 Bookmark + History | Viết integration test bookmark và lịch sử đọc | Done |
| TC-009 Avatar Upload | Viết integration test upload avatar Cloudinary | Done |

*[Screenshot minh chứng: Jira board hiển thị Task Name, Assignee: Trần Gia Hiển, Status, Assigned Date, Completion Date]*

---

### Nguyễn Duy Trường  **~20%**

> **Phụ trách:** TC-012, TC-013, TC-014, TC-015, TC-016, TC-017, Mục 1 (phần cá nhân)

**Bằng chứng công việc (Jira / Git):**

| Tên Task | Mô tả | Trạng thái |
|---|---|---|
| TC-012 Create Story + Cover | Viết integration test tạo truyện và upload cover | Done |
| TC-013 RBAC Premium 403 | Viết security test RBAC chapter premium hết hạn | Done |
| TC-014 VNPAY Checkout URL | Viết integration test tạo URL thanh toán | Done |
| TC-015 VNPAY IPN Success | Viết integration test xác thực IPN + cấp Premium | Done |
| TC-016 vnp_txn_ref Unique | Viết unit test sinh mã giao dịch không trùng lặp | Done |
| TC-017 VNPAY Invalid Checksum | Viết security test từ chối IPN sai checksum | Done |

*[Screenshot minh chứng: Jira board hiển thị Task Name, Assignee: Nguyễn Duy Trường, Status, Assigned Date, Completion Date]*

---

### Nguyễn Phú Thọ  **~20%**

> **Phụ trách:** TC-018, TC-019, TC-020, TC-021, TC-022, Mục 1 (phần cá nhân), Mục 5

**Bằng chứng công việc (Jira / Git):**

| Tên Task | Mô tả | Trạng thái |
|---|---|---|
| TC-018 Publish → RabbitMQ → Worker | Viết integration test luồng xuất bản qua message queue | Done |
| TC-019 AI Content Flag | Viết integration test worker AI phát hiện vi phạm | Done |
| TC-020 Cron Reputation | Viết integration test cron trừ điểm reputation trễ lịch | Done |
| TC-021 Admin API Reject Reader | Viết security test JWT role check Admin API | Done |
| TC-022 CI/CD Auto Test | Viết integration test pipeline lint + pytest tự động | Done |
| Upload Presentation Video | Quay, biên tập, upload video YouTube | Done |

*[Screenshot minh chứng: Jira board hiển thị Task Name, Assignee: Nguyễn Phú Thọ, Status, Assigned Date, Completion Date]*

---

### Huỳnh Yến Nhi  **~15%**

> **Phụ trách:** TC-023, TC-024, TC-025, TC-026, TC-027, TC-028, Mục 1 (phần cá nhân)

**Bằng chứng công việc (Jira / Git):**

| Tên Task | Mô tả | Trạng thái |
|---|---|---|
| TC-023 WebSocket Autosave | Viết integration test autosave dừng 5s → DB update | Done |
| TC-024 Comment Real-time | Viết integration test broadcast bình luận WebSocket | Done |
| TC-025 Responsive Mobile | Usability test responsive <768px (5 trang core) | Done |
| TC-026 Responsive Tablet | Usability test responsive 768–1023px | Done |
| TC-027 A11y Color Contrast | Accessibility test tương phản màu 3 chế độ đọc | Done |
| TC-028 Cross-browser | Compatibility test Chrome/Edge/Firefox/Safari | Done |

*[Screenshot minh chứng: Jira board hiển thị Task Name, Assignee: Huỳnh Yến Nhi, Status, Assigned Date, Completion Date]*

> **Ghi chú:** Tổng đóng góp = 100%. Mỗi task được giao và hoàn thành bởi đúng một thành viên.

---

## 2. Test Plan

**Written by:** [MSSV] Trần Gia Hiển
**Edited by:** [MSSV] Phạm Hương Trà
**Reviewed by:** [MSSV] Huỳnh Yến Nhi

---

### 2.1 Phạm vi kiểm thử (Scope)

Dự án YAG là nền tảng đọc và sáng tác truyện với các tính năng cốt lõi: xác thực người dùng, thanh toán Premium (VNPAY), AI gợi ý nội dung và tìm kiếm ngữ nghĩa, xuất bản và kiểm duyệt nội dung tự động, WebSocket real-time và giao diện responsive.

**Trong phạm vi kiểm thử:**
- Toàn bộ API backend (FastAPI): xác thực, thanh toán, AI engine, RBAC
- Frontend (Next.js): 5 trang core, responsive, accessibility
- Luồng async: RabbitMQ, Celery worker, cron job
- Bảo mật: JWT, RBAC, rate limit, checksum validation
- Tích hợp hệ thống: Redis, Cloudinary, VNPAY IPN, Gemini API

**Ngoài phạm vi:**
- Kiểm thử hiệu năng tải cao (load testing)
- Kiểm thử thâm nhập chuyên sâu (penetration testing)
- Các dịch vụ bên thứ ba ngoài môi trường sandbox

---

### 2.2 Kỹ thuật kiểm thử (Testing Techniques)

| Kỹ thuật | Áp dụng trên | Công cụ |
|---|---|---|
| **Unit Testing** | Hàm băm Bcrypt, sinh chữ ký HMAC-SHA512, tính khoảng cách cosine pgvector, sinh vnp_txn_ref | `pytest`, `unittest.mock` |
| **Integration Testing** | Luồng API end-to-end, Redis cache, VNPAY IPN, RabbitMQ → Worker, WebSocket autosave | `pytest`, `httpx`, `TestClient (FastAPI)` |
| **Security Testing** | JWT authentication, RBAC, rate limiting, checksum validation, Admin access control | `pytest`, `httpx`, Postman |
| **Usability Testing** | Responsive layout Mobile <768px và Tablet 768–1023px, 5 trang core | Browser DevTools, manual |
| **Accessibility Testing** | Tương phản màu sắc chế độ Light/Dark/Sepia (WCAG 2.1 AA) | Lighthouse, axe DevTools |
| **Compatibility Testing** | Cross-browser: Chrome, Edge, Firefox, Safari | BrowserStack / manual |

---

### 2.3 Đối tượng kiểm thử (Test Objects)

**Functions / Modules:**
- `auth.utils.hash_password()` — Bcrypt rounds=12
- `payment.utils.generate_hmac_signature()` — VNPAY HMAC-SHA512
- `ai.search.compute_cosine_distance()` — pgvector
- `payment.utils.generate_txn_ref()` — unique transaction ID
- `auth.middleware.rate_limiter()` — Redis sliding window

**API Endpoints:**
- `POST /api/v1/auth/register` và `/login`
- `GET /api/v1/chapters/{chapter_id}` (Redis cache + RBAC)
- `POST /api/v1/payment/vnpay/checkout`
- `POST /api/v1/payment/vnpay/ipn`
- `POST /api/v1/stories/{id}/publish`
- `WS /ws/editor/{story_id}` (WebSocket autosave)

**Documents / Tài liệu:**
- SRS — kiểm tra các use case được triển khai đúng yêu cầu
- API specification — kiểm tra response schema đúng contract

---

### 2.4 Môi trường kiểm thử

- **Backend:** FastAPI + PostgreSQL + Redis chạy local Docker Compose
- **VNPAY:** Sandbox environment (vnpayment.vn/sandbox)
- **AI:** Gemini API key dev, pgvector extension trên PostgreSQL 15
- **CI/CD:** GitHub Actions chạy pytest tự động khi push

---

### 2.5 Tiêu chí hoàn thành (Exit Criteria)

- Tất cả 28 test case được thực thi
- Tỷ lệ pass ≥ 95% (cho phép tối đa 1 lỗi mức Medium, không chấp nhận lỗi Critical)
- Mọi test case Critical (TC-001 → TC-005, TC-010, TC-013÷015, TC-017÷019, TC-021, TC-023) phải **Passed**

---

## 3. Test Cases

### 3.1 Danh sách Test Cases

**Written by:** [MSSV] Phạm Hương Trà  
**Edited by:** [MSSV] Trần Gia Hiển  
**Reviewed by:** [MSSV] Nguyễn Phú Thọ

> Nhóm tập trung viết test spec chi tiết cho **5 tính năng quan trọng nhất**: U001 Đăng ký/Đăng nhập, U012 Thanh toán VNPAY, U013 Kiểm duyệt AI, U007 Đọc truyện & RBAC Premium, U004 WebSocket Autosave.

| Seq | Test Case | Feature | Loại | Ưu tiên | Người viết |
|---|---|---|---|---|---|
| 1 | TC-001: Bcrypt hash password | U001 Auth | Unit | Critical | Hương Trà |
| 2 | TC-002: VNPAY HMAC-SHA512 signature | U012 Payment | Unit | Critical | Hương Trà |
| 3 | TC-003: pgvector Cosine distance accuracy | U008 AI Search | Unit | Critical | Hương Trà |
| 4 | TC-004: Register → JWT → Call protected API | U001 | Integration | Critical | Gia Hiển |
| 5 | TC-005: Login brute-force rate limit | U001 Security | Security | Critical | Gia Hiển |
| 6 | TC-006: OTP password reset flow | U001 | Integration | High | Gia Hiển |
| 7 | TC-007: Redis chapter cache hit/miss | U007 | Integration | High | Gia Hiển |
| 8 | TC-008: Bookmark + reading history update | U007 | Integration | Medium | Gia Hiển |
| 9 | TC-009: Avatar upload validation + Cloudinary | U002 | Integration | High | Gia Hiển |
| 10 | TC-010: AI semantic search end-to-end | U008 | Integration | Critical | Hương Trà |
| 11 | TC-011: Miu AI suggestion 3 options JSON | U006 | Integration | High | Hương Trà |
| 12 | TC-012: Create story + cover upload | U003 | Integration | High | Duy Trường |
| 13 | TC-013: RBAC premium chapter 403 expired | U011 | Security | Critical | Duy Trường |
| 14 | TC-014: VNPAY checkout URL generation | U012 | Integration | Critical | Duy Trường |
| 15 | TC-015: VNPAY IPN success → premium_until update | U012 | Integration | Critical | Duy Trường |
| 16 | TC-016: vnp_txn_ref uniqueness | U012 | Unit | High | Duy Trường |
| 17 | TC-017: VNPAY IPN invalid checksum → reject | U012 Security | Security | Critical | Duy Trường |
| 18 | TC-018: Publish → RabbitMQ → Worker → Approved | U005 + U013 | Integration | Critical | Phú Thọ |
| 19 | TC-019: Worker AI flags violating content | U013 | Integration | Critical | Phú Thọ |
| 20 | TC-020: Cron trừ reputation khi trễ lịch | U014 | Integration | High | Phú Thọ |
| 21 | TC-021: Admin API reject reader JWT | U015 Security | Security | Critical | Phú Thọ |
| 22 | TC-022: CI/CD lint + pytest auto-block on fail | DevOps | Integration | High | Phú Thọ |
| 23 | TC-023: WebSocket autosave 5s trigger | U004 | Integration | Critical | Yến Nhi |
| 24 | TC-024: Comment broadcast real-time | U010 | Integration | High | Yến Nhi |
| 25 | TC-025: Responsive Mobile <768px (5 core pages) | Frontend | Usability | High | Yến Nhi |
| 26 | TC-026: Responsive Tablet 768–1023px | Frontend | Usability | Medium | Yến Nhi |
| 27 | TC-027: A11y color contrast Light/Dark/Sepia | S07 Reader | Accessibility | High | Yến Nhi |
| 28 | TC-028: Cross-browser compatibility 4 browsers | Frontend | Compatibility | High | Yến Nhi |

---

### 3.2 Test Case Specifications

> Phần dưới đây trình bày spec chi tiết cho **5 test case đại diện cho 5 tính năng Critical nhất**.

---

#### TC-004: Register → JWT → Call Protected API

**Written by:** [MSSV] Trần Gia Hiển  
**Edited by:** [MSSV] Phạm Hương Trà  
**Reviewed by:** [MSSV] Nguyễn Duy Trường

| Test Case | TC-004 |
|---|---|
| **Related feature** | U001 — Đăng ký / Đăng nhập |
| **Context** | Người dùng mới thực hiện đăng ký tài khoản, nhận JWT access token và dùng token đó để gọi một API yêu cầu xác thực |
| **Input Data** | `POST /api/v1/auth/register` body: `{ "username": "testuser_tc004", "email": "tc004@yag.dev", "password": "P@ssw0rd!123" }` |
| **Expected Output** | 1. Register trả về HTTP 201, body chứa `access_token` (JWT) và `token_type: "bearer"` <br> 2. Decode JWT: payload chứa `user_id`, `username`, `role: "reader"` <br> 3. `GET /api/v1/profiles/me` với header `Authorization: Bearer <token>` trả về HTTP 200 và thông tin profile đúng với user vừa tạo |
| **Test steps** | 1. Gửi `POST /api/v1/auth/register` với body trên <br> 2. Xác nhận response status = 201 <br> 3. Lấy `access_token` từ response body <br> 4. Decode JWT, kiểm tra payload fields <br> 5. Gửi `GET /api/v1/profiles/me` với header Bearer token <br> 6. Xác nhận status = 200 và `email` trùng khớp |
| **Actual Output** | *(điền sau khi chạy)* |
| **Result** | Passed / Failed |

---

#### TC-005: Login Brute-Force Rate Limit

**Written by:** [MSSV] Trần Gia Hiển  
**Edited by:** [MSSV] Phạm Hương Trà  
**Reviewed by:** [MSSV] Nguyễn Phú Thọ

| Test Case | TC-005 |
|---|---|
| **Related feature** | U001 — Bảo mật đăng nhập |
| **Context** | Kẻ tấn công gửi nhiều lần đăng nhập sai liên tiếp vào cùng một tài khoản; hệ thống phải kích hoạt rate limiting để ngăn brute-force |
| **Input Data** | `POST /api/v1/auth/login` body: `{ "email": "target@yag.dev", "password": "WrongPass!" }` — gửi lặp lại 6 lần liên tiếp trong vòng 60 giây |
| **Expected Output** | 1. Các lần 1–5: HTTP 401 với message `"Invalid credentials"` <br> 2. Lần thứ 6 trở đi: HTTP 429 `"Too many login attempts. Please try again later."` <br> 3. Sau 60 giây: tài khoản tự động mở khóa, đăng nhập đúng mật khẩu trả về HTTP 200 |
| **Test steps** | 1. Tạo user `target@yag.dev` trong DB <br> 2. Gửi 5 request đăng nhập sai → kiểm tra từng response trả về 401 <br> 3. Gửi request thứ 6 → kiểm tra response trả về 429 <br> 4. Chờ 61 giây <br> 5. Gửi request đăng nhập đúng mật khẩu → kiểm tra response 200 |
| **Actual Output** | *(điền sau khi chạy)* |
| **Result** | Passed / Failed |

---

#### TC-014: VNPAY Checkout URL Generation

**Written by:** [MSSV] Nguyễn Duy Trường  
**Edited by:** [MSSV] Phạm Hương Trà  
**Reviewed by:** [MSSV] Trần Gia Hiển

| Test Case | TC-014 |
|---|---|
| **Related feature** | U012 — Thanh toán VNPAY |
| **Context** | Reader đã đăng nhập thực hiện checkout gói Premium 1 tháng (99.000 VNĐ); hệ thống phải sinh URL thanh toán VNPAY hợp lệ |
| **Input Data** | `POST /api/v1/payment/vnpay/checkout` header: `Authorization: Bearer <reader_jwt>` body: `{ "package": "premium_1m", "amount": 99000, "bank_code": "NCB" }` |
| **Expected Output** | 1. HTTP 200 với body chứa `payment_url` (URL bắt đầu bằng `https://sandbox.vnpayment.vn/paymentv2/vpcpay.html?`) <br> 2. URL chứa tham số: `vnp_Amount=9900000`, `vnp_CurrCode=VND`, `vnp_TmnCode=<configured_tmn_code>`, `vnp_SecureHash` hợp lệ (HMAC-SHA512) <br> 3. `vnp_TxnRef` là duy nhất, được lưu vào DB với trạng thái `pending` |
| **Test steps** | 1. Đăng nhập với tài khoản reader, lấy JWT <br> 2. Gửi POST checkout với body trên <br> 3. Kiểm tra status = 200 <br> 4. Parse `payment_url` từ response <br> 5. Xác minh URL domain là VNPAY sandbox <br> 6. Decode các query params, kiểm tra `vnp_Amount`, `vnp_CurrCode` <br> 7. Tính lại HMAC-SHA512 phía test → so sánh với `vnp_SecureHash` <br> 8. Query DB kiểm tra `vnp_TxnRef` tồn tại với status `pending` |
| **Actual Output** | *(điền sau khi chạy)* |
| **Result** | Passed / Failed |

---

#### TC-015: VNPAY IPN Success → Premium Update

**Written by:** [MSSV] Nguyễn Duy Trường  
**Edited by:** [MSSV] Phạm Hương Trà  
**Reviewed by:** [MSSV] Trần Gia Hiển

| Test Case | TC-015 |
|---|---|
| **Related feature** | U012 — Xử lý IPN callback VNPAY |
| **Context** | Sau khi người dùng thanh toán thành công, VNPAY gửi IPN callback đến server; hệ thống phải xác thực chữ ký, cập nhật trạng thái giao dịch và cấp quyền Premium cho user |
| **Input Data** | `POST /api/v1/payment/vnpay/ipn` — payload IPN hợp lệ từ VNPAY sandbox, `vnp_ResponseCode=00`, `vnp_TransactionStatus=00`, `vnp_SecureHash` được tính đúng bằng HMAC-SHA512 với secret key test |
| **Expected Output** | 1. HTTP 200 với body `{ "RspCode": "00", "Message": "Confirm Success" }` <br> 2. DB: record transaction với `vnp_TxnRef` cập nhật `status = "success"` <br> 3. DB: `users.premium_until` của user tương ứng được set = `NOW() + 30 days` <br> 4. Không gửi IPN response thứ hai nếu gọi lại cùng `vnp_TxnRef` (idempotent) |
| **Test steps** | 1. Chuẩn bị: tạo transaction `pending` trong DB với `vnp_TxnRef = "YAG_TC015_001"` <br> 2. Tính `vnp_SecureHash` hợp lệ cho payload IPN success <br> 3. Gửi POST IPN với payload đã ký <br> 4. Kiểm tra response = `{ "RspCode": "00", "Message": "Confirm Success" }` <br> 5. Query DB: `transactions` status = `success` <br> 6. Query DB: `users.premium_until` > `NOW()` <br> 7. Gửi lại cùng IPN → kiểm tra response `RspCode: "02"` (already confirmed) |
| **Actual Output** | *(điền sau khi chạy)* |
| **Result** | Passed / Failed |

---

#### TC-023: WebSocket Autosave 5s Trigger

**Written by:** [MSSV] Huỳnh Yến Nhi  
**Edited by:** [MSSV] Phạm Hương Trà  
**Reviewed by:** [MSSV] Trần Gia Hiển

| Test Case | TC-023 |
|---|---|
| **Related feature** | U004 — Soạn thảo WebSocket Autosave |
| **Context** | Tác giả đang soạn chương truyện; sau khi ngừng gõ 5 giây, hệ thống phải tự động lưu nội dung vào DB qua WebSocket |
| **Input Data** | Kết nối WebSocket tới `ws://localhost:8000/ws/editor/{story_id}` với JWT author hợp lệ. Gửi message: `{ "type": "content_update", "content": "Nội dung chương TC-023", "chapter_id": "<chapter_id>" }`. Sau đó **không** gửi thêm message trong 5 giây. |
| **Expected Output** | 1. Kết nối WebSocket thành công (HTTP 101 Switching Protocols) <br> 2. Sau 5 giây không có input: server gửi message `{ "type": "autosave_confirm", "status": "saved", "saved_at": "<timestamp>" }` <br> 3. DB: bảng `chapters` cập nhật `content = "Nội dung chương TC-023"` và `updated_at` trong khoảng 5–6 giây sau khi gửi |
| **Test steps** | 1. Tạo chapter draft trong DB <br> 2. Kết nối WebSocket với JWT author <br> 3. Ghi lại timestamp T0 <br> 4. Gửi `content_update` message <br> 5. Không gửi thêm gì, chờ tối đa 7 giây <br> 6. Nhận và xác nhận message `autosave_confirm` từ server <br> 7. Query DB kiểm tra `content` và `updated_at` trong khoảng [T0+4s, T0+6s] |
| **Actual Output** | *(điền sau khi chạy)* |
| **Result** | Passed / Failed |

---

## 4. AI Usage Declaration

**Written by:** [MSSV] Trần Gia Hiển (tổng hợp)

*Tuân theo AI Usage Guideline của môn học. Nhóm YAG khai báo việc sử dụng AI trong giai đoạn Testing như sau:*

| Công cụ AI | Mục đích sử dụng | Thành viên | Ghi chú |
|---|---|---|---|
| GitHub Copilot | Sinh boilerplate pytest fixtures, mock objects | Gia Hiển, Phú Thọ | Review thủ công toàn bộ code sinh ra |
| ChatGPT / Claude | Hỗ trợ soạn thảo mô tả test case, kiểm tra logic test steps | Hương Trà | Không dùng để viết code test trực tiếp |
| Gemini (project) | Tính năng AI Miu Sidebar (U006) — là đối tượng kiểm thử, không phải công cụ hỗ trợ viết doc | Hương Trà | Dùng trong môi trường sandbox |

*Toàn bộ test logic, expected output và phân tích kết quả được xác nhận bởi thành viên phụ trách. AI không được dùng để tạo ra kết quả kiểm thử (actual output) hay bỏ qua bước thực thi thực tế.*

---

## 5. Presentation

Nhóm đã ghi hình video thuyết trình theo template được cung cấp. Mỗi thành viên trình bày phần mình đóng góp. Thời lượng video không vượt quá 30 phút.

| Thành viên | Phần trình bày |
|---|---|
| Phạm Hương Trà | Test Plan (Mục 2) + Tổng quan Test Cases |
| Trần Gia Hiển | TC-004, TC-005 (Auth testing) |
| Nguyễn Duy Trường | TC-014, TC-015 (Payment testing) |
| Nguyễn Phú Thọ | TC-018, TC-019 (Async/DevOps testing) |
| Huỳnh Yến Nhi | TC-023, TC-025–028 (WebSocket & Frontend testing) |

**YouTube Link:** *(điền link sau khi upload — Unlisted hoặc Public)*

---

## 6. Reflective Report

**Written by:** [MSSV] Trần Gia Hiển (tổng hợp ý kiến nhóm)

**Các mục hữu ích nhất:**

- **Mục 2 — Test Plan:** Buộc nhóm phải thống nhất phạm vi kiểm thử và lựa chọn kỹ thuật trước khi viết code test. Điều này giúp tránh việc mỗi người kiểm thử theo hướng khác nhau. Ví dụ cụ thể: nhờ xác định rõ "Security Testing" là một kỹ thuật riêng, nhóm đã phát hiện TC-017 (VNPAY invalid checksum) là test case quan trọng nhưng dễ bị bỏ sót nếu chỉ tập trung vào integration test.

- **Mục 3.2 — Test Case Specifications:** Bảng format chuẩn (Context, Input Data, Expected Output, Test Steps) rất có giá trị. Khi điền "Expected Output" trước khi chạy test, nhóm buộc phải hiểu rõ contract của API thay vì chỉ chạy rồi xem kết quả.

**Các mục ít cần thiết hơn (trong ngữ cảnh dự án này):**

- **Mục 3.1 — Danh sách test cases dạng bảng:** Khi đã có Mục 3.2 với spec chi tiết, bảng tổng hợp ở 3.1 tạo ra sự trùng lặp thông tin. Đề xuất: giữ bảng 3.1 như một "index" nhanh, không cần cột Description vì thông tin này đã có trong 3.2.

- **Phần "Edited by / Reviewed by" lặp ở mỗi section:** Với dự án 5 người, mỗi section có 3 trường author/editor/reviewer gây overhead. Trong thực tế nhóm dùng Git commit history để truy vết chỉnh sửa hiệu quả hơn.