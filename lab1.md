# 1.Phân tích iến trúc
Đề xuất MVC vì:
- Lợi ích
    + Tách biệt giữa các thành phần: Giúp dễ dàng thay đổi giao diện hoặc quy trình nghiệp vụ mà không ảnh hưởng đến các phần còn lại của     hệ thống.
    + Dễ mở rộng và bảo trì: Các thay đổi trong nghiệp vụ tính lương hay yêu cầu mới của nhân viên có thể được triển khai dễ dàng nhờ vào     sự tách biệt giữa Model, View, và Controller.
    + Bảo mật và kiểm soát: Phân quyền truy cập cho phép nhân viên chỉ xem và chỉnh sửa dữ liệu của mình, đồng thời quản trị viên có          quyền quản lý cao hơn trong hệ thống.

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
![diagram](https://www.planttext.com/api/plantuml/png/X5FBReCm4Bpp5HRt_40FLSZZa0Dg53MvR-rjwjROr3QjeYfVraC_gR_GDGP2WIWSGEpEUcQ7uVVxP-uyM5yLAYc1ly4HMPeVbYop_4LwvBwocBAl965qjOZS25HKPCt55JZ7raMfp0bnK7wK1NAmOb3ULiG03X-iG3limQb0xRjgfsm57fveY6MSetDfJyDbUhLO6gr9kZHwehsrvfMQEMWwCj2i5XtgdCJxlsqF4ZzxH9sOTb-sqHxjCt2SrjCQiDRUdlQR2SGEIsDzu97ws4ESnwHaZJLAiKmKKjzYRXLUTfsaRywCAaRq0pV8Mn_GQ4S1Q1UzGCRVDTIlzbkzLm5Hug3T28oXdCtk-nBlo35hFgH0oWM59wsXFK30nqc2xl2zGkSZb95higmKX1p5kJe9OuQzesTMvyrD4jHp0LWAyAGalAS9wPwZ5k7N-mC00F__0m00)
  
# 2.Cơ chế phân tích
- Cơ chế xử lý lương tự động
      + Lý do: Hệ thống cần tự động thực hiện thanh toán vào mỗi thứ Sáu cho nhân viên theo giờ và cuối tháng cho nhân viên lương cố định        mà không cần can thiệp thủ công.
      + Phù hợp cho: Đảm bảo tính chính xác và hiệu suất trong việc xử lý lương.
- Cơ chế tính toán lương và hoa hồng
      + Lý do: Cần thiết để tính lương cho nhân viên theo giờ (tính cả thời gian làm thêm) và lương cùng hoa hồng cho nhân viên bán hàng        dựa trên doanh số.
      + Phù hợp cho: Tính toán chính xác số tiền lương và hoa hồng cho từng loại nhân viên.
- Cơ chế truy cập và liên kết dữ liệu với hệ thống cũ
      + Lý do: Hệ thống mới cần tương tác với cơ sở dữ liệu Quản lý Dự án (DB2) để lấy mã số công việc mà không thay đổi dữ liệu trong cơ       sở dữ liệu cũ.
      + Phù hợp cho: Duy trì sự nhất quán với dữ liệu dự án của công ty và tiết kiệm chi phí.
-  Cơ chế xử lý báo cáo và truy vấn nhân viên
      + Lý do: Hệ thống cần cung cấp khả năng báo cáo để nhân viên có thể xem số giờ làm, tổng lương đã nhận, số ngày nghỉ phép còn lại,        và các truy vấn liên quan khác.
      + Phù hợp cho: Đáp ứng nhu cầu theo dõi thông tin và minh bạch trong thông tin làm việc của nhân viên.
 
# 3.Phân tích ca sử dụng Payment
![diagram](https://www.planttext.com/api/plantuml/png/R90n3i8m34LtJf6n35mW0nAY30n8I9p0fAwmv2QGE9LwDWQEn1LeAAaATBJ_VzzVVjuVk-RAhaDKgxKwGkSTymbzImQrydYB6AHVDsYbM2w-3HEa184pX3SZdh35d9kK8W_xSip8nDpTAJj_C_NPCeH0DHaGSbOh0smYWs2l3rt_NHFyW79nbLOLChNe4_HHDesBLiQ4mPZ8t4ihwuJgBZ_cXti1003__mC0)

- Employee: Chịu trách nhiệm lưu trữ và cung cấp thông tin cá nhân của nhân viên, đặc biệt các thông tin cần thiết cho việc tính lương.
- TimeCard: Đảm bảo dữ liệu chấm công được ghi nhận và lưu trữ, phục vụ cho việc tính lương theo giờ hoặc theo dự án.
- PaymentClassification: Tính toán tiền lương dựa trên phân loại của nhân viên. Lớp này có nhiệm vụ tính toán lương theo giờ làm việc (nếu là lương theo giờ), lương cố định, hoặc lương cố định cộng hoa hồng (nếu là lương hoa hồng).
- PaymentMethod: Xác định phương thức thanh toán của nhân viên và gửi tiền đến nơi nhận lương.
- PayrollDatabase: Cung cấp dữ liệu cho lớp PayrollService và cập nhật các thay đổi về thông tin nhân viên hoặc chấm công nếu có.
- PayrollService: Điều phối các hoạt động để xử lý lương. Chịu trách nhiệm điều khiển và kết nối các lớp khác trong ca sử dụng này.

# 4.Phân tích ca sử dụng Maintain Timecard
![diagram](https://www.planttext.com/api/plantuml/png/Z91D3e8m48NtdA9BIF02BDm0YMxK18th0eCsKehJbgHdS-6Hl8Ajf8aXNR2Sd-_DU_DvlKi-zi80aCsMd1c7Xc9R0KwiWOmWF3L8THbRgi1Fuy8MATa9ZV8gy05jIl8xnHiSDAy1asYXuwHFrA3eUulIcigVj4864_ZxRXBxObyaqO88-lk7GrTTAxUjZ3G8rlKHvoZbeD2io-7mO0199_0BizuwpuqOEeQyidWSV9KFbP51ADQPsNAbgDBI4by0003__mC0)

- Employee: Lớp này chịu trách nhiệm cung cấp thông tin của nhân viên và xác thực quyền truy cập khi yêu cầu cập nhật bảng chấm công.
- TimeCard: Đại diện cho từng bản ghi chấm công của nhân viên. Mỗi bản ghi chứa thông tin về số giờ làm, ngày làm việc, và mã công việc.
- PayrollDatabase: Chịu trách nhiệm lưu trữ thông tin của nhân viên và các bảng chấm công, đảm bảo rằng tất cả bản ghi chấm công được cập nhật và lưu trữ đúng cách.
- TimecardService: Chịu trách nhiệm quản lý yêu cầu cập nhật bảng chấm công của nhân viên, xử lý việc tạo mới hoặc cập nhật các bản ghi chấm công, và xác nhận trạng thái cập nhật tới nhân viên.
