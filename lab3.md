# Analysis class to design element map
|Analysis Class|Analysis Class|
|--------------|--------------|
|Employee|EmployeeEntity|
|TimeCard|TimeCardEntity|
|PaymentMethod|PaymentMethodEntity|
|PayrollService|PayrollProcessor|
|EmployeeRepository|EmployeeDataAccess|
|TimecardRepository|TimecardDataAccess|
|PaymentRepository|PaymentDataAccess|
|ReportGenerator|ReportGeneratorComponent|

# Design element to owning package map
|Design Element|Owning Package|
|--------------|--------------|
|EmployeeEntity|Data|
|TimeCardEntity|Data|
|PaymentMethodEntity|Data|
|PayrollProcessor|Service|
|ReportGeneratorComponent|Report|
|EmployeeDataAccess|DataAccess|
|TimecardDataAccess|DataAccess|
|PaymentDataAccess|DataAccess|
|PayrollUI|Presentation|
|SalaryCalculator|Business Logic|
|PayrollReportGenerator|Report|



