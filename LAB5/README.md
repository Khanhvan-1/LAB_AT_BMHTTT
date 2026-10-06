BÁO CÁO BÀI THỰC HÀNH LAB 5

Thông tin sinh viên:

• Họ và tên: Nguyễn Hưng Văn Khánh

• Mã số sinh viên: 1150080021  

Tên bài Lab

• Bài Lab: Lab 5 - Thiết lập mô hình tường lửa pfSense (pfSense Firewall Configuration)

Nội dung đã thực hiện

• Kiểm tra cấu hình mạng trên máy thật bằng ipconfig và route print nhằm tránh xung đột địa chỉ giữa WAN, LAN và DMZ.

• Thiết lập mạng LAN Host-Only trên VMware với dải 10.0.0.0/8, máy thật sử dụng địa chỉ 10.0.0.100/8.

• Thiết lập mạng DMZ riêng trên VMware với dải 172.16.0.0/16.

• Tạo máy ảo pfSense CE 2.7.2-RELEASE (amd64) và cấu hình 3 card mạng WAN, LAN và DMZ.

• Cấu hình WAN pfSense ở chế độ Bridged để kết nối với mạng vật lý của máy thật.

• Cấu hình LAN của pfSense với địa chỉ 10.0.0.1/8.

• Cấu hình DMZ của pfSense với địa chỉ 172.16.0.1/16.

• Cấu hình Windows Server Domain Controller trong LAN với địa chỉ 10.0.0.2/8, Gateway 10.0.0.1 và DNS 10.0.0.2.

• Cấu hình DNS Forwarder trên Domain Controller để phân giải tên miền Internet.

• Truy cập và cấu hình giao diện quản trị WebGUI của pfSense tại https://10.0.0.1.

• Kiểm tra Automatic Outbound NAT của pfSense đối với các mạng LAN và DMZ.

• Vô hiệu hóa các rule Default allow LAN to any và xây dựng firewall rule riêng để kiểm soát lưu lượng.

• Thực hiện Reset States sau khi thay đổi firewall rule nhằm tránh ảnh hưởng của các kết nối đã được lưu trong State Table.

• Tạo máy LAN-Test sử dụng Ubuntu Server với địa chỉ 10.0.0.3/8 để kiểm thử chính sách firewall giữa các host trong LAN.

• Tạo máy DMZ-Web sử dụng Windows Server và IIS với địa chỉ 172.16.0.2/16.

• Thực hiện các tình huống cấu hình Firewall và NAT trên pfSense:

\- Tình huống 1: Chặn ICMP nhưng vẫn cho phép DNS và Web.

\- Tình huống 2: Chỉ cho phép một host cụ thể trong LAN truy cập Internet.

\- Tình huống 3: Cô lập vùng DMZ khỏi mạng LAN nhưng vẫn cho phép DMZ truy cập Internet.

\- Tình huống 4: Cấu hình Port Forward từ WAN vào Web Server trong DMZ.

\- Tình huống 5: Bật logging cho firewall rule và kiểm tra Firewall Log.

Kết quả thực hiện

• Máy thật sử dụng kết nối Wi-Fi:

\- IPv4: 192.168.1.23/24

\- Default Gateway: 192.168.1.1

• VMware Host-Only LAN được cấu hình:

\- Network: 10.0.0.0/8

\- IP máy thật: 10.0.0.100

\- Subnet Mask: 255.0.0.0

\- Default Gateway: để trống

\- DNS: để trống

\- DHCP VMware: Disabled

• VMware DMZ được cấu hình:

\- Network: 172.16.0.0/16

\- Subnet Mask: 255.255.0.0

\- DHCP VMware: Disabled

• pfSense được cấu hình:

\- WAN: \[điền IP WAN pfSense sau]

\- LAN: 10.0.0.1/8

\- DMZ: 172.16.0.1/16

• Domain Controller:

\- IP: 10.0.0.2/8

\- Gateway: 10.0.0.1

\- DNS: 10.0.0.2

\- DNS Forwarder: 8.8.8.8

• LAN-Test:

\- IP: 10.0.0.3/8

\- Gateway: 10.0.0.1

• DMZ-Web:

\- IP: 172.16.0.2/16

\- Gateway: 172.16.0.1

\- Web Server: IIS

\- DNS: 8.8.8.8 sau khi cho phép DMZ truy cập Internet

• Tình huống 1 – Chặn ICMP, cho phép Web/DNS:

\- ping 8.8.8.8: thất bại do ICMP bị chặn.

\- Truy vấn DNS: thành công.

\- Truy cập HTTPS bằng curl.exe -4 https://example.com: thành công.

\- Kết quả chứng minh firewall có thể chặn một giao thức trong khi vẫn cho phép các dịch vụ cần thiết.

• Tình huống 2 – Chỉ cho một host LAN ra Internet:

\- Domain Controller 10.0.0.2: truy cập Internet thành công.

\- LAN-Test 10.0.0.3: không truy cập Internet được.

\- Rule Pass cho 10.0.0.2 được đặt phía trên rule Block toàn bộ LAN net.

• Tình huống 3 – Cô lập DMZ khỏi LAN:

\- Trước khi tạo rule Block, DMZ-Web 172.16.0.2 có thể ping Domain Controller 10.0.0.2.

\- Sau khi thêm Block DMZ net → LAN net và Reset States, DMZ-Web không thể truy cập Domain Controller.

\- DMZ-Web vẫn có thể truy cập Internet nhờ rule Pass DMZ net → Any.

• Tình huống 4 – Port Forward WAN → DMZ:

\- IIS trên DMZ-Web hoạt động tại 172.16.0.2:80.

\- pfSense được cấu hình Port Forward:

&#x20; - Interface: WAN

&#x20; - Protocol: TCP

&#x20; - Destination Port: 8080

&#x20; - Redirect IP: 172.16.0.2

&#x20; - Redirect Port: 80

\- Từ máy thật truy cập http://\[IP-WAN-pfSense]:8080 và hiển thị trang IIS thành công.

\- IP WAN thực tế: \[điền sau]

• Tình huống 5 – Firewall Logging:

\- Bật tùy chọn ghi log cho rule Block.

\- Tạo lưu lượng bị firewall chặn.

\- Kiểm tra tại Status → System Logs → Firewall.

\- Firewall Log hiển thị thông tin lưu lượng bị chặn và rule tương ứng.

• Sau mỗi lần thay đổi firewall rule hoặc NAT, thực hiện Apply Changes và Diagnostics → States → Reset States để bảo đảm kết quả kiểm thử không bị ảnh hưởng bởi state cũ.

Lưu ý khi kiểm tra / chạy lại bài

• Môi trường ảo hóa: VMware Workstation.

• Firewall: pfSense CE 2.7.2-RELEASE amd64.

• File cài đặt: pfSense-CE-2.7.2-RELEASE-amd64.iso.

• WAN pfSense: Bridged với mạng vật lý của máy thật.

• LAN: 10.0.0.0/8.

• pfSense LAN: 10.0.0.1.

• Máy thật quản trị pfSense: 10.0.0.100.

• Domain Controller: 10.0.0.2.

• LAN-Test: 10.0.0.3.

• DMZ: 172.16.0.0/16.

• pfSense DMZ: 172.16.0.1.

• DMZ-Web: 172.16.0.2.

• Không cấu hình Default Gateway hoặc DNS trên card VMware Host-Only 10.0.0.100 của máy thật.

• Không sử dụng mạng NAT có địa chỉ thuộc 10.0.0.0/8 cho WAN vì sẽ gây chồng lấn với LAN.

• Rule firewall trên pfSense được xử lý từ trên xuống dưới, vì vậy phải kiểm tra đúng thứ tự rule.

• Khi thay đổi rule, cần dừng kết nối kiểm thử cũ, Apply Changes và Reset States trước khi kiểm tra lại.

• Giữ Anti-Lockout Rule để tránh tự khóa quyền truy cập WebGUI của pfSense.

• pfSense CE 2.7.2 được sử dụng trong môi trường thực hành cô lập, không sử dụng làm firewall Internet-facing trong hệ thống thực tế.

• Chỉ thực hiện các thử nghiệm Firewall/NAT trong môi trường máy ảo của bài Lab.

