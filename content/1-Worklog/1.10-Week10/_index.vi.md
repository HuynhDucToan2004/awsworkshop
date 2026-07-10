---
title: "Worklog Tuần 10"
date: 2026-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


### Mục tiêu tuần 10:
* Đảm bảo tính ổn định của các chức năng cốt lõi (Auth, Product, Library, Purchase) trước khi deploy.
* Hỗ trợ kiểm thử nghiệm thu (UAT) trên các luồng nghiệp vụ thực tế (Buyer/Admin/Seller).
* Hỗ trợ cấu hình và kiểm thử hạ tầng Cloud (EC2, RDS, S3, IAM) để đảm bảo hệ thống vận hành đúng sơ đồ kiến trúc.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Rà soát toàn diện các chức năng cốt lõi: Auth, product listing, search, admin dashboard. <br>- Lập danh sách các lỗi tiềm ẩn cần ổn định trước khi đưa lên môi trường cloud. | 22/06/2026 | 22/06/2026 |  |
| 3 | - Kiểm thử User Flow: buyer đăng ký/đăng nhập, mua hàng, xem lịch sử mua hàng. <br>- Hỗ trợ debug lỗi tải file lịch sử mua hàng và 3D preview. | 23/06/2026 | 23/06/2026 |  |
| 4 | - Kiểm thử Admin/Seller flow (category, product management). <br>- Hỗ trợ team chạy seed-required.js an toàn; gán role admin qua SQL để verify quyền quản trị. | 24/06/2026 | 24/06/2026 | |
| 5 | - Hỗ trợ Backend triển khai lên EC2; verify kết nối private giữa EC2 và RDS PostgreSQL. <br>- Hỗ trợ debug lỗi SSL khi kết nối Prisma với RDS. | 25/06/2026 | 25/06/2026 | https://docs.aws.amazon.com/rds/ |
| 6 | - Test phân quyền S3 qua IAM Role (least privilege). <br>- Kiểm thử luồng upload/stream file sản phẩm từ S3, đảm bảo backend đọc dữ liệu an toàn. | 26/06/2026 | 26/06/2026 | https://docs.aws.amazon.com/s3/ |

### Kết quả đạt được:
* Hệ thống đạt trạng thái MVP, sẵn sàng cho demo: Frontend chạy ổn định trên Vercel, Backend vận hành trên EC2 với PM2.
* Dữ liệu đã chuyển sang Amazon RDS PostgreSQL và file sản phẩm được quản lý an toàn trên Amazon S3 với IAM Role được cấu hình chuẩn.
* Hỗ trợ team fix thành công nhiều lỗi nghiêm trọng: Lỗi SSL Prisma-RDS, lỗi 404 trên Vercel, các vấn đề về phân quyền Admin/API Proxy và đồng bộ dữ liệu S3.
* Đã ghi nhận hướng xử lý soft-delete cho sản phẩm (thay cho hard-delete) để đảm bảo toàn vẹn dữ liệu đơn hàng.
* Đề xuất các bước tiếp theo: Cấu hình CloudWatch Logs, bảo mật thông tin với SSM Parameter Store và tối ưu frontend với CloudFront.

