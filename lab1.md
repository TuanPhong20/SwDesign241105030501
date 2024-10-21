Đề xuất Kiến trúc Layered vì:
- Khả năng mở rộng tốt: Việc phân tầng giúp hệ thống dễ dàng mở rộng khi số lượng nhân viên và khối lượng dữ liệu tăng lên.
- Bảo trì dễ dàng: Mỗi tầng trong kiến trúc xử lý một chức năng cụ thể, giúp dễ dàng bảo trì và cập nhật hệ thống.
- Tính bảo mật cao: Sử dụng các cơ chế bảo mật hiện đại như mã hóa, xác thực và kiểm tra audit logs giúp bảo vệ thông tin nhạy cảm.
- Tích hợp dễ dàng: Khả năng tích hợp với cơ sở dữ liệu DB2 hiện tại mà không cần thay thế giúp tiết kiệm chi phí và thời gian.
  
Presentation Layer (Tầng giao diện):
- Giao diện mà người dùng tương tác với hệ thống.
- Hiển thị dữ liệu và nhận input từ người dùng (như thông tin chấm công, báo cáo).

Business Logic Layer (Tầng nghiệp vụ):
- Xử lý các quy tắc nghiệp vụ của hệ thống (tính toán lương, hoa hồng, xử lý báo cáo).
- Đảm bảo các thao tác theo đúng logic kinh doanh của tổ chức.

Data Access Layer (Tầng truy xuất dữ liệu):
- Quản lý việc kết nối và tương tác với cơ sở dữ liệu.
- Thực hiện các thao tác đọc/ghi dữ liệu cần thiết cho hệ thống.

Integration Layer (Tầng tích hợp):
- Tích hợp hệ thống với các dịch vụ và cơ sở dữ liệu bên ngoài (ví dụ, cơ sở dữ liệu DB2 quản lý dự án).
- Đóng vai trò trung gian, đảm bảo tính tương thích giữa các hệ thống khác nhau.

# Biểu đồ Package
![Use Case diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XTNSNPcda9HVd4g5vThRa5EVcLgge9kQO5kZPr2Q75g4PTpJcPgNWcAK71fGMfHMMPnVX6AC4Axhfs2Xaz-UcQU9efQ966egNfwS245AmK_VqKWmD3YN9IQM9AgeA_WafgJ2cI0BDEqKl1KICnLICzFuU9oICrB0Ve50000__y30000))
  
