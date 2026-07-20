---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice warning %}}

{{% /notice %}}

# SMART HOME ENERGY WASTE MONITORING & ALERT SYSTEM

## An AWS Serverless Solution for Monitoring and Alerting Energy Waste Using Virtual Sensors

### 1. Executive Summary

The Smart Home Energy Waste Monitoring & Alert System is a real-time electricity consumption monitoring and energy waste detection system built on an AWS Serverless architecture. The system uses virtual sensors running on AWS Lambda to simulate electricity data such as power, voltage, current, device status, and room occupancy status. The data is transmitted through AWS IoT Core, processed by Lambda Waste Detector, stored in Amazon DynamoDB, and used to send alerts through Amazon SNS when the system detects that a device remains turned on while no one is using the room.

The platform is designed for smart homes, laboratories, smart classrooms, and shared working spaces where electricity consumption needs to be monitored and energy waste reduced. The dashboard is built with React, Next.js, and TailwindCSS, deployed using AWS Amplify, protected by AWS WAF, distributed through Amazon CloudFront, and secured with Amazon Cognito authentication.

### 2. Problem Statement

*Current Problem*

In laboratories, classrooms, and shared working spaces, electrical devices such as lights, fans, air conditioners, and computers are often left on after people have left the room. This causes energy waste, increases operating costs, and reduces the effectiveness of energy management. In addition, manual inspection makes it difficult for administrators to continuously monitor electricity consumption in real time.

Traditional electricity monitoring systems often require physical sensors, dedicated servers, fixed databases, and high deployment costs. For a student project or prototype, using physical sensors may increase both complexity and cost.

*Proposed Solution*

The proposed solution uses an AWS Serverless architecture to build an electricity monitoring system with virtual sensors. Lambda Virtual Sensor automatically generates electricity data every minute through Amazon EventBridge. The data is sent to AWS IoT Core using the MQTT protocol, after which an AWS IoT Rule forwards it to Lambda Waste Detector for analysis.

When the system detects an energy waste condition, such as a device being turned on while no one is in the room and its power consumption exceeding the configured threshold, it performs two actions in parallel: storing telemetry and alert data in Amazon DynamoDB and sending an email alert to the user through Amazon SNS.

The system also includes Lambda Report Generator, which runs daily at 00:05 AM to read data from DynamoDB, generate a report, and store it in an Amazon S3 Report Bucket. The dashboard can call Amazon API Gateway and Lambda API Handler to view monitoring data, review alert history, and download reports.

*Benefits*

The solution automates electricity monitoring, reduces dependence on manual inspections, and provides near-real-time alerts when signs of energy waste are detected. By using serverless services such as AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon EventBridge, Amazon SNS, and Amazon S3, the system is scalable, cost-efficient, and does not require server management.

Within the scope of the project, the system can be deployed at a low cost, making it suitable for a testing budget of approximately 30–50 USD or less when service usage is optimized. The architecture can also be extended in the future to connect physical sensors, support additional rooms and devices, and provide more advanced analytics dashboards.

### 3. Solution Architecture

The system is deployed using an AWS Serverless architecture in the Asia Pacific (Singapore) Region, ap-southeast-1. The user access layer includes Amazon Route 53, Amazon CloudFront, AWS WAF, and AWS Amplify. Users access the dashboard through a domain managed by Route 53. CloudFront acts as the CDN and edge delivery layer, AWS WAF protects the frontend, and AWS Amplify hosts the Next.js application.

The authentication and API layer uses Amazon Cognito, Amazon API Gateway, and Lambda API Handler. Users sign in through Cognito to receive a JWT token. When the dashboard calls the API, API Gateway validates the token and forwards the request to Lambda API Handler. Lambda API Handler reads and writes data in Amazon DynamoDB and retrieves reports from the Amazon S3 Report Bucket.

The sensor data processing layer uses Amazon EventBridge, Lambda Virtual Sensor, AWS IoT Core, an IoT Rule, and Lambda Waste Detector. EventBridge triggers Lambda Virtual Sensor every minute to generate simulated electricity data. The data is published to AWS IoT Core, after which the IoT Rule routes it to Lambda Waste Detector. Lambda Waste Detector evaluates energy waste conditions and performs two parallel actions: storing data in DynamoDB and sending alerts through Amazon SNS Email.

The reporting layer uses an EventBridge rule that runs daily at 00:05 AM to trigger Lambda Report Generator. This Lambda function reads telemetry and alert data from DynamoDB, generates a daily summary, and writes the report file to the Amazon S3 Report Bucket.

Amazon CloudWatch is used to collect logs and metrics and provide monitoring support for components such as Lambda, API Gateway, EventBridge, IoT Core, and SNS. This allows the team to verify whether the system runs according to schedule, whether Lambda functions encounter errors, whether the IoT Rule invokes Waste Detector, and whether SNS sends alerts successfully.

 ![Smart Home Energy Waste Monitoring Architecture](/images/2-Proposal/screenshot 2026-07-02 105425.png)

*AWS Services Used*

- Amazon Route 53: Manages the domain name and routes users to the content delivery layer.
- Amazon CloudFront: Distributes the frontend through a CDN, helping the dashboard load faster and more reliably.
- AWS WAF: Protects the frontend from abnormal or malicious requests.
- AWS Amplify: Hosts and deploys the Next.js web application for the dashboard.
- Amazon Cognito: Manages user sign-in, authentication, and JWT token issuance.
- Amazon API Gateway: Provides API endpoints through which the frontend calls the backend.
- AWS Lambda: Handles serverless backend processing through four main functions: Lambda API Handler, Lambda Virtual Sensor, Lambda Waste Detector, and Lambda Report Generator.
- Amazon EventBridge: Creates scheduled triggers for the virtual sensor every minute and for daily report generation at 00:05 AM.
- AWS IoT Core: Receives simulated electricity data through the MQTT protocol.
- AWS IoT Rule: Routes telemetry data from AWS IoT Core to Lambda Waste Detector.
- Amazon DynamoDB: Stores shared data, including Rooms, Telemetry, Alerts, and Reports Metadata.
- Amazon SNS: Sends email alerts when energy waste is detected.
- Amazon S3: Stores daily report files in the Report Bucket.
- Amazon CloudWatch: Monitors logs and metrics and supports debugging for Lambda, API Gateway, EventBridge, IoT Core, and SNS.
- AWS Budgets: Tracks costs and sends alerts when spending exceeds the configured budget threshold.

*Component Design*

- Users: Access the dashboard through a web browser to view electricity data, alerts, and reports.
- Web Interface: The dashboard is built with React, Next.js, and TailwindCSS and deployed using AWS Amplify.
- Edge/Frontend Layer: Amazon Route 53 routes the domain to Amazon CloudFront. AWS WAF protects CloudFront, while CloudFront distributes the frontend application hosted by AWS Amplify.
- User Management: Amazon Cognito handles user sign-in, authentication, and JWT token issuance.
- Backend API: Amazon API Gateway receives requests from the dashboard, validates JWT tokens, and invokes Lambda API Handler to process business logic.
- Virtual Sensor: Lambda Virtual Sensor is triggered every minute by Amazon EventBridge to generate simulated electricity data such as power, voltage, current, device status, and room occupancy status.
- IoT Data Ingestion: AWS IoT Core receives MQTT data from Lambda Virtual Sensor. An AWS IoT Rule routes this data to Lambda Waste Detector.
- Energy Waste Detection: Lambda Waste Detector checks energy waste conditions, such as a device being turned on, no one being present in the room, and power consumption exceeding the configured threshold.
- Data Storage: Amazon DynamoDB stores telemetry, alerts, rooms, and reports metadata in one shared data table.
- Alerting: Amazon SNS sends email alerts when energy waste is detected.
- Reporting: Lambda Report Generator runs daily at 00:05 AM, reads data from DynamoDB, generates a report, and stores it in the Amazon S3 Report Bucket.
- System Monitoring: Amazon CloudWatch records logs and metrics to verify whether Lambda functions run on schedule, whether the IoT Rule invokes the detector, whether API errors occur, and whether SNS sends alerts successfully.

### 4. Roadmap and Deployment Milestones

- Phase 1 — Design and Preparation:  
Complete the system requirements, design the AWS architecture diagram, identify the required services, and configure AWS Budgets to control project costs.

- Phase 2 — Deploy the Virtual Sensor Flow:  
Create DynamoDB, SNS, Lambda Virtual Sensor, Lambda Waste Detector, AWS IoT Core, an IoT Rule, and an EventBridge rule that runs every minute. Verify that data is generated, transmitted through IoT Core, processed, and stored in DynamoDB.

- Phase 3 — Deploy the API and Authentication:  
Create an Amazon Cognito User Pool, Amazon API Gateway, and Lambda API Handler. Test whether the frontend or Postman can call the API using a JWT token and read data from DynamoDB.

- Phase 4 — Deploy the Dashboard and Reporting Functions:  
Deploy the Next.js dashboard using AWS Amplify. Create Lambda Report Generator, an EventBridge rule that runs daily at 00:05 AM, and an S3 Report Bucket for storing report files.

- Phase 5 — Testing and Finalization:  
Test the complete system, review logs in CloudWatch, test SNS email alerts, verify report files in S3, and optimize costs before the project presentation.

### 5. Budget Estimation

Costs can be estimated using the [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).  
Alternatively, download the [budget estimation file](../attachments/budget_estimation.pdf).

*Estimated Infrastructure Costs*

- AWS Lambda: **0.00 USD/month**.
- Amazon DynamoDB: **0.05 USD/month**.
- AWS IoT Core: **0.08 USD/month**.
- Amazon SNS: **0.02 USD/month**.
- Amazon API Gateway: **0.02 USD/month**.
- Amazon S3: **0.01 USD/month**.
- Amazon Cognito: **0.00 USD/month**.
- Amazon EventBridge: **0.00 USD/month**.
- AWS Amplify Hosting: **0.50 USD/month**.
- Amazon CloudWatch: **0.00 USD/month**.

*Total*: approximately **0.70 USD/month**, equivalent to **8.40 USD over 12 months**.

- *AWS WAF*: Enabled only during testing. If maintained continuously, it may add approximately **23 USD/month**.
- *Hardware*: **0 USD**, because the project uses virtual sensors.

### 6. Risk Assessment

*Risk Matrix*

- AWS budget overrun: Medium impact, medium probability. This may be caused by increased CloudWatch log volume, WAF or CloudFront charges, or EventBridge rules running continuously.
- Missing IAM permissions for Lambda: High impact, medium probability. This may prevent Lambda from writing to DynamoDB, publishing to SNS, or sending data to AWS IoT Core.
- SNS email not delivered: Medium impact, medium probability. A common cause is an unconfirmed email subscription.
- IoT Rule does not invoke Lambda Waste Detector: High impact, medium probability. This may be caused by an incorrect MQTT topic, an incorrect SQL statement, or missing Lambda invocation permission.
- API Gateway JWT authentication error: High impact, medium probability. This may be caused by an incorrectly configured Cognito authorizer or a missing Authorization header from the frontend.
- Simulated sensor data is not realistic enough: Medium impact, high probability. Because the data is simulated, detection rules must be carefully designed to provide a clear demonstration.
- Dashboard cannot access the API: Medium impact, medium probability. This may be caused by CORS issues, an incorrect API Gateway endpoint, or an invalid token.
- Report is not generated on schedule: Medium impact, low probability. This may be caused by an incorrect EventBridge schedule, Lambda timeout, or missing permission to write to S3.

*Mitigation Strategies*

- Cost: Create an AWS Budget, monitor the Billing Dashboard, and configure CloudWatch Logs retention.
- IAM Permissions: Apply least-privilege permissions to each Lambda function and carefully verify DynamoDB, SNS, IoT Core, and S3 permissions.
- SNS Email: Confirm the email subscription immediately after creating the SNS topic.
- IoT Rule: Test Lambda Virtual Sensor manually, verify the MQTT topic, and review Lambda Waste Detector logs in CloudWatch.
- JWT and Cognito: Test user sign-in, obtain a JWT token, and call API Gateway using Postman or the dashboard.
- CORS: Configure CORS in API Gateway so that the Amplify frontend can call the backend.
- Reporting: Test Lambda Report Generator manually before attaching the daily EventBridge rule.
- Simulated Data: Create multiple virtual sensor scenarios, including occupied and unoccupied rooms, devices turned on and off, and high and low power consumption, to clearly demonstrate energy waste detection.

*Contingency Plan*

- If AWS IoT Core configuration fails, Lambda Waste Detector can be tested directly using a sample JSON event.
- If Cognito is not completed, API Gateway can first be demonstrated in test mode, and the JWT authorizer can be added later.
- If the Amplify deployment is not ready, the frontend can be run locally while calling the actual API Gateway endpoint to demonstrate that the AWS backend works.
- If automatic report generation is not ready, Lambda Report Generator can be run manually to generate a report file in S3.
- If costs increase unexpectedly, the EventBridge rule can be temporarily disabled and unnecessary log groups can be removed after screenshots have been captured as evidence.

### 7. Expected Outcomes

- Technical Improvement:  
The system automates electricity monitoring in smart homes or laboratories, replacing manual inspection with a scheduled serverless pipeline. Electricity data is generated by virtual sensors, transmitted through AWS IoT Core, analyzed by Lambda, and stored centrally in DynamoDB. When energy waste is detected, the system can send near-real-time email alerts.

- Operational Value:  
The dashboard allows users to monitor electricity consumption, view alert history, and download daily reports. Using AWS Serverless services reduces the need for server management, simplifies deployment, and makes it easier to support additional rooms, devices, or physical sensors in the future.

- Scalability:  
In the future, the system can be extended from virtual sensors to physical sensors such as smart meters, ESP32 devices, or IoT power measurement devices. Additional features may include electricity consumption trend analysis, anomaly prediction, device on/off schedule optimization, and an administration dashboard for multiple rooms or buildings.