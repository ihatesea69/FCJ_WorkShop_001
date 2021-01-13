+++
title = "Tài khoản và Nhóm Admin"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

**Nội dung:**
- [Tạo Admin Group](#tạo-admin-group)
- [Tạo Admin User](#tạo-admin-user)

#### Tạo Admin Group

1.	**Đăng nhập vào Bảng điều khiển** ở trang [AWS Web Service page](https://aws.amazon.com/)
2.	Nhấn vào tên tài khoản ở góc trên bên phải và chọn **My Security Credentials**

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

3.	Ở thanh bên trái, chọn **Groups** sau đó chọn **Create Group**
4.	Nhập tên Group (Ví dụ: AdminGroup) và chọn **Next Step**

![Image](/images/1-account-setup/GroupName.png?width=90pc)

5.	Ở phần Gán Quyền nhấn chọn **AdministratorAccesss** sau đó chọn **Next Step**

![Image](/images/1-account-setup/GroupPolicy.png?width=90pc)

6.	Xem lại tên Group và các Quyền và chọn **Create Group**

#### Tạo Admin User

1.	Ở thanh bên trái, chọn **Users** sau đó chọn **Add User**
2.	Nhập tên User (Ví dụ: Admin) sau đó nhấn chọn **Programmatic access** và chọn **Next:Permissions**

![Image](/images/1-account-setup/AddUser.png?width=90pc)

3.	Ở tab **Add user to group** chọn **AdminGroup** mà chúng ta tạo trước đó hoặc chọn tab **Attach existing policies directly** và chọn **Administrator Access**

![Image](/images/1-account-setup/UserPolicy.png?width=90pc)

4.	Chọn **Next:Tags**
5.	Tags (thẻ) là một tùy chọn không bắt buộc để tổ chức, theo dõi, hoặc điều khiển truy cập của user, thế nên bạn có thể thêm tags hoặc không
6.	Chọn **Next:Review**
7.	Kiểm tra thông tin chi tiết user sau đó chọn **Create User**
8.	Sau khi tạo thành công, download file **.csv** để lưu trữ Security Credential cho những tính năng sau này.
