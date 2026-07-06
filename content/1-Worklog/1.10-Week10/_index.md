---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 

{{% /notice %}}




### Week 10 Objectives:

* Learn about Amazon Cognito and user authentication mechanisms.
* Create a User Pool and App Client for the dashboard.
* Build an Amazon API Gateway HTTP API.
* Configure a JWT Authorizer to secure the API.
* Develop a Lambda API Handler to provide data to the frontend.
* Create an Amazon S3 Report Bucket to store energy reports.
* Develop a Lambda Report Generator and configure a daily report generation schedule.

### Tasks to Be Completed This Week:

| Day       | Tasks                                                                                                                                                                                                                                              | Start Date | Completion Date | Reference Materials                                                                                                   |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------- |
| Monday    | - Learn about Amazon Cognito User Pools. <br> - Create the energy-waste-user-pool User Pool. <br> - Create the energy-waste-dashboard-client App Client. <br> - Configure email-based sign-in. <br> - Create a test user account.              | 22/06/2026 | 22/06/2026      | https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools.html                                     |
| Tuesday   | - Create the energy-waste-http-api API Gateway HTTP API. <br> - Create Routes for retrieving Rooms, Telemetry, Alerts, and Reports. <br> - Configure the $default Stage. <br> - Enable Automatic Deployment and configure CORS.                | 23/06/2026 | 23/06/2026      | https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html                                            |
| Wednesday | - Create a JWT Authorizer using the Cognito User Pool. <br> - Configure the Issuer and Audience. <br> - Attach the Authorizer to the Routes. <br> - Develop the energy-api-handler Lambda function. <br> - Test the API using an Access Token.   | 24/06/2026 | 24/06/2026      | https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-jwt-authorizer.html                             |
| Thursday  | - Create an Amazon S3 Report Bucket. <br> - Keep Block Public Access enabled. <br> - Configure default encryption. <br> - Grant the Lambda function permission to read and write reports in Amazon S3.                                             | 25/06/2026 | 25/06/2026      | https://docs.aws.amazon.com/s3/                                                                                       |
| Friday    | - Develop the energy-report-generator Lambda function. <br> - Read data from DynamoDB and aggregate the report information. <br> - Generate a JSON file and store it in Amazon S3. <br> - Create an EventBridge Scheduler to run daily at 00:05. | 26/06/2026 | 26/06/2026      | https://docs.aws.amazon.com/lambda/ <br> https://docs.aws.amazon.com/lambda/latest/dg/with-eventbridge-scheduler.html |

### Week 10 Achievements:

* I understood the role of Amazon Cognito in user management and authentication.

* I successfully created the energy-waste-user-pool User Pool and the energy-waste-dashboard-client App Client.

* I created a test user account and successfully signed in.

* I built the energy-waste-http-api API Gateway HTTP API.

* I created endpoints for retrieving Rooms, Telemetry, Alerts, and Reports.

* I configured a JWT Authorizer to secure the API.

* I developed a Lambda API Handler to retrieve data from DynamoDB and return JSON responses to the frontend.

* I created an Amazon S3 Report Bucket and kept the reports private.

* I developed a Lambda Report Generator to aggregate data and generate energy consumption reports.

* I created an EventBridge Scheduler to invoke the Lambda Report Generator daily at 00:05.

* The tasks completed in Week 10 established the authentication, API, and report generation components of the system.

