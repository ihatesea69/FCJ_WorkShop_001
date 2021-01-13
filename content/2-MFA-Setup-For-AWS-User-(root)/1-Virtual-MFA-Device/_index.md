+++
title = "Virtual MFA Device"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note %}}
To enable MFA, you must signed in AWS using your root user.
{{% /notice %}}

#### Enable a Virtual MFA Device using Console

To configure and enable a virtual MFA device:

1. Sign in to AWS Console.
2. In the top right of the navigation bar, you will see your account name, choose it and choose **My Security Credentials** then expand Multi-factor authentication (MFA).

![Virtual MFA Device](/images/1-account-setup/MySecurity.png?width=15pc)

3. Choose **Active MFA**.
4. In Manage MFA Device, choose **Virutal MFA device** then choose **Continue**.
5. Install a compatible app on your mobile device or computer. [List of the application](https://aws.amazon.com/iam/features/mfa/?audit=2019q1).
6. After install application on your device, scan the QR code.
7. In the MFA code 1, enter six digit number, wait 30 seconds enter the next six digit number and choose **Assign MFA**.
8. Now you have done to enable **Virtual MFA Device**.
