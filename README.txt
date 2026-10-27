KhoRack - Quản lý vị trí kho

CÀI ĐẶT
1. Cài Python 3.10 trở lên.
2. Mở Terminal/CMD tại thư mục này.
3. Chạy: python -m pip install -r requirements.txt
4. Chạy: python app.py
5. Mở trình duyệt: http://127.0.0.1:5000

TÍNH NĂNG
- Bốn khu mặc định KHU 1, KHU 2, KHU 3, KHU 4; mỗi tab có dữ liệu riêng. Mã nội bộ cũ vẫn được hỗ trợ khi nhập Excel.
- Đổi tên rack bằng chuột phải vào tiêu đề rack.
- Thêm tab, đổi tên tab bằng nhấp đúp.
- Nhập/sửa box bằng nhấp đúp hoặc menu chuột phải.
- Di chuyển box bằng cách giữ chuột phải và kéo đến ô khác.
- Tìm kiếm và gợi ý box trên TẤT CẢ các tab; chọn kết quả sẽ tự mở đúng tab và làm nổi bật vị trí.
- Tải file Excel mẫu bằng nút “File Excel mẫu”, nhập dữ liệu bằng “Nhập Excel”.
- Các ô trống hiển thị trống, không còn số 1-20 làm chữ hiển thị mặc định.

EXCEL
Cột bắt buộc: Tab, Rack, Tier, Position, BoxCode.
- Mỗi dòng tương ứng một vị trí box.
- Rack: KHU 1, KHU 2, KHU 3, KHU 4 hoặc tên rack đã đổi; cũng chấp nhận ML, IV#1, IV#2, IV#3.
- Tier: T1/T2/T3 tùy rack.
- Position: số ô từ 1 đến 24.
- BoxCode: mã box; để trống sẽ xóa dữ liệu tại vị trí đó.
- Có thể nhập thêm tab mới bằng cách ghi tên tab chưa tồn tại.
- File mẫu có 2 dòng ví dụ, hãy xóa hoặc thay bằng dữ liệu thật trước khi nhập.
- Nhập Excel sẽ cập nhật/ghi đè các vị trí được liệt kê; những vị trí không có trong file được giữ nguyên.

DỮ LIỆU
Dữ liệu tự lưu tại khorack_data.json trong thư mục ứng dụng. Sao lưu file này định kỳ.


TÍNH NĂNG KHÔI PHỤC
- Nút “↶ Khôi phục” hoàn tác thao tác xóa tab hoặc xóa tên box gần nhất.
- Lịch sử hoàn tác giữ tối đa 30 thao tác trong phiên trình duyệt hiện tại. Tải lại trang sẽ xóa lịch sử hoàn tác; dữ liệu đã lưu vẫn giữ nguyên.
