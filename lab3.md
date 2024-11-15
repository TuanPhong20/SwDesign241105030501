# Subsystem context diagrams
- Các hệ thống con trong hệ thống: PrintService, ProjectManagementDatabase, BankSystem.
- Hệ thống PrintService
  
![diagram](https://www.planttext.com/api/plantuml/png/j5FBQiCm4BphAnPV-Y0nxTKO4vhq46WX4EXTaJUEg2ovqhh1jFco7lf9_ONAJXt7YNEi3WBjZ7PdPwMVh--98swfp1KZIGfXOQMc9TftAH0Oku8PhgL642OlZ4PD3jP6ARELEeFdbobmApQIK51faHLSlF8C8PWQJTRpqC8Jhz06yC70Bw6uSx3WLGqUaU9O70v9yaTkbiMt4XtvAqx9ulgcGNPinxfYSqrerzmBxjMIX_2yrzLHygAEjwanBvIf4ETf14loI3O2nnMtLGGpKwuKZY35j1GaZNPjx2Q21sCKSZsWx55xLwiB5jH5VUFOSFfDdqlfiBwaBdukhSCor6WvOJhpcuVzFg1sMQvSvGZp4wd7viMnQrbzoVzavU41MbIyOMzauO3hT3zVla_1pfzK62OdWu-WT7Y9sWuaEfZbMFzw_3aUmqd2LeE3hQGDQvC4Ts5u6y00t-sDmXHMLKU_hxd9mB-8G5XijB09whJ-fxy0003__mC0)

-Hệ thống ProjectManagementDatabase
![diagram](https://www.planttext.com/api/plantuml/png/j9EnJiCm48PtFyMDHA8la05LfKXqG49YOBuwHmXrxCXt6Ih4ap7qaVeAjOEfqZHf9IIy9F9zvyl_HTv_x-OiwAMjZP9A304yU_T1MfxGOaarMLcYu1gPb58GbZR8F4t1PqV5LP8aB1Plg6wCsnAjYXnUn5Usp7Be0SU-jYbGA5KUNUjvfFSMcX-Wl_KUuLVdDnGsbwvT6mep5iuPGjkT_zNBy90EFOyr0lrMJYtWrZjZxfsL-2H_cdxGsrd8BiNCqZUcAPKLyc-e2LRNVF_5zVzvZWdEtSncTqUTEQ3Mn4ny1GpL67U2clQY1l87qq4ywWsFKkazGE4VLwLbTK5_hs7ioip95l5ogGC0003__mC0)

- Hệ thống BankSystem
  
![diagram](https://www.planttext.com/api/plantuml/png/j5DDImCn4BtdLmozQCKMpsKfKgiWg1GAtgVPQRkOJPRC15sqlyo3Fyc_OBQVcrgFvX3Op9itRzxCVdz-NREWbr0Q9OKOWX7QbsdDGgLIPp2cUM49j2ihPyaAmzmPuruBku37vnj0hvU5a9RWILMeNt11qBbnLdp4aOS7hCbtu5r1FDeWCqomRe8jK9Rf_STmk0MlJ-MT9kQOKiRgvzrrPALMwb3itWhvEMfAQnNxv_j3IsrgyMXvJluks9pFKMiNh3o5SaP-05FniSLBmB9v7S3OXPcXoqqIQYcS7QDG3CIxEu2HSuRGdf1tQwElzIaVRilAk9fesrnqWTROr86JmbhXHE1HTyT23-4uT0cSqAMofs766yicthtLgVAMeLd6UsJL85Fr_sloVZyz6MpWl2mg1hJvPlmR3bQ_DwxV7oPxCO30z1VmU50HNELH4gisHVRHwq52kTF0y5h8KXtJTAxw_OiEnAnjsKCYxnQVSfZLAettUgSaxH9OgMkoUVD3_m000F__0m00)

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
|EmployeeEntity|Data Access::Employee Management|
|TimeCardEntity|Data Access::Employee Management|
|PaymentMethodEntity|DataAccess::Payment|
|PayrollProcessor|Business Services::Payroll Processing|
|ReportGeneratorComponent|Report|
|EmployeeDataAccess|DataAccess|
|TimecardDataAccess|DataAccess|
|PaymentDataAccess|DataAccess|
|PayrollUI|Presentation|
|SalaryCalculator|Business Logic|
|PayrollReportGenerator|Report|

# Architectural layers and their dependencies
![diagram](https://www.planttext.com/api/plantuml/png/V9D1JiCm44NtESKe-rw01IgKWYeLAG9wWC4TMgkE7TcJHOGu6GkEn1MmcwGnSTBih3SlF_vsVhz_bexHSbsgh49nmWD1NbXof1bP6WrRRCZcy9c1VuH2vw30nXgbTfliAnki-zf9JHvlpK6AArvXZV1pnaReXIfZ-OaqMUH_v1KLscQ5IjJgZEBC1sI4Eo7EiMdWkgoKQOZ2M3iLmJTPaa2xduJ-KqjVGSJ6iU_ew5hcMhFaPfItyda9wBAUYO-cfpxjqZ8i5hT9Tt03-SwHXOrctva8PvLdoLHGqnQ2_4WiZXVcN_DXPloqgC7l6GGuuoTT3dg7eDsxctd1w784lLjGn-RCyUK9Qh-YbahoyaH5SNFjeGIvW-rk9uhf-neEEh7IEgAIuakGc4lI-_2Z_W400F__0m00)


