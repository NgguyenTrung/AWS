---
title : "Verify IoT Flow"
date : 2026-07-05 
weight : 5
chapter : false
pre : " <b> 5.8.5 </b> "
---

AWS IoT calls Lambda asynchronously, so after publishing, wait a few seconds before checking the results.

#### A. Check DynamoDB

1. Open a new AWS Console tab.
2. Search for: **DynamoDB**.
3. Choose: **Tables**.
4. Select the table: `EnergyWasteData`.
5. Click: **Explore table items**.

![DynamoDB Table](/images/5-Workshop/5.8-AWS-IoT-Core/DynamoDB.png)

![DynamoDB Items](/images/5-Workshop/5.8-AWS-IoT-Core/03-dynamodb-telemetry-alert.png)

#### B. Check SNS Email

1. Open the email registered with SNS.
2. You should receive an email containing the JSON alert data from AWS Energy Waste Alert.

![SNS Email](/images/5-Workshop/5.8-AWS-IoT-Core/04-email-alert-from-iot-rule.png)