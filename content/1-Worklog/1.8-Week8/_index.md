---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
{{% notice warning %}} 

{{% /notice %}}



### Week 8 Objectives:

* Understand the requirements of the **Smart Home Energy Waste Monitoring and Alert System** project.
* Analyze and design the overall system architecture on AWS.
* Configure the AWS Region and AWS Budget to manage resources and control costs.
* Create a shared database using Amazon DynamoDB.
* Configure an email alert service using Amazon SNS.
* Develop a Virtual Sensor Lambda function to simulate electricity consumption data.
* Develop a Waste Detector Lambda function to detect energy waste conditions.

### Tasks to Be Completed This Week:

| Day       | Tasks                                                                                                                                                                                                                                                                                                                   | Start Date | Completion Date | Reference Materials                    |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | -------------------------------------- |
| Monday    | - Study the requirements of the **Smart Home Energy Waste Monitoring and Alert System** project. <br> - Identify the main functions of the system. <br> - Analyze the data collection, energy waste detection, alert delivery, and report generation flows. <br> - Design a serverless architecture using AWS services. | 08/06/2026 | 08/06/2026      | <https://aws.amazon.com/serverless/> |
| Tuesday   | - Select the **Asia Pacific (Singapore) – ap-southeast-1** Region. <br> - Configure an AWS Budget to monitor costs. <br> - Review the IAM permissions required to deploy the project.                                                                                                                                   | 09/06/2026 | 09/06/2026      | <https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-best-practices.html> |
| Wednesday | - Create the **EnergyWasteData** Amazon DynamoDB table. <br> - Configure PK as the Partition Key and SK as the Sort Key. <br> - Select the On-Demand billing mode. <br> - Design the data structure for storing Room, Telemetry, Alert, and Report records.                                                             | 10/06/2026 | 10/06/2026      | <https://docs.aws.amazon.com/dynamodb/> |
| Thursday  | - Create an Amazon SNS Topic for sending energy waste alerts. <br> - Create an Email Subscription. <br> - Confirm the Subscription from the email inbox. <br> - Test the notification delivery function.  | 11/06/2026 | 11/06/2026      |  <https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html> |
| Friday    | - Develop the **energy-virtual-sensor** Lambda function. <br> - Develop the **energy-waste-detector** Lambda function. <br> - Configure Environment Variables. <br> - Grant the Lambda functions permissions to access DynamoDB, SNS, and CloudWatch Logs.                                                              | 12/06/2026 | 12/06/2026      | <https://docs.aws.amazon.com/lambda/latest/dg/welcome.html>  |

### Week 8 Achievements:

* I understood the objectives and requirements of the system for monitoring, detecting, and issuing alerts about energy waste.

* I designed the overall serverless architecture for the project.

* I selected the Asia Pacific (Singapore) Region, with the Region code **ap-southeast-1**.

* I configured an AWS Budget to monitor and control project costs.

* I successfully created the **EnergyWasteData** DynamoDB table.

* I understood how Partition Keys and Sort Keys can be used to store multiple data types within a single table.

* I created an Amazon SNS Topic and successfully confirmed the Email Subscription.

* I developed the Virtual Sensor Lambda function to generate simulated electricity consumption data.

* I developed the Waste Detector Lambda function to process data, store records in DynamoDB, and send alerts through Amazon SNS.

* The tasks completed in Week 8 established the system’s core foundation for data storage, data processing, and alert delivery.
