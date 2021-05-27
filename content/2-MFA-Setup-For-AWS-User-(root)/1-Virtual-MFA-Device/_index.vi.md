+++
title = "Thiết bị MFA ảo"
date = 2021
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
2. Góc trên bên phải, bạn sẽ thấy tên account của bạn, chọn vào và chọn **My Security Credentials**.

![Virtual MFA Device](/images/1-account-setup/MySecurity_v1.png?width=15pc)

3. Mở rộng **Multi-factor authentication (MFA)** và chọn **Active MFA**.

![MFA Section](/images/1-account-setup/MFA.png?width=90pc)

4. Trong Manage MFA Device, chọn **Virtual MFA device** sau đó chọn **Continue**.
5. Cài đặt ứng dụng tương thích trên điện thoại của bạn. [Danh sách ứng dụng MFA](https://aws.amazon.com/iam/features/mfa/?audit=2019q1).
6. Sau khi cài đặt ứng dụng, chọn **Show QR Code** và dùng điện thoại đang mở ứng dụng MFA của bạn để scan mã QR.
    - ***Ví dụ:** Bạn đang sử dụng *Microsoft Authenticator*.
![MFA QR Scanner](/images/1-account-setup/MFAScannerQR.png?width=90pc)
7. Ở ô **MFA code 1**, nhập 6 kí tự số trong app, đợi 30 giây sau đó nhập tiếp 6 kí tự số vào ô **MFA Code 2** và chọn **Assign MFA**.
8. Bây giờ bạn đã hoàn thành kích hoạt **thiết bị MFA ảo**.
