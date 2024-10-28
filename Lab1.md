1. Phân tích Kiến trúc
- Kiến trúc đề xuất: dựa trên các yêu cầu và mô tả của bài toán, kiến trúc phù hợp cho hệ thống trả lương. có thể áp dụng kiến trúc Client-Server 3 tầng để đảm bảo tính mở rộng, hiệu suất và bảo mật
- Lý do chọn và ý nghĩa từng thành phần:
  + Client Layer: Cho phép nhân viên tương tác với hệ thống. Các hoạt động này sẽ được giới hạn để đảm bảo tính bảo mật, ví dụ: chỉ có thể xem và cập nhật bảng chấm công của mình.
  + Application Layer: Chịu trách nhiệm xử lý logic nghiệp vụ và các yêu cầu từ Client Layer. Các yêu cầu từ Client Layer sẽ được xử lý tại đây trước khi kết nối với Database Layer để đảm bảo tính toàn vẹn dữ liệu.
  + Database Layer: Lưu trữ dữ liệu về nhân viên, bảng chấm công, và các dữ liệu khác. Cơ sở dữ liệu Project Management hiện tại sẽ chỉ được truy cập cho các yêu cầu thông tin về dự án, còn thông tin về nhân viên và bảng chấm công sẽ được lưu trữ trong một cơ sở dữ liệu mới để không ảnh hưởng đến cơ sở dữ liệu hiện có.
- Biểu đồ package mô tả kiến trúc:
