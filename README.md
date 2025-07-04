# BÁO CÁO NHÓM ĐỀ TÀI VULNERABLE AND OUTDATED COMPONENTS
## Heartbleed (CVE-2014-0160)
* Đây là lỗ hổng nghiêm trọng trong OpenSSL phiên bản 1.0.1 đến 1.0.1f, cho phép đọc bộ nhớ máy chủ từ xa.
### MỤC TIÊU: Cấu hình máy victim (Ubuntu 14.04) dễ bị tấn công Heartbleed (CVE-2014-0160)
#### 🔧 Bước 1: Cài đặt Ubuntu 14.04
TRÊN WINDOWS TẢI UBUNTU 14.04
```
Start-BitsTransfer -Source "http://releases.ubuntu.com/14.04/ubuntu-14.04.6-desktop-amd64.iso" -Destination "C:\Users\HAIDA\Downloads\ubuntu-14.04.6-desktop-amd64.iso"
```
KIỂM TRA THƯ MỤC HIỆN TẠI XEM CÓ UBUNTU 14.04 CHƯA
```
Get-ChildItem -Path "C:\Users\HAIDA\Downloads" | Where-Object { $_.Name -like "*.iso" }
```
Sau đó thêm vào VMware
#### 🛠️ Bước 2: Cài đặt Apache2 và OpenSSL Trên Ubuntu
KIỂM TRA PHIÊN BẢN OPENSSL
```
openssl version
```
Hoặc
```
openssl version -a
```
=> OpenSSL 1.0.1f 6 Jan 2014 ✅
#### 🛡️ Bước 3: Cài Apache2 và mod_ssl
```
sudo apt-get update
sudo apt-get install apache2
sudo a2enmod ssl
```
#### 🛡️ Bước 4: Tạo chứng chỉ SSL tự ký
```
sudo mkdir /etc/apache2/ssl

sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/apache2/ssl/apache.key \
-out /etc/apache2/ssl/apache.crt
```
##### 💡 Gợi ý khi được hỏi:

- Country Name: VN

- State: HCM

- Common Name (CN): localhost (rất quan trọng)

- Các mục khác cứ điền đại cũng được
#### ⚙️ Bước 5: Cấu hình Apache để bật HTTPS
```
sudo nano /etc/apache2/sites-available/default-ssl.conf
```
TÌM VÀ SỬA
```
SSLCertificateFile      /etc/ssl/certs/ssl-cert-snakeoil.pem
SSLCertificateKeyFile   /etc/ssl/private/ssl-cert-snakeoil.key
```
THÀNH
```
SSLCertificateFile    /etc/apache2/ssl/apache.crt
SSLCertificateKeyFile /etc/apache2/ssl/apache.key
```
#### 🧩 Bước 6: Bật site SSL & khởi động lại Apache
```
sudo a2ensite default-ssl
sudo service apache2 restart
```
#### ✅ Bước 7: Kiểm tra dịch vụ chạy trên HTTPS
```
curl -k https://localhost
```
### 🌿 Cấu hình xong môi trường
