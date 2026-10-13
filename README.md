# Render VIP — bản cập nhật V9

Tải `RenderVIP_Fix_V9_PROTECTED.zip`. Gói mã hóa AES-256; mật khẩu được gửi riêng trong cuộc trò chuyện, không lưu trên GitHub.

1. Mở bằng WinRAR/7-Zip, nhập mật khẩu rồi giải nén `RenderVIP_Fix_V9.zip` ở bên trong.
2. Đóng tool và chờ các job/worker dừng; chạy `SUA_RENDER_VIP_ALL.bat` mới.
3. Chọn EXE chính hoặc `Auto_Render_VIP_V21_NATIVE_PORTABLE_TEST.py` của tool trong thư mục app có runtime/voices, ngoài `_BACKUP_RENDER_VIP_...`.
4. BAT kiểm tra phiên bản, sao lưu và cập nhật 15 nguồn Python. Khi thành công, mở `CHAY_RENDER_VIP_DA_SUA.bat` trong thư mục app. EXE cũ vẫn là bản cũ.

V9 tập trung vào vòng đời một worker tổng hợp giọng, xử lý âm thanh có giới hạn bộ nhớ, hiệu chỉnh cấu hình TTS theo máy và đo thời gian từng công đoạn. Giữ nguyên 8 bước tổng hợp, speed giọng 1.05 và chất lượng CQ/CRF18. Không mặc định nhiều luồng CPU hơn sẽ nhanh hơn; không tự thay Torch/CUDA hoặc model.

Cache giọng LRU mặc định tối đa 512 MiB, chừa 4 GiB trống và dự trù đĩa của job đang chạy. Dùng lại WAV đã xác minh khi đổi gain/crop/Speed; thay text/model/style/thuật toán/route thì key đổi. Cache lỗi/thiếu đĩa được bỏ qua; có thể tắt bằng `AUTODUBBING_PIPER_CACHE=0`.

Giữ model Supertonic còn khỏe/rảnh giữa các job; chuẩn bị cửa sổ SRT liên tục; cache preflight Nemotron; resample trong process; bỏ audio xuất khi Gốc=0; decode tiếng gốc một lần lên WORK khi đủ dung lượng; trim trong encode đầu và gộp tempo AI vào mix. FINAL có thể ghép checkpoint trực tiếp khi đủ điều kiện. Hiệu chỉnh mới thử số luồng CPU, chưa tự chọn batch/provider thắng. Report có GPU/NVENC/Video Decode khi driver cung cấp; chưa có benchmark V9 trên máy người dùng.

Log mới có đường dẫn `V9 PERFORMANCE REPORT` đến JSON theo job. Stage chạy chồng/lồng nhau nên không cộng thời gian stage thành thời gian DONE. So lại cùng video/SRT/giọng/thiết lập và Speed=1, rồi batch 2–3 job. Lưu cả log và JSON để xác định điểm nghẽn còn lại.

Log TT_101 thực tế cho thấy V7 hoàn tất trong 9 phút 51 giây, còn V8 mất 25 phút 06 giây. Thời gian tổng hợp 1563 câu lần lượt là 422,1 và 722,7 giây. Cả hai có 21 yêu cầu, 28 batch nội bộ và cùng tổng thời lượng WAV thô 3946,914 giây. V8 ở lần chạy này chậm hơn; log chưa đủ dữ liệu để kết luận nguyên nhân. V9 chưa có benchmark model thật trên Windows chứng minh giảm bao nhiêu phút/job.

Giữ các chức năng V8: ô nhập Gốc/AI 0–200%; Speed DONE 0,5–2,0× đồng bộ video/âm thanh/phụ đề; ghép SRT theo mã video và quốc gia/ngôn ngữ trong tên hoặc thư mục; xử lý màu/trim/FPS nhất quán. 200% là biên độ 2× trước limiter, không phải cam kết độ to cảm nhận gấp đôi. Speed DONE là tốc độ phát thành phẩm, khác với tốc độ render. Ghép SRT chưa nhận diện ngôn ngữ từ nội dung câu.

Giữ các sửa V3–V7: launcher Python cô lập; đường dẫn portable; lưu job/âm lượng/preview; một synth; batching và GPU/CPU fallback; sửa cao độ và logic speaker. Model/runtime/bản quyền không bị thay. Nếu thiếu GUI, BAT tải thư viện từ PyPI vào thư mục riêng, cần Internet. Có BAT khôi phục trong backup.

Kết quả kiểm tra cuối cùng nằm trong `BAO_CAO_KIEM_TRA.json` của gói. Kiểm tra Qt/subprocess/CPU FFmpeg và bộ cài chạy trên Linux/PowerShell 7.4.6. Chưa chạy BAT/model thật trên Windows RTX 5060 Ti/Xeon hoặc đo độ chính xác trên audio người dùng đã gán nhãn.

Nguồn V9 đã qua 537 kiểm tra chính và 94 kiểm tra phụ; đóng gói/payload 23 kiểm tra, bộ cài/khôi phục 35 và tự tìm Python/cô lập GUI 20 kiểm tra đạt. Đã kiểm tra payload BAT và launcher thực. Gói có báo cáo triển khai và đối chiếu đầy đủ log V7/V8.

Giữ các gói V1–V8 để tham khảo. Không đăng mã Python hoặc mật khẩu ở dạng đọc được trên GitHub.
