# Xử lý hồ sơ lưu trữ công chứng

Chương trình chạy trên Windows dùng để chuẩn bị hồ sơ PDF trước khi lưu trữ: đổi tên file, xóa trang trắng, ký số bằng USB Token và kiểm tra lại bộ hồ sơ sau khi ký.

Kho này chỉ chứa bản phát hành (file .exe) và hướng dẫn sử dụng, không chứa mã nguồn.

## Tải về

Vào mục [Releases](../../releases), tải file `XuLyHoSoLuuTru.exe` của phiên bản mới nhất. Chương trình đóng gói thành một file duy nhất, không cần cài Python hay thư viện nào khác.

Yêu cầu: Windows 10 hoặc 11. Để ký số cần USB Token đã cài driver của nhà cung cấp chứng thư số (chương trình đọc được cả driver 32-bit và 64-bit).

Lần đầu chạy, nếu Windows hiện "Windows protected your PC", bấm "More info" rồi "Run anyway".

## Các chức năng

Mọi tab dùng chung một danh sách file. Thêm file hoặc cả thư mục bằng nút trong khung Danh sách file, hoặc kéo thả vào cửa sổ.

1. Đổi tên file: đặt tên theo mẫu, xem trước từng trang, xoay trang.
2. Xóa trang trắng PDF: chỉnh mức trắng và độ sáng tối thiểu, xem thống kê ngay trên trang đang mở. File không có trang trắng được giữ nguyên từng byte nên chữ ký số còn hiệu lực. File bị xóa trang thì chữ ký cũ chắc chắn hỏng; ô "Gỡ chữ ký số của file bị xóa trang" được tick sẵn để gỡ hẳn chữ ký đó, sau đó ký lại.
3. Ký số PDF: ký từng file hoặc cả danh sách bằng USB Token, đặt vị trí con dấu bằng cách kéo khung trên trang xem trước. Ô "Chữ ký số cũ trong file" cho chọn gỡ chữ ký lỗi và giữ chữ ký hợp lệ (mặc định), giữ nguyên mọi chữ ký cũ, hoặc gỡ hết rồi ký mới. Trước khi ký, chương trình cảnh báo nếu còn file chưa xóa trang trắng, vì xóa trang sau khi ký sẽ làm hỏng chữ ký.
4. Kiểm tra / Gỡ chữ ký số: quét danh sách và phân loại từng file thành đã ký hợp lệ, ký số lỗi, chưa ký số hoặc không đọc được, kèm số trang trắng còn lại. Từ kết quả quét có thể gỡ chữ ký của file lỗi, sao chép file vào các thư mục `1_KySoLoi`, `2_ChuaKySo`, `3_DaKySo`, `4_KhongDocDuoc`, hoặc xuất nhật ký CSV mở bằng Excel.

## Hậu kiểm bộ hồ sơ sau khi ký

Cách kiểm tra để không sót file chưa ký hoặc còn trang trắng:

1. Thêm thư mục chứa file thành phẩm vào danh sách.
2. Mở tab "Kiểm tra / Gỡ chữ ký số", tick "Kiểm tra cả trang trắng", bấm "Quét danh sách".
3. Đọc hộp tổng kết. File được tính ĐẠT khi đã ký số hợp lệ và không còn trang trắng. Nếu có file chưa đạt, bảng tự lọc chỉ còn những file đó, cột Kết luận ghi rõ cần làm gì.
4. Xử lý xong thì quét lại cho tới khi hộp tổng kết báo tất cả đều ĐẠT.

Hộp tổng kết cũng báo file PDF trong danh sách chưa được quét, file bị sửa sau khi quét và file không phải PDF.

Trang trắng được kiểm theo thông số đang đặt ở tab Xóa trang trắng. Khi hậu kiểm, để đúng thông số đã dùng lúc xóa trang.

## Chữ ký bị coi là lỗi khi nào

Chương trình báo ký số lỗi trong các trường hợp:

1. Nội dung đã ký bị thay đổi, hoặc file bị ghi lại sau khi ký.
2. Trang bị sửa, thêm hoặc xóa sau khi ký bằng cách ghi thêm vào cuối file.
3. Chữ ký trống (ký chưa hoàn tất) hoặc dữ liệu chữ ký hỏng.
4. File bị cắt cụt.
5. Chữ ký mật mã không khớp với chứng thư đính kèm.

Thêm chữ ký mới, thêm chú thích hay dữ liệu xác thực dài hạn sau khi ký không làm thay đổi nội dung trang nên vẫn tính là hợp lệ.

Chương trình không kiểm tra chứng thư còn hạn, đã bị thu hồi hay tổ chức cấp chứng thư có được tin cậy hay không. Chữ ký mà Acrobat báo "chưa xác định" chỉ vì máy chưa tin cậy tổ chức cấp chứng thư vẫn được tính là hợp lệ. Muốn kiểm tra hiệu lực chứng thư, dùng Adobe Acrobat hoặc phần mềm của nhà cung cấp chứng thư số.

## Bản quyền và dùng thử

Bản dùng thử có 500 tác vụ. Một tác vụ là ký số thành công một file hoặc xóa trang trắng thành công một file. Mở chương trình, xem trước, đổi tên, xoay trang, kiểm tra và gỡ chữ ký không tính lượt. File xử lý lỗi, sai PIN hay bấm hủy giữa chừng cũng không mất lượt.

Hết lượt dùng thử, chương trình hiện mã máy để xin Key kích hoạt. Mục "Bản quyền" trên thanh công cụ cho xem số lượt còn lại và nhập Key.
