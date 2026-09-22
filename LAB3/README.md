BÁO CÁO BÀI THỰC HÀNH LAB 3

Thông tin sinh viên:

•  Họ và tên: Nguyễn Hưng Văn Khánh

•  Mã số sinh viên: 1150080021

Tên bài Lab

•  Bài Lab: Lab 3 - Nhận diện và ứng phó các mối đe dọa đến an toàn thông tin

Nội dung đã thực hiện

•  Mô phỏng và kiểm tra tải HTTP local (DDoS) trên cổng 8080 bằng script Python

•  Phân tích log email phát hiện tấn công gửi thư hàng loạt (Mail bomb/Spam)

•  Phân tích email lừa đảo (Phishing) và nhận diện các kịch bản Social Engineering trong tệp CSV

•  Dọn dẹp môi trường (xóa persistence Run key, gỡ Scheduled Task, tắt HTTP server, xóa tài khoản lab3user)

•  Kiểm tra trạng thái bảo vệ thời gian thực của Microsoft Defender

•  Băm toàn vẹn SHA-256 cho toàn bộ tệp bằng chứng và đóng gói file nén

Kết quả thực hiện

•  Chạy hoàn tất kịch bản tải local 50 requests thành công với 0 failures

•  Trích xuất và đếm thành công người gửi mail bất thường bulk-sender@example.invalid (60 mail)

•  Nhận diện đủ 5 chỉ dấu lừa đảo trên phishing\_email.txt và phân loại chính xác 6 kịch bản Social Engineering (SE01 - SE06)

•  Cleanup hoàn tất sạch sẽ: cổng 8080 đã tắt, các entry duy trì (Run key, Scheduled Task) và user lab3user đã được loại bỏ

•  Xác minh Microsoft Defender duy trì hoạt động bảo vệ (AntivirusEnabled, RealTimeProtectionEnabled, IsTamperProtected đều đạt True)

•  Xuất thành công tệp evidence\_sha256.csv chứa mã băm đầy đủ các tệp minh chứng và nén hoàn chỉnh tệp LAB3\_Evidence.zip

Lưu ý khi kiểm tra / chạy lại bài

•  Môi trường: Windows PowerShell (Administrator)

•  Thư mục bằng chứng: C:\\LAB3\\Evidence

•  Tệp nén minh chứng: LAB3\_Evidence.zip

