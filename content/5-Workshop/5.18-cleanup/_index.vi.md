---
title : "Cleanup"
date : 2024-01-01
weight : 19
chapter : false
pre : " <b> 5.18. </b> "
---

#### Dọn dẹp tài nguyên


Phải xóa lịch chạy trước để Lambda Virtual Sensor và Lambda Report Generator không tiếp tục được gọi trong lúc dọn dẹp.

1. **Mở EventBridge Scheduler**
   * Tại thanh tìm kiếm, nhập `EventBridge` và chọn Amazon EventBridge.
   * Trong menu bên trái, mở **Scheduler** -> **Schedules**.

2. **Xóa lịch cảm biến ảo**
   * Tìm và đánh dấu `schedule_virtual_sensor_every_1_min`.
   * Chọn **Delete** và nhập chuỗi xác nhận.

3. **Xóa lịch tạo báo cáo**
   * Tìm và đánh dấu `schedule_report_daily_0005`.
   * Chọn **Delete**.
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-EventBridge-Scheduler.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-EventBridge-Scheduler2.png)

Không thể xóa Web ACL khi nó vẫn đang liên kết với ứng dụng Amplify. Phải gỡ liên kết trước rồi mới xóa Web ACL.

1. **Mở ứng dụng Amplify**
   * Tìm và mở **AWS Amplify**.
   * Chọn ứng dụng: `energy-waste-dashboard`.
   * Mở **Hosting** -> **Firewall**.

2. **Gỡ Web ACL**
   * Tìm Web ACL đang liên kết, chọn **Actions** -> **Disassociate firewall**.
   * Nhập xác nhận và chờ trạng thái liên kết được gỡ bỏ.

3. **Xóa Web ACL**
   * Tìm và mở **AWS WAF & Shield**.
   * Đổi Region thành **Global (CloudFront)** và chọn **Web ACLs**.
   * Chọn Web ACL vừa gỡ, bấm **Delete** và xác nhận.

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Web-ACL.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Web-ACL2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/AWS-Amplify.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/AWS-Amplify2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-APi-Gateway.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-API-Gateway2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Cognito.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Cognito2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Rule.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Rule2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Lambda.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-Lambda2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-SNS.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-SNS2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-DynamoDB.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-DynamoDB2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-IAM-Roles.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-IAM-Role2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-CloudWatch.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-CloudWatch2.png)

![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-S3-1.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-S3-2.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-S3-3.png)
![hosted zone](/images/5-Workshop/5.18-cleanup/Xoa-S3-4.png)

