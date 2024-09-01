+++
title = "Tạo hàm Lambda chuyển đổi văn bản thành âm thanh"
date = 2023
weight = 5
chapter = false
pre = "<b>3.5 </b>"
+++

## Tạo hàm Lambda để chuyển đổi văn bản thành âm thanh

Trong bước này, chúng ta sẽ tạo một hàm Lambda để chuyển đổi văn bản được lưu trữ trong bảng DynamoDB thành tệp âm thanh. Hàm này sẽ là một thành phần quan trọng trong ứng dụng chuyển đổi văn bản thành giọng nói không máy chủ của chúng ta.

## Các bước để tạo hàm Lambda

1. **Điều hướng đến Lambda Functions**
   - Trong Bảng điều khiển quản lý AWS, đi đến dịch vụ Lambda.
   - Trong bảng điều khiển bên trái, chọn "Functions".
   - *Lưu ý: Nếu bảng điều khiển bị thu gọn, nhấp vào biểu tượng menu để mở rộng nó.*

2. **Bắt đầu tạo hàm**
   - Nhấp vào nút "Create function".

3. **Cấu hình cài đặt hàm**
   - Chọn "Author from scratch" cho một triển khai tùy chỉnh.
   - Sử dụng cấu hình sau:
     - **Tên hàm:** `ConvertToAudio`
     - **Runtime:** Python 3.12
     - **Vai trò thực thi:** 
       - Mở rộng "Change default execution role"
       - Chọn "Use an existing role"
       - Chọn "Lab-Lambda-Role" từ danh sách thả xuống

4. **Tạo hàm**
   - Cuộn xuống cuối trang và nhấp vào "Create function".

5. **Triển khai mã hàm**
   - Trong phần "Function code", bạn sẽ thấy một trình soạn thảo mã.
   - Xóa bất kỳ mã hiện có trong trình soạn thảo.
   - Sao chép và dán mã Python được cung cấp (hiển thị bên dưới) vào trình soạn thảo.

## Tổng quan về mã hàm

Hàm Lambda mà bạn sắp tạo sẽ:
- Lấy nội dung văn bản từ DynamoDB dựa trên ID bài viết được cung cấp.
- Chia văn bản thành các đoạn nhỏ hơn (nếu cần thiết).
- Sử dụng Amazon Polly để chuyển đổi từng đoạn văn bản thành giọng nói.
- Lưu các tệp âm thanh kết quả vào một bucket S3.

Hàm này được thiết kế để xử lý nội dung dài bằng cách chia nó thành các phần nhỏ hơn, đảm bảo rằng ngay cả các bài viết dài cũng có thể được chuyển đổi thành âm thanh một cách hiệu quả.

Bây giờ, hãy triển khai chức năng cốt lõi của hàm Lambda `ConvertToAudio` của chúng ta: