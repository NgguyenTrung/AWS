---
title: "5.4.2 Khởi tạo Dữ liệu Mẫu (Room Item)"
weight: 2
description: "Chèn một bản ghi dữ liệu phòng mẫu bằng định dạng JSON để kiểm tra hoạt động của bảng."
---


Bây giờ, chúng ta sẽ tạo một bản ghi (item) mẫu để chứng minh bảng hoạt động ổn định.

### Các bước thực hiện:

1. Điều hướng theo sơ đồ: `DynamoDB` ➔ `Tables` ➔ chọn bảng `EnergyWasteData`.
2. Nhấp chọn nút **Explore table items** ở góc trên cùng bên phải.

![Truy cập giao diện Explore Table Items](/images/5-Workshop/5.4-dynamodb/11.png)

1. Nhấp tiếp vào nút **Create item**.
2. Trên giao diện nhập, bấm chọn nút chuyển đổi sang chế độ **JSON view**.
3. Sao chép và dán đoạn mã dữ liệu JSON dưới đây vào khung soạn thảo:

```json
{
  "PK": {
    "S": "ROOM#lab-01"
  },
  "SK": {
    "S": "PROFILE"
  },
  "entityType": {
    "S": "Room"
  },
  "roomId": {
    "S": "lab-01"
  },
  "roomName": {
    "S": "Smart Home Lab"
  },
  "powerThresholdW": {
    "N": "120"
  },
  "createdBy": {
    "S": "manual-console"
  }
}