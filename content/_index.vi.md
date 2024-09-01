+++
title = "Xây dựng ứng dụng Text-to-Speech không máy chủ với Amazon Polly"
date = 2024
weight = 1
chapter = false
+++

# Xây dựng ứng dụng Text-to-Speech không máy chủ với Amazon Polly

## Tổng quan

Tổng hợp giọng nói là một thách thức phức tạp. Việc đọc từng chữ cái trong một câu không đảm bảo kết quả có ý nghĩa. Một số thách thức phổ biến trong ứng dụng text-to-speech bao gồm:

1. **Từ đồng âm khác nghĩa:** "Tôi sống ở Las Vegas" so với "Buổi thuyết trình này phát trực tiếp từ Las Vegas".
2. **Chuẩn hóa văn bản:** Giải mã viết tắt, từ viết tắt và đơn vị đo lường. Ví dụ: "St." có thể là "Street" hoặc "Saint".
3. **Chuyển đổi văn bản thành âm vị:** Trong tiếng Anh, "tough", "through", và "though" có cách phát âm khác nhau tùy thuộc vào ngữ cảnh.
4. **Từ ngoại lai:** "déjà vu", tên riêng như "François Hollande", và tiếng lóng như "ASAP", "LOL".

Amazon Polly cung cấp giải pháp vượt qua những thách thức này, cho phép bạn tập trung vào việc xây dựng ứng dụng text-to-speech mà không cần lo lắng về vấn đề diễn giải.

## Amazon Polly: Công nghệ AI tiên tiến

Amazon Polly chuyển đổi văn bản thành giọng nói tự nhiên, cho phép bạn tạo ra các ứng dụng có khả năng giao tiếp như con người. Đây là dịch vụ AI của Amazon sử dụng công nghệ học sâu tiên tiến để tổng hợp giọng nói giống người thật. Hiện tại, Polly hỗ trợ hàng chục giọng nói chân thực bằng hơn 20 ngôn ngữ, giúp bạn xây dựng ứng dụng hỗ trợ giọng nói cho nhiều quốc gia khác nhau.

### Ưu điểm nổi bật:

- **Phản hồi nhanh:** Hỗ trợ đối thoại tương tác thời gian thực
- **Lưu trữ linh hoạt:** Có thể lưu cache và tái sử dụng file âm thanh
- **Không giới hạn sử dụng:** Không tính phí bổ sung cho việc sử dụng giọng nói đã chuyển đổi
- **Dễ dàng tích hợp:** Chỉ cần gửi văn bản đến API của Amazon Polly

## Mục tiêu workshop

Trong workshop này, bạn sẽ xây dựng một ứng dụng không máy chủ cơ bản sử dụng Amazon Polly để chuyển đổi văn bản thành giọng nói. Ứng dụng có giao diện người dùng đơn giản, cho phép nhập văn bản bằng nhiều ngôn ngữ khác nhau và chuyển đổi thành file âm thanh có thể phát trực tiếp trên trình duyệt web.

Mặc dù workshop này sử dụng bài viết blog làm ví dụ, bạn có thể áp dụng cho nhiều loại văn bản khác như:

- Đọc công thức nấu ăn trong khi nấu nướng
- Nghe tin tức hoặc sách khi đang lái xe hoặc đạp xe

Hãy bắt đầu hành trình khám phá công nghệ text-to-speech với Amazon Polly!