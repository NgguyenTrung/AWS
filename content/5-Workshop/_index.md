---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Secure Hybrid Access to S3 using VPC Endpoints

#### Overview

**AWS PrivateLink** provides private connectivity to AWS services from VPCs and your on-premises networks, without exposing your traffic to the Public Internet.

In this lab, you will learn how to create, configure, and test VPC endpoints that enable your workloads to reach AWS services without traversing the Public Internet.

You will create two types of endpoints to access Amazon S3: a Gateway VPC endpoint, and an Interface VPC endpoint. These two types of VPC endpoints offer different benefits depending on if you are accessing Amazon S3 from the cloud or your on-premises location.

#### Content

1. [Workshop overview](5.1-workshop-overview/)
2. [Prerequisite](5.2-prerequisite/)
3. [Budget and region](5.3-budget-and-region/)
4. [DynamoDB](5.4-dynamodb/)
5. [SNS email alert](5.5-sns-email-alert/)
6. [Lambda waste detector](5.6-lambda-waste-detector/)
7. [Lambda virtual sensor](5.7-lambda-virtual-sensor/)
8. [IoT Core rule](5.8-iot-core-rule/)
9. [EventBridge schedule](5.9-eventbridge-schedule/)
10. [CloudWatch testing](5.10-cloudwatch-testing/)
11. [Cognito user pool](5.11-cognito-user-pool/)
12. [API Gateway HTTP API](5.12-api-gateway-http-api/)
13. [Lambda API handler](5.13-lambda-api-handler/)
14. [S3 report bucket](5.14-s3-report-bucket/)
15. [Lambda report generator](5.15-lambda-report-generator/)
16. [Next.js + Amplify](5.16-nextjs-amplify/)
17. [CloudFront, WAF, custom domain](5.17-cloudfront-waf-custom-domain/)
18. [End-to-end testing](5.18-end-to-end-testing/)
19. [Cleanup](5.19-cleanup/)
