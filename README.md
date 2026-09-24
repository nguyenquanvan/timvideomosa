# Footage Scout cho Windows

Kho phát hành bộ cài Footage Scout và hướng dẫn cập nhật cho nhân viên. Bản mới được đưa lên trang [Releases](https://github.com/nguyenquanvan/timvideomosa/releases) của kho này; website cũ chưa được cập nhật. Thay đổi của từng bản nằm trong ghi chú phát hành.

## Cài lần đầu

1. Mở [bản phát hành mới nhất](https://github.com/nguyenquanvan/timvideomosa/releases/latest).
2. Tải `FootageScout-Setup-<phiên-bản>-win-x64.exe` rồi chạy bộ cài. Yêu cầu Windows 10/11 64-bit; bộ cài tự chuẩn bị WebView2 nếu máy thiếu.
3. Mở app, vào **Cài đặt → AI → chọn model → Tải, kiểm tra & dùng ngay**. Model AI được tải riêng trên từng máy, không nằm trong bộ cài; giữ app mở trong lần tải đầu. Card đồ họa 8 GB nên chọn Ministral 3B hoặc Gemma 3 4B.

## Cập nhật

- **Máy đang dùng 0.42.4 trở lên:** khi app báo có bản mới, bấm **Lưu & cập nhật ngay** (hoặc vào **Cài đặt → Cập nhật**). App tải nền, kiểm tra kích thước và SHA-256 của bộ cài, lưu công việc, cài rồi mở lại. Chờ việc đang chạy (tìm kiếm, phân tích, cắt/xuất video, tải model) xong trước khi bấm.
- **Máy đang dùng 0.42.1 đến 0.42.3:** vào **Cài đặt → Cập nhật → Kiểm tra lại → Tải bộ cài đã kiểm tra**. Lưu công việc, đóng app và chạy bộ cài vừa tải. Từ lần sau dùng được nút **Lưu & cập nhật ngay**.
- **Máy đang dùng 0.42.0 trở xuống:** tải bộ cài mới nhất từ trang Releases, lưu công việc, đóng app và chạy bộ cài một lần.

Cập nhật giữ nguyên dự án, bản nháp, API key, model đã tải và video đã cắt/xuất trong thư mục dữ liệu trên máy (mặc định `%LOCALAPPDATA%\FootageScout`). Bản mã nguồn/portable không tự cập nhật; tải bộ cài thủ công.

## Nội dung mỗi bản phát hành

| Tệp | Dùng để |
| --- | --- |
| `FootageScout-Setup-<phiên-bản>-win-x64.exe` | Bộ cài Windows x64. |
| `FootageScout-Setup-<phiên-bản>-win-x64.exe.sha256` | Kiểm tra bộ cài: một dòng gồm mã SHA-256 và tên tệp. |
| `footage-scout-win-x64.json` | Chức năng cập nhật trong app đọc tệp này: phiên bản, đường dẫn tải, kích thước, SHA-256 và ghi chú. Bản mới nhất luôn ở [`releases/latest/download/footage-scout-win-x64.json`](https://github.com/nguyenquanvan/timvideomosa/releases/latest/download/footage-scout-win-x64.json). |
| `FootageScout-Source-<phiên-bản>-Windows.zip` và `.sha256` | Gói mã nguồn cho kỹ thuật, chỉ có ở một số bản. |

Kiểm tra bộ cài đã tải bằng PowerShell rồi so với mã trong tệp `.sha256`:

```powershell
Get-FileHash .\FootageScout-Setup-<phiên-bản>-win-x64.exe -Algorithm SHA256
```

## Khi phát hành bản mới

- Đưa lên đủ ba tệp: bộ cài, tệp `.sha256` và `footage-scout-win-x64.json`. Các trường `version`, `download_url`, `size`, `sha256` trong JSON phải khớp bộ cài của chính bản đó.
- Không đánh dấu bản là pre-release hoặc draft, nếu không `releases/latest` vẫn trỏ về bản cũ.
- Kho cần được công khai để nhân viên tải mà không phải đăng nhập GitHub. Không đưa API key, dữ liệu dự án hoặc model cá nhân lên kho này.
