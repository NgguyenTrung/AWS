---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}}

{{% /notice %}}


### Mục tiêu tuần 10:

* Tìm hiểu Amazon Cognito và cơ chế xác thực người dùng.
* Tạo User Pool và App Client cho dashboard.
* Xây dựng Amazon API Gateway HTTP API.
* Cấu hình JWT Authorizer để bảo vệ API.
* Xây dựng Lambda API Handler để cung cấp dữ liệu cho frontend.
* Tạo S3 Report Bucket để lưu báo cáo điện năng.
* Xây dựng Lambda Report Generator và lịch tạo báo cáo hằng ngày.


### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Amazon Cognito User Pool. <br> - Tạo User Pool energy-waste-user-pool. <br> - Tạo App Client energy-waste-dashboard-client. <br> - Cấu hình đăng nhập bằng email. <br> - Tạo tài khoản người dùng thử nghiệm. | 22/06/2026 | 22/06/2026 | <https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools.html> |
| 3 | - Tạo API Gateway HTTP API energy-waste-http-api. <br> - Tạo các Route lấy Rooms, Telemetry, Alerts và Reports. <br> - Cấu hình Stage $default. <br> - Bật Automatic Deployment và cấu hình CORS. | 23/06/2026 | 23/06/2026 | <https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html> |
| 4 | - Tạo JWT Authorizer sử dụng Cognito User Pool. <br> - Cấu hình Issuer và Audience. <br> - Gắn Authorizer vào các Route. <br> - Xây dựng Lambda energy-api-handler. <br> - Kiểm tra API bằng Access Token. | 24/06/2026 | 24/06/2026 | <https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-jwt-authorizer.html>  |
| 5 | - Tạo Amazon S3 Report Bucket. <br> - Giữ Block Public Access được bật. <br> - Cấu hình mã hóa mặc định. <br> - Cấp quyền để Lambda đọc và ghi báo cáo trong S3. | 25/06/2026 | 25/06/2026 | <https://docs.aws.amazon.com/s3/> |
| 6 | - Xây dựng Lambda energy-report-generator. <br> - Đọc dữ liệu từ DynamoDB và tổng hợp báo cáo. <br> - Tạo file JSON và lưu vào Amazon S3. <br> - Tạo EventBridge Scheduler chạy lúc 00:05 hằng ngày. | 26/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/lambda/> <br> <https://docs.aws.amazon.com/lambda/latest/dg/with-eventbridge-scheduler.html> |


### Kết quả đạt được tuần 10:

* Em đã hiểu vai trò của Amazon Cognito trong việc quản lý và xác thực người dùng.

* Em đã tạo thành công User Pool energy-waste-user-pool và App Client energy-waste-dashboard-client.

* Em đã tạo tài khoản người dùng thử nghiệm và đăng nhập thành công.

* Em đã xây dựng API Gateway HTTP API energy-waste-http-api.

* Em đã tạo các endpoint để truy xuất Rooms, Telemetry, Alerts và Reports.

* Em đã cấu hình JWT Authorizer để bảo vệ API.

* Em đã xây dựng Lambda API Handler để đọc dữ liệu từ DynamoDB và trả dữ liệu JSON cho frontend.

* Em đã tạo S3 Report Bucket và giữ báo cáo ở trạng thái private.

* Em đã xây dựng Lambda Report Generator để tổng hợp dữ liệu và tạo báo cáo điện năng.

* Em đã tạo EventBridge Scheduler chạy Lambda Report Generator lúc 00:05 hằng ngày.

* Những công việc trong tuần 10 đã hoàn thành phần xác thực, API và chức năng tạo báo cáo của hệ thống.

