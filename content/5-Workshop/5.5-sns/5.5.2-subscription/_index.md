---
title: "5.5.2 Register & Confirm Email Subscription"
weight: 2
description: "Bind a targeted notification email endpoint to the SNS Topic and execute subscription verification actions."
---



With the parent topic established, we must couple a communication endpoint to process outbound notification payloads. This laboratory relies on the **Email** transfer mechanism.

### Step 1: Initiate Subscription in the Console

1. On the detail sheet for `energy-waste-alert-topic`, navigate down to the **Subscriptions** pane.
2. Click the **Create subscription** button.
3. Populate the field variables using the properties below:
   * **Topic ARN:** Leave untouched (it references the active topic context automatically).
   * **Protocol:** Click the option dropdown list and choose **Email**.
   * **Endpoint:** Provide your personal, active email address where alert items should be redirected.

![Configuring Email Subscription Settings](/images/5-Workshop/5.5-sns/sns-topic-created.png)

1. Click the **Create subscription** action button.

---

### Step 2: Approve the Subscription Request

AWS messaging workflows invoke a safety constraint requiring owner validation before distributing data.

1. Access the webmail inbox corresponding to the target endpoint configured previously.
2. Look for an automated delivery item arriving from **AWS Notifications**.
3. Expand the mail message view and click the embedded **Confirm subscription** link text.

Your internet browser will open a secondary workspace pane rendering a successful **Subscription confirmed!** block alongside the unique subscription identity string.

![Browser Displaying Subscription Confirmed](/images/5-Workshop/5.5-sns/sns-create-email-subscription.png)

---

### Step 3: Audit State Verification on AWS Console

1. Return to the **AWS Console** terminal layout under `SNS` ➔ `Topics` ➔ `energy-waste-alert-topic`.
2. Examine the records pool within the **Subscriptions** layout block (Click the refresh reload option if mandatory).
3. Assure that the data column attribute value transitions from *Pending confirmation* to a green label: **Confirmed**.

![Confirming Subscription Status Validation](/images/5-Workshop/5.5-sns/sns-subscription-confirmed.png)