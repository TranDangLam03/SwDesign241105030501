1. Subsystem context diagrams
   * Biểu đồ ngữ cảnh của BankSystem
     
   * Giải thích
     - PayrollController có thể tương tác với nhiều hệ thống khác nhau thông qua các giao diện, như IBankSystem ở đây, giúp hệ thống Payroll System dễ dàng mở rộng
       hoặc thay đổi hệ thống ngân hàng mà không ảnh hưởng đến chức năng chính.
     - BankSystem là một hệ thống con xử lý việc chuyển khoản và xác nhận lại kết quả về cho PayrollController nếu có quy trình kiểm tra.
     - Paycheck và BankInformation là các dữ liệu đầu vào quan trọng để đảm bảo giao dịch được thực hiện chính xác.
   * Biểu đồ ngữ cảnh của BankSystem
     
   * Giải thích
     - PayrollController: Đây là thành phần điều khiển chính trong hệ thống Payroll System. PayrollController gửi yêu cầu in phiếu lương bằng cách gọi phương thức
       printPaycheck thông qua giao diện IPrintService. Yêu cầu này bao gồm:
       + Paycheck: Chứa thông tin chi tiết về phiếu lương của nhân viên, bao gồm số tiền và thông tin cá nhân.
       + PrintInformation: Chứa thông tin về định dạng và các yêu cầu in ấn, như kiểu giấy, số lượng bản in.
   - IPrintService (Giao diện dịch vụ in ấn): PayrollController tương tác với IPrintService để thực hiện yêu cầu in phiếu lương. Giao diện này giúp
        PayrollController không cần biết chi tiết về cách PrintService thực hiện in ấn, mà chỉ cần gọi phương thức printPaycheck.
     - PrintService (Hệ thống con dịch vụ in ấn): PrintService là hệ thống con chịu trách nhiệm xử lý yêu cầu in phiếu lương. PrintService nhận thông tin từ
       IPrintService và thực hiện in phiếu lương dựa trên dữ liệu trong Paycheck và PrintInformation.
     - Paycheck và PrintInformation:
       + Paycheck là một thực thể chứa thông tin chi tiết về phiếu lương, bao gồm số tiền lương và các chi tiết liên quan đến nhân viên.
       + PrintInformation là một thực thể chứa các yêu cầu in ấn cụ thể, chẳng hạn như định dạng in, số lượng bản in, và kiểu giấy.
