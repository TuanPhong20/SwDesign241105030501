# 1.Đề xuất Kiến trúc MVC  vì:
- Tách biệt giữa các thành phần: Giúp dễ dàng thay đổi giao diện hoặc quy trình nghiệp vụ mà không ảnh hưởng đến các phần còn lại của hệ thống.
- Dễ mở rộng và bảo trì: Các thay đổi trong nghiệp vụ tính lương hay yêu cầu mới của nhân viên có thể được triển khai dễ dàng nhờ vào sự tách biệt giữa Model, View, và Controller.
- Bảo mật và kiểm soát: Phân quyền truy cập cho phép nhân viên chỉ xem và chỉnh sửa dữ liệu của mình, đồng thời quản trị viên có quyền quản lý cao hơn trong hệ thống.

Model (Mô hình):
- Lớp Model chứa các thành phần quản lý dữ liệu và logic xử lý nghiệp vụ liên quan đến bảng lương.
- Các đối tượng trong Model sẽ bao gồm: Employee (Nhân viên), Timecard (Bảng chấm công), PurchaseOrder (Đơn hàng), và Payment (Thanh toán).
- Model cũng quản lý kết nối tới cơ sở dữ liệu Quản lý Dự án hiện có (DB2) để lấy dữ liệu về dự án và số hiệu công việc mà không cần cập nhật hoặc thay đổi nội dung.

View (Giao diện):
- View sẽ chịu trách nhiệm hiển thị thông tin và giao tiếp với người dùng.
- Giao diện Windows-based giúp nhân viên nhập thông tin chấm công, đơn hàng, và xem báo cáo chi tiết về số giờ làm, số lương đã nhận, thời gian nghỉ phép còn lại.
- Đối với quản trị viên bảng lương, View sẽ cung cấp giao diện để quản lý thông tin nhân viên và chạy các báo cáo quản trị.

Controller (Điều khiển):
- Controller sẽ xử lý các yêu cầu từ người dùng, điều phối giữa View và Model.
- Khi nhân viên nhập thông tin chấm công hoặc yêu cầu xem báo cáo, Controller sẽ nhận các yêu cầu này, xác minh thông tin và tương tác với Model để lưu hoặc truy xuất dữ liệu tương ứng.
- Đối với các thao tác đặc biệt như tính toán bảng lương tự động, Controller sẽ điều khiển quá trình này dựa trên cấu trúc nghiệp vụ trong Model và trả kết quả qua View.

Biểu đồ Package
![package diagram](https://www.planttext.com/api/plantuml/png/X5FBReCm4Bpp5HRt_40FLSZZa0Dg53MvR-rjwjROr3QjeYfVraC_gR_GDGP2WIWSGEpEUcQ7uVVxP-uyM5yLAYc1ly4HMPeVbYop_4LwvBwocBAl965qjOZS25HKPCt55JZ7raMfp0bnK7wK1NAmOb3ULiG03X-iG3limQb0xRjgfsm57fveY6MSetDfJyDbUhLO6gr9kZHwehsrvfMQEMWwCj2i5XtgdCJxlsqF4ZzxH9sOTb-sqHxjCt2SrjCQiDRUdlQR2SGEIsDzu97ws4ESnwHaZJLAiKmKKjzYRXLUTfsaRywCAaRq0pV8Mn_GQ4S1Q1UzGCRVDTIlzbkzLm5Hug3T28oXdCtk-nBlo35hFgH0oWM59wsXFK30nqc2xl2zGkSZb95higmKX1p5kJe9OuQzesTMvyrD4jHp0LWAyAGalAS9wPwZ5k7N-mC00F__0m00)
  
