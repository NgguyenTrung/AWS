---
title: "5.6.2 Env variables"
weight: 1
---



Instead of hardcoding system configuration values such as the DynamoDB table name or the SNS topic ARN, we will use environment variables to simplify configuration management for the Lambda function.

### Steps:

1. Open the details page of the newly created **energy-waste-detector** function.
2. Select the **Configuration** tab from the main function menu.
3. In the left-side menu, select **Environment variables**.
4. Click the **Edit** button in the upper-right corner.
5. Click **Add environment variable** and enter the following three Key-Value pairs exactly:
   * **Key:** `DDB_TABLE` | **Value:** `EnergyWasteData`
   * **Key:** `SNS_TOPIC_ARN` | **Value:** `arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic`
   * **Key:** `POWER_THRESHOLD_W` | **Value:** `120`
6. Click **Save** to save all environment variable configurations.

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-env.png)