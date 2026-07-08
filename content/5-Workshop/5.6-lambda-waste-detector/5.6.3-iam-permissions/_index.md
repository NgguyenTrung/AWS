---
title: "5.6.3 IAM permission"
weight: 1
---



By default, an AWS Lambda function does not have permission to write data to DynamoDB or send notifications through Amazon SNS. Therefore, we need to attach an inline policy to grant the required permissions.

### Steps:

1. On the **energy-waste-detector** function page, go to the **Configuration** tab and select **Permissions**.
2. In the **Execution role** section, click the current role name. The role name will look similar to:

```text
energy-waste-detector-role-pmsoahv7
```

The system will open the IAM Role page in a new browser tab.

3. On the IAM Role page, click **Add permissions** and select **Create inline policy** from the drop-down menu.
4. Switch to the **JSON** tab.
5. Delete all default content in the editor and paste the following permission policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "WriteEnergyWasteData",
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData"
    },
    {
      "Sid": "PublishEnergyWasteAlert",
      "Effect": "Allow",
      "Action": [
        "sns:Publish"
      ],
      "Resource": "arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic"
    }
  ]
}
```

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-iam-policy-json.png)

Click:

```text
Create policy
```

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-iam-policy-created.png)