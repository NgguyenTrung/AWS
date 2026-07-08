---
title : "Cấu hình Rate mỗi 1 phút"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.9.2 </b> "
---

1. **Chọn loại Schedule**
   + Tại **Schedule type**, chọn: **Rate-based schedule**.
   + Không chọn: `Cron-based schedule`.
   + Nhập `rate(1 minute)` vào ô **Rate expression**, hoặc điền **Value:** `1` và **Unit:** `minute`. Lưu ý dùng số ít `minute`, không nhập `minutes`.

2. **Flexible time window**
   + Tại **Flexible time window**, chọn: **Off**.
   + Khi bị tắt, Scheduler không được phép trì hoãn invocation.

3. **Timeframe**
   + Giữ **Start date and time** và **End date and time** để trống.
   + Có thể giữ Timezone là **UTC**.

4. Bấm: **Next**.

![Rate Settings](/images/5-Workshop/5.9-EventBridge/01-cau-hinh-schedule-moi-phut.png)