---
title : "Configure CORS and Security Origins"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.16.4 </b> "
---

####  Update API Gateway CORS

Go to:

```text
API Gateway
→ APIs
→ energy-waste-http-api
→ CORS
→ Edit
```

Configure:

**Allow origins**

```text
http://localhost:3000
https://main.d2ppdnlr5ik3e8.amplifyapp.com
```

**Allow headers**

```text
authorization
content-type
```

**Allow methods**

```text
GET
OPTIONS
```

**Expose headers**

```text
Để trống
```

**Max age**

```text
300
```

**Allow credentials**

```text
Off
```

Bấm:

```text
Save
```

![Giao diện Đăng nhập](/images/5-Workshop/5.16/Allow-origins.png)