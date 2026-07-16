---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}} 

{{% /notice %}}


### Week 11 Objectives:

* Build the dashboard interface using Next.js.
* Connect the frontend to Amazon Cognito and API Gateway.
* Upload the project source code to GitHub.
* Deploy the application using AWS Amplify Hosting.
* Learn about the CloudFront distribution managed by AWS Amplify in the background.
* Enable AWS WAF to protect the web application.
* Review Amazon Route 53 and the option of using a custom domain.
* Perform end-to-end system testing and control project costs.

### Tasks to Be Completed This Week:

| Day       | Tasks                                                                                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Materials                                                                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monday    | - Initialize the Next.js project. <br> - Build the login interface. <br> - Build a dashboard displaying Rooms, Telemetry, Alerts, and Reports. <br> - Integrate Amazon Cognito with the frontend.                                                                                                                                           | 29/06/2026 | 29/06/2026      | https://nextjs.org/docs/app/getting-started                                                                                                             |
| Tuesday   | - Connect the frontend to API Gateway. <br> - Send the Access Token in the Authorization Header. <br> - Implement sign-in, session persistence, and sign-out functions. <br> - Test downloading JSON reports from Amazon S3.                                                                                                                | 30/06/2026 | 30/06/2026      | https://docs.amplify.aws/ <br> https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-jwt-authorizer.html                                |
| Wednesday | - Upload the source code to the energy-waste-dashboard GitHub repository. <br> - Create an AWS Amplify application. <br> - Connect the repository and the main branch. <br> - Configure Environment Variables. <br> - Deploy the dashboard using Amplify Hosting.                                                                       | 01/07/2026 | 01/07/2026      | https://docs.github.com/en/repositories <br> https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html                                          |
| Thursday  | - Review the CloudFront distribution managed by Amplify Hosting. <br> - Confirm that a separate CloudFront Distribution is not required. <br> - Enable Amplify-recommended Firewall Protection. <br> - Review AWS Managed Rules and Sampled Requests. <br> - Review Route 53 and custom domain configuration.                               | 02/07/2026 | 02/07/2026      | https://docs.aws.amazon.com/amplify/latest/userguide/WAF-integration.html <br> https://docs.aws.amazon.com/amplify/latest/userguide/custom-domains.html |
| Friday    | - Perform end-to-end testing of the entire system. <br> - Test EventBridge, Lambda, AWS IoT Core, DynamoDB, and Amazon SNS. <br> - Test Amazon Cognito, API Gateway, AWS Amplify, and the dashboard. <br> - Test report generation and downloading from Amazon S3. <br> - Disable EventBridge Scheduler and remove AWS WAF to reduce costs. | 03/07/2026 | 03/07/2026      | https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html               |

### Week 11 Achievements:

* I built a Next.js dashboard with sign-in, sign-out, Telemetry, Alerts, and Reports features.

* I connected the frontend to Amazon Cognito and API Gateway.

* I uploaded the source code to the energy-waste-dashboard GitHub repository.

* I successfully deployed the application using AWS Amplify Hosting.

* I confirmed that AWS Amplify uses CloudFront in the background and that a separate CloudFront Distribution was not required.

* I enabled AWS WAF protection for the Amplify application.

* I reviewed the AWS Managed Rule Groups and Sampled Requests.

* I reviewed Amazon Route 53 and attempted to register a custom domain.

* The custom domain registration process was not completed because the domain registration request failed.

* I confirmed that alert emails were successfully sent through Amazon SNS.

* I verified that the JSON report was generated and stored in Amazon S3.

* I confirmed that direct access through the Object URL returned an AccessDenied response, while authenticated users could download the report using a Pre-signed URL.

* I disabled the EventBridge Scheduler schedules after testing.

* I removed AWS WAF from the application to minimize additional costs.

* The tasks completed in Week 11 finalized the user interface, production deployment, security configuration, and end-to-end testing of the entire system.
