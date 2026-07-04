---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Đảm bảo truy cập Hybrid an toàn đến S3 bằng cách sử dụng VPC endpoint

#### Tổng quan

**AWS PrivateLink** cung cấp kết nối riêng tư đến các dịch vụ aws từ VPCs hoặc trung tâm dữ liệu (on-premise) mà không làm lộ lưu lượng truy cập ra ngoài public internet.

Trong bài lab này, chúng ta sẽ học cách tạo, cấu hình, và kiểm tra VPC endpoints để cho phép workload của bạn tiếp cận các dịch vụ AWS mà không cần đi qua Internet công cộng.

Chúng ta sẽ tạo hai loại endpoints để truy cập đến Amazon S3: gateway vpc endpoint và interface vpc endpoint. Hai loại vpc endpoints này mang đến nhiều lợi ích tùy thuộc vào việc bạn truy cập đến S3 từ môi trường cloud hay từ trung tâm dữ liệu (on-premise).

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-prerequisite/)
3. [Ngân sách và khu vực](5.3-budget-and-region/)
4. [DynamoDB](5.4-dynamodb/)
5. [Cảnh báo email SNS](5.5-sns-email-alert/)
6. [Lambda waste detector](5.6-lambda-waste-detector/)
7. [Lambda virtual sensor](5.7-lambda-virtual-sensor/)
8. [IoT Core rule](5.8-iot-core-rule/)
9. [EventBridge schedule](5.9-eventbridge-schedule/)
10. [Kiểm thử CloudWatch](5.10-cloudwatch-testing/)
11. [Cognito user pool](5.11-cognito-user-pool/)
12. [API Gateway HTTP API](5.12-api-gateway-http-api/)
13. [Lambda API handler](5.13-lambda-api-handler/)
14. [S3 report bucket](5.14-s3-report-bucket/)
15. [Lambda report generator](5.15-lambda-report-generator/)
16. [Next.js + Amplify](5.16-nextjs-amplify/)
17. [CloudFront, WAF, custom domain](5.17-cloudfront-waf-custom-domain/)
18. [End-to-end testing](5.18-end-to-end-testing/)
19. [Dọn dẹp](5.19-cleanup/)
