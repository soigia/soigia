# Render VIP — bản cập nhật V8

Tải `RenderVIP_Fix_V8_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu được gửi riêng trong cuộc trò chuyện, không lưu trên GitHub.

1. Mở bằng WinRAR/7-Zip, nhập mật khẩu, lấy `RenderVIP_Fix_V8.zip` và giải nén ZIP bên trong.
2. Đóng tool và chờ các job/worker dừng; chạy `SUA_RENDER_VIP_ALL.bat` mới.
3. Chọn EXE chính hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py` của tool, trong thư mục app có runtime/voices, ngoài `_BACKUP_RENDER_VIP_...`.
4. BAT kiểm tra phiên bản, sao lưu và cập nhật 12 nguồn Python. Khi thành công, mở `CHAY_RENDER_VIP_DA_SUA.bat` trong thư mục app. EXE cũ vẫn là bản cũ.

V8 thêm ô nhập Gốc/AI 0–200%, nhớ theo job/preset và đồng bộ thanh kéo. 200% là biên độ 2× (+6 dB) trước limiter; âm thanh chạm giới hạn đỉnh sẽ được hạn chế để giảm vỡ tiếng. Preview trực tiếp còn giới hạn 100%.

Tốc độ DONE 0,5–2,0×, mặc định 1,0×, đổi đồng bộ video/âm thanh/phụ đề; giữ cao độ và chỉ đổi nhịp mỗi nguồn audio một lần. Dùng trong SRT Master, Video Master/READY và REUP. Tốc độ phát không đồng nghĩa mức tăng tốc render. TTS vẫn một worker, giữ nguyên bước/chất lượng giọng.

Ghép SRT theo mã video và quốc gia/ngôn ngữ, kể cả tiêu đề bản dịch khác. Đổi quốc gia kiểm tra SRT trước khi đổi metadata/giọng; thiếu/trùng/sai sẽ báo rõ. Tránh tạo job trùng quốc gia. Có thể chọn thủ công SRT ngoài thư mục quét để giải quyết trường hợp chưa tìm thấy; thông tin giọng đã chọn được giữ cùng quốc gia.

Anti dùng một mức chỉnh màu nhẹ cho toàn job/checkpoint/chạy tiếp. REUP giữ lựa chọn bật/tắt; không tạo thông tin điện thoại/ngày quay giả. Sửa bộ lọc crop/blur/flip/logo/SRT/Anti bị áp hai lần khi trim video đã render, và giữ FPS theo lưới hình gốc. Các sửa này bảo đảm xử lý nhất quán; không chứng minh nguyên nhân thiếu view hoặc cam kết tránh kiểm tra nội dung trùng của YouTube.

Bộ điều phối không giảm luồng video chỉ vì câu dài hoặc callback của một batch bị lặp. So throughput tương đương và áp lực CPU đo được; giữ nguồn lực khi video có backlog. Chưa có benchmark V8 trên máy người nhận để cam kết số giây/câu hoặc phút/job.

Giữ các sửa V3–V7: launcher Python cô lập; đường dẫn portable; lưu job/âm lượng/preview; một synth; tái sử dụng Supertonic; batching và GPU/CPU fallback; sửa cao độ và logic speaker. Model/runtime/bản quyền không bị thay. Nếu thiếu GUI, BAT tải thư viện từ PyPI vào thư mục riêng, cần Internet. Có BAT khôi phục trong backup.

So log TT_101: 747 câu đầu cũ190,8s → V7179,5s (giảm11,3s≈5,9%). V7 đủ1563câu, tổng hợp422,1s, cảjob591s. Khác thiết lập hiệnSRT/cache nên chưa phải benchmark kiểm soát. Thời lượng WAV3s không phải thời gian máy tính tổng hợp1câu.

Kiểm tra Qt/subprocess/CPU FFmpeg và bộ cài chạy trong môi trường Linux/PowerShell7.4.6. Chưa chạy BAT/model thật trên Windows RTX5060Ti/Xeon hoặc đo độ chính xác trên audio người nhận gán nhãn. Nên thử một video ngắn trước batch lớn.

Giữ các gói V1–V7 để tham khảo; dùng V8 mới. Không đăng mã Python hoặc mật khẩu ở dạng đọc được trên GitHub.

Kết quả V8:367 bài Python+94 kiểm tra phụ;18 kiểm tra builder;35 cập nhật/khôi phục;20 runtime/GUI;payload BAT và launcher thật đều đạt.
