---
title: "5.5.3 Test Publishing a Message"
weight: 3
description: "Simulate a live JSON formatted energy waste alert and verify the email delivery."
---


To verify that the communication pipeline works correctly, we will manually publish a test message directly from the AWS Console.

### Step-by-Step Instructions:

1. On the **energy-waste-alert-topic** detail page, click the **Publish message** button at the top right.
2. In the **Message details** section, configure the subject:
   * **Subject - optional:** `Test energy waste alert`
3. Scroll down to the **Message body** section:
   * Select **Identical payload for all delivery protocols**.
   * Copy the following JSON payload (which simulates an energy waste event) and paste it into the text box:

```json
{
  "alertType": "ENERGY_WASTE",
  "roomId": "lab-01",
  "deviceId": "aircon-01",
  "deviceStatus": "ON",
  "occupancy": false,
  "powerW": 180,
  "message": "Test alert from Amazon SNS for Smart Home Energy Waste Monitoring System."
}