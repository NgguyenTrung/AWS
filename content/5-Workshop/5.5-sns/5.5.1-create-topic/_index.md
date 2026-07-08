---
title: "5.5.1 Create SNS Topic"
weight: 1
description: "Configure Standard Topic classification with customized Name and Display Name attributes."
---



Proceed to initialize the required identity parameters for your messaging hub using the configuration values detailed below:

### Specification Criteria:

* **Type:** Select the **Standard** option.
* **Name:** `energy-waste-alert-topic`
* **Display name - optional:** `EnergyWasteAlert`

> 💡 **Architecture Insight:** Unlike FIFO profiles which guarantee strict ordering, the **Standard** delivery type yields maximum throughput performance while supporting an expansive set of endpoint protocols including Lambda, Email, and SQS, matching our dynamic energy monitoring requirements.

![SNS Topic Attribute Setup](/images/5-Workshop/5.5-sns/sns-open-create-topic.png)

Once you complete entering the parameters above, scroll to the bottom of the section and click the **Create topic** button.

The console interface will refresh to reveal a green banner reading: *"Topic energy-waste-alert-topic created successfully."*, indicating the asset is ready for target registration.

![Confirming Successful Topic Creation](/images/5-Workshop/5.5-sns/sns-topic-config.png)