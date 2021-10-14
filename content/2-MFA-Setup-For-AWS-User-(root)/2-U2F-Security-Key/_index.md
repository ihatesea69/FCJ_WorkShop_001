+++
title = "U2F Security Key"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++
{{%notice info%}}
The following steps require a U2F security key.
{{%/notice%}}

#### Enable U2F security key via Console

U2F is an open authentication standard hosted by the [FIDO Alliance](https://fidoalliance.org/). When you enable a U2F key in AWS, the U2F security key creates a new key pair for use with only AWS. First, you enter your credentials. When prompted, you tap the U2F security key, which responds to the authentication challenge issued by AWS. 

1. Sign-in to AWS Console.
2. In the upper right corner, you'll see your account name, select and select **My Security Credentials**.

![Image](/images/1-account-setup/MySecurity_v1.png?width=15pc)

**Note:** To manage a U2F security key for your own IAM user while protecting sensitive MFA-related actions, you must have the permissions from the following policy.
<!-- policy not associated with user -->
>   1. In the left bar, select **Policies** then select **Create policy**. Select **JSON** tab and paste the policy document from below:
>
>   ```json
>   {
>       "Version": "2012-10-17",
>       "Statement": [
>           {
>               "Sid": "AllowManageOwnUserMFA",
>               "Effect": "Allow",
>               "Action": [
>                   "iam:DeactivateMFADevice",
>                   "iam:EnableMFADevice",
>                   "iam:GetUser",
>                   "iam:ListMFADevices",
>                   "iam:ResyncMFADevice"
>               ],
>               "Resource": "arn:aws:iam::*:user/${aws:username}"
>           },
>           {
>               "Sid": "DenyAllExceptListedIfNoMFA",
>               "Effect": "Deny",
>               "NotAction": [
>                   "iam:EnableMFADevice",
>                   "iam:GetUser",
>                   "iam:ListMFADevices",
>                   "iam:ResyncMFADevice"
>               ],
>               "Resource": "arn:aws:iam::*:user/${aws:username}",
>               "Condition": {
>                   "BoolIfExists": {
>                       "aws:MultiFactorAuthPresent": "false"
>                   }
>               }
>           }
>       ]
>   }
>   ```
>
>   2. Select **Next: Tags**. You'll be presented with a screen about **Tags**, a tool used to identify groups of AWS resources.
>   3. Select **Next: Review**. This is a screen that allows you to review the policy that you are creating. 
>   4. Enter the name of the policy (for example, `MFAHardDevice`) and select **Create policy**.
>
>   ![MFA Policy](/images/1-account-setup/MFAPolicy.png?width=90pc)

3. In the left bar, select **Dashboard** and then select **Enable MFA**.

![Dashboard](/images/1-account-setup/Dashboard.png?width=90pc)

4. Expand **Multi-factor authentication (MFA)** and then select **Active MFA**.

![MFA Section](/images/1-account-setup/MFA.png?width=90pc)

5. Under **Manage MFA Device**, select **U2F security key** then press **Continue**.
6. Plug the U2F security key into your computer.

![Image](/images/1-account-setup/U2FSK.png?width=30pc)

7. Follow the on-screen prompts to press the U2F security key, and then select **Close** when U2F is successfully set up.
