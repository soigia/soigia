# Render VIP — bản chọn một tệp (V2)

Tải `RenderVIP_Fix_V2_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu chỉ gửi trong cuộc trò chuyện, không lưu trên GitHub.

1. Dùng WinRAR hoặc 7-Zip mở gói, nhập mật khẩu, lấy `RenderVIP_Fix_V2.zip` rồi giải nén ZIP bên trong.
2. Đóng tool, chạy `SUA_RENDER_VIP_ALL.bat` ở nơi vừa giải nén.
3. Chọn một tệp tool `.exe` hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py`. BAT tự nhận thư mục, tìm Python, sao lưu và áp dụng 10 file Python đã sửa.
4. Khi cập nhật xong, mở `CHAY_RENDER_VIP_DA_SUA.bat` trong thư mục tool.

Nếu thiếu GUI nhưng có Python 64-bit 3.10 trở lên hoạt động, BAT cần Internet để cài PyQt6/NumPy/OpenCV/psutil từ PyPI vào thư mục riêng. Pip bootstrap được kiểm tra SHA256. Model, Python runtime gốc và Torch/CUDA không bị thay. BAT không yêu cầu chọn `python.exe`.

Chọn EXE của bộ native portable đầy đủ: BAT chuẩn bị bản Python mới cạnh EXE, dùng model/runtime hiện có. EXE cũ vẫn là bản cũ; BAT không chỉnh nội dung hoặc giải mã EXE và giữ nguyên cơ chế bản quyền của mã Python.

Đã qua 18 kiểm tra tự nhận/cài GUI và 24 kiểm tra sao lưu/khôi phục trên Linux PowerShell, cùng kiểm tra payload, syntax, Python GUI probe và pip bootstrap tải thật từ PyPI. Chưa chạy BAT/cài GUI trực tiếp trên Windows hoặc render với model thật trên máy người nhận.

Gói `RenderVIP_Fix_PROTECTED.zip` là bản đầu, còn giữ lại để tham khảo. Hãy dùng bản V2 ở trên.
