---
title : "SNS Email Alert"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Khi bạn tạo một Interface Endpoint hoặc gateway, bạn có thể đính kèm một chính sách điểm cuối để kiểm soát quyền truy cập vào dịch vụ mà bạn đang kết nối. Chính sách VPC Endpoint là chính sách tài nguyên IAM mà bạn đính kèm vào điểm cuối. Nếu bạn không đính kèm chính sách khi tạo điểm cuối, thì AWS sẽ đính kèm chính sách mặc định cho bạn để cho phép toàn quyền truy cập vào dịch vụ thông qua điểm cuối.

Bạn có thể tạo chính sách chỉ hạn chế quyền truy cập vào các S3 bucket cụ thể. Điều này hữu ích nếu bạn chỉ muốn một số Bộ chứa S3 nhất định có thể truy cập được thông qua điểm cuối.

Trong phần này, bạn sẽ tạo chính sách VPC Endpoint hạn chế quyền truy cập vào S3 bucket được chỉ định trong chính sách VPC Endpoint.

![sns-open-create-topic](/images/5-Workshop/5.5-sns-email-alert/sns-open-create-topic.png)

![sns-topic-config](/images/5-Workshop/5.5-sns-email-alert/sns-topic-config.png)

![sns-topic-created](/images/5-Workshop/5.5-sns-email-alert/sns-topic-created.png)

![ns-create-email-subscription](/images/5-Workshop/5.5-sns-email-alert/sns-create-email-subscription.png)

![sns-email-confirmed-browser](/images/5-Workshop/5.5-sns-email-alert/sns-email-confirmed-browser.png)

![sns-subscription-confirmed](/images/5-Workshop/5.5-sns-email-alert/sns-subscription-confirmed.png)

![sns-publish-test-message](/images/5-Workshop/5.5-sns-email-alert/sns-publish-test-message.png)

![sns-test-email-received](/images/5-Workshop/5.5-sns-email-alert/sns-test-email-received.png)