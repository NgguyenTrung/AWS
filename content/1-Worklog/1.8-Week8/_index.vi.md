---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
{{% notice warning %}}

{{% /notice %}}

### Mục tiêu tuần 8:

* Tìm hiểu yêu cầu của dự án Smart Home Energy Waste Monitoring and Alert System.
* Phân tích và thiết kế kiến trúc tổng thể của hệ thống trên AWS.
* Thiết lập Region và AWS Budget để quản lý tài nguyên và kiểm soát chi phí.
* Tạo cơ sở dữ liệu dùng chung bằng Amazon DynamoDB.
* Thiết lập dịch vụ gửi cảnh báo qua email bằng Amazon SNS.
* Xây dựng Lambda Virtual Sensor để mô phỏng dữ liệu điện năng.
* Xây dựng Lambda Waste Detector để phát hiện tình trạng lãng phí điện.


### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu yêu cầu của dự án **Smart Home Energy Waste Monitoring and Alert System**. <br> - Xác định các chức năng chính của hệ thống. <br> - Phân tích luồng thu thập dữ liệu, phát hiện lãng phí, gửi cảnh báo và tạo báo cáo. <br> - Thiết kế kiến trúc Serverless sử dụng các dịch vụ AWS. | 08/06/2026 | 08/06/2026 | <https://www.youtube.com/@AWSStudyGroup> |
| 3 | - Chọn Region **Asia Pacific (Singapore) – ap-southeast-1**. <br> - Thiết lập AWS Budget để theo dõi chi phí. <br> - Kiểm tra các quyền IAM cần thiết để triển khai dự án. | 09/06/2026 | 09/06/2026 | <https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-best-practices.html>|
| 4 | - Tạo bảng Amazon DynamoDB **EnergyWasteData**. <br> - Cấu hình Partition Key là PK và Sort Key là SK. <br> - Chọn chế độ tính phí On-demand. <br> - Thiết kế cấu trúc lưu Room, Telemetry, Alert và Report. | 10/06/2026 | 10/06/2026 | <https://docs.aws.amazon.com/dynamodb/> |
| 5 | - Tạo Amazon SNS Topic để gửi cảnh báo lãng phí điện. <br> - Tạo Email Subscription. <br> - Xác nhận Subscription từ hộp thư email. <br> - Kiểm tra chức năng gửi thông báo. | 11/06/2026 | 11/06/2026 |  <https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html>|
| 6 | - Xây dựng Lambda **energy-virtual-sensor**. <br> - Xây dựng Lambda **energy-waste-detector**. <br> - Cấu hình Environment Variables. <br> - Cấp quyền DynamoDB, SNS và CloudWatch Logs cho Lambda. | 12/06/2026 | 12/06/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/welcome.html>  |


### Kết quả đạt được tuần 8:

* Em đã hiểu được mục tiêu và yêu cầu của hệ thống giám sát, phát hiện và cảnh báo lãng phí điện năng.

* Em đã thiết kế được kiến trúc Serverless tổng thể cho dự án.

* Em đã thống nhất sử dụng Region Asia Pacific (Singapore), mã Region ap-southeast-1.

* Em đã thiết lập AWS Budget để theo dõi và kiểm soát chi phí.

* Em đã tạo thành công bảng DynamoDB EnergyWasteData.

* Em đã hiểu cách sử dụng Partition Key và Sort Key để lưu nhiều loại dữ liệu trong cùng một bảng.

* Em đã tạo Amazon SNS Topic và xác nhận Email Subscription thành công.

* Em đã xây dựng Lambda Virtual Sensor để tạo dữ liệu mô phỏng điện năng.

* Em đã xây dựng Lambda Waste Detector để xử lý dữ liệu, lưu dữ liệu vào DynamoDB và gửi cảnh báo bằng Amazon SNS.

* Những công việc trong tuần 8 đã hoàn thành phần nền tảng lưu trữ, xử lý dữ liệu và gửi cảnh báo của hệ thống.

