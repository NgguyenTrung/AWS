---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}}

{{% /notice %}}


### Mục tiêu tuần 11:

* Xây dựng giao diện dashboard bằng Next.js.
* Kết nối frontend với Amazon Cognito và API Gateway.
* Đưa mã nguồn dự án lên GitHub.
* Triển khai ứng dụng bằng AWS Amplify Hosting.
* Tìm hiểu CloudFront được AWS Amplify quản lý phía sau.
* Bật AWS WAF để bảo vệ ứng dụng web.
* Kiểm tra Route 53 và khả năng sử dụng custom domain.
* Thực hiện kiểm thử toàn bộ hệ thống và kiểm soát chi phí.


### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Khởi tạo dự án Next.js. <br> - Xây dựng giao diện đăng nhập. <br> - Xây dựng dashboard hiển thị Rooms, Telemetry, Alerts và Reports. <br> - Tích hợp Amazon Cognito với frontend. | 29/06/2026 | 29/06/2026 | <https://nextjs.org/docs/app/getting-started>  |
| 3 | - Kết nối frontend với API Gateway. <br> - Gửi Access Token trong Authorization Header. <br> - Xử lý đăng nhập, duy trì phiên và đăng xuất. <br> - Kiểm tra tải báo cáo JSON từ Amazon S3. | 30/06/2026 | 30/06/2026 | <https://docs.amplify.aws/> <br> <https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-jwt-authorizer.html> |
| 4 | - Đưa mã nguồn lên GitHub repository energy-waste-dashboard. <br> - Tạo ứng dụng AWS Amplify. <br> - Kết nối repository và branch main. <br> - Cấu hình Environment Variables. <br> - Triển khai dashboard lên Amplify Hosting. | 01/07/2026 | 01/07/2026 | <https://docs.github.com/en/repositories> <br> <https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html> |
| 5 | - Kiểm tra CloudFront do Amplify Hosting quản lý. <br> - Không tạo CloudFront Distribution riêng. <br> - Bật Amplify-recommended Firewall Protection. <br> - Kiểm tra AWS Managed Rules và Sampled Requests. <br> - Kiểm tra Route 53 và custom domain. | 02/07/2026 | 02/07/2026 | <https://docs.aws.amazon.com/amplify/latest/userguide/WAF-integration.html> <br> <https://docs.aws.amazon.com/amplify/latest/userguide/custom-domains.html> |
| 6 | - Thực hiện kiểm thử End-to-End toàn hệ thống. <br> - Kiểm tra EventBridge, Lambda, IoT Core, DynamoDB và SNS. <br> - Kiểm tra Cognito, API Gateway, Amplify và dashboard. <br> - Kiểm tra tạo và tải báo cáo từ Amazon S3. <br> - Tắt EventBridge Scheduler và tháo AWS WAF để giảm chi phí. | 03/07/2026 | 03/07/2026 | <https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html> <br> <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |


### Kết quả đạt được tuần 11:

* Em đã xây dựng dashboard bằng Next.js với các chức năng đăng nhập, đăng xuất, hiển thị Telemetry, Alerts và Reports.

* Em đã kết nối frontend với Amazon Cognito và API Gateway.

* Em đã đưa mã nguồn lên GitHub repository energy-waste-dashboard.

* Em đã triển khai ứng dụng thành công bằng AWS Amplify Hosting.

* Dashboard production hoạt động tại:

  * https://main.d2ppdnlr5ik3e8.amplifyapp.com

* Em đã xác nhận AWS Amplify sử dụng CloudFront phía sau và không cần tạo thêm CloudFront Distribution riêng.

* Em đã bật AWS WAF cho ứng dụng Amplify.

* Em đã kiểm tra các AWS Managed Rule Groups và Sampled Requests.

* Em đã kiểm tra Route 53 và thử đăng ký custom domain.

* Quá trình đăng ký custom domain chưa hoàn thành do yêu cầu đăng ký tên miền bị thất bại.

* Em đã thực hiện kiểm thử toàn hệ thống với kết quả:

  * Rooms: 1
  * Telemetry: 20
  * Alerts: 9
  * Reports: 1

* Em đã kiểm tra email cảnh báo được gửi thành công qua Amazon SNS.

* Em đã kiểm tra báo cáo JSON được tạo và lưu trong Amazon S3.

* Em đã xác nhận Object URL trực tiếp trả về AccessDenied, trong khi người dùng đăng nhập có thể tải báo cáo bằng Pre-signed URL.

* Em đã tắt các EventBridge Scheduler sau khi kiểm thử.

* Em đã tháo AWS WAF khỏi ứng dụng để hạn chế chi phí phát sinh.

* Những công việc trong tuần 11 đã hoàn thành phần giao diện, triển khai production, bảo mật và kiểm thử toàn bộ hệ thống.

