+++
title = "Đề cương Hội thảo"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++


## Mục tiêu

Sau khi hoàn thành hội thảo này, bạn sẽ có thể:

- Tạo bảng Amazon DynamoDB để lưu trữ dữ liệu
- Tạo API RESTful với Amazon API Gateway
- Tạo các hàm AWS Lambda được kích hoạt bởi API Gateway
- Kết nối các hàm AWS Lambda với Amazon Simple Notification Service (SNS)
- Sử dụng Amazon Polly để tổng hợp giọng nói bằng nhiều ngôn ngữ và giọng điệu khác nhau

## Thời lượng

Hội thảo này kéo dài khoảng 90 phút để hoàn thành.

## Môi trường Hội thảo

Bạn sẽ xây dựng một ứng dụng không máy chủ, nghĩa là bạn không cần làm việc với các máy chủ - không cần cung cấp, vá lỗi, hoặc mở rộng. AWS Cloud sẽ tự động xử lý các tác vụ này, cho phép bạn tập trung vào ứng dụng của mình.

Ứng dụng cung cấp hai phương pháp:
1. Gửi thông tin về các bài viết mới để chuyển đổi thành tệp MP3
2. Lấy thông tin về các bài viết (bao gồm các liên kết đến các tệp MP3 được lưu trữ trong Amazon S3 bucket)

Cả hai phương pháp đều được hiển thị dưới dạng dịch vụ web RESTful thông qua Amazon API Gateway.



![architecture](./images/architecture.png)





## Khi ứng dụng gửi thông tin về các bài viết mới:

1. Thông tin được nhận bởi dịch vụ web RESTful được hiển thị bởi Amazon API Gateway. Dịch vụ web này được kích hoạt bởi một trang web tĩnh được lưu trữ trên Amazon Simple Storage Service (Amazon S3).

2. Amazon API Gateway kích hoạt một hàm AWS Lambda, "Bài viết mới", chịu trách nhiệm khởi tạo quá trình tạo tệp MP3.

3. Hàm Lambda chèn thông tin về bài viết vào bảng Amazon DynamoDB, nơi lưu trữ thông tin về tất cả các bài viết.

4. Để chạy toàn bộ quá trình không đồng bộ, Amazon Simple Notification Service (Amazon SNS) được sử dụng để tách rời quá trình nhận thông tin về các bài viết mới và bắt đầu chuyển đổi chúng thành tệp âm thanh.

5. Một hàm Lambda khác, "Chuyển đổi thành âm thanh", được đăng ký vào chủ đề SNS của bạn và được kích hoạt bất cứ khi nào có một tin nhắn mới xuất hiện (có nghĩa là một bài viết mới cần được chuyển đổi thành tệp âm thanh).

6. Hàm Lambda "Chuyển đổi thành âm thanh" sử dụng Amazon Polly để chuyển đổi văn bản thành tệp âm thanh bằng ngôn ngữ được chỉ định (cùng ngôn ngữ với văn bản).

7. Tệp MP3 mới được lưu trong một S3 bucket chuyên dụng.

8. Thông tin về bài viết được cập nhật trong bảng DynamoDB. URL đến tệp âm thanh được lưu trữ trong S3 bucket được lưu cùng với dữ liệu đã lưu trước đó.

## Khi ứng dụng lấy thông tin về các bài viết:

1. Dịch vụ web RESTful được triển khai bằng Amazon API Gateway. Amazon API Gateway hiển thị phương pháp để lấy thông tin về các bài viết. Các phương pháp này chứa văn bản của bài viết và liên kết đến S3 bucket nơi tệp MP3 được lưu trữ. Dịch vụ web này được kích hoạt bởi một trang web tĩnh được lưu trữ trên Amazon S3.

2. Amazon API Gateway kích hoạt hàm Lambda "Lấy bài viết", triển khai logic để lấy dữ liệu bài viết.

3. Hàm Lambda "Lấy bài viết" lấy thông tin về bài viết (bao gồm tham chiếu đến Amazon S3) từ bảng DynamoDB và trả về thông tin đó.
