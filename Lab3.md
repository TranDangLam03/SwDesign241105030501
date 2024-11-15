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
     - EmployeeApplication (EA):
       + Đại diện cho các ứng dụng của nhân viên, tương tác với PrintService để yêu cầu in báo cáo hoặc các tài liệu liên quan đến bảng lương.
     - PayrollControllerProcess (PC):
       + Được triển khai trên máy chủ bảng lương, quá trình này tương tác với PrintService để in tài liệu bảng lương khi cần thiết.
     - PrintService:
       + Hệ thống con cung cấp các chức năng in ấn, xử lý yêu cầu in từ cả EmployeeApplication và PayrollControllerProcess.
