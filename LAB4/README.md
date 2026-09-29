BÁO CÁO BÀI THỰC HÀNH LAB 4

Thông tin sinh viên:

•  Họ và tên: Nguyễn Hưng Văn Khánh

•  Mã số sinh viên: 1150080021

Tên bài Lab

•  Bài Lab:Lab 4 - Khảo sát và đánh giá bề mặt mạng bằng Nmap

Nội dung đã thực hiện

• Thiết lập môi trường mạng Host-Only giữa Kali Linux và Metasploitable 2 trên VMware Workstation

• Kiểm tra địa chỉ IP và khả năng kết nối giữa Kali Linux và Metasploitable 2

• Thực hiện Host Discovery bằng Nmap để phát hiện các host đang hoạt động trong mạng 172.16.16.0/24

• Thực hiện các kỹ thuật quét TCP gồm TCP Connect Scan (-sT), SYN Scan (-sS), FIN Scan (-sF), Xmas Scan (-sX), NULL Scan (-sN) và ACK Scan (-sA)

• Thực hiện quét UDP các cổng phổ biến bằng -sU --top-ports 20

• Nhận diện dịch vụ và phiên bản bằng -sV

• Nhận diện hệ điều hành mục tiêu bằng -O và tổng hợp thông tin bằng Aggressive Scan (-A)

• Sử dụng NSE Script để thu thập thông tin SMB bằng smb-os-discovery và kiểm tra MS17-010 bằng smb-vuln-ms17-010

• Xuất kết quả Nmap dưới các định dạng TXT, XML, Grepable và HTML  

Kết quả thực hiện

• Kali Linux được cấu hình IP Host-Only: 172.16.16.133/24

• Metasploitable 2 có địa chỉ IP: 172.16.16.132/24

• Kiểm tra kết nối Kali → Metasploitable 2 thành công với 4 packets transmitted, 4 received, 0% packet loss

• Host Discovery phát hiện 4 host đang hoạt động: 172.16.16.1, 172.16.16.132, 172.16.16.133 và 172.16.16.254

• TCP Connect Scan phát hiện 23 cổng TCP mở, trong đó có các dịch vụ FTP, SSH, Telnet, SMTP, DNS, HTTP, SMB, MySQL, PostgreSQL, VNC, IRC và Apache Tomcat

• Version Detection xác định được một số dịch vụ như:

\- FTP: vsftpd 2.3.4

\- SSH: OpenSSH 4.7p1 Debian 8ubuntu1

\- HTTP: Apache httpd 2.2.8

\- SMB: Samba smbd 3.X - 4.X

\- MySQL: MySQL 5.0.51a-3ubuntu5

\- PostgreSQL: PostgreSQL DB 8.3.0 - 8.3.7

\- VNC: VNC protocol 3.3

\- Tomcat: Apache Tomcat/Coyote JSP engine 1.1

&#x20; • OS Detection nhận diện máy mục tiêu chạy Linux 2.6.X, chi tiết dự đoán Linux 2.6.9 - 2.6.33

&#x20; • UDP Scan phát hiện 53/udp (DNS) và 137/udp (NetBIOS-NS) ở trạng thái open; một số cổng khác ở trạng thái open|filtered

&#x20; • NSE smb-os-discovery xác định hệ điều hành SMB là Unix (Samba 3.0.20-Debian), tên máy metasploitable, domain localdomain

&#x20; • NSE smb-vuln-ms17-010 không trả về trạng thái VULNERABLE, do đó không có đủ bằng chứng để kết luận mục tiêu bị ảnh hưởng bởi MS17-010

&#x20; • Xuất thành công các tệp kết quả:

\- nmap\_result.txt

\- nmap\_result.xml

\- nmap\_result.html

\- smb.txt

&#x20; • Lọc thành công thông tin cổng 445/tcp open microsoft-ds từ tệp Grepable bằng grep

Lưu ý khi kiểm tra / chạy lại bài

• Môi trường máy quét: Kali Linux trên VMware Workstation

• Máy mục tiêu: Metasploitable 2

• Mạng thực hành: Host-Only 172.16.16.0/24

• IP Kali Linux: 172.16.16.133

• IP Metasploitable 2: 172.16.16.132

• Phiên bản Nmap sử dụng: Nmap 7.99

• Các tệp kết quả Nmap được lưu trong thư mục Home của người dùng Kali

• Chỉ thực hiện quét trên các máy ảo thuộc môi trường thực hành Host-Only, không quét các hệ thống bên ngoài khi chưa được phép.

