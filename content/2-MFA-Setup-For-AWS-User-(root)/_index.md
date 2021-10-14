+++
title = "MFA for AWS Accounts"
date = 2021
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

For increased security, we recommend that you configure multi-factor authentication (MFA) to help protect your AWS resources.

You can enable **one** MFA device (of any kind) per root user or IAM user. 

In this guide, we will go through 3 MFA options:
1. [**Virtual MFA devices**](1-virtual-mfa-device) (applications) on your smartphone such as Microsoft Authenticator, Google Authenticator, or Okta Verify. 
2. Physical [**U2F security key**](2-u2f-security-key) such as a YubiKey.
3. [**Hardware MFA devices**](3-other-hardware-mfa-device) such as the Gemalto token.
