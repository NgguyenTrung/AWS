---
title: "5.4.1 Configure Table Details & Settings"
weight: 1
description: "Set up core parameters including Partition key, Sort key, and Capacity mode for DynamoDB."
---

# 5.4.1 Configure Table Details

On the table creation page, proceed to fill in the core configuration details exactly as follows:

### 1. Table Details
* **Table name:** `EnergyWasteData`
* **Partition key:** `PK` (Data type: **String**)
* **Sort key - optional:** `SK` (Data type: **String**)

> ⚠️ **CRITICAL NOTE:** 
> You must capitalize **PK** and **SK** exactly as shown. DO NOT write them as lower-case `pk`, `sk`, `roomId`, or `id`. The backend Lambda function code will interact directly with these exact capitalized keys later on.

![Table Details Configuration](/images/5-Workshop/5.4-dynamodb/dynamodb-open-create-table.png)

---

### 2. Table Settings

Scroll down to configure advanced options optimized for this workshop environment:

* Under **Table settings**, select **Customize settings**.
* Under **Table class**, select **DynamoDB Standard**.
* Under **Read/write capacity settings** ➔ **Capacity mode**, select: **On-demand**.

> 💡 **Why choose On-demand?** This demo project does not require pre-provisioned read/write capacity limits. Selecting On-demand reduces configuration steps and fits perfectly for workshop execution.

![On-demand Capacity Mode Configuration](/images/5-Workshop/5.4-dynamodb/dynamodb-table-details.png)

### 3. Finalize Other Default Settings
* **Secondary indexes:** Leave blank (Do not create).
* **Encryption:** Keep *AWS owned key* or default.
* **Deletion protection:** Temporarily set to **Off**.
* **Tags:** Can be skipped.

After reviewing all properties, click the **Create table** button at the bottom. The system will initialize the table until its status switches to **Active**.

![DynamoDB Table in Active Status](/images/5-Workshop/5.4-dynamodb/dynamodb-on-demand-settings.png)