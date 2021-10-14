+++
title = "Hardware MFA Device"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

{{%notice info%}}
The following steps require a hardware MFA device.
{{%/notice%}}

#### Enabling a hardware MFA device through Console

A hardware MFA device generates a six-digit numeric code based upon a time-synchronized one-time password algorithm. 
Hardware MFA devices and U2F security keys are both physical devices that you purchase. The difference is that hardware MFA devices generate a code that you view and then enter when prompted when signing it to AWS. 

1. Sign-in to the AWS Console.
2. In the upper right corner, you'll see your account name, select and select **My Security Credentials**.

![Image](/images/1-account-setup/MySecurity_v1.png?width=15pc)

**Note:** To manage a hardware MFA device for your own IAM user while protecting sensitive MFA-related actions, you must have the permissions from the following policy.
<!-- policy not associated with user -->
> 1. In the left bar, select **Policies** then select **Create policy**. Select **JSON** tab and paste the policy document from below:
> 
> ```json
> {
>     "Version": "2012-10-17",
>     "Statement": [
>         {
>             "Sid": "AllowManageOwnUserMFA",
>             "Effect": "Allow",
>             "Action": [
>                 "iam:DeactivateMFADevice",
>                 "iam:EnableMFADevice",
>                 "iam:GetUser",
>                 "iam:ListMFADevices",
>                 "iam:ResyncMFADevice"
>             ],
>             "Resource": "arn:aws:iam::*:user/${aws:username}"
>         },
>         {
>             "Sid": "DenyAllExceptListedIfNoMFA",
>             "Effect": "Deny",
>             "NotAction": [
>                 "iam:EnableMFADevice",
>                 "iam:GetUser",
>                 "iam:ListMFADevices",
>                 "iam:ResyncMFADevice"
>             ],
>             "Resource": "arn:aws:iam::*:user/${aws:username}",
>             "Condition": {
>                 "BoolIfExists": {
>                     "aws:MultiFactorAuthPresent": "false"
>                 }
>             }
>         }
>     ]
> }
> ```
> 
> 2. Select **Next: Tags**. You'll be presented with a screen about **Tags**, a tool used to identify groups of AWS resources.
> 3. Select **Next: Review**. This is a screen that allows you to review the policy that you are creating. 
> 4. Enter the name of the policy (for example, `MFAHardDevice`) and select **Create policy**.
> 
> ![MFA Policy](/images/1-account-setup/MFAPolicy.png?width=90pc)

3. In the left bar, select **Dashboard** and then select **Enable MFA**.

![Dashboard](/images/1-account-setup/Dashboard.png?width=90pc)

4. Expand Multi-factor authentication (MFA) and then select **Active MFA**.

![MFA Section](/images/1-account-setup/MFA.png?width=90pc)

5. Under **Manage MFA Device**, select **Other Hardware MFA Device** then press **Continue**.
6. Enter **Serial Number** in the back of the device.

![Image](/images/1-account-setup/HardwareMFA.png?width=30pc)

7. Enter MFA code 1. Wait 30 seconds or until the code changes, then enter MFA code 2.
8. Select **Assign MFA**.
