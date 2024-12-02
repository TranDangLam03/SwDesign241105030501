# Thiết kế các ca sử dụng cho hệ thống "Payroll System"
1. Login - Use Case Interaction Diagram
![diagram](https://www.planttext.com/api/plantuml/svg/V9313S8m34NlcS8Bi007L0JYn9K1tCI2YDIf71VKsJWm4YkGg5IbHUAOd_VydRmUpoefYdPDC6Wr2covFoKIKyUE7KeFntZsV8ZI61jP9OOXsGs7a55YzTf3qVQeM6CYOpvpOBMP9i0QCfl3BjymDWJ83bfCwHx5cOaRfQaagpSCtg4IM25NEZ4aiyIo-Rr7rko5x7Ncp83LlouV6OHI5_ItQF4mvrCRi8TGib6gY5tvsZS0003__mC0)
- Mô tả sơ đồ:
  + Actor: Người dùng (AnyUser) nhập thông tin đăng nhập vào giao diện đăng nhập (LoginForm).
  + Boundary: LoginForm là giao diện người dùng mà người dùng tương tác.
  + Control: LoginController xử lý logic kiểm tra thông tin đăng nhập.
  + Entity: UserDatabase chứa dữ liệu người dùng, giúp LoginController xác nhận thông tin người dùng.
- Quá trình:
  + Người dùng nhập thông tin (tên người dùng và mật khẩu).
  + LoginForm gửi yêu cầu kiểm tra đến LoginController.
  + LoginController truy vấn UserDatabase để kiểm tra tính hợp lệ của thông tin.
  + Kết quả từ UserDatabase được trả lại LoginController.
  + LoginController thông báo cho LoginForm để hiển thị kết quả đăng nhập (thành công hay lỗi).

2. Maintain Timecard - Use Case Interaction Diagram
  * Mô tả sơ đồ:
![diagram](https://www.planttext.com/api/plantuml/svg/b59BRW8n3Dtd5Bu05s1H8HMwgzH5Bs0ICpDL4eyS1sdEne8ZSGLIjKC6qIcmjFC-VdPEX-CgAOhcu0rQPO5Dw3qFH6RBEJgK0JwxG1R5lR44OpcgiByqNtzgJs8eQgSLFjOVmbzazHqZDXHASusAMqnapEW5YvSh5rW2znH1HwchnmcukXTAGmesYnIBM-O4EU4NrexKjlVminb6snQb8R3iA5qaO34tgP1cgV705JKpxt5Fvq_tQO3RzRekzHw7clk_MvHPYahBMT9ZbyXzIKHF727XddvPhj9M5Dttnpm3003__mC0)
- Actor: Nhân viên (Employee) là người nhập thông tin vào biểu mẫu chấm công.
- Boundary: TimecardForm là giao diện cho phép nhân viên xem và chỉnh sửa chấm công của mình.
- Control: TimecardController xử lý logic truy xuất và lưu dữ liệu chấm công.
- Entity: Timecard chứa dữ liệu về giờ làm của nhân viên.
- Entity: ProjectManagementDatabase chứa mã dự án (charge codes).

3. Run Payroll - Use Case Interaction Diagram
  * Mô tả sơ đồ:
![diagram](https://www.planttext.com/api/plantuml/svg/X591JWCn3Bpd5Vu07-20AXOEt93W0yRhgb6zIUHuA-tREF0ale3J9Lf4YyZ1aPsPySJ9v_l7hXggpPC49CiABqirdWR9T0oKasaMUCR5DndML5W39uksmEDK92_CFN-D4nFgs7Cdqe5TwItFQKJrYiPah4yjx95uExd7T5oRX_331DpSNVQ7MpZRXhAUGD5CN6kuH3gzktJMdeqEmBqWiTfrJh-9SvHD8vyOhD_klow4GhEWSVDt7Tqdqz3Atz1rLW75u24gaszSSeqMmDTLdMrgRIQSHZ35LFqjOqw1fRBpYcE7i_QVEh_VnTLAAsssN3liFBIlyWK00F__0m00)
- Actor: SystemClock đại diện cho hệ thống tự động kích hoạt quá trình tính lương vào thời gian xác định (ví dụ, cuối tuần).
- Control: PayrollController xử lý quy trình tính lương cho nhân viên.
- Entity: Employee chứa thông tin về nhân viên.
- Entity: Timecard chứa giờ làm của nhân viên, giúp tính lương.
- Entity: Paycheck tạo ra thông báo lương sau khi tính toán.
- Boundary: PrinterInterface dùng để in séc nếu lương được trả bằng séc giấy, còn BankSystem là hệ thống chuyển khoản cho thanh toán qua chuyển khoản ngân hàng.
