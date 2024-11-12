#Phân tích ca sử dụng create employee
1. Mô tả
- Payroll Administrator: Là tác nhân chính, người sẽ thực hiện các thao tác thêm thông tin nhân viên vào hệ thống.
- Payroll System: Là hệ thống chịu trách nhiệm lưu trữ thông tin nhân viên mới và đảm bảo rằng dữ liệu được lưu trữ chính xác và có thể được truy xuất sau này.

2. Biểu đồ tuần tự
  ![diagram](https://www.planttext.com/api/plantuml/png/R94zRiCm38LtdOB8dWjuA18a7Jerg4z0IpIWLdyLwG0-MuSUALUefFp0XRD9vFSU7y7Bp--E1RDCtYd5NpP0ZanAATGICvnmpj6vlV4sM9QCjOWCM0ig5Q7LDc4GsDnGw6SMyfjASNl-nrvzSd4cEgBWW4mDDCDpg3N9fnAd3eJjoyspWqCc588x2H_qFH6BklOhsIGTd7BqIM0imH_mMoXVZs9ZM3iNmTcQXVMH1AtZXNM9j4xmFdoINWOmGmSzdkdvN3F0ThbF3AFDlWdMIzox3wVhS0Fzf3KnZvDpSxdQZe8ff_m3003__mC0)

3. Hành vi của từng lớp
EmployeeController: Lớp này nhận yêu cầu từ Employee để tạo báo cáo cá nhân. Lớp này kiểm tra quyền hạn của người dùng (Employee) và điều hướng yêu cầu đến EmployeeReportService.
EmployeeReportService: Lớp trung tâm chịu trách nhiệm thu thập và xử lý dữ liệu báo cáo của nhân viên. Lớp này sử dụng các lớp Repository (EmployeeRepository, PayrollRepository, TimecardRepository) để lấy dữ liệu cần thiết và tạo tệp báo cáo thông qua PDFGenerator.
EmployeeRepository: Lớp này tương tác với cơ sở dữ liệu để lấy dữ liệu cá nhân của nhân viên.
PayrollRepository: Lấy thông tin về bảng lương của nhân viên từ cơ sở dữ liệu.
TimecardRepository: Lấy dữ liệu về giờ làm việc để đưa vào báo cáo nếu cần.
PDFGenerator: Tạo tệp PDF từ dữ liệu đã tổng hợp và trả lại tệp cho EmployeeReportService.

4. Quan hệ giữa các lớp
EmployeeController quản lý yêu cầu từ Employee, ủy quyền đến EmployeeReportService.
EmployeeReportService xử lý dữ liệu và tạo báo cáo. Nó lấy dữ liệu từ các lớp Repository (EmployeeRepository, PayrollRepository, TimecardRepository) và chuyển đến PDFGenerator để tạo tệp.
PDFGenerator chịu trách nhiệm tạo tệp báo cáo và gửi lại tệp PDF đã tạo.

5. Biểu đồ lớp phân tích
![diagram](https://www.planttext.com/api/plantuml/png/d9912i8m44NtEKMM2de15w9OTIlg1OPsa43Ib4aKYdWo5nx9AvZKrgHDLtOJcF_daVpVz_ErCXR8NfLakGHZ-05gqbAk2oLAOIo1rSJlxC5QlH4skhJUXLxY_hjWYSwBHwmqsGarnxckSCOh851ckk27R1SuN-C9wIPo_9koLPNKDJOBHhYhrW5bEp432vFVVZmDeFRPevnMwsEYOQ2SXS8Sg1Z5T6AV4q-ZwsIx_JSBdKJij3OPlnCI6MrklXmsneODEakl3DQlnibfogad2J2rfEcCOAA7inMMXVypFm000F__0m00)

# Phân tích ca sử dụng Create Administrative Report
1. Mô tả
Ca sử dụng Create Administrative Report cho phép người dùng với quyền quản trị (Payroll Administrator) tạo các báo cáo hành chính. Các báo cáo này bao gồm thông tin về nhân viên, tiền lương, giờ làm việc, và các dữ liệu hành chính khác phục vụ cho mục đích theo dõi và quản lý.

2. Biểu đồ tuần tự 
![diagram](https://www.planttext.com/api/plantuml/png/R999RiGW44NtdABKguwKle0NKLiUihMmBu3iKeI2mGrq8fyjYnmfLmYJus3rYg7U_yKlyVFrVJMMQNkV1J7lN89M1e4GDbgbeMEhLaAKqymbDrOpTqaMX_EHBqnQE8LIfQJr7EeJC0DbbJCK5wLjZ_g3ZnW8skT4Coz2hOYUDDmrMGFMq1nBppbGtO4Q-8mZqzC16uvcTVkA4aEcw5EtX3nA39SNbwc0IYEp236EMsvtD9QKbQ_Jle2tQ8SHEEkm3Ek2p-0wizay4TfxkA4UjblgcbbsteY6mYNvRNNmG99sKPgUcIcxNPdA_uL356x3oPJ3hjpgMS-wtSEvGqhc2TUrRlUsRjzoWK6NXlPtv-VapHuCk81QVKgXsBJZLvIJ_vI_0000__y30000)

3. Hành vi của từng lớp
AdminController: Lớp này nhận yêu cầu từ Payroll Administrator để tạo báo cáo. Nó kiểm tra quyền hạn của người dùng và điều hướng yêu cầu đến ReportService.
ReportService: Đây là lớp trung tâm cho việc tổng hợp và xử lý dữ liệu báo cáo. Dựa vào loại báo cáo được yêu cầu và các tham số, lớp này yêu cầu các lớp Repository để lấy dữ liệu cần thiết và sử dụng PDFGenerator để tạo tệp báo cáo.
EmployeeRepository: Lớp này tương tác với cơ sở dữ liệu để lấy dữ liệu nhân viên cho báo cáo.
PayrollRepository: Lớp này lấy dữ liệu bảng lương từ cơ sở dữ liệu dựa trên yêu cầu từ ReportService.
TimecardRepository: Lấy dữ liệu chấm công để đưa vào báo cáo nếu cần.
PDFGenerator: Tạo tệp PDF từ dữ liệu đã tổng hợp, sau đó trả lại tệp cho ReportService.

4. Quan hệ giữa các lớp
AdminController là lớp điều khiển, quản lý và ủy quyền các yêu cầu tạo báo cáo.
ReportService phụ trách chính trong việc tổng hợp dữ liệu từ các lớp EmployeeRepository, PayrollRepository, và TimecardRepository.
PDFGenerator nhận dữ liệu từ ReportService để tạo báo cáo và trả lại tệp PDF đã tạo.

5. Biểu đồ lớp phân tích
![diagram](https://www.planttext.com/api/plantuml/png/d9912i8m44NtEKMM2de15w9OTIlg1OPsa43Ib4aKYdWo5nx9AvZKrgHDLtOJcF_daVpVz_ErCXR8NfLakGHZ-05gqbAk2oLAOIo1rSJlxC5QlH4skhJUXLxY_hjWYSwBHwmqsGarnxckSCOh851ckk27R1SuN-C9wIPo_9koLPNKDJOBHhYhrW5bEp432vFVVZmDeFRPevnMwsEYOQ2SXS8Sg1Z5T6AV4q-ZwsIx_JSBdKJij3OPlnCI6MrklXmsneODEakl3DQlnibfogad2J2rfEcCOAA7inMMXVypFm000F__0m00) 
