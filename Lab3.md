1. Subsystem context diagrams
   * Biểu đồ ngữ cảnh của BankSystem
     ![diagram](https://www.planttext.com/api/plantuml/png/j5DDImCn4BtdLmozQCKMpsKfKgiWg1GAtgVPQRkOJPRC15sqlyo3Fyc_OBQVcrgFvX3Op9itRzxCVdz-NREWbr0Q9OKOWX7QbsdDGgLIPp2cUM49j2ihPyaAmzmPuruBku37vnj0hvU5a9RWILMeNt11qBbnLdp4aOS7hCbtu5r1FDeWCqomRe8jK9Rf_STmk0MlJ-MT9kQOKiRgvzrrPALMwb3itWhvEMfAQnNxv_j3IsrgyMXvJluks9pFKMiNh3o5SaP-05FniSLBmB9v7S3OXPcXoqqIQYcS7QDG3CIxEu2HSuRGdf1tQwElzIaVRilAk9fesrnqWTROr86JmbhXHE1HTyT23-4uT0cSqAMofs766yicthtLgVAMeLd6UsJL85Fr_sloVZyz6MpWl2mg1hJvPlmR3bQ_DwxV7oPxCO30z1VmU50HNELH4gisHVRHwq52kTF0y5h8KXtJTAxw_OiEnAnjsKCYxnQVSfZLAettUgSaxH9OgMkoUVD3_m000F__0m00)
   * Giải thích
     - PayrollController:
       + Đóng vai trò là thành phần điều khiển, thực hiện chức năng chạy hệ thống trả lương (run payroll) và gửi yêu cầu tới hệ thống ngân hàng để thực hiện các
         khoản thanh toán.
       + Tương tác với IBankSystem qua phương thức deposit, trong đó hệ thống gửi thông tin lương (Paycheck) đến ngân hàng đích (BankInformation).
     - IBankSystem:
       + Là một interface (giao diện) đại diện cho các dịch vụ ngân hàng, cung cấp phương thức deposit, được sử dụng để xử lý việc gửi tiền vào tài khoản ngân hàng.
       + IBankSystem định nghĩa phương thức deposit với các tham số là thông tin tiền lương (Paycheck) và thông tin ngân hàng (BankInformation).
     - BankSystem:
       + Được xác định là một proxy của hệ thống con, thay mặt cho IBankSystem, nó triển khai phương thức deposit để thực hiện các thao tác gửi tiền thực tế.
       + BankSystem liên kết đến các thực thể Paycheck và BankInformation, xử lý thông tin cần thiết để thực hiện các giao dịch.
     - Paycheck và BankInformation:
       + Paycheck: Là một thực thể đại diện cho thông tin về lương của nhân viên, chứa các dữ liệu cần thiết để xử lý thanh toán.
       + BankInformation: Là thực thể chứa thông tin về tài khoản ngân hàng của người nhận.
   * Biểu đồ ngữ cảnh của PrintSevice
     ![diagram](https://www.planttext.com/api/plantuml/png/j5FBQiCm4BphAnPV-Y0nxTKO4vhq46WX4EXTaJUEg2ovqhh1jFco7lf9_ONAJXt7YNEi3WBjZ7PdPwMVh--98swfp1KZIGfXOQMc9TftAH0Oku8PhgL642OlZ4PD3jP6ARELEeFdbobmApQIK51faHLSlF8C8PWQJTRpqC8Jhz06yC70Bw6uSx3WLGqUaU9O70v9yaTkbiMt4XtvAqx9ulgcGNPinxfYSqrerzmBxjMIX_2yrzLHygAEjwanBvIf4ETf14loI3O2nnMtLGGpKwuKZY35j1GaZNPjx2Q21sCKSZsWx55xLwiB5jH5VUFOSFfDdqlfiBwaBdukhSCor6WvOJhpcuVzFg1sMQvSvGZp4wd7viMnQrbzoVzavU41MbIyOMzauO3hT3zVla_1pfzK62OdWu-WT7Y9sWuaEfZbMFzw_3aUmqd2LeE3hQGDQvC4Ts5u6y00t-sDmXHMLKU_hxd9mB-8G5XijB09whJ-fxy0003__mC0)
   * Giải thích
     - PayrollController:
       + Là thành phần điều khiển bảng lương, nó gửi yêu cầu đến IPrintService để in tài liệu bảng lương (paycheck) cho nhân viên nếu phương thức thanh toán là
         nhận trực tiếp hoặc qua thư.
     - EmployeeApplication:
       + Là ứng dụng của nhân viên, nơi nhân viên có thể yêu cầu in các báo cáo như số giờ làm việc hoặc các thông tin khác liên quan.
     - IPrintService:
       + Là một giao diện đại diện cho các dịch vụ in, định nghĩa phương thức print, nhận đối số là một tài liệu (document) để in.
       + IPrintService thực hiện vai trò kết nối giữa các thành phần và hệ thống con PrintService, giống như cách IBankSystem kết nối với BankSystem.
     - PrintService:
       + Là hệ thống con thực tế thực hiện các lệnh in ấn. PrintService nhận tài liệu và thực hiện quy trình in tương ứng.
     - Document:
       + Là thực thể đại diện cho tài liệu cần in, có thể là bảng lương hoặc báo cáo tùy theo yêu cầu từ PayrollController hoặc EmployeeApplication.
   * Biểu đồ ngữ cảnh của ProjectManagementDatabase
     ![diagram](https://www.planttext.com/api/plantuml/png/j9EnJiCm48PtFyMDHA8la05LfKXqG49YOBuwHmXrxCXt6Ih4ap7qaVeAjOEfqZHf9IIy9F9zvyl_HTv_x-OiwAMjZP9A304yU_T1MfxGOaarMLcYu1gPb58GbZR8F4t1PqV5LP8aB1Plg6wCsnAjYXnUn5Usp7Be0SU-jYbGA5KUNUjvfFSMcX-Wl_KUuLVdDnGsbwvT6mep5iuPGjkT_zNBy90EFOyr0lrMJYtWrZjZxfsL-2H_cdxGsrd8BiNCqZUcAPKLyc-e2LRNVF_5zVzvZWdEtSncTqUTEQ3Mn4ny1GpL67U2clQY1l87qq4ywWsFKkazGE4VLwLbTK5_hs7ioip95l5ogGC0003__mC0)
   * Giải thích
     - PayrollController:
       + Thành phần này đại diện cho bộ điều khiển bảng lương và tương tác với ProjectManagementDatabase để lấy dữ liệu dự án. Thông tin này cần thiết để đảm bảo
       tính toán đúng chi phí và mã thanh toán khi xử lý bảng lương.
     - EmployeeApplication:
       + Ứng dụng của nhân viên sử dụng dữ liệu từ ProjectManagementDatabase cho mục đích chấm công, giúp ghi lại thời gian làm việc của nhân viên trên các dự án cụ
       thể và các mã thanh toán liên quan.
     - IProjectManagementDatabase:
       + Là giao diện định nghĩa các chức năng truy xuất thông tin dự án của hệ thống. Giao diện này cung cấp phương thức getProjectData, nhận projectID và trả về
       thông tin dự án cần thiết để hỗ trợ quá trình tính toán của các thành phần khác trong hệ thống.
       + Giao diện này đóng vai trò làm cầu nối, cho phép các thành phần khác như PayrollController và EmployeeApplication truy cập dữ liệu dự án một cách gián tiếp
       thông qua ProjectManagementDatabase.
     - ProjectManagementDatabase:
       + Là hệ thống con thực hiện các chức năng truy xuất dữ liệu dự án thực tế. ProjectManagementDatabase nhận yêu cầu từ IProjectManagementDatabase, xử lý các
       truy vấn và trả về thông tin cần thiết cho Project.
     - Project:
       + Là thực thể đại diện cho thông tin dự án, chứa các chi tiết cần thiết về mã dự án, tên dự án, và các thông tin liên quan khác. Dữ liệu này được trả về qua
       IProjectManagementDatabase cho các thành phần yêu cầu như PayrollController và EmployeeApplication.
2. Analysis class to design element map
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
3. Design element to owning package map
|Design Element|Owning Package|
|--------------|--------------|
|EmployeeEntity|Data Access::Employee Management|
|TimeCardEntity|Data Access::Employee Management|
|PaymentMethodEntity|DataAccess::Payment|
|PayrollProcessor|Business Services::Payroll Processing|
|ReportGeneratorComponent|Presentation::Report::Payroll|
|EmployeeDataAccess|DataAccess::Employee|
|TimecardDataAccess|DataAccess::Employee|
|PaymentDataAccess|DataAccess::Payment|
|PayrollUI|Presentation::Payroll|
|SalaryCalculator|BusinessLogic::Payroll|
|PayrollReportGenerator|Presentation::Report::Payroll|
4. Architectural layers and their dependencies
![diagram](https://www.planttext.com/api/plantuml/png/T9D1JiCm44NtFiKe-rw01IeA1NLHgIgK_SWPg8LZH_PKA4ASZ0L7uWhO96dSECdEUVFdPxudlzy_Qy_e-5nhqQ1ynpU2uaNHHm6V0i8ZDNeFUsoTrVgu5LzYh2kjuVYQt6prtbb9tbkNe0Crrl4Z6NB8L-G9DRgsH2tF-X-bJlV827SojhkssjIDjYrHBEXu0fzLJH9TDGl3HzPaE66fuSvMf1UyDeOLjnEVClXaeFVO4P_iG8FB9KrOhMwpjE06YgCd1rl38IN9off2P5LHcayVnG_4ydHXeSshNT3d0OtwWK642_eimr7U8-XczmiD9kiGvVs1UhQadAvBb0udwgYY89w9A4skkvGexc4txKmmGrxZHMUgF8uaf7G9CkMQJ1L_mJy0003__mC0)
