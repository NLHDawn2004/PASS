# KIVORA PWA

Ứng dụng quản lý mật khẩu cục bộ, dùng được trên iPhone qua Safari.

## Cài đặt bằng iPhone (GitHub Pages)

1. Đăng nhập github.com trong Safari, tạo repository mới tên `keyvault-pwa`, chọn **Private** nếu muốn giữ mã nguồn riêng. Lưu ý GitHub Pages trên một số gói chỉ hỗ trợ public repository; nếu không thể bật Pages, sử dụng repository public nhưng tuyệt đối không tải dữ liệu mật khẩu/bản sao lưu lên repository.
2. Tải các tệp `index.html`, `app.js`, `sw.js`, `manifest.webmanifest`, `icon.svg`, `icon-192.png`, `icon-512.png` lên thư mục gốc của repository qua **Add file → Upload files**. Nếu khó thao tác trên điện thoại, trong Safari chọn **Yêu cầu trang web cho máy tính**.
3. Vào **Settings → Pages → Build and deployment → Deploy from a branch**, chọn nhánh `main`, thư mục `/(root)`, nhấn Save.
4. Chờ triển khai; mở `https://TEN-TAI-KHOAN.github.io/keyvault-pwa/`.
5. Trong Safari chọn Chia sẻ → Thêm vào Màn hình chính → Thêm.

## Lưu ý bảo mật

- Mật khẩu được mã hóa AES-256-GCM bằng khóa dẫn xuất PBKDF2-SHA256 (600.000 vòng) từ mật khẩu chính, với salt ngẫu nhiên 16 byte và IV ngẫu nhiên 12 byte cho mỗi lần lưu.
- Dữ liệu mã hóa lưu trong localStorage của origin. Không có server, không có đồng bộ. Xóa dữ liệu Safari, thay đổi origin hoặc gỡ PWA có thể làm mất kho. Hãy sao lưu định kỳ qua nút **Xuất bản sao lưu**.
- Nếu quên mật khẩu chính, không có cơ chế khôi phục. Sao lưu mã hóa cũng cần mật khẩu chính.
- Bản này không hỗ trợ Face ID. Face ID/WebAuthn yêu cầu quy trình thiết kế bảo mật riêng.
- Favicon lấy từ Google S2, chỉ gửi **tên miền** dịch vụ, không gửi tài khoản/mật khẩu. Có thể tắt bằng cách sửa `render()` trong `app.js` nếu không muốn tiết lộ tên miền dịch vụ cho bên thứ ba.
- Sao chép mật khẩu vào clipboard có thể khiến ứng dụng khác đọc được; clipboard không được tự xóa.
- Chỉ triển khai trên HTTPS tin cậy, bảo vệ tài khoản GitHub bằng 2FA. Hosting cung cấp mã JavaScript, nên người quản lý hosting hoặc ai chiếm quyền tài khoản hosting có thể sửa mã để lấy mật khẩu khi bạn mở kho. Đây chưa phải sản phẩm được kiểm toán bảo mật.
- Không nhập mật khẩu quan trọng vào phiên bản thử nghiệm khi chưa được kiểm tra bảo mật và khôi phục dữ liệu.

## Phiên bản nhóm tài khoản
- Nhập Tên loại tài khoản / Tài khoản / Mật khẩu.
- Google, GG và Gmail được nhóm thành Google; Facebook/FB thành Facebook.
- Chạm tiêu đề nhóm để xổ xuống hoặc thu gọn.
- Gõ vào thanh tìm kiếm để lọc và xem gợi ý nhóm phù hợp.
- Không sử dụng mật khẩu ví dụ `123456` làm mật khẩu thật.


## Thêm nhanh 3 dòng
Mở kho, dán vào ô Thêm nhanh theo thứ tự: tên dịch vụ, tên tài khoản, mật khẩu (mỗi mục một dòng), rồi chọn Lưu tài khoản nhanh. Google/GG/Gmail tự gom nhóm Google. Tìm kiếm gợi ý nhóm và tên tài khoản. Không dán mật khẩu thật vào các bản demo hoặc website không tin cậy.
