+++
title = "Tạo Amazon S3 Bucket"
date = 2023
weight = 2
chapter = false
pre = "<b>3.2 </b>"
+++

## Nhiệm vụ 2: Tạo Amazon S3 Bucket

Trong nhiệm vụ này, chúng ta sẽ tạo một Amazon S3 bucket để lưu trữ tất cả các tệp âm thanh được tạo bởi ứng dụng của chúng ta. S3 (Simple Storage Service) là một cơ sở hạ tầng lưu trữ dữ liệu có khả năng mở rộng cao, đáng tin cậy và độ trễ thấp do AWS cung cấp.

### Tại sao chọn S3?

Amazon S3 là một lựa chọn lý tưởng cho việc lưu trữ tệp âm thanh của chúng ta vì:

1. Nó cung cấp độ bền 99.999999999% (11 số 9).
2. Nó có hiệu suất độ trễ thấp.
3. Nó tích hợp liền mạch với các dịch vụ AWS khác.
4. Nó cung cấp các kiểm soát bảo mật linh hoạt.

### Các bước để tạo một S3 Bucket:

1. **Truy cập Bảng điều khiển quản lý AWS**
   - Mở trình duyệt web của bạn và điều hướng đến Bảng điều khiển quản lý AWS.
   - Trong thanh tìm kiếm ở trên cùng, gõ "S3" và chọn nó từ kết quả.

2. **Khởi tạo tạo Bucket**
   - Trên bảng điều khiển S3, nhấp vào nút "Create bucket".

3. **Cấu hình cài đặt Bucket**
   - **Tên Bucket**: Nhập một tên duy nhất như `audioposts-123456789`.
     - Thay thế `123456789` bằng một số ngẫu nhiên.
     - 📝 **Quan trọng**: Sao chép tên bucket này vào trình soạn thảo văn bản của bạn để sử dụng sau này.
   
   - **Khu vực**: Chọn một khu vực gần với đối tượng mục tiêu của bạn để có hiệu suất tốt hơn.
   
   - **Quyền sở hữu đối tượng**: Chọn "ACLs enabled".
   
   - **Cài đặt chặn truy cập công khai**: 
     - Bỏ chọn "Block all public access".
     - Để tất cả các tùy chọn khác không được chọn.
     
     > ⚠️ **Lưu ý**: Trong môi trường sản xuất, nên sử dụng các cài đặt ít quyền nhất có thể. Chúng ta đang sử dụng các cài đặt này cho mục đích minh họa.

   - **Phiên bản hóa**: Cân nhắc bật tính năng này để theo dõi thay đổi và dễ dàng quay lại phiên bản trước.
   
   - **Mã hóa**: Bật mã hóa phía máy chủ để tăng cường bảo mật.

4. **Xác nhận cảnh báo truy cập công khai**
   - Một hộp cảnh báo sẽ xuất hiện với nội dung: "Turning off block all public access might result in this bucket and the objects within becoming public."
   - Chọn hộp kiểm để xác nhận điều này.

5. **Tạo Bucket**
   - Nhấp vào nút "Create bucket" ở cuối trang.

### Khắc phục sự cố

Nếu bạn gặp lỗi "The requested bucket name is not available":
1. Nhấp vào liên kết "Edit" ở đầu trang.
2. Thay đổi tên bucket.
3. Thử lại cho đến khi bạn tìm thấy một tên khả dụng.

Hãy nhớ rằng, mỗi Amazon S3 bucket phải có một tên duy nhất trên toàn cầu trong tất cả các AWS.

### Các bước tiếp theo

Bây giờ chúng ta đã thiết lập xong S3 bucket, chúng ta sẵn sàng bắt đầu lưu trữ các tệp âm thanh của mình. Trong nhiệm vụ tiếp theo, chúng ta sẽ cấu hình ứng dụng của mình để tương tác với bucket này, cho phép chúng ta tải lên và truy xuất các tệp âm thanh khi cần thiết.