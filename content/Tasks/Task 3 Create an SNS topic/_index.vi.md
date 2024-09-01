+++
title = "Tạo một chủ đề SNS"
date = 2023
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

## Nhiệm vụ 3: Tạo một chủ đề SNS

Trong nhiệm vụ này, chúng ta sẽ tạo một chủ đề Amazon Simple Notification Service (SNS) để tạo điều kiện giao tiếp giữa các hàm Lambda của chúng ta. Đây là một bước quan trọng trong kiến trúc serverless của chúng ta để chuyển đổi các bài viết blog thành âm thanh.

### Tại sao sử dụng SNS?

Kiến trúc của ứng dụng chúng ta chia quá trình chuyển đổi văn bản thành giọng nói thành hai hàm Lambda vì một số lý do:

1. **Xử lý không đồng bộ**: Điều này cho phép người dùng nhận được xác nhận ngay lập tức về việc gửi bài viết của họ mà không cần chờ đợi quá trình chuyển đổi âm thanh hoàn tất.

2. **Khả năng mở rộng**: Nó cho phép hệ thống của chúng ta xử lý các bài viết có độ dài khác nhau một cách hiệu quả, từ các đoạn ngắn đến các bài viết dài.

3. **Kiến trúc tách biệt**: Bằng cách tách biệt quá trình tạo bài viết và quá trình chuyển đổi âm thanh, chúng ta tạo ra một hệ thống linh hoạt và dễ bảo trì hơn.

SNS hoạt động như keo dán giữa hai hàm này, cho phép giao tiếp liền mạch và kích hoạt quá trình chuyển đổi âm thanh.

### Các bước để tạo một chủ đề SNS:

1. **Truy cập SNS trong Bảng điều khiển AWS**
   - Mở Bảng điều khiển quản lý AWS
   - Trong thanh tìm kiếm ở trên cùng, gõ "SNS" và chọn "Simple Notification Service"

2. **Điều hướng đến Chủ đề**
   - Trong bảng điều khiển bên trái, chọn "Topics"
   - Lưu ý: Bạn có thể cần mở rộng bảng điều khiển bằng cách nhấp vào biểu tượng menu

3. **Tạo một Chủ đề Mới**
   - Nhấp vào "Create topic"
   - Cấu hình các chi tiết sau:
     - Loại: Chọn "Standard"
     - Tên: Nhập "new_posts"
     - Tên hiển thị: Nhập "New Posts"

4. **Hoàn tất Tạo Chủ đề**
   - Cuộn xuống cuối trang
   - Nhấp vào "Create topic"

5. **Lưu ARN của Chủ đề**
   - Sau khi tạo, bạn sẽ thấy ARN của Chủ đề (Amazon Resource Name)
   - Sao chép ARN này và lưu vào trình soạn thảo văn bản để sử dụng sau
   - ARN sẽ trông giống như sau:
     ```
     arn:aws:sns:us-west-2:123456789012:new_posts
     ```

### Lưu ý quan trọng

Bạn sẽ sử dụng ARN của Chủ đề này khi cấu hình các hàm Lambda trong các nhiệm vụ tiếp theo. Nó rất quan trọng để thiết lập liên kết giao tiếp giữa các hàm của bạn.

### Các bước tiếp theo

Với chủ đề SNS của bạn đã được tạo, bạn đã sẵn sàng chuyển sang nhiệm vụ tiếp theo trong việc xây dựng ứng dụng blog-to-audio serverless của mình. Chủ đề SNS này sẽ đóng vai trò quan trọng trong việc kích hoạt quá trình chuyển đổi âm thanh cho mỗi bài viết blog mới.