\# BÁO CÁO BÀI THỰC HÀNH LAB 6



\## 1. Thông tin sinh viên



\- \*\*Họ và tên:\*\* Nguyễn Hưng Văn Khánh

\- \*\*Mã số sinh viên:\*\* 1150080021



\## 2. Tên bài Lab



\- \*\*Bài Lab:\*\* Lab 6 – Cấu hình xác thực LDAP trên pfSense với Active Directory (LDAP Authentication with Active Directory).



\## 3. Mục tiêu thực hành



\- Tìm hiểu cơ chế xác thực LDAP và cách pfSense kết nối với Active Directory.

\- Cấu hình máy chủ xác thực LDAP trên pfSense.

\- Khai báo thông tin Domain Controller, Base DN, Authentication Containers và Bind Credentials.

\- Kiểm tra khả năng kết nối và xác thực tài khoản người dùng trong Active Directory.

\- Phân tích lỗi phát sinh trong quá trình xác thực và kiểm tra nhật ký hệ thống để xác định nguyên nhân.



\## 4. Nội dung đã thực hiện



\- Kiểm tra cấu hình mạng giữa pfSense và máy chủ Windows Server chạy Active Directory.

\- Xác định domain Active Directory đang sử dụng là `lab5.local`.

\- Kiểm tra địa chỉ IP của Domain Controller là `10.6.0.10`.

\- Mở công cụ Active Directory Users and Computers để kiểm tra cấu trúc domain và tài khoản người dùng.

\- Xác định OU chứa tài khoản người dùng thực hành là `LAB6-Users`.

\- Kiểm tra tài khoản người dùng `SV A`, có tên đăng nhập `sv\_a`.

\- Kiểm tra tài khoản người dùng `SV B` trong OU `LAB6-Users`.

\- Xác định tài khoản dịch vụ LDAP là `Service LDAP`, có tên đăng nhập `svc\_pfsense\_ldap`.

\- Kiểm tra thuộc tính Distinguished Name (DN) của tài khoản dịch vụ LDAP.

\- Truy cập giao diện quản trị WebGUI của pfSense để cấu hình máy chủ xác thực.

\- Tạo máy chủ xác thực có tên `LAB6-AD`, sử dụng loại xác thực LDAP.

\- Khai báo địa chỉ Domain Controller `10.6.0.10`.

\- Cấu hình Base DN, Authentication Containers, Bind Credentials DN và các thuộc tính tìm kiếm người dùng.

\- Sử dụng thuộc tính `sAMAccountName` để tìm kiếm tài khoản đăng nhập.

\- Thực hiện kiểm tra xác thực LDAP trên pfSense.

\- Kiểm tra nhật ký LDAP Debug để xác định bước phát sinh lỗi trong quá trình xác thực.



\## 5. Kết quả cấu hình



\### 5.1. Thông tin Active Directory



\- \*\*Domain:\*\* `lab5.local`

\- \*\*Domain Controller:\*\* `10.6.0.10`

\- \*\*OU người dùng:\*\* `OU=LAB6-Users,DC=lab5,DC=local`

\- \*\*Tài khoản người dùng kiểm thử:\*\* `sv\_a`

\- \*\*Tài khoản dịch vụ LDAP:\*\* `svc\_pfsense\_ldap`

\- \*\*DN tài khoản dịch vụ LDAP:\*\* `CN=Service LDAP,CN=Users,DC=lab5,DC=local`



\### 5.2. Thông tin máy chủ xác thực trên pfSense



\- \*\*Tên máy chủ xác thực:\*\* `LAB6-AD`

\- \*\*Loại xác thực:\*\* LDAP

\- \*\*Hostname/IP:\*\* `10.6.0.10`

\- \*\*Base DN:\*\* `DC=lab5,DC=local`

\- \*\*Authentication Containers:\*\* `OU=LAB6-Users,DC=lab5,DC=local`

\- \*\*Bind Credentials DN:\*\* `CN=Service LDAP,CN=Users,DC=lab5,DC=local`

\- \*\*User Naming Attribute:\*\* `sAMAccountName`

\- \*\*Group Naming Attribute:\*\* `cn`

\- \*\*Group Member Attribute:\*\* `memberOf`



\### 5.3. Kiểm tra kết nối và xác thực



\- Đã kiểm tra khả năng kết nối mạng từ pfSense đến máy chủ Active Directory.

\- Đã kiểm tra kết nối TCP đến địa chỉ `10.6.0.10` trên cổng `636`. Kết quả kết nối TCP thành công chỉ xác nhận cổng có thể truy cập, chưa chứng minh quá trình xác thực LDAP thành công.

\- Cấu hình đang được kiểm tra sử dụng LDAP trên cổng `389`.

\- Khi thử xác thực tài khoản `sv\_a`, nhật ký LDAP Debug ghi nhận bộ lọc tìm kiếm `(samAccountName=sv\_a)`.

\- Nhật ký ghi nhận lỗi `Could not bind to LDAP server LAB6-AD. Please check the bind credentials.`



Kết quả cho thấy quá trình xác thực hiện chưa thành công và lỗi được ghi nhận ở bước Bind với máy chủ LDAP. Cần tiếp tục kiểm tra mật khẩu Bind, trạng thái tài khoản `Service LDAP` và các thông tin xác thực liên quan trước khi kết luận nguyên nhân cuối cùng.



\## 6. Đánh giá kết quả



\### Nội dung đã thực hiện được



\- Xác định được domain Active Directory và địa chỉ Domain Controller.

\- Xác định được OU chứa người dùng thực hành.

\- Xác định được tên đăng nhập của người dùng `SV A`.

\- Xác định được DN của tài khoản dịch vụ LDAP.

\- Thiết lập được các thông số cơ bản của máy chủ xác thực `LAB6-AD` trên pfSense.

\- Đọc được nhật ký LDAP Debug và xác định lỗi xảy ra ở bước Bind.



\### Nội dung cần tiếp tục hoàn thiện



\- Kiểm tra lại mật khẩu và trạng thái tài khoản `Service LDAP`.

\- Kiểm tra lại thông tin Bind Credentials trong cấu hình pfSense.

\- Thực hiện lại bài kiểm tra LDAP sau khi xác minh thông tin tài khoản dịch vụ.

\- Xác nhận pfSense có thể tìm kiếm và xác thực thành công người dùng `sv\_a`.

\- Chỉ ghi nhận kết quả xác thực thành công sau khi bài kiểm tra thực tế trả về kết quả phù hợp.



\## 7. Kết luận



Qua bài thực hành Lab 6, em đã tìm hiểu và thực hiện các bước cấu hình máy chủ xác thực LDAP trên pfSense kết hợp với Active Directory. Bài thực hành giúp em hiểu vai trò của Base DN, Authentication Containers, Bind Credentials và thuộc tính `sAMAccountName` trong quá trình tìm kiếm và xác thực người dùng.



Trong quá trình kiểm thử, hệ thống phát sinh lỗi tại bước Bind với máy chủ LDAP. Thông qua nhật ký LDAP Debug, em xác định được vị trí cần kiểm tra và tiếp tục xử lý thông tin tài khoản dịch vụ LDAP để hoàn thiện quá trình xác thực.



Bài thực hành giúp em nâng cao kỹ năng cấu hình xác thực tập trung, kiểm tra kết nối giữa các máy trong môi trường ảo hóa và phân tích nhật ký khi xử lý sự cố.



\## 8. Lưu ý khi kiểm tra và chạy lại bài



\- Sử dụng đúng domain `lab5.local` đang được cấu hình trên Windows Server.

\- Kiểm tra địa chỉ IP của Domain Controller trước khi cấu hình pfSense.

\- Đảm bảo pfSense có thể kết nối đến máy chủ Active Directory.

\- Kiểm tra chính xác Base DN và DN của tài khoản dịch vụ LDAP.

\- Đảm bảo mật khẩu Bind Credentials trùng khớp với mật khẩu hiện tại của tài khoản dịch vụ.

\- Kiểm tra tài khoản dịch vụ có bị vô hiệu hóa, khóa hoặc yêu cầu đổi mật khẩu hay không.

\- Phân biệt lỗi kết nối TCP với lỗi xác thực LDAP: kết nối được cổng mạng không đồng nghĩa với việc Bind thành công.

\- Sau mỗi lần thay đổi cấu hình, lưu lại và thực hiện kiểm tra xác thực LDAP.

\- Chỉ kết luận hệ thống hoạt động thành công khi có kết quả kiểm thử xác nhận.

