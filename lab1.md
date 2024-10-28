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

- Biểu đồ Package
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

# 5.Hợp nhất kết quả phân tích
- Tổng quan hệ thống
    + Hệ thống Payroll của Acme được thiết kế nhằm đáp ứng yêu cầu về quản lý và xử lý thanh toán lương cho nhân viên, cũng như việc ghi      nhận và quản lý thông tin chấm công. Hệ thống hỗ trợ ba loại nhân viên (nhân viên theo giờ, nhân viên hưởng lương cố định, và nhân        viên có hoa hồng), cho phép họ nhập thông tin chấm công và yêu cầu thanh toán thông qua giao diện máy tính để bàn.
- Mối quan hệ giữa các lớp
    + Employee: Liên kết với TimeCard và PurchaseOrder, đại diện cho thông tin nhân viên.
    + TimeCard: Lưu trữ thông tin chấm công và liên kết với TimecardService.
    + PurchaseOrder: Lưu trữ thông tin giao dịch bán hàng và liên kết với PaymentService.
    + PayrollDatabase: Là cơ sở dữ liệu trung tâm, chứa thông tin toàn diện về nhân viên, bảng chấm công, và đơn mua hàng.
    + PaymentService: Xử lý các yêu cầu thanh toán và tính toán lương, liên kết với PayrollDatabase.
    + TimecardService: Quản lý các hoạt động liên quan đến bảng chấm công, liên kết với PayrollDatabase.
- biểu đồ hợp nhất 2 ca sử dụng
![diagram](https://www.planttext.com/api/plantuml/png/X5HBRi8m4Dtd52DM89KBP561e5AxeKXGTUtOKneHn-dOHeggdgoB7gbNw8HFi4aeNcGnVlFUcu_p-_qpiKwGyxf8AY6tOeCmM8gQJ570ghOEzG0-4-0Z2s4jFEYgC3NYCTYSCJpDKrWvoijD45m8ZJtXgLA4rlRSiAp6qgthAixxIWBzTQvn9aX5-dFXEANv1i57uyc-6jgYuZlZioAydRqBsk32wmpfkjhIatmN5fz98TsMd6hZInUfnNI7ndAMo9Wr80ImOeUduePEfcsbenHs9bS1b93juWuRdY7gwjn-nfu6rAlUz7U5jCjbB2v58Nt1nHmn3UkPQjJf7q15Hl8Oh-5RnvtXIIwfpmBXXqVhNYh5DcA-E_Y_7wLn-LlTbzdZf5tWyVZ-l4qfwqj3odOnyGwaO7scStS0jladih2w5BGe-K4foEezEcRQSySZIKzj3N8kLkR2jNM6NzDLP5l8JMIdoWWUcZpwZXZITYSjy1H4svom7_s9VZysc_1u9bYgvaVq1m00__y30000)

- Chức năng
    + Employee: Lưu trữ thông tin của nhân viên, bao gồm ID, tên, địa chỉ, và phương thức thanh toán.
    + TimeCard: Ghi nhận và lưu trữ thông tin về số giờ làm việc của nhân viên theo từng ngày và mã công việc.
    + PurchaseOrder: Ghi nhận các giao dịch bán hàng của nhân viên hưởng hoa hồng, bao gồm ngày bán và số tiền bán.
    + PayrollDatabase: Lưu trữ thông tin toàn diện và cho phép truy xuất và cập nhật dữ liệu cho các lớp khác.
    + PaymentService: Tính toán và thực hiện thanh toán cho nhân viên dựa trên thông tin từ PayrollDatabase.
    + TimecardService: Quản lý các yêu cầu cập nhật bảng chấm công từ nhân viên và lưu trữ thông tin vào PayrollDatabase.
      
- Lợi ích của việc hợp nhất
    + Tính nhất quán: Hợp nhất các lớp liên quan giúp tạo ra một cấu trúc hệ thống nhất quán và dễ hiểu, giảm thiểu sự trùng lặp và giúp      tăng cường khả năng bảo trì.
    + Dễ dàng mở rộng: Cấu trúc này cho phép việc mở rộng hệ thống dễ dàng hơn, với khả năng tích hợp các chức năng mới trong tương lai 
    mà không làm gián đoạn các chức năng hiện tại.
    + Tăng cường bảo mật: Mỗi lớp có nhiệm vụ rõ ràng, giúp dễ dàng hơn trong việc kiểm soát quyền truy cập và bảo vệ dữ liệu của nhân 
    viên.
    + Quản lý hiệu quả: Hợp nhất các lớp liên quan giúp tối ưu hóa việc quản lý thông tin, từ đó nâng cao hiệu quả hoạt động của hệ thống.
- Kết luận
    + Việc hợp nhất kết quả phân tích cho hai ca sử dụng "Select Payment" và "Maintain Timecard" đã cung cấp cái nhìn toàn diện về hệ         thống quản lý bảng lương của Acme, Inc. Qua quá trình phân tích, chúng ta đã xác định rõ ràng các lớp phân tích, mối quan hệ giữa 
    chúng, cũng như chức năng và nhiệm vụ của từng lớp.
