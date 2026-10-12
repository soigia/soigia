# Render VIP — bản cập nhật V5

Tải `RenderVIP_Fix_V5_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu chỉ gửi trong cuộc trò chuyện, không lưu trên GitHub.

1. Dùng WinRAR hoặc 7-Zip mở gói, nhập mật khẩu, lấy `RenderVIP_Fix_V5.zip` rồi giải nén ZIP bên trong vào thư mục mới.
2. Đóng tool và chờ các job/worker kết thúc; chạy `SUA_RENDER_VIP_ALL.bat` mới.
3. Chọn EXE chính hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py` trong thư mục app có runtime và voices, ngoài thư mục sao lưu.
4. BAT tự nhận thư mục, tìm Python, sao lưu và cập nhật 10 file Python. Khi thành công, mở `CHAY_RENDER_VIP_DA_SUA.bat` ngay trong app.

V5 sửa việc các callback lúc mở ứng dụng ghi đè cài đặt âm lượng đã lưu; nhãn phần trăm được đồng bộ với thanh kéo dù signals bị chặn. Giữ riêng cài đặt từng job sau khi khôi phục. Nếu bản cũ đã lưu nhầm 100%, đặt lại mức mong muốn và áp dụng cho mọi job một lần.

Preview có thể co vừa panel hẹp thay vì kích thước tối thiểu 480px làm video bị cắt. Tỷ lệ chia panel được nhớ bằng số, không khôi phục binary Qt state cũ.

Giữ một synth sống trong ứng dụng: server Supertonic đang rảnh phải được đóng và thu hồi trước khi worker khác/Piper/nghe thử mở process. Giữ model/process khi cùng worker đổi giọng. Batch mặc định 100 nếu ít nhất 12 CPU khả dụng và 12GiB RAM trống, nếu không là 50; cấu hình môi trường riêng vẫn được giữ. Worker có giới hạn padding và thu nhỏ batch khi thiếu bộ nhớ. Giữ số bước và tốc độ giọng; cần đo lại trên máy thật để biết mức cải thiện.

Log TT_101 gần nhất: 747/1563 câu đã tổng hợp qua 3 prefix trong tổng 190.8s của các lời gọi synth (~3.915 câu/s). Log chưa kết thúc; không phải thời gian toàn job. Các log trước chỉ bị chặn ở ECAPA, chưa có số liệu synth để so phần trăm tăng tốc. Có số liệu gốc trong ZIP bên trong.

Bao gồm sửa V3 phát hiện tiến trình và V4 launcher Python cô lập: không nạp .pyd Python 3.12 của EXE vào Python 3.10. BAT từ chối cập nhật bên trong thư mục _BACKUP_RENDER_VIP.

Nếu thiếu thư viện GUI, BAT tải gói từ PyPI vào thư mục riêng; cần Internet. Không thay Torch/CUDA/model gốc. Job, cấu hình và dữ liệu cấp phép được giữ lại. EXE cũ không được cập nhật; launcher mở bản Python đã sửa. Có BAT khôi phục trong thư mục sao lưu.

Kiểm tra: 160 bài kiểm tra Python + 50 subtests, 35 kiểm tra cập nhật/khôi phục, 18 kiểm tra tìm runtime/cài GUI; payload và launcher thật đều được kiểm tra. Có kiểm tra Qt thật khôi phục âm lượng, từng job và fit khung hình; kiểm tra tiến trình thật phải đóng worker trước khi worker thứ hai mở. Các kiểm tra chạy trên Linux/PowerShell 7.4.6; chưa chạy BAT trực tiếp trên Windows hoặc đo model thật trên RTX/Xeon của người nhận.

Các gói V1–V4 được giữ lại để tham khảo. Hãy dùng V5.
