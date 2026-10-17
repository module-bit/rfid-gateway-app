<p align="center">
  <img src="assets/logo.png" alt="ModuleBit" width="200">
</p>

<h1 align="center">RFID Gateway</h1>

Phần mềm kết nối và quản lý **reader RFID UHF Hopeland** trên Windows: đọc tag realtime, cấu hình reader,
ghi / khoá tag, và cung cấp API (REST + WebSocket) cho hệ thống khác (ERP, WMS…).

Toàn bộ thao tác làm trên giao diện web, chương trình chỉ gồm **một file `rfid-gateway.exe`**.

## Tải về

Vào mục **[Releases](../../releases)**, tải file `RFID-Gateway-<phiên bản>.zip` của bản mới nhất.

## Yêu cầu

- Windows 10 / 11 (64-bit)
- [Git for Windows](https://git-scm.com/download/win), cài với tuỳ chọn mặc định (dùng để tải license)
- Kết nối Internet tới GitHub (cổng 22) khi khởi động
- **License do nhà cung cấp cấp cho từng máy**

## Cài đặt

1. Giải nén file zip vào một thư mục riêng, ví dụ `C:\RFID\`.
2. Nhấp đúp **`rfid-gateway.exe`**. Trình duyệt tự mở `http://127.0.0.1:8080`.
3. Trang **Kích hoạt RFID Gateway** hiện ra:
   - nhập **mã khách hàng** do nhà cung cấp cấp → **Lưu**;
   - bấm **Sao chép** (hoặc **Tải file .txt**) và gửi thông tin máy cho nhà cung cấp.
4. Khi nhà cung cấp báo đã cấp license, bấm **Kiểm tra lại** (trang cũng tự kiểm tra mỗi phút) → vào giao diện chính.

Chương trình chạy ngầm, không có cửa sổ. Nhấp đúp `rfid-gateway.exe` lần nữa chỉ mở lại trình duyệt.

## Sử dụng

| Việc | Cách làm |
|---|---|
| Thêm reader | Nút **+** ở cột Reader: qua mạng LAN (IP + cổng, thường 9090) hoặc cổng COM |
| Đọc tag | Tab **Đọc tag** → chọn ăng-ten → **Đọc liên tục** / **Đọc 1 lần** |
| Cấu hình reader | Tab **Cấu hình reader** (công suất, ăng-ten, tần số, mạng, GPIO…) |
| Giao diện sáng / tối | **⚙ → Giao diện → Sáng / Tối / Hệ thống** |
| Cho máy khác gọi API | **⚙ → Truy cập từ mạng LAN** (tự khởi động lại). Mỗi hệ thống bên ngoài cần OAuth client: menu **⋮** của reader → **Truy cập API** |
| Xem license | **⚙ → Thông tin license** |
| Thoát | **⚙ → Thoát chương trình** |

## Cập nhật lên bản mới

1. **⚙ → Thoát chương trình**.
2. Chép `rfid-gateway.exe` của bản mới đè lên file cũ.
3. Mở lại `rfid-gateway.exe`.

**Giữ nguyên** các file chương trình tự tạo cạnh exe:

| File / thư mục | Nội dung |
|---|---|
| `guard\` | Mã khách hàng và **khoá bảo mật riêng của máy**. Không xoá, không gửi file `id_ed25519` cho ai |
| `rfid-gateway.json` | Danh sách reader, tên hiển thị, OAuth client, cài đặt LAN |
| `rfid-gateway.log` | Nhật ký chạy (gửi kèm khi cần hỗ trợ) |

## Hỗ trợ

Khi gặp lỗi, gửi cho nhà cung cấp: ảnh chụp trang lỗi, **mã máy** (⚙ → Thông tin license) và file `rfid-gateway.log`.
