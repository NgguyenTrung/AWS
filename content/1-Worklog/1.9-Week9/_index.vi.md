---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}}

{{% /notice %}}


### Mục tiêu tuần 9:

* Tìm hiểu dịch vụ AWS IoT Core và giao thức MQTT.
* Kết nối Lambda Virtual Sensor với AWS IoT Core.
* Tạo IoT Rule để chuyển dữ liệu đến Lambda Waste Detector.
* Tạo EventBridge Scheduler để tự động gọi Lambda theo chu kỳ.
* Kiểm tra quá trình xử lý dữ liệu bằng Amazon CloudWatch Logs.
* Kiểm tra dữ liệu Telemetry và Alert trong DynamoDB.
* Kiểm tra chức năng gửi email cảnh báo qua Amazon SNS.


### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu AWS IoT Core và giao thức MQTT. <br> - Xác định MQTT Topic sử dụng cho dữ liệu điện năng. <br> - Cấu hình Lambda Virtual Sensor publish dữ liệu đến Topic home/lab/telemetry. <br> - Kiểm tra dữ liệu bằng MQTT Test Client. | 15/06/2026 | 15/06/2026 | <https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html> |
| 3 | - Tạo AWS IoT Rule. <br> - Viết câu lệnh SQL để nhận dữ liệu từ MQTT Topic. <br> - Cấu hình Action gọi Lambda energy-waste-detector. <br> - Cấp quyền để AWS IoT Core gọi Lambda. | 16/06/2026 | 16/06/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/services-iot.html>|
| 4 | - Tạo EventBridge Scheduler schedule_virtual_sensor_every_1_min. <br> - Cấu hình biểu thức rate(1 minute). <br> - Chọn Target là Lambda energy-virtual-sensor. <br> - Tạo Execution Role cho EventBridge Scheduler. | 17/06/2026 | 17/06/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/with-eventbridge-scheduler.html>|
| 5 | - Kiểm tra CloudWatch Logs của Lambda Virtual Sensor. <br> - Kiểm tra Lambda được EventBridge gọi mỗi phút. <br> - Kiểm tra quá trình publish dữ liệu đến AWS IoT Core. <br> - Kiểm tra CloudWatch Logs của Lambda Waste Detector. | 18/06/2026 | 18/06/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html>|
| 6 | - Kiểm tra dữ liệu Telemetry và Alert trong DynamoDB. <br> - Kiểm tra điều kiện phát hiện lãng phí điện. <br> - Kiểm tra email cảnh báo từ Amazon SNS. <br> - Tắt EventBridge Scheduler sau khi kiểm thử. | 19/06/2026 | 19/06/2026 | <https://docs.aws.amazon.com/dynamodb/> <br> <https://docs.aws.amazon.com/sns/> |


### Kết quả đạt được tuần 9:

* Em đã hiểu vai trò của AWS IoT Core trong việc tiếp nhận và định tuyến dữ liệu IoT.

* Em đã hiểu cách sử dụng giao thức MQTT để truyền dữ liệu điện năng.

* Em đã cấu hình Lambda Virtual Sensor publish dữ liệu đến MQTT Topic home/lab/telemetry.

* Em đã sử dụng MQTT Test Client để kiểm tra dữ liệu được gửi đến AWS IoT Core.

* Em đã tạo IoT Rule để chuyển dữ liệu đến Lambda Waste Detector.

* Em đã tạo EventBridge Scheduler với chu kỳ rate(1 minute).

* Em đã kiểm tra CloudWatch Logs và xác nhận Lambda Virtual Sensor được gọi tự động.

* Em đã xác nhận Lambda Waste Detector nhận dữ liệu từ IoT Rule và lưu Telemetry vào DynamoDB.

* Em đã kiểm tra điều kiện phát hiện lãng phí điện khi thiết bị đang bật, phòng không có người và công suất vượt ngưỡng.

* Em đã xác nhận hệ thống tạo Alert trong DynamoDB và gửi email cảnh báo qua Amazon SNS.

* Những công việc trong tuần 9 đã hoàn thành luồng thu thập, xử lý và cảnh báo lãng phí điện theo thời gian thực.


