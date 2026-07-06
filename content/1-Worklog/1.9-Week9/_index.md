---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}} 

{{% /notice %}}



### Week 9 Objectives:

* Learn about AWS IoT Core and the MQTT protocol.
* Connect the Virtual Sensor Lambda function to AWS IoT Core.
* Create an IoT Rule to forward data to the Waste Detector Lambda function.
* Create an EventBridge Scheduler to invoke the Lambda function automatically at regular intervals.
* Monitor the data processing flow using Amazon CloudWatch Logs.
* Verify Telemetry and Alert records in DynamoDB.
* Test the email alert function through Amazon SNS.

### Tasks to Be Completed This Week:

| Day       | Tasks                                                                                                                                                                                                                                                                              | Start Date | Completion Date | Reference Materials                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------------------------------- |
| Monday    | - Learn about AWS IoT Core and the MQTT protocol. <br> - Determine the MQTT Topic used for electricity consumption data. <br> - Configure the Virtual Sensor Lambda function to publish data to the home/lab/telemetry Topic. <br> - Verify the data using the MQTT Test Client. | 15/06/2026 | 15/06/2026      | https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html   |
| Tuesday   | - Create an AWS IoT Rule. <br> - Write an SQL statement to receive data from the MQTT Topic. <br> - Configure an Action to invoke the energy-waste-detector Lambda function. <br> - Grant AWS IoT Core permission to invoke the Lambda function.                                 | 16/06/2026 | 16/06/2026      | https://docs.aws.amazon.com/lambda/latest/dg/services-iot.html               |
| Wednesday | - Create the EventBridge Scheduler named schedule_virtual_sensor_every_1_min. <br> - Configure the rate(1 minute) expression. <br> - Select the energy-virtual-sensor Lambda function as the Target. <br> - Create an Execution Role for EventBridge Scheduler.              | 17/06/2026 | 17/06/2026      | https://docs.aws.amazon.com/lambda/latest/dg/with-eventbridge-scheduler.html |
| Thursday  | - Review the CloudWatch Logs of the Virtual Sensor Lambda function. <br> - Verify that EventBridge invokes the Lambda function every minute. <br> - Verify that data is published to AWS IoT Core. <br> - Review the CloudWatch Logs of the Waste Detector Lambda function.        | 18/06/2026 | 18/06/2026      | https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html  |
| Friday    | - Verify Telemetry and Alert records in DynamoDB. <br> - Test the conditions used to detect energy waste. <br> - Verify the alert email sent through Amazon SNS. <br> - Disable the EventBridge Scheduler after testing.                                                           | 19/06/2026 | 19/06/2026      | https://docs.aws.amazon.com/dynamodb/ <br> https://docs.aws.amazon.com/sns/  |

### Week 9 Achievements:

* I understood the role of AWS IoT Core in receiving and routing IoT data.

* I learned how the MQTT protocol is used to transmit electricity consumption data.

* I configured the Virtual Sensor Lambda function to publish data to the home/lab/telemetry MQTT Topic.

* I used the MQTT Test Client to verify that data was successfully sent to AWS IoT Core.

* I created an IoT Rule to forward data to the Waste Detector Lambda function.

* I created an EventBridge Scheduler using the rate(1 minute) schedule expression.

* I reviewed CloudWatch Logs and confirmed that the Virtual Sensor Lambda function was invoked automatically.

* I confirmed that the Waste Detector Lambda function received data from the IoT Rule and stored Telemetry records in DynamoDB.

* I tested the energy waste detection conditions when a device was turned on, the room was unoccupied, and the power consumption exceeded the defined threshold.

* I confirmed that the system created Alert records in DynamoDB and sent alert emails through Amazon SNS.

* The tasks completed in Week 9 established the real-time energy waste data collection, processing, and alerting flow.
