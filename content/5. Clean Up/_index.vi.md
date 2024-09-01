+++
title = "Dọn Dẹp"
date = 2020-05-14T00:38:32+07:00
weight = 5
chapter = false
pre = "<b>5. </b>"
+++


## Dọn Dẹp

Nếu bạn tham gia một sự kiện do AWS tổ chức, bạn không cần lo lắng về việc dọn dẹp bất kỳ tài nguyên nào. AWS sẽ xử lý quá trình dọn dẹp cho bạn.

Tuy nhiên, nếu bạn đã thực hiện hội thảo này trong tài khoản AWS của riêng mình, điều quan trọng là phải xóa stack CloudFormation để tránh bất kỳ chi phí không mong muốn nào trên hóa đơn AWS của bạn. Thực hiện theo các bước sau để dọn dẹp tài nguyên của bạn:

1. Mở [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).

2. Chọn stack bạn đã tạo cho hội thảo này (ví dụ: `polly-serverless-stack`).

3. Nhấp vào nút "Delete" ở đầu trang chi tiết stack.

4. Trong hộp thoại xác nhận, nhấp vào "Delete stack" để xác nhận việc xóa.

5. Chờ quá trình xóa stack hoàn tất. Quá trình này có thể mất vài phút.

6. Khi stack đã bị xóa, tất cả các tài nguyên liên quan sẽ được xóa khỏi tài khoản của bạn.

Bằng cách làm theo các bước này, bạn đảm bảo rằng tất cả các tài nguyên được tạo trong suốt hội thảo được dọn dẹp đúng cách, ngăn chặn bất kỳ chi phí không cần thiết nào.

Hãy nhớ rằng, luôn là một thực hành tốt để xem xét tài khoản AWS của bạn thường xuyên và xóa bất kỳ tài nguyên không sử dụng nào để duy trì một môi trường sạch sẽ và hiệu quả về chi phí.
