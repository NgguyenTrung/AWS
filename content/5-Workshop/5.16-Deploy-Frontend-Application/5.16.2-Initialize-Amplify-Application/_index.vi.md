---
title : "Khởi tạo Ứng dụng trên AWS Amplify"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.16.2 </b> "
---

#### 1. Tạo  AWS Amplify Hosting

##### Bước 1: Truy cập AWS Amplify

1. Đăng nhập vào **AWS Management Console**.
2. Kiểm tra Region ở góc trên bên phải là:

```text
Asia Pacific (Singapore)
ap-southeast-1
```

3. Tại thanh tìm kiếm của AWS Console, nhập:

```text
Amplify
```

4. Chọn dịch vụ:

```text
AWS Amplify
```

##### Bước 2: Bắt đầu triển khai ứng dụng

1. Tại trang **All apps**, nhấn:

```text
Create new app
```

Một số giao diện có thể hiển thị nút:

```text
Deploy an app
```

2. Tại phần chọn nhà cung cấp mã nguồn, chọn:

```text
GitHub
```

3. Nhấn:

```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/Amplify1.png)

##### Bước 3: Chọn repository và branch

1. Tại phần **Repository**, chọn:

```text
energy-waste-dashboard
```

2. Tại phần **Branch**, chọn:

```text
main
```

3. Nhấn:

```text
Next
```
![Amplify Source Provider](/images/5-Workshop/5.16/Amolyfy2.png)
##### Bước 4: Kiểm tra App settings

Tại trang **App settings**, kiểm tra tên ứng dụng:

```text
App name:
energy-waste-dashboard
```

AWS Amplify phải tự nhận diện Framework là:

```text
Next.js
```

Kiểm tra phần **Build settings**:

```text
Frontend build command:
npm run build
```

```text
Build output directory:
.next
```

Giữ nguyên các thiết lập:

```text
Build instance type:
Standard
```

```text
Build image:
Amazon Linux 2023
```


 Kéo xuống phần:

```text
Advanced settings
```

 Mở rộng phần này để tìm:

```text
Environment variables
```
```text
Advanced settings
→ Environment variables
```

Nhấn:

```text
Add new
```

Mỗi biến môi trường gồm hai cột:

```text
Key
Value
```

#####  Thêm biến AWS Region

Tại dòng đầu tiên, nhập:

```text
Key:
NEXT_PUBLIC_AWS_REGION
```

```text
Value:
ap-southeast-1
```

##### Thêm Cognito User Pool ID

Nhấn:

```text
Add new
```

Nhập:

```text
Key:
NEXT_PUBLIC_COGNITO_USER_POOL_ID
```

```text
Value:
ap-southeast-1_OiGmvapoL
```

Nhấn:

```text
Add new
```

Nhập:

```text
Key:
NEXT_PUBLIC_COGNITO_CLIENT_ID
```

```text
Value:
42bod21u3a1g499u643mt056fm
```


Nhấn:

```text
Add new
```

Nhập:

```text
Key:
NEXT_PUBLIC_API_BASE_URL
```

```text
Value:
https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com
```
Nhấn:
```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings32.png)
![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings33.png)

Nhấn:
```text
Next
```
![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings34.png)
Nhấn:
```text
Save and deploy
```
![Amplify Source Provider](/images/5-Workshop/5.16/04-amplify-build-deployed.png)