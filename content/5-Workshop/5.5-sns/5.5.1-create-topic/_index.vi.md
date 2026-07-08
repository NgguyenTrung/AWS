---
title: "5.5.1 Khởi tạo SNS Topic"
weight: 1
description: "Cấu hình phân loại Standard Topic kèm định danh Name và Display Name phục vụ phát thông điệp."
---



Tiến hành thiết lập các tham số định danh cốt lõi cho kênh thông báo (Topic) theo quy chuẩn dưới đây:

### Các thông số cấu hình cụ thể:

* **Type:** Lựa chọn loại hình **Standard**.
* **Name:** `energy-waste-alert-topic`
* **Display name - optional:** `EnergyWasteAlert`

> 💡 **Mẹo thiết lập:** Khác với định dạng FIFO yêu cầu quản lý nghiêm ngặt về thứ tự, chế độ **Standard** cung cấp hiệu năng truyền tải thông tin tối đa, hỗ trợ đa dạng giao thức như Lambda, Email, SQS và hoàn toàn đáp ứng tốt bài toán cảnh báo lãng phí năng lượng của workshop.

![Cấu hình thuộc tính SNS Topic](/images/5-Workshop/5.5-sns/sns-open-create-topic.png)


Sau khi hoàn tất việc điền các thông tin trên, cuộn chuột xuống cuối trang và nhấn chọn nút **Create topic**.

Hệ thống sẽ chuyển hướng và hiển thị một biểu ngữ thông báo màu xanh lá cây với nội dung: *"Topic energy-waste-alert-topic created successfully."* để xác nhận tiến trình tạo thành công.

![Xác nhận Topic khởi tạo thành công](/images/5-Workshop/5.5-sns/sns-topic-config.png)