+++
title = "Tài khoản và Nhóm Admin"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Trong bước này, chúng ta sẽ tạo Admin Group trước và gán quyền AdministratorAccess cho nó. Sau đó, chúng ta sẽ tạo Admin User và thêm nó vào Admin Group để cho Admin User được hưởng quyền AdministratorAccess mà chúng ta đã gán vào Admin Group trước đấy.

**Nội dung:**
- [Tạo Admin Group](#tạo-admin-group)
- [Tạo Admin User](#tạo-admin-user)

#### Tạo Admin Group

1.	**Đăng nhập vào Bảng điều khiển** ở trang [AWS Web Service page](https://aws.amazon.com/)
2.	Nhấn vào tên tài khoản ở góc trên bên phải và chọn **My Security Credentials**

![Image](/images/1-account-setup/MySecurity_v1.png?width=12pc)

3.	Ở thanh bên trái, chọn **User Groups** sau đó chọn **Create Group**
4.	Nhập tên Group (Ví dụ: AdminGroup) dưới **User group name** <!-- updated: according to new version-->

![Image](/images/1-account-setup/GroupName_v2.png?width=90pc) <!-- updated: according to new version-->

5.	Ở phần Gán Quyền, gõ **AdministratorAccess** vào hộp tìm kiếm và nhấn Enter. Sau dó, tick vào **AdministratorAccess** và chọn **Create Group** <!-- updated: according to new version-->

![Image](/images/1-account-setup/GroupPolicy_v2.png?width=90pc) <!-- updated: according to new version-->

#### Tạo Admin User

1.	Ở thanh bên trái, chọn **Users** sau đó chọn **Add User**
2.	Nhập tên User (Ví dụ: Admin) sau đó nhấn chọn **Programmatic access** và chọn **Next:Permissions**

![Image](/images/1-account-setup/AddUser.png?width=90pc)

3.	Ở tab **Add user to group** chọn **AdminGroup** mà chúng ta tạo trước đó hoặc chọn tab **Attach existing policies directly** và chọn **Administrator Access**

![Image](/images/1-account-setup/UserPolicy.png?width=90pc)

4.	Chọn **Next:Tags**. **Tags** (thẻ) là một tùy chọn không bắt buộc để tổ chức, theo dõi, hoặc điều khiển truy cập của user, thế nên bạn có thể thêm tags hoặc không.
5.	Chọn **Next:Review**.
6.	Kiểm tra thông tin chi tiết user sau đó chọn **Create User**.
7.	Sau khi tạo thành công, download file **.csv** để lưu trữ Security Credential cho những tính năng sau này.
