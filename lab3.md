# Subsystem context diagrams
- Các hệ thống con trong hệ thống: PrintService, ProjectManagementDatabase, BankSystem.
- Hệ thống PrintService
  
![diagram](https://www.planttext.com/api/plantuml/png/j5FBReCm4BpxArPS-b22sYj2A6hIGwHMYXIfTyTiY5LZKwzfXDfyMG_zfFv23IaX9EHO7opO6U_Epje_NzyJSjowCbVCIQSG5bPgjqJxBWN2yyiKPaWoqunT-Q-rr0Z2v8NHg1t1sYXbjb9d3PDRiP4EXIijieABLvuX15EZdVKyjF34AxG1V33mIoXE10jUrU0HAOx5uIT9_iZDilXM8Zb_X9GihcyQPCTsh2isrmxjcdlflLho49xt-ZjANjJnDZNcXJ8LuZoDOEayaes0kEAsYc1cofN24QIObi99ewcDtKJmO8n2hWUKFMhlRtN1WhgeRnmRJh_fSoaTrfVKnS-bTLY66YrtcCxyvc6_3wXTbYkgo65-8lNOl3YcbjMN_4zM7YwWHSKRzaOM15od-_doVGfsVgN2C3aPV0GbuILgEv3eO1Qn_l7uSpo6auIj1eAjT1lM9Wdkml0sW04-xOt255PLHx-lkSd0kuX0M6oqi0dgj7wnlm000F__0m00)

-Hệ thống ProjectManagementDatabase
![diagram]()

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
|PaymentMethodEntity|Data|
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


