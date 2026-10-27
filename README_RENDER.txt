KHO RACK WEB - TRIỂN KHAI LÊN RENDER

A. ĐƯA CODE LÊN GITHUB
1. Giải nén ZIP này.
2. Tạo repository mới trên GitHub, ví dụ KhoRackWeb.
3. Tải LÊN CÁC FILE BÊN TRONG thư mục đã giải nén (app.py, Procfile, requirements.txt, templates/, static/...). Không tải cả thư mục bọc bên ngoài nếu muốn dùng Root Directory để trống.
4. Đảm bảo app.py nằm ngay ở thư mục gốc repository.

B. TẠO WEB SERVICE TRÊN RENDER
1. Đăng nhập https://render.com và chọn New + > Web Service.
2. Kết nối GitHub và chọn repository vừa tạo.
3. Cấu hình:
   - Runtime: Python 3
   - Root Directory: để trống (nếu app.py ở gốc repository)
   - Build Command: pip install -r requirements.txt
   - Start Command: gunicorn app:app --workers 1 --threads 4 --timeout 120
4. Chọn Create Web Service và chờ deploy hoàn tất.
5. Mở URL *.onrender.com được Render cấp để kiểm tra.

C. LƯU Ý QUAN TRỌNG VỀ DỮ LIỆU
- Ứng dụng lưu dữ liệu vào khorack_data.json. Trên Render, ổ đĩa của Web Service thông thường là tạm thời; dữ liệu file có thể mất khi deploy lại/restart.
- Nếu cần giữ dữ liệu kho lâu dài, cần gắn Persistent Disk vào Web Service (tính năng này thường yêu cầu gói trả phí), đặt Mount Path là /var/data và thêm Environment Variable: DATA_DIR=/var/data. Code đã hỗ trợ biến DATA_DIR.
- Nếu chưa gắn Persistent Disk, hãy xuất/sao lưu dữ liệu theo cách phù hợp trước khi deploy lại. File khorack_data.json bị .gitignore để tránh vô tình đưa dữ liệu kho riêng tư lên GitHub.
- Chỉ dùng 1 worker (cấu hình trên) vì ứng dụng hiện lưu một file JSON; không tăng số worker.

D. CHẠY THỬ TRÊN MÁY TÍNH
python -m pip install -r requirements.txt
python app.py
Sau đó mở http://127.0.0.1:5000
