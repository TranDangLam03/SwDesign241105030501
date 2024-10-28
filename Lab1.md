1. Phân tích Kiến trúc
- Kiến trúc đề xuất: dựa trên các yêu cầu và mô tả của bài toán, kiến trúc phù hợp cho hệ thống trả lương. có thể áp dụng kiến trúc Client-Server 3 tầng để đảm bảo tính mở rộng, hiệu suất và bảo mật
- Lý do chọn và ý nghĩa từng thành phần:
  + Client Layer: Cho phép nhân viên tương tác với hệ thống. Các hoạt động này sẽ được giới hạn để đảm bảo tính bảo mật, ví dụ: chỉ có thể xem và cập nhật bảng chấm công của mình.
  + Application Layer: Chịu trách nhiệm xử lý logic nghiệp vụ và các yêu cầu từ Client Layer. Các yêu cầu từ Client Layer sẽ được xử lý tại đây trước khi kết nối với Database Layer để đảm bảo tính toàn vẹn dữ liệu.
  + Database Layer: Lưu trữ dữ liệu về nhân viên, bảng chấm công, và các dữ liệu khác. Cơ sở dữ liệu Project Management hiện tại sẽ chỉ được truy cập cho các yêu cầu thông tin về dự án, còn thông tin về nhân viên và bảng chấm công sẽ được lưu trữ trong một cơ sở dữ liệu mới để không ảnh hưởng đến cơ sở dữ liệu hiện có.
- Biểu đồ package mô tả kiến trúc
![Diagram](https://www.planttext.com/api/plantuml/svg/V98zRiCm38LtdOBGr0wvGAV4yHB01G8KpSuohAj6bWJz132Adgn3ZzGhL7A6k7RSZS9x_FX8wEVhUnqY-fWwBHpI2Li6kTMAJOG6U_OIFWG0QGm1v7DW3piJsRyYiRmAE-DIX0DgTSIeh97YKrnv6-Uqea6u0QrIK8PprTXMqGZwn9IyYZritvXE8w76YB3tbdANCktVOKLymS0t9ksnzrPhgAiHB7FUcI8yeidzNLcyhk2kuHQfln_OqxrXjPh5XWSWstN9b4KvY9bUUaO1iX-fB52yi_CjJ3XV74luoS5Af58ikATNp7PtUHN-J1to_t-hJF0SlU8p1yWvKOWrcsFvMxy0003__mC0)
2. Cơ chế phân tích
- Authentication & Authorization: Đảm bảo chỉ nhân viên mới được truy cập và chỉ truy cập dữ liệu cá nhân của họ, trong khi Payroll Administrator có quyền truy cập mở rộng.
- Data Validation: Kiểm tra dữ liệu bảng chấm công, đặc biệt là số giờ làm không vượt quá giới hạn hợp lý (<= 24 giờ mỗi ngày).
- Commission Calculation: Tính toán hoa hồng cho các nhân viên hưởng hoa hồng dựa trên tỷ lệ phần trăm và doanh số.
- Payroll Scheduling: Hệ thống phải tự động chạy quy trình trả lương vào thứ Sáu hàng tuần và ngày làm việc cuối cùng của tháng.
- Database Synchronization: Tương tác với cơ sở dữ liệu Project Management để lấy thông tin dự án và đồng bộ dữ liệu giữa các tầng khác nhau.
- Payment Method Processing: Xử lý phương thức thanh toán theo yêu cầu của nhân viên (nhận tại công ty, gửi qua bưu điện hoặc chuyển khoản).
3. Phân tích ca sử dụng Select Payment Method
- Biểu đồ lớp:
![Diagram](https://www.planttext.com/api/plantuml/svg/L50x3i8m3Drp2gjx1zPE7M1We4BY16vgWKISH8qpH1KdO-18N04bBT1EVdfwF_dzVBL1S9J8HYbjC0Gui3Sk4S6a06gmo5G0iJ_k2_AOJYGtDwZ7rtJ6n6HbfXSdpveCKMiNhNIHUneBqwEzTpbw7J4wOouf2F4I4Vs0Gajublx6LRiAN5sNkorlLlisyhzwrTC0eyKh1QLQiaF-mmS00F__0m00)
