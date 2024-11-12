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
![diagram](https://www.planttext.com/api/plantuml/png/b5HBJiCm4Dtx5BEZNVG2MLIL219T01Mjn7gQJ1kBn8vi9wX2d8m5H-8AE77iveSGMKIPxtkUUSxtvzT66rIcAdB6RY2c4nS49YCea0j8SjIQDDZFndUh20t1NL7cya84prHAPQ3I10bgOgpD3t4NtfEgUKBmpg1vpYH8sIx3f0LrvZQDO6yK5-TbD6h4FkO1kiuhrLhN1ixh6pzYGSE8aGRpUraf_IBLAzcwM5R7d7hHFUQa1_x0ts77Q72n37qd33stwV6SNqnObNWfI9W7CfaS9bje4vD1dkiUf8_iNDrMdEGSeGClA46LUaAciyU4KdiqUs3xTdRsotmQo7Ps3LZd3s2xIYMP5SIJIabvHDaOVy5X8IjX9aY7i8mvkEigZXRK2qrZxSNbb37Ma-rKIvwwR4MM5TN_b6EuCOfoD5mAdV5Ii_aBi5gjnygDWfmqh4TbWtoRwHbgI9q8vYl2eliLxHRXhLtZVDbmPVrQtOmTxA9mld8q_QWTl0OKQQ_9ch4DYRJvpVm0003__mC0)

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

# Phân tích ca sử dụng Maintain Employee Information
1. Mô Tả
Ca sử dụng "Maintain Employee Information" cho phép người quản lý hoặc nhân viên có quyền truy cập cập nhật thông tin của nhân viên trong hệ thống Payroll System. Thông tin này bao gồm tên, địa chỉ, phương thức thanh toán, và phân loại công việc (theo giờ, lương tháng, hoặc có hoa hồng). Quá trình này sẽ đảm bảo rằng mọi thông tin được cập nhật kịp thời và chính xác trong cơ sở dữ liệu để hỗ trợ các chức năng tính lương và báo cáo.

2. Biểu Đồ Tuần Tự
![diagram](https://www.planttext.com/api/plantuml/png/b9AnJiGm38PtFuNL_LwW0pe430mid8xTj2v4f4aLEqLzDWOUYLSWhQxNbj8JPCWGsv___FRNn-TUb8B6seAy6OV12mDGeJxWKJWW2MPtTMDznupNPMrS1asgC8Lfo2cEiGTozC8rEprmQ4t1YwmdigOaDTxz5XqPZznuCQbr1ubZj3j7bZ9kIIa36FJjhhObv7XiKbUUCFUkyh2PtyDMIlFnYP57ZEangqpSNHOp5M1WYLQJqVRapQ0ir4CKC9sB8jU6vNYWzgV2EMTAdGFE3f5gCCzHMHPLYo_DkzruLvcJNlGLnW6psV5FKv9O52nIHGjifHzM-tzh-gL8PhpwTsmdlpa47z9IbG3xTFVh_Wq00F__0m00)

3. Hành Vi của Từng Lớp
EmployeeManagementService: Xử lý yêu cầu cập nhật thông tin nhân viên và điều phối các thao tác cần thiết. Nhận yêu cầu từ giao diện người dùng, gọi các chức năng trong EmployeeRepository và ValidationService để kiểm tra và cập nhật thông tin trong cơ sở dữ liệu.
EmployeeRepository: Quản lý truy xuất và cập nhật dữ liệu của nhân viên. Chức năng chính là lưu và cập nhật thông tin của nhân viên vào cơ sở dữ liệu.
ValidationService: Thực hiện kiểm tra tính hợp lệ của dữ liệu, như định dạng địa chỉ email hoặc độ dài của tên. Đảm bảo rằng thông tin đưa vào là hợp lệ trước khi lưu vào cơ sở dữ liệu.
Employee: Đại diện cho đối tượng nhân viên với các thuộc tính như employeeId, name, address, paymentMethod. Đối tượng này cũng chứa các phương thức để lấy và cập nhật thông tin cá nhân.

4. Quan Hệ Giữa Các Lớp
EmployeeManagementService tương tác với EmployeeRepository để cập nhật thông tin nhân viên trong cơ sở dữ liệu.
EmployeeManagementService sử dụng ValidationService để xác thực thông tin trước khi lưu.
EmployeeRepository truy xuất và lưu thông tin nhân viên vào cơ sở dữ liệu.

5.  Biểu Đồ Lớp Phân Tích
![diagram](https://www.planttext.com/api/plantuml/png/f98zRiCm38LtdOB8L0F91JmKMJfao58ZtTc8TONQeY4g1eoY9-lG8_KAbVmNst7HePha9_BZ8-dlpw-zU7J-KXPAtem5nq9AgNE18l1GLWKtH4Uqc5D9rcVaQdCcU5SGpwNIw6a8EzWNlgF-8nspanIUcGj2gpwMv4UgM8ndrmn8mPhM8JKRtSNav0Tz33te53BlZCsJQzQru1CM9dWrR1SjrDt3VvheKRjRAvrkiQIvWbex4fcB5JPnn4Vohpmdn8PRNybSxiRVlanhR671ty8gUvXfQEZtJUzszslRIc6JXKq1Et0KQ1Jk9XZP_86wtKCWzUAIC2atTH4pJctd0cZrM5_wz7ZsP7Nyfty0003__mC0)

# Phân Tích Ca Sử Dụng: Run Payroll
1. Mô Tả
Ca sử dụng "Run Payroll" chịu trách nhiệm tính toán lương cho nhân viên dựa trên thông tin thời gian làm việc, mức lương, và các khoản khấu trừ. Hệ thống cần thu thập dữ liệu về thời gian làm việc của từng nhân viên, các loại phụ cấp, khấu trừ và thực hiện các bước tính toán để xác định tổng số tiền lương cho mỗi kỳ thanh toán. Cuối cùng, hệ thống sẽ lưu trữ và tạo báo cáo về thông tin lương.

2. Biểu Đồ Tuần Tự
![diagram](https://www.planttext.com/api/plantuml/png/T991RiCW44NtSugvG2xWHPKehRADabnW1BD0nM0DE9BFraMFr2lKniMHxUaEyT_t6mm_Nz_7b4bottf8dowWnCG0G2P7mPDjNO1kp9rn7OMCLneaUdzdUJh3g-YZxNmSc6_SnUJ6-h2A7wvbGsB_YU_aIOOpUTDx6bFDEbKbNpYm50JAV7XusupLuAqFTG_MsKJl9stmmgyJu3jdSZx17iI3OdlrA1CemltPPs7TdujxIhMjIufj-oiRh6l-os2BgAAbPMjDaUbNCnslBBa2E1EWywf_PfOlMKrVNa2pICvnl0ekBC2HWvtUzIy0003__mC0)

3. Hành Vi của Từng Lớp
PayrollService: Lớp chính điều phối việc tính lương. Nhận lệnh từ người dùng để chạy quá trình tính lương, lấy thông tin về nhân viên từ EmployeeRepository, thông tin về thời gian làm việc từ TimecardRepository, và thông tin về lương cơ bản từ SalaryCalculator.
EmployeeRepository: Quản lý truy xuất thông tin nhân viên, bao gồm loại công việc, phương thức thanh toán và các thuộc tính cơ bản như lương theo giờ hay lương tháng.
TimecardRepository: Lưu và truy xuất thông tin chấm công của nhân viên. Đảm bảo rằng hệ thống có đủ dữ liệu về số giờ làm việc để tính toán chính xác.
SalaryCalculator: Thực hiện các tính toán liên quan đến lương, bao gồm lương cơ bản, khấu trừ và các phụ cấp. Sau đó, trả về kết quả cuối cùng cho PayrollService.
PayrollReportGenerator: Tạo và lưu trữ báo cáo lương cho mỗi nhân viên sau khi tính toán hoàn tất.

4. Quan Hệ Giữa Các Lớp
PayrollService là lớp trung tâm, điều phối quá trình tính lương bằng cách tương tác với EmployeeRepository, TimecardRepository, và SalaryCalculator.
EmployeeRepository và TimecardRepository cung cấp thông tin cần thiết cho việc tính toán lương.
SalaryCalculator xử lý các phép tính phức tạp liên quan đến lương dựa trên dữ liệu từ các lớp khác.
PayrollReportGenerator tạo báo cáo dựa trên kết quả từ SalaryCalculator.

5.  Biểu Đồ Lớp Phân Tích
![diagram](https://www.planttext.com/api/plantuml/png/X5JDIWCn4BxdAK9F5UmBz205AyM38gtYEMw66ffDoYHRMCGdy-0Z-GeccwIRRYBkOM5dvljBXltv-buPoz1shIJc81H5RO2GHZ9Zw1FhKKkv0po91kW7eVx1JiN6_6f9JrfmyfaGT-rHwXvW2qTjXDNO9zGUR6gkmJ8XpHpYzprVqfr5eVQEBmsDdC-YXOOXhtAcvffPLYTC4oFXZac6_IsJJIUPuqjqJQn063ZJZQQkgOri8w-JuBfxavdZU3pUCDeDAC1SPXyA4DfL5JCOICHE8SoMvnmv5sNoK5UiXSlAaVKjAFi0zbrFXeFgrbah8wMq_mc-wmxDgyO3y98af9XIF1OUB-E76WxOzM3ElpthP3yNYvlQ0YxfR0EM9ZdAm_hDQl3AhaLukdZAtQPLiSLQEMJwWdYbLU0Vwp88XrMX8VsC51fvPezuCM2og8FNAkXyeGbK3pWrvQ7n6ZD_vcomSlwvHL8vuDmD8MG5Ylk_qIy0003__mC0)

# Phân Tích Ca Sử Dụng: Select Payment Method
1. Mô Tả
Ca sử dụng "Select Payment Method" cho phép người dùng chọn phương thức thanh toán để sử dụng trong quá trình thanh toán lương cho nhân viên. Hệ thống cung cấp các tùy chọn thanh toán khác nhau như chuyển khoản ngân hàng, tiền mặt, hoặc thẻ tín dụng, và lưu lại lựa chọn của người dùng cho từng nhân viên.

2. Biểu Đồ Tuần Tự
![diagram](https://www.planttext.com/api/plantuml/png/X9512i9034NtEKKku0Mw4AM86mLHFC3OfXYSJifCBFHiBZoILx05QUkqucv8yj__oRmUprLGu_LUMWWtTkWb4C1GD9cAntCW3rLRuemhunGFfYd9wObypHdDjOvKIU1Mt7nrDsLbfI4QjQ6Zus8PGHCyaQMi1-AUz2evV4-DT0ComIqfhcl3rbmiHOG04m4kPknt71IbcAX_vaslqbxlVzxf3TfTJKsVXIcF4LF1RE1KNC6-DChYOCQtovr4xDuJLkJoxiUXVxq1003__mC0)

3. Hành Vi của Từng Lớp
PaymentService: Đây là lớp chính điều phối việc chọn phương thức thanh toán. Lớp này nhận lệnh từ người dùng để lấy các phương thức thanh toán khả dụng và lưu lại lựa chọn của họ.
PaymentRepository: Chịu trách nhiệm quản lý các phương thức thanh toán trong cơ sở dữ liệu, bao gồm việc truy xuất danh sách các phương thức thanh toán có sẵn.
EmployeeRepository: Lớp này lưu trữ và cập nhật thông tin phương thức thanh toán đã chọn cho nhân viên.
PaymentMethod: Đại diện cho từng phương thức thanh toán (chuyển khoản, tiền mặt, thẻ tín dụng) với các thuộc tính như loại phương thức và chi tiết liên quan.

4. Quan Hệ Giữa Các Lớp
PaymentService là lớp trung tâm, điều phối việc chọn phương thức thanh toán bằng cách tương tác với PaymentRepository để lấy danh sách phương thức thanh toán khả dụng và với EmployeeRepository để lưu lại phương thức được chọn.
PaymentRepository chịu trách nhiệm cung cấp danh sách các phương thức thanh toán, để PaymentService có thể hiển thị cho người dùng.
EmployeeRepository nhận nhiệm vụ lưu trữ và cập nhật thông tin phương thức thanh toán của nhân viên khi họ hoàn tất việc chọn.

5. Biểu Đồ Lớp Phân Tích
![](https://www.planttext.com/api/plantuml/png/Z5DTIiGm47xFAOO-hM0lK6HP4Hy45TcU83OVky4sAPrOAEB9VF18Ni5qc-wsJGNp-4s-dvb9Vhw-T-nauzwhKl2RDjHOXX2YA2KplSYkWd4vcbONe0z1_M6KA5oeFS4ThTgWgalR0GygezmrsXokgJgLBiXLHgtLIdmkvFUeBMjdcsvqEC3TjbANyhN4OC0RptxKx6vcljkBs7r84AknRF7Vj1dDRluLUQW6WtJPw1HzbXNck8BphV4PZ3eOPUEK0suYoM4ZKBDqYrPwdyK-qtIxieECaZsyE5fGFLJ3S3XPKrWPl9V8_T1fp1NuYLYvEvKu4JqAZgbnq4dyi0zFlxF6ZzTm7FriiiuxMl_ocUI2c8Z-x61K_qL-0G00__y30000)

# Code java mô phỏng ca sử dụng Maintain Timecard
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

// Lớp Timecard đại diện cho bản ghi chấm công của nhân viên
class Timecard {
    private Date date;
    private int hoursWorked;
    
    public Timecard(Date date, int hoursWorked) {
        this.date = date;
        this.hoursWorked = hoursWorked;
    }
    
    public Date getDate() {
        return date;
    }

    public int getHoursWorked() {
        return hoursWorked;
    }

    public void setHoursWorked(int hoursWorked) {
        this.hoursWorked = hoursWorked;
    }
    
    @Override
    public String toString() {
        return "Date: " + date + ", Hours Worked: " + hoursWorked;
    }
}

// Lớp Employee đại diện cho nhân viên có danh sách các bản ghi chấm công
class Employee {
    private String employeeId;
    private List<Timecard> timecards;

    public Employee(String employeeId) {
        this.employeeId = employeeId;
        this.timecards = new ArrayList<>();
    }
    
    public String getEmployeeId() {
        return employeeId;
    }
    
    public List<Timecard> getTimecards() {
        return timecards;
    }
    
    public void addTimecard(Timecard timecard) {
        timecards.add(timecard);
    }
    
    public void updateTimecard(Date date, int hoursWorked) {
        for (Timecard timecard : timecards) {
            if (timecard.getDate().equals(date)) {
                timecard.setHoursWorked(hoursWorked);
                return;
            }
        }
        System.out.println("Timecard not found for date: " + date);
    }
    
    public void displayTimecards() {
        System.out.println("Timecards for Employee ID: " + employeeId);
        for (Timecard timecard : timecards) {
            System.out.println(timecard);
        }
    }
}

// Lớp TimecardSystem quản lý việc chấm công của nhân viên
public class TimecardSystem {
    private List<Employee> employees;
    
    public TimecardSystem() {
        employees = new ArrayList<>();
    }
    
    public Employee findEmployee(String employeeId) {
        for (Employee employee : employees) {
            if (employee.getEmployeeId().equals(employeeId)) {
                return employee;
            }
        }
        return null;
    }
    
    public void addEmployee(String employeeId) {
        Employee employee = new Employee(employeeId);
        employees.add(employee);
    }

    public void addTimecard(String employeeId, Date date, int hoursWorked) {
        Employee employee = findEmployee(employeeId);
        if (employee != null) {
            employee.addTimecard(new Timecard(date, hoursWorked));
            System.out.println("Timecard added successfully.");
        } else {
            System.out.println("Employee not found.");
        }
    }
    
    public void updateTimecard(String employeeId, Date date, int hoursWorked) {
        Employee employee = findEmployee(employeeId);
        if (employee != null) {
            employee.updateTimecard(date, hoursWorked);
            System.out.println("Timecard updated successfully.");
        } else {
            System.out.println("Employee not found.");
        }
    }
    
    public void displayEmployeeTimecards(String employeeId) {
        Employee employee = findEmployee(employeeId);
        if (employee != null) {
            employee.displayTimecards();
        } else {
            System.out.println("Employee not found.");
        }
    }

    public static void main(String[] args) {
        TimecardSystem system = new TimecardSystem();
        
        // Thêm nhân viên mới
        system.addEmployee("E001");
        
        // Thêm bản ghi chấm công cho nhân viên
        Date date1 = new Date(); // Giả định ngày hiện tại
        system.addTimecard("E001", date1, 8);
        
        // Hiển thị bản ghi chấm công của nhân viên
        system.displayEmployeeTimecards("E001");
        
        // Cập nhật bản ghi chấm công của nhân viên
        system.updateTimecard("E001", date1, 9);
        
        // Hiển thị lại bản ghi chấm công sau khi cập nhật
        system.displayEmployeeTimecards("E001");
    }
}
