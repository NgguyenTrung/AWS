---
title : "Initialize Amplify Application"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.16.2 </b> "
---


#### 1. Create AWS Amplify Hosting

##### Step 1: Access AWS Amplify

1. Sign in to the **AWS Management Console**.
2. Verify that the Region in the upper-right corner is:

```text
Asia Pacific (Singapore)
ap-southeast-1
```

3. In the AWS Console search bar, enter:

```text
Amplify
```

4. Select the following service:

```text
AWS Amplify
```

##### Step 2: Start deploying the application

1. On the **All apps** page, click:

```text
Create new app
```

Some interfaces may display the following button instead:

```text
Deploy an app
```

2. In the source code provider section, select:

```text
GitHub
```

3. Click:

```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/Amplify1.png)

##### Step 3: Select the repository and branch

1. In the **Repository** section, select:

```text
energy-waste-dashboard
```

2. In the **Branch** section, select:

```text
main
```

3. Click:

```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/Amolyfy2.png)

##### Step 4: Verify the App settings

On the **App settings** page, verify the application name:

```text
App name:
energy-waste-dashboard
```

AWS Amplify should automatically detect the framework as:

```text
Next.js
```

Verify the **Build settings** section:

```text
Frontend build command:
npm run build
```

```text
Build output directory:
.next
```

Keep the following settings unchanged:

```text
Build instance type:
Standard
```

```text
Build image:
Amazon Linux 2023
```

Scroll down to the following section:

```text
Advanced settings
```

Expand this section to find:

```text
Environment variables
```

```text
Advanced settings
→ Environment variables
```

Click:

```text
Add new
```

Each environment variable contains two columns:

```text
Key
Value
```

##### Add the AWS Region variable

In the first row, enter:

```text
Key:
NEXT_PUBLIC_AWS_REGION
```

```text
Value:
ap-southeast-1
```

##### Add the Cognito User Pool ID

Click:

```text
Add new
```

Enter:

```text
Key:
NEXT_PUBLIC_COGNITO_USER_POOL_ID
```

```text
Value:
ap-southeast-1_OiGmvapoL
```

Click:

```text
Add new
```

Enter:

```text
Key:
NEXT_PUBLIC_COGNITO_CLIENT_ID
```

```text
Value:
42bod21u3a1g499u643mt056fm
```

Click:

```text
Add new
```

Enter:

```text
Key:
NEXT_PUBLIC_API_BASE_URL
```

```text
Value:
https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com
```

Click:

```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings32.png)
![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings33.png)

Click:

```text
Next
```

![Amplify Source Provider](/images/5-Workshop/5.16/AWS-Amplify-Build-settings34.png)

Click:

```text
Save and deploy
```

![Amplify Source Provider](/images/5-Workshop/5.16/04-amplify-build-deployed.png)
