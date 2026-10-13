# Render VIP — bản cập nhật V7

Tải `RenderVIP_Fix_V7_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu chỉ gửi trong cuộc trò chuyện, không lưu trên GitHub.

1. Dùng WinRAR hoặc 7-Zip mở gói, nhập mật khẩu, lấy `RenderVIP_Fix_V7.zip` rồi giải nén ZIP bên trong vào thư mục mới.
2. Đóng tool và chờ các job/worker kết thúc; chạy `SUA_RENDER_VIP_ALL.bat` mới.
3. Chọn EXE chính hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py` trong thư mục app có runtime và voices, ngoài thư mục sao lưu.
4. BAT tự tìm Python, sao lưu và cập nhật 10 file Python. Khi thành công, mở `CHAY_RENDER_VIP_DA_SUA.bat` ngay trong app.

V7 nâng cả thanh Gốc và AI lên 0–200% khi xuất DONE, giữ mặc định 100%. Giá trị được giữ trong preset, từng job và MASTER. Có limiter đỉnh cho audio khuếch đại; MASTER premix không tăng gain lần hai. Nghe thử trực tiếp còn giới hạn 100%; tooltip ghi rõ. Kiểm tra WAV PCM thực xác nhận 200%≈2×100% khi chưa chạm giới hạn đỉnh, giữ đúng thời lượng và không hard clip.

Cách xếp giọng giữ như V6: các nhóm nam/nữ trong mỗi đoạn SRT được chia batch và chạy tuần tự trong một process. Với KR/JP Supertonic, bốn ONNX dùng chung nạp một lần; đổi giọng chỉ đổi style đã cache, không mở model mới từng câu. WAV theo cue riêng và được ghép lại theo SRT; không có hai job nam/nữ chạy song song. Piper cổ điển dùng các model giọng ONNX riêng vẫn nạp theo nhóm/batch nhưng nối tiếp. Khóa một synth áp dụng trong một phiên tool.

V6 sửa lỗi đo cao độ khiến giọng cao bị đo thấp một/nhiều quãng tám (tín hiệu thử 260Hz trước bị đo thành130Hz). Đo/tham chiếu55–500Hz; các đoạn cắt chồng nhau không còn được tính như nhiều mẫu độc lập. Ngăn gộp speaker có bằng chứng nói cùng lúc hoặc có nhiều mẫu cao độ đối nghịch ổn định. Cache giọng đổi phiên bản để không giữ quyết định cũ; lần đầu cần phân tích lại. Không thêm model hoặc tải mới để nhận diện giọng. Cao độ vẫn là dấu hiệu âm học, không bảo đảm giới tính thật hay chính xác100% trên phim.

TTS gom theo thời lượng dự đoán để giảm vùng đệm phải tính qua vector/vocoder, chỉ tách khi giảm được ít nhất20% lượng tính đệm dự kiến. Ghi nhớ batch nhỏ sau OOM; AUTO xử lý lỗi CUDA/kernel hoặc thiếu bộ nhớ ở cả chuẩn bị và render. Tôn trọng CPU affinity/quota và giữ batch theo khả năng CPU/RAM. Giữ8bước và speed1.05.

Chuẩn bị/nghe thử/render dùng chung khóa một synth; grouped và streaming dùng chung vòng đời Supertonic server. Không có nhánh hai Piper. Dọn đúng process khi lỗi/hủy, tái sử dụng model khi đổi giọng trong cùng worker. Log hiện sec/cue, PID/tái sử dụng process và provider thực tế; hiện các cảnh báo fallback/downshift thay vì che chúng.

Log TT_101 hiện có:747/1563câu tổng hợp trong tổng190.8s của các lời gọi synth (~0.255s/câu). Log chưa kết thúc; không phải thời gian toàn job hoặc số liệu3s/câu. Chưa có benchmark V6 với model thật trên máy người nhận để tính phần trăm tăng tốc, không cam kết0.2s/câu trên mọi máy.

Giữ các sửa V3–V5: phát hiện tiến trình đúng hơn; launcher Python cô lập, tránh .pyd3.12 vào Python3.10; nhớ mức âm lượng/nhãn%, từng job và preview vừa panel. Nếu bản cũ đã lưu nhầm100%, đặt lại mức mong muốn và áp dụng cho tất cả job một lần.

Nếu thiếu thư viện GUI, BAT tải gói từ PyPI vào thư mục riêng; cần Internet. Không thay Torch/CUDA/model gốc. EXE cũ chưa được sửa; launcher mở bản Python mới. Có BAT khôi phục trong thư mục sao lưu.

Kiểm tra:242 bài Python+54subtests;35kiểm tra cập nhật/khôi phục;18kiểm tra tìm runtime/cài GUI; payload và launcher thật. Gồm Qt thật, subprocess thật và render CPU FFmpeg tổng hợp, cùng tín hiệu giọng mô phỏng/họa âm, ghép speaker, thiếu bộ nhớ/GPU fallback. Chạy trên Linux/PowerShell7.4.6; chưa chạy BAT/model thật trên Windows RTX/Xeon và chưa đo độ chính xác bằng audio gán nhãn của người nhận.

Các gói V1–V6 giữ lại để tham khảo. Hãy dùng V7.
