---
title : "Kiểm tra luồng IoT hoàn chỉnh"
date : 2026-07-05 
weight : 5
chapter : false
pre : " <b> 5.8.5 </b> "
---

AWS IoT gọi Lambda bất đồng bộ nên sau khi publish, hãy chờ khoảng vài giây rồi mới kiểm tra kết quả.

#### A. Kiểm tra DynamoDB

1. Mở AWS Console trong tab mới.
2. Tìm: **DynamoDB**.
3. Chọn: **Tables**.
4. Chọn bảng: `EnergyWasteData`.
5. Bấm: **Explore table items**.

![DynamoDB Table](/images/5-Workshop/5.8-AWS-IoT-Core/DynamoDB.png)

![DynamoDB Items](/images/5-Workshop/5.8-AWS-IoT-Core/03-dynamodb-telemetry-alert.png)

#### B. Kiểm tra Email SNS

1. Mở email đã đăng ký với SNS.
2. Bạn sẽ nhận được email chứa định dạng JSON cảnh báo từ AWS Energy Waste Alert[cite: 11].

![SNS Email](/images/5-Workshop/5.8-AWS-IoT-Core/04-email-alert-from-iot-rule.png)