+++
title = "Hardware MFA Device"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

**Contents**
- [Enable a Hardware MFA Device using Console](#enable-a-hardware-mfa-device-using-console)

#### Enable a Hardware MFA Device using Console

1. Sign in to AWS Console.
2. In the top right of the navigation bar, you will see your account name, choose it and choose **My Security Credentials** then expand Multi-factor authentication (MFA).

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

3. To manage Hardware MFA Device, you must have permission from following policy. In the left bar, choose **Policies** then choose **Create policy**, choose the **JSON** tab and paste the following:

```js
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowManageOwnUserMFA",
            "Effect": "Allow",
            "Action": [
                "iam:DeactivateMFADevice",
                "iam:EnableMFADevice",
                "iam:GetUser",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "DenyAllExceptListedIfNoMFA",
            "Effect": "Deny",
            "NotAction": [
                "iam:EnableMFADevice",
                "iam:GetUser",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}",
            "Condition": {
                "BoolIfExists": {
                    "aws:MultiFactorAuthPresent": "false"
                }
            }
        }
    ]
}
```

4. Choose **Review policy**.
5. Enter the name of policy then choose **Create policy**.
6. In the left bar, choose **Dashboard** expand **Active MFA on your root account** then choose **Manage MFA**.
7. Expand Multi-factor authentication (MFA) then choose **Active MFA**.
8. Choose **Other Hardware MFA Device** click **Continue**.
9. Enter the **Serial Number** on the back of device.

![Image](/images/1-account-setup/HardwareMFA.png?width=30pc)

10. Enter MFA code 1 then wait 30 seconds and enter the MFA code 2.
11. Choose **Assign MFA**.
