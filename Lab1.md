1. Phân tích Kiến trúc
- Kiến trúc đề xuất: dựa trên các yêu cầu và mô tả của bài toán, kiến trúc phù hợp cho hệ thống trả lương. có thể áp dụng kiến trúc Client-Server 3 tầng để đảm bảo tính mở rộng, hiệu suất và bảo mật
- Lý do chọn và ý nghĩa từng thành phần:
  + Client Layer: Cho phép nhân viên tương tác với hệ thống. Các hoạt động này sẽ được giới hạn để đảm bảo tính bảo mật, ví dụ: chỉ có thể xem và cập nhật bảng chấm công của mình.
  + Application Layer: Chịu trách nhiệm xử lý logic nghiệp vụ và các yêu cầu từ Client Layer. Các yêu cầu từ Client Layer sẽ được xử lý tại đây trước khi kết nối với Database Layer để đảm bảo tính toàn vẹn dữ liệu.
  + Database Layer: Lưu trữ dữ liệu về nhân viên, bảng chấm công, và các dữ liệu khác. Cơ sở dữ liệu Project Management hiện tại sẽ chỉ được truy cập cho các yêu cầu thông tin về dự án, còn thông tin về nhân viên và bảng chấm công sẽ được lưu trữ trong một cơ sở dữ liệu mới để không ảnh hưởng đến cơ sở dữ liệu hiện có.
- Biểu đồ package mô tả kiến trúc
![Diagram](https://www.planttext.com/api/plantuml/svg/V98zRiCm38LtdOBGr0wvGAV4yHB01G8KpSuohAj6bWJz132Adgn3ZzGhL7A6k7RSZS9x_FX8wEVhUnqY-fWwBHpI2Li6kTMAJOG6U_OIFWG0QGm1v7DW3piJsRyYiRmAE-DIX0DgTSIeh97YKrnv6-Uqea6u0QrIK8PprTXMqGZwn9IyYZritvXE8w76YB3tbdANCktVOKLymS0t9ksnzrPhgAiHB7FUcI8yeidzNLcyhk2kuHQfln_OqxrXjPh5XWSWstN9b4KvY9bUUaO1iX-fB52yi_CjJ3XV74luoS5Af58ikATNp7PtUHN-J1to_t-hJF0SlU8p1yWvKOWrcsFvMxy0003__mC0)
