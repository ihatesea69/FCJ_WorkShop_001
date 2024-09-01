+++
title = "Tạo hàm Lambda cho bài viết mới"
date = 2023
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++

## Nhiệm vụ 4: Tạo hàm Lambda cho bài viết mới

Trong nhiệm vụ này, chúng ta sẽ tạo hàm Lambda đầu tiên cho ứng dụng của mình. Hàm này sẽ đóng vai trò là điểm đầu vào, nhận thông tin về các bài viết mới cần được chuyển đổi thành tệp âm thanh.

### Tại sao chọn Lambda?

AWS Lambda cho phép chúng ta chạy mã mà không cần cung cấp hoặc quản lý máy chủ. Nó lý tưởng cho trường hợp sử dụng của chúng ta vì:

1. Chi phí hiệu quả - chúng ta chỉ trả tiền cho thời gian tính toán mà chúng ta sử dụng.
2. Nó tự động mở rộng theo số lượng yêu cầu.
3. Nó tích hợp liền mạch với các dịch vụ AWS khác như DynamoDB và SNS.

### Các bước để tạo hàm Lambda:

1. **Truy cập Lambda trong Bảng điều khiển AWS**
   - Mở Bảng điều khiển quản lý AWS
   - Trong thanh tìm kiếm ở trên cùng, tìm kiếm và chọn "Lambda"

2. **Tạo một hàm mới**
   - Nhấp vào "Create function"
   - Chọn "Author from scratch"
   - Cấu hình các cài đặt sau:
     - Tên hàm: `PostReader_NewPost`
     - Runtime: Python 3.12
     - Vai trò thực thi: Sử dụng vai trò hiện có
     - Vai trò hiện có: Chọn `Lab-Lambda-Role`
   - Nhấp vào "Create function"

3. **Thêm mã hàm**
   - Trong phần Function code, xóa mã hiện có
   - Dán mã Python sau:

   ```python
   import boto3
   import os
   import uuid

   def lambda_handler(event, context):

       recordId = str(uuid.uuid4())
       voice = event["voice"]
       text = event["text"]

       print('Generating new DynamoDB record, with ID: ' + recordId)
       print('Input Text: ' + text)
       print('Selected voice: ' + voice)

       # Tạo bản ghi mới trong bảng DynamoDB
       dynamodb = boto3.resource('dynamodb')
       table = dynamodb.Table(os.environ['DB_TABLE_NAME'])
       table.put_item(
           Item={
               'id' : recordId,
               'text' : text,
               'voice' : voice,
               'status' : 'PROCESSING'
           }
       )

       # Gửi thông báo về bài viết mới tới SNS
       client = boto3.client('sns')
       client.publish(
           TopicArn = os.environ['SNS_TOPIC'],
           Message = recordId
       )

       return recordId
   ```

4. **Kiểm tra mã**
   Hàm Lambda thực hiện các nhiệm vụ sau:
   - Lấy hai tham số đầu vào:
     - Voice: Một trong số hàng chục giọng nói được hỗ trợ bởi Amazon Polly
     - Text: Nội dung của bài viết cần được chuyển đổi thành tệp âm thanh
   - Tạo một bản ghi mới trong bảng DynamoDB với thông tin về bài viết mới
   - Gửi thông tin về bài viết mới tới SNS (ID của bài viết được gửi dưới dạng tin nhắn)
   - Trả về ID của mục DynamoDB cho người dùng

5. **Triển khai hàm**
   - Nhấp vào "Deploy" để lưu các thay đổi của bạn

6. **Cấu hình biến môi trường**
   - Điều hướng đến tab "Configuration"
   - Trong bảng điều khiển bên trái, chọn "Environment variables"
   - Nhấp vào "Edit" và thêm các biến sau:
     - Key: `SNS_TOPIC`, Value: [Dán ARN chủ đề SNS của bạn]
     - Key: `DB_TABLE_NAME`, Value: `posts`
   - Nhấp vào "Save"

7. **Cập nhật cấu hình hàm**
   - Trong bảng điều khiển bên trái của tab Configuration, chọn "General configuration"
   - Nhấp vào "Edit"
   - Cập nhật Timeout thành 10 giây
   - Nhấp vào "Save"

### Kiểm tra hàm Lambda

1. **Tạo một sự kiện kiểm tra**
   - Điều hướng đến tab "Test"
   - Cấu hình một sự kiện kiểm tra mới với các chi tiết sau:
     - Tên sự kiện: Joanna
     - JSON sự kiện:
     ```json
     {
       "voice": "Joanna",
       "text": "This is working!"
     }
     ```
   - Nhấp vào "Save"

2. **Chạy kiểm tra**
   - Nhấp vào "Test" để thực thi sự kiện kiểm tra của bạn
   - Bạn sẽ thấy thông báo "Execution result: succeeded"
   - Mở rộng phần "Details" để xem nhật ký thực thi

Chúc mừng! Bạn đã tạo và kiểm tra thành công hàm Lambda cho bài viết mới. Hàm này sẽ đóng vai trò là điểm đầu vào cho ứng dụng của bạn, xử lý các bài viết mới và bắt đầu quá trình chuyển đổi âm thanh.