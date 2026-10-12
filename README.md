# Render VIP — bản cập nhật V3

Tải `RenderVIP_Fix_V3_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu chỉ gửi trong cuộc trò chuyện, không lưu trên GitHub.

1. Dùng WinRAR hoặc 7-Zip mở gói, nhập mật khẩu, lấy `RenderVIP_Fix_V3.zip` rồi giải nén ZIP bên trong.
2. Đóng tool và chờ các job/worker kết thúc; chạy `SUA_RENDER_VIP_ALL.bat`.
3. Chọn một tệp tool `.exe` hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py`. BAT tự nhận thư mục, tìm Python, sao lưu và áp dụng 10 file Python đã sửa.
4. Sau khi thành công, mở `CHAY_RENDER_VIP_DA_SUA.bat`.

V3 sửa điều kiện báo nhầm tool đang chạy khi trình xem/soạn thảo mở tệp trong thư mục tool. Tool hoặc worker thực sự đang chạy vẫn chặn cập nhật; thông báo có tên tiến trình và PID. BAT không tự tắt tiến trình.

Nếu thiếu thư viện GUI, BAT tải gói từ PyPI vào thư mục riêng; cần Internet. Không thay Torch/CUDA/model gốc. Job, cấu hình và dữ liệu cấp phép được giữ lại. EXE cũ không được cập nhật; launcher mở bản Python đã sửa dùng runtime/model hiện có. Có BAT khôi phục trong thư mục sao lưu.

Đã qua 34 kiểm tra phát hiện tiến trình/sao lưu/khôi phục và 18 kiểm tra tự nhận/cài GUI trên Linux PowerShell, cùng kiểm tra payload, cú pháp, Python GUI probe và pip bootstrap tải thật từ PyPI. Chưa chạy BAT/cài GUI trực tiếp trên Windows hoặc render với model thật trên máy người nhận.

Các gói V1/V2 được giữ lại để tham khảo. Hãy dùng V3 ở trên.
