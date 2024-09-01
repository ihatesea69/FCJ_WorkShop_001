+++
title = "Công khai hàm Lambda dưới dạng dịch vụ web RESTful"
date = 2023
weight = 8
chapter = false
pre = "<b>3.8 </b>"
+++

## Nhiệm vụ 8: Công khai hàm Lambda dưới dạng dịch vụ web RESTful

Trong nhiệm vụ quan trọng này, chúng ta sẽ sử dụng Amazon API Gateway để công khai các hàm Lambda của chúng ta dưới dạng dịch vụ web RESTful. Điều này cho phép dễ dàng gọi logic ứng dụng của chúng ta bằng cách sử dụng các giao thức HTTP tiêu chuẩn, nâng cao khả năng truy cập và tích hợp.

## Tạo API Gateway

1. Điều hướng đến Bảng điều khiển AWS Management Console
2. Trong thanh tìm kiếm, gõ "API Gateway" và chọn nó
3. Trong bảng REST API, nhấp vào "Build"
4. Cấu hình chi tiết API:
   - Chọn "New API"
   - Tên API: `PostReaderAPI`
   - Mô tả: API cho Ứng dụng PostReader
   - Loại Endpoint: Regional
5. Nhấp vào "Create API"

## Cấu hình các phương thức HTTP

### Phương thức POST

1. Trong bảng Resources, chọn tài nguyên gốc (/)
2. Nhấp vào "Create Method" và chọn POST
3. Thiết lập hàm Lambda:
   - Hàm Lambda: Chọn hàm chứa `PostReader_NewPost`
4. Nhấp vào "Create Method"

### Phương thức GET

1. Trong bảng Resources, chọn tài nguyên gốc (/)
2. Nhấp vào "Create Method" và chọn GET
3. Thiết lập hàm Lambda:
   - Hàm Lambda: Chọn hàm chứa `PostReader_GetPost`
4. Nhấp vào "Create Method"

## Kích hoạt CORS

Cross-Origin Resource Sharing (CORS) cho phép gọi API từ các tên miền khác nhau:

1. Chọn tài nguyên gốc (/)
2. Nhấp vào "Enable CORS"
3. Cấu hình cài đặt CORS:
   - Phản hồi Gateway: Chọn "Default 4XX" và "Default 5XX"
   - Access-Control-Allow-Methods: Chọn GET và POST
4. Nhấp vào "Save"

## Cấu hình Tham số Query

Đối với phương thức GET:

1. Chọn phương thức GET
2. Trong cài đặt Method Request, nhấp vào "Edit"
3. Mở rộng "URL Query String Parameters"
4. Thêm một tham số query:
   - Tên: `postId`
5. Nhấp vào "Save"

## Thiết lập Request Mapping

Để đảm bảo định dạng JSON đúng:

1. Chọn phương thức GET
2. Đi đến tab "Integration Request"
3. Chỉnh sửa cài đặt:
   - Request body passthrough: "When there are no templates defined (recommended)"
4. Mở rộng "Mapping Templates"
5. Thêm một mẫu mapping:
   - Content-Type: `application/json`
   - Nội dung mẫu:
     ```json
     {
         "postId": "$input.params('postId')"
     }
     ```
6. Nhấp vào "Save"

## Triển khai API

1. Nhấp vào "Deploy API"
2. Tạo một stage mới:
   - Tên stage: `Dev`
3. Nhấp vào "Deploy"
4. Sao chép "Invoke URL" và lưu lại để sử dụng sau

## 🎉 Chúc mừng!

Bạn đã công khai thành công các hàm Lambda của mình dưới dạng dịch vụ web RESTful bằng cách sử dụng Amazon API Gateway. Sự tích hợp mạnh mẽ này cho phép giao tiếp liền mạch giữa backend không máy chủ của bạn và các ứng dụng hoặc dịch vụ front-end khác nhau.

### Các bước tiếp theo
- Kiểm tra các endpoint API của bạn bằng các công cụ như Postman hoặc cURL
- Triển khai các biện pháp bảo mật thích hợp, chẳng hạn như khóa API hoặc tích hợp AWS Cognito
- Xem xét thiết lập các kế hoạch sử dụng API và điều chỉnh để quản lý lưu lượng

Bằng cách hoàn thành nhiệm vụ này, bạn đã thêm một lớp truy cập quan trọng vào ứng dụng blog-to-audio không máy chủ của mình, mở đường cho các tương tác khách hàng mạnh mẽ và có thể mở rộng.