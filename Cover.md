# Trang bìa — Test Plan

**Nguồn mẫu:** `FSOFT.Template_Test Plan.xlsx`, trang **Cover** (trang 1).

---

## Template

**TEST PLAN**

---

## Thông tin tài liệu

| Trường | Giá trị |
|--------|---------|
| **Document Code** | 148e-BM/DE/HDCV/FSOFT |
| **Version** | 1.0 |
| **Effective Date** | 15/04/2026 |

*Ghi chú: Mã và khung bìa theo biểu mẫu FSOFT; phiên bản 1.0 là phiên bản Test Plan áp dụng cho đồ án DATN.*

---

## Đối tượng kiểm thử (theo mã nguồn dự án)

**Tên hệ thống:** Nền tảng thương mại điện tử DATN (tham chiếu triển khai: `api.shoppie.live` trên client).

**Thành phần cần kiểm thử:**

| Thành phần | Mô tả ngắn |
|------------|------------|
| **DATN_api-main** | Backend **NestJS** (`ecom`), API REST, Swagger tại `/api`, xác thực JWT, phân quyền (role, permission), đa ngôn ngữ (i18n), giới hạn tần suất (throttler), WebSocket. **Prisma** + cơ sở dữ liệu. Tích hợp: **VNPay**, **Recurly**, **GHN** (giaohangnhanh), **AWS S3** (media), email, Redis/Bull (cấu trúc sẵn). Các miền nghiệp vụ: auth, user, profile, brand, category, product, cart, order, discount, review, seller request, audit, recommendation. |
| **DATN_web_client-main** | Ứng dụng web **Next.js 15** (`ecommerce-nextjs-app`), cổng **8000** khi dev, giao diện (Radix, Tailwind), i18n, Redux + React Query, CASL (quyền), tích hợp thanh toán/Recurly phía client, chat realtime (socket.io-client). |

**Phạm vi kiểm thử gợi ý trên bìa:** Kiểm thử tích hợp hệ thống gồm API, giao diện người dùng và luồng nghiệp vụ TMĐT (duyệt sản phẩm, giỏ hàng, đặt hàng, thanh toán, vận chuyển, đánh giá, quản trị/đăng ký bán hàng nếu có), cùng các yêu cầu phi chức năng liên quan (bảo mật truy cập, toàn vẹn dữ liệu, hiệu năng cơ bản theo kế hoạch chi tiết).

---

*Biểu mẫu Excel gốc dùng ô ngày dạng số serial (44757 ≈ 15/07/2022); tài liệu này dùng ngày hiệu lực đồ án như bảng trên.*
