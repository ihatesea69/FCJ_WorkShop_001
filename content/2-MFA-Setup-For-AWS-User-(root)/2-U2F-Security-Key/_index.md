+++
title = "U2F Security"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

**Contents**
- [Enable a U2F Security Key using Console](#enable-a-u2f-security-key-using-console)

#### Enable a U2F Security Key using Console

U2F Security Key is an open authentication that allow user to securely access to online service with one single security key and with no software needed.

1. Sign in to AWS Console
2. In the top right of the navigation bar, you will see your account name, choose it and choose **My Security Credentials** then expand Multi-factor authentication (MFA) 

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

3. To manage U2F security key, you must have permission from following policy. In the left bar, choose **Policies** then choose **Create policy**, choose the **JSON** tab and paste the following:

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
4. Choose **Review policy** 
5. Enter the name of policy then choose **Create policy**
6. In the left bar, choose **Dashboard** expand **Active MFA on your root account** then choose **Manage MFA**
7. Expand Multi-factor authentication (MFA) then choose **Active MFA**
8. In the **Manage MFA Device**, choose **U2F security key** then click **Continue**
9. Insert the U2F security key into your computer's USB port.

![Image](/images/1-account-setup/U2FSK.png?width=30pc)

10. Tap the U2F security key, and then choose **Close** when U2F setup is complete.
