+++
title = "Khóa bảo mật U2F"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

**Nội dung**
- [Kích hoạt khóa bảo mật U2F thông qua Console](#kích-hoạt-khóa-bảo-mật-u2f-thông-qua-console)

**Nếu bạn không có thiết bị phần cứng , có thể bỏ qua các thao tác dưới đây nhé.**

#### Kích hoạt khóa bảo mật U2F thông qua Console

U2F Security Key là một giao thức chứng thực mở cho phép người dùng có thể truy cập các dịch vụ trực tuyết với một khóa bảo mật duy nhất mà không cần sử dụng đến bất kì phần mềm nào.

1. Đăng nhập vào AWS Console.
2. Góc trên bên phải, bạn sẽ thấy tên account của bạn, chọn vào và chọn **My Security Credentials** sau đó mở rộng Multi-factor authentication (MFA).

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

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
8. Trong **Manage MFA Device**, chọn **U2F security key** sau đó nhấn **Continue**.
9. Cắm khóa bảo mật U2F vào cổng USB của máy tính.

![Image](/images/1-account-setup/U2FSK.png?width=30pc)

10. Nhấn vào khóa bảo mật U2F, và sau đó chọn **Close** khi U2F thiết lập thành công.
