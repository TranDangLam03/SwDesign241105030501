1. Subsystem context diagrams
   * Biểu đồ ngữ cảnh của BankSystem
     
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
   * Biểu đồ ngữ cảnh của BankSystem
     
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

3. Design element to owning package map

4. Architectural layers and their dependencies
