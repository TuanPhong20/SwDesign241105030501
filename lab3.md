# Subsystem context diagrams
- Các hệ thống con trong hệ thống: BankSystem, PrintService, ProjectManagementDatabase.
![diagram](https://www.planttext.com/api/plantuml/png/P94n3i8m34NtdiBApWKO42giI8YUm1I30arI4XS98Kx6m96u0h6RfT0fjPzVlfNFwxrCZ947rrKzjXSy4Mpn7aFNDVV4vE1HGVxQuFhWoJEOqePLY6G0anv-eHhzPHGe8hz_dcWzDnHljXqzMlYdmfbQtg3FqLmkhP5nZwcCRDPrfICI0cQpXLu5Sp0xkWwKMBQHCQEKDeLIVAxBI1SQHXwIcQeqa50D-GFig0-nUCREHAILLV176nso3VvNbgDESesBWUnJf49CdGKXHjlbTCzgcPF8Mtq1003__mC0)

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

# Architectural layers and their dependencies
![diagram](https://www.planttext.com/api/plantuml/png/V9D1JiCm44NtESKe-rw01IgKWYeLAG9wWC4TMgkE7TcJHOGu6GkEn1MmcwGnSTBih3SlF_vsVhz_bexHSbsgh49nmWD1NbXof1bP6WrRRCZcy9c1VuH2vw30nXgbTfliAnki-zf9JHvlpK6AArvXZV1pnaReXIfZ-OaqMUH_v1KLscQ5IjJgZEBC1sI4Eo7EiMdWkgoKQOZ2M3iLmJTPaa2xduJ-KqjVGSJ6iU_ew5hcMhFaPfItyda9wBAUYO-cfpxjqZ8i5hT9Tt03-SwHXOrctva8PvLdoLHGqnQ2_4WiZXVcN_DXPloqgC7l6GGuuoTT3dg7eDsxctd1w784lLjGn-RCyUK9Qh-YbahoyaH5SNFjeGIvW-rk9uhf-neEEh7IEgAIuakGc4lI-_2Z_W400F__0m00)


