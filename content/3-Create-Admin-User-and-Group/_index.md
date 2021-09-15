+++
title = "Tạo Admin Group và Admin User"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Tạo Admin Group

1.	**Đăng nhập vào Bảng điều khiển** ở trang [AWS Web Service page](https://aws.amazon.com/)
2.	Nhấn vào tên tài khoản ở góc trên bên phải và chọn **My Security Credentials**

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

3.	Ở thanh bên trái, chọn **User Groups** sau đó chọn **Create Group**
4.	Dưới mục **Name the group**, nhập tên Group (Ví dụ: *AdminGroup*) và cuộn chuột xuống dưới

![Image](/images/1-account-setup/GroupName.png?width=90pc)

5.	Ở phần **Attach permissions policies**, gõ **AdministratorAccess** vào thanh tìm kiếm và nhấn chọn nó. Cuối cùng, chọn **Create Group**.

![Image](/images/1-account-setup/GroupPolicy.png?width=90pc)

#### Tạo Admin User

1.	Ở thanh bên trái, chọn **Users** sau đó chọn **Add User**
2.	Nhập tên User (Ví dụ: *AdminUser*).
  + Click **AWS Management Console access**. 
  + Click **Programmatic Access**.
  + Click **Custom password** rồi gõ một password tùy ý của bạn (lưu ý: bạn phải ghi nhớ mật khẩu này cho những lần đăng nhập trong tương lai). 
  + Bỏ chọn mục **User must create a new password...**.
  + Click **Next:Permissions**.

![Image](/images/1-account-setup/AddUser.png?width=90pc)

{{% notice note %}}
 Bằng cách chọn **AWS Management Console access**, bạn vừa cho phép IAM User được truy cập vào AWS thông qua bảng điều khiển AWS trên web.\
 Việc bỏ mục **User must create a new password...** cho phép người dùng khi lần đầu đăng nhập vào IAM User đó không cần phải tạo mật khẩu mới.
{{% /notice %}}

3.	Click tab **Add user to group** và click **AdminGroup** mà chúng ta tạo trước đó.
4.	Click **Next:Tags**
    - Tags (thẻ) là một tùy chọn không bắt buộc để tổ chức, theo dõi, hoặc điều khiển truy cập của user, thế nên bạn có thể thêm tags hoặc không.
5.	Click **Next:Review**.
6.	Kiểm tra thông tin chi tiết user sau đó chọn **Create User**.
{{% notice info %}}
Sau khi tạo user, bạn sẽ thấy hiện lên hộp thoại download thông tin access key và secret key. Đây là thông tin dùng để thực hiện **Programmatic access** tới các tài nguyên của AWS thông qua **AWS CLI** và **AWS SDK**. Tạm thời chúng ta sẽ chưa sử dụng tới.

{{% /notice %}}