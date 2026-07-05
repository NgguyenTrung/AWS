---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}}

{{% /notice %}}


### Mục tiêu tuần 6:

* Tìm hiểu dịch vụ Amazon RDS for PostgreSQL và vai trò của cơ sở dữ liệu quan hệ trên AWS.
* Hiểu quy trình tạo, cấu hình và quản lý một PostgreSQL database trên Amazon RDS.
* Tìm hiểu các phương pháp sao lưu và khôi phục dữ liệu trên Amazon RDS.
* Hiểu các cơ chế đảm bảo tính sẵn sàng cao và khôi phục sau thảm họa.
* Thực hành gán IAM Role cho Amazon EC2 để truy cập tài nguyên AWS an toàn.


### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Học nội dung **RDS PostgreSQL on AWS – Introduction**. <br> - Tìm hiểu khái niệm và vai trò của Amazon Relational Database Service. <br> - Tìm hiểu cách Amazon RDS hỗ trợ PostgreSQL. <br> - Tìm hiểu các thành phần cơ bản như DB Instance, DB Engine, Storage và Endpoint. <br> - Tìm hiểu các bước tạo và kết nối đến một PostgreSQL database trên Amazon RDS. | 25/05/2026 | 25/05/2026 | <https://www.youtube.com/@AWSStudyGroup> |
| 3 | - Học nội dung **RDS PostgreSQL on AWS – Backup and Restore**. <br> - Tìm hiểu cơ chế Automated Backup và Manual Snapshot. <br> - Tìm hiểu thời gian lưu giữ bản sao lưu. <br> - Tìm hiểu chức năng Point-in-Time Recovery. <br> - Tìm hiểu cách khôi phục một DB Instance từ Snapshot hoặc bản sao lưu tự động. | 26/05/2026 | 26/05/2026 | <https://www.youtube.com/@AWSStudyGroup> |
| 4 | - Học nội dung **RDS PostgreSQL on AWS – High Availability and Disaster Recovery**. <br> - Tìm hiểu kiến trúc Multi-AZ Deployment. <br> - Tìm hiểu cơ chế đồng bộ dữ liệu và tự động chuyển đổi dự phòng. <br> - Tìm hiểu Read Replica và trường hợp sử dụng. <br> - Phân biệt High Availability với Disaster Recovery. | 27/05/2026 | 27/05/2026 | <https://www.youtube.com/@AWSStudyGroup> |
| 5 | - Làm bài lab **Encryption with AWS Key Management Service (KMS)**. <br> - Thực hành tạo và quản lý khóa mã hóa bằng AWS KMS. <br> - Tìm hiểu AWS managed keys và customer managed keys. <br> - Thực hành mã hóa và giải mã dữ liệu. <br> - Tìm hiểu Key Policy và quyền sử dụng khóa mã hóa. | 28/05/2026 | 28/05/2026 | <https://www.youtube.com/@AWSStudyGroup>|
| 6 | - Làm bài lab **Access Control with IAM Policies and Conditions**. <br> - Tìm hiểu cách sử dụng IAM Policy để kiểm soát quyền truy cập. <br> - Tìm hiểu cách sử dụng phần Condition trong IAM Policy. <br> - Làm bài lab **Instance Profiling with IAM Roles for EC2**. <br> - Thực hành tạo IAM Role và Instance Profile cho EC2. <br> - Tìm hiểu cách EC2 truy cập dịch vụ AWS mà không cần lưu Access Key trực tiếp trên máy chủ. | 29/05/2026 | 29/05/2026 | <https://www.youtube.com/@AWSStudyGroup>|


### Kết quả đạt được tuần 6:

* Em đã hiểu được vai trò của Amazon RDS trong việc triển khai và quản lý cơ sở dữ liệu quan hệ trên AWS.

* Em đã tìm hiểu cách Amazon RDS hỗ trợ PostgreSQL và các thành phần cơ bản gồm:
  * DB Instance
  * DB Engine
  * Storage
  * Endpoint
  * Security Group

* Em hiểu được các phương pháp sao lưu dữ liệu trên Amazon RDS gồm:
  * Automated Backup
  * Manual Snapshot
  * Point-in-Time Recovery

* Em biết cách khôi phục một DB Instance từ Snapshot hoặc bản sao lưu tự động.

* Em đã hiểu được vai trò của Multi-AZ Deployment trong việc đảm bảo tính sẵn sàng cao.

* Em phân biệt được High Availability và Disaster Recovery.

* Em đã tìm hiểu cách Read Replica hỗ trợ mở rộng khả năng đọc và giảm tải cho cơ sở dữ liệu chính.

* Em hiểu được vai trò của AWS KMS trong việc tạo, quản lý và sử dụng khóa mã hóa.


* Em hiểu được cách sử dụng IAM Policy và Condition để kiểm soát quyền truy cập chi tiết hơn.

* Em đã thực hành tạo IAM Role và Instance Profile cho Amazon EC2.

* Em hiểu được cách Amazon EC2 sử dụng IAM Role để truy cập các dịch vụ AWS mà không cần lưu Access Key và Secret Access Key trực tiếp trên máy chủ.



