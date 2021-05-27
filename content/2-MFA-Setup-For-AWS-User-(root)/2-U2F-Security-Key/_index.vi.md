+++
title = "Khóa bảo mật U2F"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

**Nội dung**
- [Kích hoạt khóa bảo mật U2F thông qua Console](#kích-hoạt-khóa-bảo-mật-u2f-thông-qua-console)


{{%notice tip%}}
Nếu bạn không có thiết bị phần cứng , có thể bỏ qua các thao tác dưới đây nhé.
{{%/notice%}}

#### Kích hoạt khóa bảo mật U2F thông qua Console

U2F Security Key là một giao thức chứng thực mở cho phép người dùng có thể truy cập các dịch vụ trực tuyếp với một khóa bảo mật duy nhất mà không cần sử dụng đến bất kì phần mềm nào.

1. Đăng nhập vào AWS Console.
2. Góc trên bên phải, bạn sẽ thấy tên account của bạn, chọn vào và chọn **My Security Credentials** sau đó mở rộng Multi-factor authentication (MFA).

![Image](/images/1-account-setup/MySecurity_v1.png?width=15pc)

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

4. Chọn **Next: Tags**. Đây là màn hình về **Tags** một công cụ dùng để phân biệt các tài nguyên của AWS.
5. Chọn  **Next: Review**. Đây là màn hình cho phép bạn review về bộ quyền mà bạn đang tạo ra. 
5. Nhập tên bộ quyền (ví dụ: MFAHardDevice) và chọn **Create policy**.

![MFA Policy](/images/1-account-setup/MFAPolicy.png?width=90pc)

6. Ở thanh bên trái , chọn **Dashboard** và sau đó chọn **Enable MFA**.

![Dashboard](/images/1-account-setup/Dashboard.png?width=90pc)

7. Mở rộng Multi-factor authentication (MFA) sau đó chọn **Active MFA**.

![MFA Section](/images/1-account-setup/MFA.png?width=90pc)

8. Trong **Manage MFA Device**, chọn **U2F security key** sau đó nhấn **Continue**.
9. Cắm khóa bảo mật U2F vào cổng USB của máy tính.

![Image](/images/1-account-setup/U2FSK.png?width=30pc)

10. Nhấn vào khóa bảo mật U2F, và sau đó chọn **Close** khi U2F thiết lập thành công.
