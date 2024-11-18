1. Subsystem context diagrams
   * Biểu đồ ngữ cảnh của BankSystem
     ![diagram](https://www.planttext.com/api/plantuml/png/j5DDImCn4BtdLmozQCKMpsKfKgiWg1GAtgVPQRkOJPRC15sqlyo3Fyc_OBQVcrgFvX3Op9itRzxCVdz-NREWbr0Q9OKOWX7QbsdDGgLIPp2cUM49j2ihPyaAmzmPuruBku37vnj0hvU5a9RWILMeNt11qBbnLdp4aOS7hCbtu5r1FDeWCqomRe8jK9Rf_STmk0MlJ-MT9kQOKiRgvzrrPALMwb3itWhvEMfAQnNxv_j3IsrgyMXvJluks9pFKMiNh3o5SaP-05FniSLBmB9v7S3OXPcXoqqIQYcS7QDG3CIxEu2HSuRGdf1tQwElzIaVRilAk9fesrnqWTROr86JmbhXHE1HTyT23-4uT0cSqAMofs766yicthtLgVAMeLd6UsJL85Fr_sloVZyz6MpWl2mg1hJvPlmR3bQ_DwxV7oPxCO30z1VmU50HNELH4gisHVRHwq52kTF0y5h8KXtJTAxw_OiEnAnjsKCYxnQVSfZLAettUgSaxH9OgMkoUVD3_m000F__0m00)
   * Giải thích
1. PayrollSystem
* Vai trò: Đây là hệ thống xử lý lương của nhân viên, chịu trách nhiệm khởi tạo quá trình thanh toán và gửi yêu cầu đến hệ thống ngân hàng để thực hiện giao dịch.
* Mối quan hệ:
  - Tương tác với EmployeePayment: PayrollSystem xử lý dữ liệu lương của nhân viên (như số tài khoản, số tiền, ngày giao dịch) để gửi cho hệ thống ngân hàng.
  - Gửi yêu cầu qua PayrollController: PayrollSystem sử dụng lớp điều khiển (PayrollController) để quản lý luồng công việc và giao tiếp với các hệ thống bên ngoài, như BankSystem.
2. Controller Layer
Thành phần: PayrollController
* Vai trò:
  - Là lớp điều khiển của PayrollSystem, chịu trách nhiệm giao tiếp giữa PayrollSystem và BankSystem.
  - Kiểm tra dữ liệu đầu vào từ EmployeePayment và gửi yêu cầu thực hiện thanh toán đến IBankSystem.
* Chức năng chính:
  - Phương thức processPayment(): Xử lý yêu cầu thanh toán từ PayrollSystem. Ví dụ:
    + Lấy dữ liệu từ EmployeePayment (bao gồm số tài khoản, số tiền, ngày giao dịch).
    + Gửi yêu cầu đến BankSystem thông qua giao diện IBankSystem.
  - Cập nhật trạng thái: Sau khi giao dịch thành công hoặc thất bại, PayrollController cập nhật trạng thái (status) của dữ liệu thanh toán trong EmployeePayment.
* Mối quan hệ:
  - Sử dụng IBankSystem: PayrollController gọi phương thức của IBankSystem để thực hiện giao dịch tài chính.
3. Entity Layer
Thành phần: EmployeePayment
* Vai trò:
  - Đây là lớp dữ liệu (entity) lưu trữ thông tin thanh toán cho từng nhân viên.
  - Đóng vai trò là trung gian truyền dữ liệu giữa PayrollSystem và PayrollController.
* Các thuộc tính:
  - accountNumber: String: Số tài khoản nhận tiền.
  - amount: Double: Số tiền cần thanh toán.
  - transactionDate: Date: Ngày thực hiện giao dịch.
  - status: String: Trạng thái của giao dịch (ví dụ: "Pending", "Success", "Failed").
* Mối quan hệ:
  - Được xử lý bởi PayrollController: Dữ liệu trong EmployeePayment được PayrollController sử dụng để khởi tạo giao dịch thanh toán.
  - Truyền dữ liệu qua hệ thống: Sau khi giao dịch hoàn tất, trạng thái (status) được cập nhật trong EmployeePayment.
4. Interface Layer
Thành phần: IBankSystem
* Vai trò:
  - Đây là giao diện trung gian giữa PayrollSystem và BankSystem, định nghĩa các phương thức mà PayrollSystem có thể sử dụng.
  - Giúp PayrollSystem tương tác với BankSystem mà không cần biết chi tiết thực hiện bên trong.
* Chức năng chính:
  - Phương thức transferFunds(accountNumber: String, amount: Double, transactionDate: Date): Boolean:
    + accountNumber: Số tài khoản mà tiền sẽ được chuyển vào.
    + amount: Số tiền cần chuyển.
    + transactionDate: Ngày thực hiện giao dịch.
    + Trả về giá trị Boolean để xác nhận giao dịch thành công hay thất bại.
* Mối quan hệ:
  - Được PayrollController sử dụng: Lớp điều khiển gọi IBankSystem để yêu cầu chuyển khoản.
  - Tương tác với Subsystem Proxy: Gửi yêu cầu từ PayrollSystem đến BankSystem thực tế thông qua lớp proxy.
5. Subsystem Proxy
Thành phần: BankSystem
* Vai trò:
  - Đây là thành phần bên trong hệ thống ngân hàng, chịu trách nhiệm thực hiện chi tiết các giao dịch tài chính.
  - Đóng vai trò như một proxy (đại diện) để xử lý logic thực tế.
* Chức năng chính:
  - Thực hiện các yêu cầu từ IBankSystem, như:
    + Xử lý giao dịch chuyển tiền.
    + Đảm bảo các giao dịch tuân thủ quy định ngân hàng (xác minh số tài khoản, kiểm tra đủ tiền trong tài khoản, v.v.).
* Mối quan hệ:
  - Nhận yêu cầu từ IBankSystem: Proxy thực hiện các giao dịch thực tế sau khi nhận yêu cầu từ giao diện.
  - Trả kết quả cho IBankSystem: Sau khi giao dịch hoàn thành, proxy gửi phản hồi về kết quả (thành công/thất bại) đến PayrollController thông qua IBankSystem.

   * Biểu đồ ngữ cảnh của PrintSevice
     ![diagram](https://www.planttext.com/api/plantuml/png/j5FBQiCm4BphAnPV-Y0nxTKO4vhq46WX4EXTaJUEg2ovqhh1jFco7lf9_ONAJXt7YNEi3WBjZ7PdPwMVh--98swfp1KZIGfXOQMc9TftAH0Oku8PhgL642OlZ4PD3jP6ARELEeFdbobmApQIK51faHLSlF8C8PWQJTRpqC8Jhz06yC70Bw6uSx3WLGqUaU9O70v9yaTkbiMt4XtvAqx9ulgcGNPinxfYSqrerzmBxjMIX_2yrzLHygAEjwanBvIf4ETf14loI3O2nnMtLGGpKwuKZY35j1GaZNPjx2Q21sCKSZsWx55xLwiB5jH5VUFOSFfDdqlfiBwaBdukhSCor6WvOJhpcuVzFg1sMQvSvGZp4wd7viMnQrbzoVzavU41MbIyOMzauO3hT3zVla_1pfzK62OdWu-WT7Y9sWuaEfZbMFzw_3aUmqd2LeE3hQGDQvC4Ts5u6y00t-sDmXHMLKU_hxd9mB-8G5XijB09whJ-fxy0003__mC0)
   * Giải thích
1. Controller Layer
Thành phần: PayrollController
* Vai trò:
  - Điều phối quá trình tạo phiếu lương và gửi yêu cầu in.
  - Tương tác giữa PayrollSystem và các dịch vụ liên quan (PrintService).
* Chức năng chính:
  - Phương thức requestPayslip():
    + Nhận yêu cầu từ PayrollSystem để tạo phiếu lương cho nhân viên.
    + Trích xuất dữ liệu như employeeId, salary, và deductions từ hệ thống nguồn (PayrollSystem).
    + Tạo đối tượng Payslip và gửi yêu cầu in phiếu qua IPrintService.
* Mối quan hệ:
  - Tạo Payslip: PayrollController khởi tạo các phiếu lương mới dựa trên dữ liệu đầu vào.
  - Sử dụng IPrintService: Gửi yêu cầu in phiếu qua giao diện định nghĩa.
2. Entity Layer
Thành phần: Payslip
* Vai trò:
  - Lưu trữ thông tin của từng phiếu lương.
  - Là thành phần trung gian chứa dữ liệu để gửi đến dịch vụ in.
* Các thuộc tính:
  - employeeId: String: Mã định danh của nhân viên.
  - salary: Double: Tổng lương của nhân viên.
  - deductions: Double: Các khoản khấu trừ.
  - generatedDate: Date: Ngày tạo phiếu lương.
* Mối quan hệ:
  - Được PayrollController tạo ra: Khi có yêu cầu từ PayrollSystem, đối tượng Payslip được tạo và sử dụng để in.
  - Là đầu vào cho IPrintService: Payslip chứa dữ liệu cần thiết để in.
3. Interface Layer
Thành phần: IPrintService
* Vai trò:
  - Là giao diện trung gian giữa PayrollController và Subsystem (PrintService).
  - Định nghĩa các phương thức mà PayrollSystem có thể sử dụng để in phiếu lương.
* Chức năng chính:
  - Phương thức printPayslip(employeeId: String, salary: Double, deductions: Double): Boolean:
  - Tham số:
  + employeeId: Mã nhân viên cần in phiếu.
  + salary: Tổng lương của nhân viên.
  + deductions: Các khoản khấu trừ.
  - Kết quả: Trả về giá trị Boolean để xác nhận in thành công hoặc thất bại.
* Mối quan hệ:
  - Nhận yêu cầu từ PayrollController: Giao diện này nhận yêu cầu in từ lớp điều khiển.
  - Tương tác với Subsystem: Chuyển tiếp yêu cầu đến lớp Subsystem để thực hiện in thực tế.
4. Subsystem
Thành phần: PrintService
* Vai trò:
  - Thực hiện chi tiết quá trình in phiếu lương, như gửi dữ liệu đến máy in hoặc lưu trữ phiếu lương dưới dạng file.
  - Đóng vai trò là thành phần "thực hiện" của hệ thống.
* Chức năng chính:
  - Phương thức printPayslip(employeeId: String, salary: Double, deductions: Double): Boolean:
  + Nhận dữ liệu từ IPrintService.
  + Thực hiện in thực tế (ví dụ: gửi lệnh in, lưu file PDF, hoặc ghi log).
  + Trả về kết quả thành công/thất bại cho giao diện.
* Mối quan hệ:
  - Nhận yêu cầu từ IPrintService: Subsystem thực hiện logic chi tiết dựa trên yêu cầu từ giao diện.

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
