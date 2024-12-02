##Thiết kế các ca sử dụng cho hệ thống "Payroll System"
1. Login - Use Case Interaction Diagram
* ![diagram](https://www.planttext.com/api/plantuml/svg/V9313S8m34NlcS8Bi007L0JYn9K1tCI2YDIf71VKsJWm4YkGg5IbHUAOd_VydRmUpoefYdPDC6Wr2covFoKIKyUE7KeFntZsV8ZI61jP9OOXsGs7a55YzTf3qVQeM6CYOpvpOBMP9i0QCfl3BjymDWJ83bfCwHx5cOaRfQaagpSCtg4IM25NEZ4aiyIo-Rr7rko5x7Ncp83LlouV6OHI5_ItQF4mvrCRi8TGib6gY5tvsZS0003__mC0)
* Mô tả sơ đồ:
- Actor: Người dùng (AnyUser) nhập thông tin đăng nhập vào giao diện đăng nhập (LoginForm).
- Boundary: LoginForm là giao diện người dùng mà người dùng tương tác.
- Control: LoginController xử lý logic kiểm tra thông tin đăng nhập.
- Entity: UserDatabase chứa dữ liệu người dùng, giúp LoginController xác nhận thông tin người dùng.
