+++
title = "Thiết bị MFA cứng"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

**Nội dung**
- [Kích hoạt thiết bị MFA phần cứng khác thông qua Console](#kích-hoạt-thiết-bị-mfa-phần-cứng-khác-thông-qua-console)

#### Kích hoạt thiết bị MFA phần cứng khác thông qua Console

1. Đăng nhập vào AWS Console.
2. Góc trên bên phải, bạn sẽ thấy tên account của bạn, chọn vào và chọn **My Security Credentials** sau đó mở rộng Multi-factor authentication (MFA).

![Image](/images/1-account-setup/MySecurity.png?width=30pc)

3. Để quản lí khóa bảo mật U2F, bạn phải có quyền từ bộ quyền sau. ở thanh bên trái, chọn **Policies** sau đó chọn **Create policy**, chọn **JSON** tab và dán phần bên dưới vào:

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

4. Chọn **Review policy**.
5. Nhập tên bộ quyền và chọn **Create policy**.
6. Ở thanh bên trái , chọn **Dashboard** mở rộng **Active MFA on your root account** sau đó chọn **Manage MFA**.
7. Mở rộng Multi-factor authentication (MFA) sau đó chọn **Active MFA**.
8. Trong **Manage MFA Device**, chọn **Other Hardware MFA Device** sau đó nhấn **Continue**.
9. Nhập **Serial Number** ở đằng sau thiết bị.

![Image](/images/1-account-setup/HardwareMFA.png?width=30pc)

10. Nhập MFA code 1 sau đó đợi 30 giây và nhập MFA code 2.
11. Chọn **Assign MFA**.