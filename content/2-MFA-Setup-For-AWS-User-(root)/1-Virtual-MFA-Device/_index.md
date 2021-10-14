+++
title = "Virtual MFA Devices"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note%}}
To enable MFA, you need to log in to AWS using the root user. 
{{% /notice%}}

#### Activate virtual MFA devices via Console

To set up and activate virtual MFA devices:

1. Sign-in to the AWS Console.
2. In the upper right corner, you will see your account name. Click the drop-down and select **My Security Credentials**.

![Virtual MFA Device](/images/1-account-setup/MySecurity_v1.png?width=15pc)

3. Expand **Multi-factor authentication (MFA)** and select **Active MFA**.

![MFA Section](/images/1-account-setup/MFA.png?width=90pc)

4. In Manage MFA Device, select **Virtual MFA device** then select **Continue**.
5. Install a [compatible Authenticator application](https://aws.amazon.com/iam/features/mfa/#Virtual_MFA_Applications) on your phone.
6. After installing the app, select **Show QR Code** and use your Authenticator application to scan the QR code.
   - Sample MFA registration with _Microsoft Authenticator_:
      ![MFA QR Scanner](/images/1-account-setup/MFAScannerQR.png?width=90pc)
1. In the **MFA code 1** box, enter 6 numeric characters from the app. Wait 30 seconds or until the next refresh, then enter the next 6 characters into the **MFA Code 2** box and select **Assign MFA**.
2. You have now completed activating your **virtual MFA device**!
