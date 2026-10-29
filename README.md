# MyVinmec demo (bản đã build, chỉ cần đăng lên)

Thư mục này là website tĩnh đã build sẵn, không cần cài đặt gì. Dữ liệu mẫu lưu trong trình duyệt (localStorage).

## Đăng bằng GitHub Pages
1. Tạo repo mới trên GitHub, upload toàn bộ file trong thư mục này (kể cả file ẩn `.nojekyll`). Thư mục có dưới 100 file nên kéo thả một lần được; hai video nặng khoảng 14 MB và 10 MB, đều dưới giới hạn 25 MB của upload qua web.
2. Vào Settings > Pages > Build and deployment, Source chọn "Deploy from a branch", Branch chọn `main` và thư mục `/ (root)`, bấm Save.
3. Chờ 1 đến 2 phút, địa chỉ hiện ở đầu trang Pages: https://TEN-USER.github.io/TEN-REPO/

Nếu dùng git thay vì kéo thả:

```bash
git init -b main
git add -A
git commit -m "MyVinmec demo"
git remote add origin https://github.com/TEN-USER/TEN-REPO.git
git push -u origin main
```

## Xem thử trên máy
Mở bằng một server tĩnh bất kỳ, ví dụ `npx serve` trong thư mục này. Mở trực tiếp file `index.html` bằng đường dẫn `file://` sẽ không chạy vì trình duyệt chặn module.

## Ghi chú
- Luồng người dùng: Đăng nhập một bước (họ tên, ngày sinh, số điện thoại hoặc email) > tải hồ sơ chấn thương và ảnh đơn thuốc > xác nhận loại chấn thương (tay hoặc chân) và danh sách thuốc > vào app với bài tập và lịch nhắc thuốc theo loại chấn thương. Có thể bỏ qua để chọn chấn thương thủ công, rồi tải đơn thuốc sau trong mục Đơn thuốc. Đăng nhập lại cùng số điện thoại hoặc email sẽ về đúng hồ sơ cũ. Mỗi người có hồ sơ, thuốc và người thân riêng, nhưng tất cả chỉ lưu trong trình duyệt của thiết bị (localStorage), không có máy chủ.
- Nhận diện hồ sơ và đơn thuốc: app chỉ nhận ra đúng hai bộ mẫu của khách (bộ tay: Hội chứng ống cổ tay, bộ chân: Thoái hóa khớp gối trái) bằng cách so khớp hình ảnh ngay trên thiết bị, không phải OCR. Ảnh khác thì không nhận ra: người dùng chọn tay hoặc chân và sửa danh sách thuốc điền sẵn. Muốn đọc ảnh bất kỳ cần OCR hoặc dịch vụ AI.
- Chia sẻ người thân: nhập thông tin người thân sẽ có liên kết gửi qua tin nhắn, email hoặc chia sẻ. Liên kết chứa sẵn ảnh chụp tình trạng lúc tạo (chỉ xem, không tự cập nhật, không thu hồi được). Bản chạy thật cần máy chủ.
- Video bài tập: chân dùng `video/tri-lieu-phuc-hoi.mp4`, tay dùng `video/tri-lieu-tay.mp4` (poster `video/tri-lieu-tay-poster.jpg`). Muốn đổi video chỉ cần thay tệp cùng tên. Các bước bài tập tay trong app được soạn từ nội dung video, cần chuyên môn xác nhận.
- Đây là bản demo thiết kế, không liên kết với Vinmec.
- Ảnh bác sĩ và các ảnh minh hoạ được cắt từ ảnh tham chiếu của tác giả, chỉ mang tính minh hoạ. Hãy thay bằng ảnh có bản quyền phù hợp trước khi công khai.
- Giọng nhắc thuốc và tập luyện: lời đọc trung tính, không gọi tên người dùng, đọc bằng các file âm thanh tiếng Việt trong `audio/` (giọng Microsoft HoaiMy, tạo sẵn cho thuốc và bài tập của hai bộ mẫu, mỗi câu một file, ghi trong `audio/manifest.json`). Thuốc hoặc bài tập ngoài bộ mẫu (ví dụ người dùng tự thêm thuốc) thì app dùng giọng đọc của trình duyệt, cần máy có giọng tiếng Việt. Muốn thêm câu mới: tạo file mp3 cho câu đó và thêm vào manifest.
