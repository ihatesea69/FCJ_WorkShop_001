+++
title = "Tạo hàm Lambda Get Post"
date = 2023
weight = 7
chapter = false
pre = "<b>3.7 </b>"
+++

## Nhiệm vụ 7: Tạo hàm Lambda Get Post

Trong nhiệm vụ này, chúng ta sẽ tạo hàm Lambda cuối cùng cung cấp phương pháp để truy xuất thông tin về các bài viết từ cơ sở dữ liệu DynamoDB của chúng ta. Hàm này đóng vai trò quan trọng trong hệ thống blog-to-audio không máy chủ của chúng ta bằng cách cho phép truy xuất dữ liệu hiệu quả.

## Tạo hàm Lambda

1. **Điều hướng đến Bảng điều khiển AWS Management Console**
2. **Trong thanh tìm kiếm ở trên cùng, gõ "Lambda" và chọn nó**
3. **Nhấp vào "Create function"**
4. **Chọn "Author from scratch" và sử dụng các cài đặt sau:**
   - **Tên hàm:** `PostReader_GetPost`
   - **Runtime:** Python 3.12
   - **Vai trò thực thi:** Sử dụng vai trò hiện có
   - **Vai trò hiện có:** Lab-Lambda-Role
5. **Cuộn xuống và nhấp vào "Create function"**

## Thêm mã hàm

Thay thế mã hiện có trong hàm Lambda bằng mã sau: