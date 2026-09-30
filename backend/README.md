# Backend Architecture Plan — Vũ Đức Nam (ducnamdev)

Thư mục này được quy hoạch sẵn cho việc phát triển hệ thống Backend trong tương lai khi bạn cần kết nối API thực tế.

---

## 1. Định Hướng Công Nghệ Đề Xuất
* **Framework:** ASP.NET Core Web API (.NET 9) hoặc Python Flask / FastAPI
* **Database:** Microsoft SQL Server / PostgreSQL
* **ORM:** Entity Framework Core
* **Security & Auth:** JWT Bearer Authentication, Rate Limiting, CORS Policy cho `localhost` và domain production

---

## 2. Các Modules & Endpoints Dự Kiến (Tương thích với Frontend)

### A. Posts Module (Quản lý bài viết Blog)
* `GET /api/posts`: Lấy danh sách bài viết (hỗ trợ phân trang, lọc theo tags: C#, Python, Security, System)
* `GET /api/posts/{slug}`: Lấy chi tiết bài viết (nội dung Markdown, thời gian đọc)
* `PATCH /api/posts/{id}/like`: Tăng lượt tim / tương tác
* `POST /api/posts/{id}/comments`: Bình luận thảo luận dưới bài viết

### B. Contact & Messages Module
* `POST /api/contact`: Tiếp nhận tin nhắn từ biểu mẫu liên hệ của nhà tuyển dụng hoặc khách truy cập
* `GET /api/directchat/sessions`: Phiên đàm thoại thời gian thực (nếu tích hợp lại SignalR)

### C. System Config & Analytics
* `GET /api/config`: Cung cấp thông tin cấu hình động cho Frontend
* `GET /api/analytics/views`: Thống kê số lượng lượt xem và truy cập website

---

## 3. Cách Bắt Đầu Khi Bạn Sẵn Sàng
```bash
# Khởi tạo Web API với .NET 9
dotnet new webapi -n DucNamDev.Api
cd DucNamDev.Api

# Cài đặt các package cần thiết
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```
