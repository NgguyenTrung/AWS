---
title: "5.5.3 Thử nghiệm xuất bản dữ liệu (Publish Message)"
weight: 3
description: "Mô phỏng phát tín hiệu cảnh báo lãng phí năng lượng dạng JSON và rà soát kết quả thư nhận được."
---



Nhằm đảm bảo luồng tin tức luân chuyển chính xác, chúng ta sẽ thực hiện kiểm thử thủ công tính năng xuất bản thông điệp trực tiếp từ bảng điều khiển quản trị.

### Các bước thực hiện:

1. Tại màn hình làm việc của topic `energy-waste-alert-topic`, nhấn chọn nút **Publish message** ở góc bên phải.
2. Trong hộp thoại cấu hình chi tiết thông điệp (Message details), thiết lập tiêu đề thư:
   * **Subject - optional:** `Test energy waste alert`
3. Di chuyển tiếp đến phần cấu hình thân bài viết (**Message body**):
   * Chọn cấu hình mặc định: **Identical payload for all delivery protocols**.
   * Sao chép đoạn mã JSON mô phỏng gói tin sự kiện lãng phí điện năng của phòng thiết bị dưới đây và dán vào ô nhập liệu:

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