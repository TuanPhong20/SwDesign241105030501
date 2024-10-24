Đề xuất Kiến trúc Layer vì:
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
![package diagram](https://www.planttext.com/api/plantuml/png/T5AzQiCm4Dxr54Tslq2740TdCAJKf6Gg6GxbC6fjoPpaWYbviWnzfBv25DDWoOv6tNs_X_wklnlha5tVDg93-OKrmQfYigGTEcKqx74WNi6F0FWubYS0SH4JTDjRfSbQs9jQoGXSuS2cQTw9lvMaqtsqQxl634Ilg3sxzHxXza2TuMaIsXJe478fHwUbHv6_HVhZE-INsb7Doq8Lcq-IRifJRFCpTevuv1zBoB8rn4tW1NfBzh5CTfhXedQFdPX91sw-WqVXsDaZqpPXY1afzaoBBt49mQTvapVqJFL_UC_Ta3xVlzaD003__mC0))
  
