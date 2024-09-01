+++
title = "Tạo bảng DynamoDB"
date = 2021
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++

## Nhiệm vụ 1: Tạo bảng DynamoDB

Trong nhiệm vụ này, chúng ta sẽ tạo một bảng Amazon DynamoDB để lưu trữ thông tin về các bài viết blog, bao gồm nội dung văn bản và URL của tệp MP3 tương ứng. Bảng này sẽ đóng vai trò là xương sống của việc lưu trữ dữ liệu cho ứng dụng của chúng ta.

### Các bước:

1. Điều hướng đến Bảng điều khiển quản lý AWS.
2. Trong thanh tìm kiếm ở trên cùng, gõ "DynamoDB" và chọn nó từ kết quả.
3. Trên bảng điều khiển DynamoDB, nhấp vào "Create table".
4. Thiết lập bảng với các chi tiết sau:
   - Tên bảng: `posts`
   - Khóa phân vùng: `id` (String)
   - Cài đặt bảng: Để mặc định
5. Nhấp vào "Create table" để hoàn tất quá trình.

### Cấu trúc bảng

Mặc dù chúng ta không cần phải định nghĩa toàn bộ cấu trúc ngay bây giờ, ứng dụng của chúng ta cuối cùng sẽ lưu trữ các thông tin sau trong bảng DynamoDB:

- `id`: Một định danh duy nhất cho mỗi bài viết (String, Khóa chính)
- `status`: Chỉ ra liệu tệp MP3 đã được tạo hay chưa (String, có thể là "UPDATED" hoặc "PROCESSING")
- `text`: Nội dung của bài viết để chuyển đổi thành âm thanh (String)
- `voice`: Giọng nói Amazon Polly được sử dụng để chuyển đổi âm thanh (String)
- `url`: Một liên kết đến bucket S3 nơi tệp âm thanh được lưu trữ (String)

Cấu trúc bảng này sẽ cho phép ứng dụng của chúng ta quản lý và truy xuất thông tin về mỗi bài viết blog và tệp âm thanh liên quan một cách hiệu quả.