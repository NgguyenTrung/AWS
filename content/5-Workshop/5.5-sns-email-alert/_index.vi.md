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

![endpoint diagram](/images/5-Workshop/5.5-sns-email-alert/s3-bucket-policy.png)

#### Kết nối tới một EC2 instance và xác minh kết nối tới S3

1. Bắt đầu một phiên AWS Session Manager mới trên instance có tên Test-Gateway-Endpoint. Từ phiên này, xác minh rằng bạn có thể liệt kê nội dung của bucket mà bạn đã tạo trong Phần 1: Truy cập S3 từ VPC:

\\\
aws s3 ls s3://<your-bucket-name>
\\\
![test](/images/5-Workshop/5.5-sns-email-alert/test1.png)

Nội dung bucket bao gồm hai tệp 1 GB được tải lên trước đó.

2. Tạo một bucket S3 mới; tuân theo mẫu đặt tên mà bạn đã sử dụng trong Phần 1, nhưng thêm '-2' vào tên. Để các trường khác là mặc định và nhấp vào create

![create bucket](/images/5-Workshop/5.5-sns-email-alert/create-bucket.png)

Tạo bucket thành công

![Success](/images/5-Workshop/5.5-sns-email-alert/create-bucket-success.png)

3. Điều hướng đến: Services > VPC > Endpoints, sau đó chọn Gateway VPC endpoint mà bạn đã tạo trước đó. Nhấp vào tab Policy. Nhấp vào Edit policy.

![policy](/images/5-Workshop/5.5-sns-email-alert/policy1.png)

Chính sách mặc định cho phép truy cập vào tất cả các S3 Buckets thông qua VPC endpoint.

4. Trong bảng điều khiển Edit Policy, sao chép & dán chính sách sau, sau đó thay thế yourbucketname-2 bằng tên bucket thứ hai của bạn. Chính sách này sẽ cho phép truy cập thông qua VPC endpoint vào bucket mới của bạn, nhưng không cho phép truy cập vào bất kỳ bucket nào khác trong Amazon S3. Nhấp vào Save để áp dụng chính sách.

\\\
{
  "Id": "Policy1631305502445",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1631305501021",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": [
      "arn:aws:s3:::yourbucketname-2",
       "arn:aws:s3:::yourbucketname-2/*"
       ],
      "Principal": "*"
    }
  ]
}
\\\

![custom policy](/images/5-Workshop/5.5-sns-email-alert/policy2.png)

Tùy chỉnh chính sách thành công

![success](/static/images/5-Workshop/5.5-sns-email-alert/success.png)

5. Từ phiên của bạn trên instance Test-Gateway-Endpoint, kiểm tra quyền truy cập vào S3 bucket mà bạn đã tạo trong Phần 1: Truy cập S3 từ VPC
\\\
aws s3 ls s3://<yourbucketname>
\\\

Lệnh này sẽ trả về lỗi vì quyền truy cập vào bucket này không được phép bởi chính sách VPC endpoint mới của bạn:

![error](/static/images/5-Workshop/5.5-sns-email-alert/error.png)

6. Quay lại thư mục home của bạn trên EC2 instance \ cd~ \

+ Tạo một tệp \\\allocate -l 1G test-bucket2.xyz \\\
+ Sao chép tệp vào bucket thứ 2 \\\ws s3 cp test-bucket2.xyz s3://<your-2nd-bucket-name>\\\

![success](/static/images/5-Workshop/5.5-sns-email-alert/test2.png)

Thao tác này thành công vì nó được phép bởi chính sách VPC endpoint.

![success](/static/images/5-Workshop/5.5-sns-email-alert/test2-success.png)

+ Sau đó chúng tôi kiểm tra quyền truy cập vào bucket đầu tiên bằng cách sao chép tệp vào bucket thứ 1 \ws s3 cp test-bucket2.xyz s3://<your-1st-bucket-name>\

![fail](/static/images/5-Workshop/5.5-sns-email-alert/test2-fail.png)

Lệnh này sẽ trả về lỗi vì quyền truy cập vào bucket này không được phép bởi chính sách VPC endpoint mới của bạn.

#### Tóm tắt Phần 3:

Trong phần này, bạn đã tạo chính sách VPC endpoint cho Amazon S3 và sử dụng AWS CLI để kiểm tra chính sách. Các hành động AWS CLI nhắm đến bucket S3 ban đầu của bạn đã không thành công vì bạn đã áp dụng chính sách chỉ cho phép truy cập vào bucket thứ hai mà bạn đã tạo. Các hành động AWS CLI nhắm đến bucket thứ hai của bạn đã thành công vì chính sách đã cho phép chúng. Những chính sách này có thể hữu ích trong các tình huống mà bạn cần kiểm soát quyền truy cập vào tài nguyên thông qua VPC endpoints.
