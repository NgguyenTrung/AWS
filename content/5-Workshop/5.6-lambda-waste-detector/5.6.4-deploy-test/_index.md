---
title: "5.6.4 Deploy test"
weight: 1
---



After completing the system configuration and security permissions, we will add the core Python processing logic to the Lambda function, run a test using simulated data, and verify the results in the output services.

### Steps:

1. Return to the **energy-waste-detector** Lambda function page and select the **Code** tab.
2. In the file explorer on the left, double-click the `lambda_function.py` file.
3. Delete all default placeholder code in the editor, then paste the complete core processing logic below:

```python
import json
import os
import uuid
from datetime import datetime, timezone
from decimal import Decimal

import boto3


DDB_TABLE = os.environ.get("DDB_TABLE", "EnergyWasteData")
SNS_TOPIC_ARN = os.environ.get("SNS_TOPIC_ARN", "")
POWER_THRESHOLD_W = float(os.environ.get("POWER_THRESHOLD_W", "120"))

dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
sns = boto3.client("sns")


def now_utc_iso():
    return datetime.now(timezone.utc).isoformat().replace("+00:00", "Z")


def to_dynamodb_value(value):
    if isinstance(value, float):
        return Decimal(str(value))

    if isinstance(value, dict):
        return {k: to_dynamodb_value(v) for k, v in value.items()}

    if isinstance(value, list):
        return [to_dynamodb_value(v) for v in value]

    return value


def parse_bool(value):
    if isinstance(value, bool):
        return value

    if isinstance(value, str):
        return value.strip().lower() in ["true", "1", "yes", "y", "on"]

    return bool(value)


def lambda_handler(event, context):
    print("Received event:")
    print(json.dumps(event, ensure_ascii=False))

    timestamp = event.get("timestamp") or now_utc_iso()

    room_id = event.get("roomId", "lab-01")
    sensor_id = event.get("sensorId", "virtual-sensor-01")
    device_id = event.get("deviceId", "unknown-device")
    device_name = event.get("deviceName", device_id)

    device_status = str(event.get("deviceStatus", "UNKNOWN")).strip().upper()
    occupancy = parse_bool(event.get("occupancy", True))
    power_w = float(event.get("powerW", 0))
    voltage_v = float(event.get("voltageV", 220))
    current_a = float(event.get("currentA", 0))
    energy_kwh = float(event.get("energyKwh", 0))

    is_waste = (
        device_status == "ON"
        and occupancy is False
        and power_w >= POWER_THRESHOLD_W
    )

    telemetry_item = {
        "PK": f"ROOM#{room_id}",
        "SK": f"TELEMETRY#{timestamp}#{sensor_id}",
        "entityType": "Telemetry",
        "roomId": room_id,
        "sensorId": sensor_id,
        "deviceId": device_id,
        "deviceName": device_name,
        "deviceStatus": device_status,
        "occupancy": occupancy,
        "powerW": power_w,
        "voltageV": voltage_v,
        "currentA": current_a,
        "energyKwh": energy_kwh,
        "timestamp": timestamp,
        "isWaste": is_waste,
        "source": "lambda-test-or-iot-core"
    }

    table.put_item(Item=to_dynamodb_value(telemetry_item))
    print("Telemetry stored in DynamoDB.")

    alert_sent = False

    if is_waste:
        alert_id = str(uuid.uuid4())[:8]

        message = (
            f"Energy waste detected in room {room_id}. "
            f"Device {device_name} is ON, room is empty, "
            f"power is {power_w}W, threshold is {POWER_THRESHOLD_W}W."
        )

        alert_item = {
            "PK": f"ROOM#{room_id}",
            "SK": f"ALERT#{timestamp}#{alert_id}",
            "entityType": "Alert",
            "alertId": alert_id,
            "roomId": room_id,
            "sensorId": sensor_id,
            "deviceId": device_id,
            "deviceName": device_name,
            "severity": "HIGH",
            "alertType": "ENERGY_WASTE",
            "message": message,
            "powerW": power_w,
            "thresholdW": POWER_THRESHOLD_W,
            "deviceStatus": device_status,
            "occupancy": occupancy,
            "timestamp": timestamp,
            "status": "OPEN"
        }

        table.put_item(Item=to_dynamodb_value(alert_item))
        print("Alert stored in DynamoDB.")

        if SNS_TOPIC_ARN:
            sns.publish(
                TopicArn=SNS_TOPIC_ARN,
                Subject="[AWS Energy Waste Alert]",
                Message=json.dumps(alert_item, indent=2, ensure_ascii=False, default=str)
            )
            alert_sent = True
            print("Alert email published to SNS.")

    return {
        "statusCode": 200,
        "body": {
            "message": "Telemetry processed successfully",
            "isWaste": is_waste,
            "alertSent": alert_sent,
            "roomId": room_id,
            "deviceId": device_id,
            "powerW": power_w
        }
    }
```

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-code-deployed.png)

### 4. Test the Lambda Waste Detector

On the Lambda function page:

```text
energy-waste-detector
```

Click:

```text
Test
```

Select:

```text
Create new event
```

Enter the event name:

```text
test_waste_event
```

In the **Event JSON** section, enter:

```json
{
  "sensorId": "virtual-sensor-01",
  "roomId": "lab-01",
  "timestamp": "2026-07-01T10:00:00Z",
  "deviceId": "aircon-01",
  "deviceName": "Air Conditioner",
  "deviceStatus": "ON",
  "occupancy": false,
  "powerW": 180,
  "voltageV": 220,
  "currentA": 0.82,
  "energyKwh": 1.25
}
```

Click:

```text
Save
```

Then click:

```text
Test
```

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-test-event.png)

After running the test:

![](/images/5-Workshop/5.6-lambda-waste-detector/lambda-waste-detector-test-success.png)

### 5. Verify the data in DynamoDB

Go to:

```text
DynamoDB
→ Tables
→ EnergyWasteData
→ Explore table items
```

Verify that the table contains new items in the following formats:

```text
TELEMETRY#2026-07-01T10:00:00Z#virtual-sensor-01
```

```text
ALERT#2026-07-01T10:00:00Z#...
```

Where:

- The `TELEMETRY` item stores the sensor data that was submitted.
- The `ALERT` item is created when the Lambda Waste Detector detects that a device is turned on while the room is unoccupied.

![](/images/5-Workshop/5.6-lambda-waste-detector/ambda-waste-detector-dynamodb-items.png)

Open Gmail. You should receive a new alert email from Amazon SNS:

![](/images/5-Workshop/5.6-lambda-waste-detector/ambda-waste-detector-email-alert.png)