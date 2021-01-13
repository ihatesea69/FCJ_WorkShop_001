+++
title = "Tạo IAM Role"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Bạn có thể sử dụng IAM roles để giao quyền truy cập vào các AWS Resources của bạn. Với IAM roles, bạn có thể thiết lập mối quan hệ tin cậy giữa tài khoản tin cậy của bạn và một tài khoản AWS tin cậy khác.

**Nội dung:**
- [Tạo AWS Role](#tạo-aws-role)

#### Tạo AWS Role

1. Đăng nhập vào AWS Managêmnt Console và mở IAM console tại [https://console.aws.amazon.com/iam/]( https://console.aws.amazon.com/iam/).
2. Ở khung điều hướng của console, chọn **Roles** và sau đó chọn **Create role**.
3. Chọn **Another AWS account** loại role.
4. Với **Account ID**, nhập AWS account ID mà bạn muốn cấp quyền truy cập đến tài nguyên của bạn.
5. Nếu bạn cấp quyền cho một tài khoản từ account mà bạn không điều khiển, và những tài khoản đó sẽ đảm nhận role này theo chương trình, sau đó chọn **Require external ID**.
6. Nếu bạn muốn hạn chế role đến những user mà đăng nhập với multi-factor authentication (MFA), chọn **Require MFA**.

![Thêm Role](/images/1-account-setup/AddRole.png?width=90pc)

7. Chọn **Next: Permission**.
8. IAM bao gồm danh sách các chính sách do AWS quản lý và khách hàng quản lí trong tài khoản của bạn, Chọn chính sách mà bạn dùng cho phân quyền hoặc chọn **Create policy** để mở 1 web tab mới và tạo mới chính sách từ đầu. Để thêm thông tin, xem bước 4 trong quy trình [Creating IAM Policies (Console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-start).
9. (Tuỳ chọn) Thiết lập permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html).

![Role Policy](/images/1-account-setup/RolePolicy.png?width=90pc)

10. Chọn **Next: Tags**.
11. (Tuỳ chọn) Thêm metadata vào role bằng cách đính kèm thẻ với cặp khoá-giá trị.
12. Chọn **Next: Review**.
13. Với **Role name**, Nhập tên cho role của bạn. Tên của role phải là duy nhất với tài khoản của bạn. Tên không được phân biệt theo trường hợp, in hoa in thường. Ví dụ role name ADMIN cũ và tạo 1 role name mới admin sẽ không được.
14. (Tuỳ Chọn) Với **Role Description**, nhập miêu tả cho role mới.

![Kiểm tra thông tin Role](/images/1-account-setup/RoleReview.png?width=90pc)

15. Xem lại role và sau đó chọn **Create role**