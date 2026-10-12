# Render VIP — gói cập nhật được mã hóa

Tệp `RenderVIP_Fix_PROTECTED.zip` được mã hóa AES-256. Mật khẩu chỉ gửi riêng cho người nhận, không lưu trong repository.

1. Tải tệp bằng nút tải file của GitHub hoặc link tải trực tiếp đã gửi trong cuộc trò chuyện.
2. Dùng WinRAR hoặc 7-Zip mở tệp, nhập mật khẩu và giải nén `RenderVIP_Fix.zip`.
3. Giải nén ZIP bên trong để lấy `SUA_RENDER_VIP_ALL.bat` và hướng dẫn.
4. Đóng tool, đặt BAT cạnh `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py`, rồi chạy BAT. Sau cập nhật, mở `CHAY_RENDER_VIP_DA_SUA.bat`.

BAT tự chứa 10 file Python đã sửa; có sao lưu và khôi phục khi cập nhật lỗi. Đây là cập nhật mã Python, chưa cập nhật EXE cũ. Cần Python GUI phù hợp và bộ model/runtime gốc đầy đủ. Không tự thay Torch/CUDA.

Payload, hash, cú pháp và giao dịch sao lưu/khôi phục đã được kiểm tra trong môi trường Linux. Chưa chạy BAT trực tiếp trên Windows hoặc thử model thật trên máy của người nhận.
