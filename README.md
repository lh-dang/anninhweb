# 🛠️ BÁO CÁO NHÓM ĐỀ TÀI VULNERABLE AND OUTDATED COMPONENTS
-  🔐 `Heartbleed (CVE-2014-0160)` Đây là lỗ hổng nghiêm trọng trong OpenSSL phiên bản 1.0.1 đến 1.0.1f, cho phép đọc bộ nhớ máy chủ từ xa.
## 🧠 Tấn công Heartbleed 📤 Hacker sẽ thu được:
| Loại dữ liệu bị lộ          | Mô tả cụ thể                                                    |
| --------------------------- | --------------------------------------------------------------- |
| 🔑 **Private key**          | Khóa riêng SSL – cực kỳ nghiêm trọng, cho phép giả mạo máy chủ  |
| 🔐 **Session token**        | Dữ liệu đăng nhập còn sống (cookie, JWT…)                       |
| 🧑 **Thông tin người dùng** | Tên, mật khẩu, email, số điện thoại nếu có người đang đăng nhập |
| 📄 **Nội dung HTTPS**       | Dữ liệu plaintext được gửi qua SSL trong phiên giao dịch        |
| 🧬 **Mã nguồn**             | Có thể tiết lộ một phần mã nguồn nếu web xử lý động             |
## 📛 Vì sao nguy hiểm?
- 🕵️ Không để lại dấu vết: Máy chủ không hề biết đang bị tấn công.
- 🔁 Tấn công liên tục: Có thể lặp đi lặp lại nhiều lần để rò từng phần bộ nhớ.
- 🧬 Không cần đăng nhập: Kẻ tấn công không cần quyền truy cập hay xác thực.
- 🔒 Lộ khóa bí mật: Nếu private key bị lộ → attacker có thể giải mã mọi lưu lượng HTTPS đã ghi lại.
## 🛡️ Đó là lý do:
> Lỗi Heartbleed được đánh giá là một trong những lỗ hổng bảo mật nghiêm trọng nhất trong lịch sử Internet.
