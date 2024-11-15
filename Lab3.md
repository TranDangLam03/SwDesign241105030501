1. Subsystem context diagrams
   - Biểu đồ ngữ cảnh của BankSystem
   - Giải thích
     + PayrollController có thể tương tác với nhiều hệ thống khác nhau thông qua các giao diện, như IBankSystem ở đây, giúp hệ thống Payroll System dễ dàng mở rộng
       hoặc thay đổi hệ thống ngân hàng mà không ảnh hưởng đến chức năng chính.
     + BankSystem là một hệ thống con xử lý việc chuyển khoản và xác nhận lại kết quả về cho PayrollController nếu có quy trình kiểm tra.
     + Paycheck và BankInformation là các dữ liệu đầu vào quan trọng để đảm bảo giao dịch được thực hiện chính xác.
