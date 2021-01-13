+++
title = "Thiết bị MFA ảo"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note %}}
Để kích hoạt MFA, bạn cần đăng nhập vào AWS sử dụng root user. 
{{% /notice %}}

#### Kích hoạt thiết bị MFA ảo thông qua Console

Để thiết lập và kích hoạt thiết bị MFA ảo:

1. Đăng nhập vào AWS Console.
2. Góc trên bên phải, bạn sẽ thấy tên account của bạn, chọn vào và chọn **My Security Credentials** sau đó mở rộng Multi-factor authentication (MFA).

![Virtual MFA Device](/images/1-account-setup/MySecurity.png?width=15pc)

3. Chọn **Active MFA**.
4. Trong Manage MFA Device, chọn **Virtual MFA device** sau đó chọn **Continue**.
5. Cài đặt ứng dụng tương thích trên điện thoại hoặc máy tính của bạn. [Danh sách ứng dụng](https://aws.amazon.com/iam/features/mfa/?audit=2019q1).
6. Sau khi cài đặt ứng dụng, scan mã QR.
7. Ở ô MFA code 1, nhập 6 kí tự số trong app, đợi 30 giây sau đó nhập tiếp 6 kí tự số và chọn **Assign MFA**.
8. Bây giờ bạn đã hoàn thành kích hoạt **thiết bị MFA ảo**.
