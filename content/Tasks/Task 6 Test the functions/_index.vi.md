+++
title = "Kiểm tra các hàm"
date = 2023
weight = 6
chapter = false
pre = "<b>3.6 </b>"
+++

## Nhiệm vụ 6: Kiểm tra các hàm

Trong nhiệm vụ quan trọng này, chúng ta sẽ xác minh chức năng của hệ thống chuyển đổi blog thành âm thanh không máy chủ của mình. Chúng ta sẽ kiểm tra toàn bộ quy trình làm việc, từ việc kích hoạt hàm Lambda ban đầu đến việc xác nhận tạo tệp âm thanh trong S3.

## Tổng quan về quy trình làm việc

1. Kích hoạt thủ công hàm Lambda Bài viết mới
2. Hàm lưu trữ dữ liệu trong DynamoDB và gửi một tin nhắn đến chủ đề SNS
3. SNS kích hoạt hàm Chuyển đổi thành âm thanh
4. Hàm Chuyển đổi thành âm thanh sử dụng Amazon Polly để tạo tệp âm thanh
5. Tệp âm thanh được lưu trữ trong bucket S3

## Quy trình kiểm tra từng bước

### 1. Kích hoạt hàm Lambda Bài viết mới

1. Điều hướng đến bảng điều khiển AWS Lambda
2. Tìm và chọn hàm `PostReader_NewPost`
3. Nhấp vào nút "Test"
4. Xác minh thông báo thành công: "Execution result: succeeded"

### 2. Xác nhận mục DynamoDB

1. Mở bảng điều khiển AWS DynamoDB
2. Trong ngăn điều hướng, chọn "Explore items"
3. Chọn bảng "posts"
4. Xác minh sự hiện diện của hai mục (do chạy thử nghiệm hai lần)
5. Lưu ý trường `url` trong mục thứ hai, cho thấy chuyển đổi âm thanh thành công

### 3. Kiểm tra thực thi hàm Chuyển đổi thành âm thanh

1. Quay lại bảng điều khiển AWS Lambda
2. Chọn hàm `ConvertToAudio`
3. Điều hướng đến tab "Monitor"
4. Kiểm tra các biểu đồ giám sát cho việc gọi hàm

> **⚠️ Cảnh báo:** Nếu bạn gặp lỗi:
> - Kiểm tra biểu đồ "Error count and success rate"
> - Xem nhật ký CloudWatch để biết thông báo lỗi chi tiết
> - Các vấn đề phổ biến: Tên bucket S3 không chính xác trong các biến môi trường

### 4. Xác minh tệp âm thanh trong S3

1. Mở bảng điều khiển AWS S3
2. Tìm và chọn bucket `audioposts-`
3. Xác nhận sự hiện diện của tệp MP3
4. Tải xuống và phát tệp - bạn sẽ nghe giọng của Polly Joanna nói "This is working!"

## Mẹo khắc phục sự cố

- Kiểm tra kỹ tất cả các quyền IAM
- Đảm bảo chủ đề và đăng ký SNS được cấu hình chính xác
- Xác minh các biến môi trường trong các hàm Lambda
- Xem lại nhật ký CloudWatch để biết thông tin lỗi chi tiết

## Các bước tiếp theo

Chúc mừng bạn đã kiểm tra thành công hệ thống chuyển đổi blog thành âm thanh không máy chủ của mình! Trong nhiệm vụ tiếp theo, chúng ta sẽ khám phá các cách để nâng cao và tối ưu hóa ứng dụng của bạn.

---

🎉 **Hoàn thành nhiệm vụ!** Bạn đã xác minh chức năng cốt lõi của ứng dụng không máy chủ của mình. Tiếp tục đến thử thách thú vị tiếp theo trong hành trình AWS của bạn!
