---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---



### Mục tiêu tuần 11:
* Đảm bảo tính ổn định của ứng dụng đã deploy và kiểm thử kỹ lưỡng link demo frontend public.
* Giám sát và xác minh (verify) luồng kết nối xuyên suốt giữa frontend, backend, database và storage thành một hệ thống hoàn chỉnh.
* Hỗ trợ quá trình chuyển đổi lưu trữ tài nguyên sản phẩm từ ổ đĩa local EC2 sang Amazon S3 (sử dụng IAM Role).
* Thực hiện debug và kiểm thử end-to-end (E2E) các lỗi xác thực (auth), quyền quản trị (admin), tải/preview file sản phẩm và quyền truy cập S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Hỗ trợ kiểm thử link demo React/Vite trên Vercel; rà soát và báo cáo lỗi SPA routing (các route `/login`, `/products`).<br>- Verify cấu hình Vercel rewrites: đảm bảo các request `/api/*` và `/webhook/*` trỏ đúng về EC2 backend mà không bị lỗi mixed content. | 29/06/2026 | 29/06/2026 | https://vercel.com/docs/rewrites |
| 3 | - Kiểm tra frontend bundle trên production để đảm bảo không còn API nào gọi nhầm vào `localhost:3000` (đã chuyển sang relative path).<br>- Hỗ trợ verify quyền của IAM Role gắn trên EC2, đảm bảo quyền S3 được giới hạn chặt chẽ ở prefix `products/*` trong bucket `marketplace-frontend-thao`. | 30/06/2026 | 30/06/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html |
| 4 | - Test thử các lệnh AWS CLI trực tiếp trên EC2 để xác nhận quyền thao tác với S3 (PutObject, ListBucket, DeleteObject) hoạt động đúng.<br>- Chạy kịch bản kiểm thử (QA) cho luồng upload, stream, preview và download file sau khi backend refactor sang dùng memoryStorage và `@aws-sdk/client-s3`. | 01/07/2026 | 01/07/2026 | https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/ |
| 5 | - Rà soát tính toàn vẹn của dữ liệu sau khi team đồng bộ (sync) các file sản phẩm cũ từ EC2 lên S3.<br>- Kiểm thử thực tế các tính năng: hiển thị thumbnail, preview/download tài liệu và 3D model qua API.<br>- Tham gia debug và hỗ trợ xử lý lỗi download ở màn hình lịch sử mua hàng (sử dụng lại library download service). | 02/07/2026 | 02/07/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html |
| 6 | - Kiểm thử UI quản lý danh mục (category) phía admin, đảm bảo hỗ trợ tốt các nhóm `DOCUMENT` và `MODEL_3D`.<br>- Cùng team rà soát lại Sơ đồ kiến trúc, đảm bảo mô tả chính xác kiến trúc hiện tại (dùng Vercel làm frontend hosting và S3 làm nơi lưu product assets). | 03/07/2026 | 03/07/2026 | https://aws.amazon.com/architecture/ |

### Kết quả đạt được tuần 11:
* Xác nhận hệ thống demo cloud (Frontend Vercel, Backend EC2, RDS PostgreSQL, S3) đã kết nối thành công và hoạt động trơn tru.
* Đã test và verify luồng upload sản phẩm mới: file được lưu chuẩn xác vào `s3://marketplace-frontend-thao/products/` thay vì lưu trên ổ cứng EC2.
* Luồng kiểm tra quyền sở hữu (ownership) của backend hoạt động tốt trước khi stream file trả phí; bucket S3 vẫn được giữ an toàn ở chế độ private.
* Tính năng hiển thị thumbnail, preview/download tài liệu và 3D preview vượt qua các bài test và hoạt động ổn định trên nền tảng S3.
* Đảm bảo hệ thống tuân thủ bảo mật: IAM Role hoạt động hiệu quả từ EC2 mà không cần lưu trữ AWS access key dài hạn trong file `.env`.
