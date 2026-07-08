---
title: "5.6.1 Create function"
weight: 1
---



To begin processing the telemetry data flow from the IoT system, we need to create a serverless compute function using AWS Lambda.

### Steps:

1. In the search bar at the top of the **AWS Management Console**, enter `Lambda`.
2. Select the **Lambda** service from the search results.
3. In the left navigation menu, select **Functions**.
4. Click the **Create function** button in the upper-right corner.

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-open-create-function.png)

1. On the **Create function** page, configure the following settings:
   * Select **Author from scratch**.
   * **Function name:** `energy-waste-detector`
   * **Runtime:** Select `Python 3.14`.

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-additional-settings.png)

2. Finally, click the **Create function** button at the bottom of the page to complete the function creation process.

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-created.png)