# Payroll System Subsystem Design Solution
1 BankSystem
1.1 Interface Realizations
- Sơ đồ
 ![diagram](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2abDYNdPmPN59QgwIGcAn0eBBbPbNabgKbfYS2b7a2UF2rS55k12w57HrxL0b5QmKb89I4tCogrABbRWSKlDIW2u00000__y30000)
- Giải thích:
  + BankSystem là hệ thống xử lý các giao dịch ngân hàng.
  + BankInterface cung cấp các chức năng mà hệ thống ngân hàng cần triển khai.
  + Mối quan hệ Realizes thể hiện rằng BankSystem hiện thực hóa (realizes) các chức năng được định nghĩa trong BankInterface.
1.2 Subsystem Dependencies Class Diagram
 - Sơ đồ
 ![diagram]([https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2abDYNdPmPN59QgwIGcAn0eBBbPbNabgKbfYS2b7a2UF2rS55k12w57HrxL0b5QmKb89I4tCogrABbRWSKlDIW2u00000__y30000](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2abDYNdPmPN59QgwIGcAn0eABh2WWiJ8No0WeoazEBIxEBm8hHHT4rk2Od9nVcbVYcvYNc9uAKOugn8MmI45Nrmx3C0Kh1QNGujHY9NI5gCQ0b46OS0k0MXnIyr90tWG0003__mC0))
- Giải thích:
  + PaymentProcessor để xử lý các giao dịch như thanh toán lương.
  + AccountManager để quản lý tài khoản ngân hàng liên kết với nhân viên.

2 PrintService
2.1 Interface Realizations
- Sơ đồ
 ![diagram](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2Ka1HPbv9S6fHMMPogf92Oh42iW0Na9bQb9QOd0fLw0dZ8vJ2XRYGTIhewjgXoIjOAIW5fIRcP5Qb5YjnEQJcfO2S0W000F__0m00).
- Giải thích:
  + PrintService đại diện cho các dịch vụ in ấn.
  + PrintInterface mô tả các chức năng như tạo báo cáo hoặc in tài liệu.
  + PrintService hiện thực hóa PrintInterface, đảm bảo thực hiện đầy đủ các chức năng.
2.2 Subsystem Dependencies Class Diagram
- Sơ đồ
 ![diagram](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2Ka1HPbv9S6fHMMPogf92Oh42iW2omg3KWloY4lVKlDIYn9By8h1QD34CSrEBN8eoorAB40R3HBYGhL7GrRL3Dql1Ia49oac5MLIiXAaDnLIGfk3Kl9HYXP9yc8mIbmDG1EHh00000F__0m00)
- Giải thích:
  + ReportGenerator để tạo nội dung báo cáo từ dữ liệu.
  + PrinterDriver để gửi báo cáo đến máy in.

3 ProjectManagementDatabase
3.1 Interface Realizations
- Sơ đồ 
 ![diagram]([https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2abDYNdPmPN59QgwIGcAn0eBBbPbNabgKbfYS2b7a2UF2rS55k12w57HrxL0b5QmKb89I4tCogrABbRWSKlDIW2u00000__y30000](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2Ka1HVbPgSeblObvYUcekKCWbiIGnAR4uLKaXiLW1AWiJuyhCAqajIajCJbLGWebvmeJ06Z14kT2CKD3LjSDKfM2be1IKcfYJMPLQhCJba9gN0d8c0000__y30000))
- Giải thích:
  + ProjectManagementDatabase là thành phần quản lý cơ sở dữ liệu cho các dự án.
  + DatabaseInterface cung cấp các chức năng như truy vấn hoặc lưu trữ dữ liệu.
  + ProjectManagementDatabase hiện thực hóa DatabaseInterface để thực hiện các chức năng này.
3.2 Subsystem Dependencies Class Diagram
- Sơ đồ
 ![diagram]([https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2abDYNdPmPN59QgwIGcAn0eBBbPbNabgKbfYS2b7a2UF2rS55k12w57HrxL0b5QmKb89I4tCogrABbRWSKlDIW2u00000__y30000](https://www.planttext.com/api/plantuml/svg/UhzxlqDnIM9HIMbk3bToVcv1VbvgNec2Ka1HVbPgSeblObvYUcekKCWbiIGnAR4uLKaXiLW1AWiJGzO84WikoIy2QWChHU8ZAmiiJIsgTCrBpyo3A4FYSw6Phg2hQuTiZ8ALWXA8cGenN0chUYJpGEg1If9JYujJ8HPbfXOhSJcavgM0F0q0003__mC0))
- Giải thích:
  + DataStorage để lưu dữ liệu về dự án.
  + QueryEngine để xử lý các câu truy vấn.
