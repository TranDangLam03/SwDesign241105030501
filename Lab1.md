1. Phân tích Kiến trúc
- Kiến trúc đề xuất: dựa trên các yêu cầu và mô tả của bài toán, kiến trúc phù hợp cho hệ thống trả lương. có thể áp dụng kiến trúc Client-Server 3 tầng để đảm bảo tính mở rộng, hiệu suất và bảo mật
- Lý do chọn và ý nghĩa từng thành phần
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
3. Phân tích ca sử dụng Payment
- Biểu đồ lớp
![Diagram](https://www.planttext.com/api/plantuml/svg/L50x3i8m3Drp2gjx1zPE7M1We4BY16vgWKISH8qpH1KdO-18N04bBT1EVdfwF_dzVBL1S9J8HYbjC0Gui3Sk4S6a06gmo5G0iJ_k2_AOJYGtDwZ7rtJ6n6HbfXSdpveCKMiNhNIHUneBqwEzTpbw7J4wOouf2F4I4Vs0Gajublx6LRiAN5sNkorlLlisyhzwrTC0eyKh1QLQiaF-mmS00F__0m00)
- Nhiệm vụ của từng lớp
  + Employee: Khởi tạo yêu cầu chọn phương thức thanh toán.
  + PayrollSystem: Xử lý yêu cầu của nhân viên, kiểm tra tính hợp lệ và cập nhật phương thức thanh toán.
  + PaymentMethod: Lớp xác định các tùy chọn thanh toán cụ thể và xử lý thông tin thanh toán của nhân viên.
4. Phân tích ca sử dụng Maintain Timecard
- Biểu đồ lớp
![Diagram](https://www.planttext.com/api/plantuml/svg/R8-n2i9038RtUuhGlODhfmuwk8YWu1pkGYjUUYMv6mxnoHny95z1UhGLmIb_uFl__7a_Nwr6b9ZO6sCzgiAEHnyo4TmDG0t4utvRr81Cvh5WvokJHN4pvZ1I4Nr8efSWDt9bjprAHuV4N-iHimJlJraZyUpteLiI9t0jKMqggEioreiD2DaWJlzYl-aD92KrfgN1JKz-0000__y30000)
- Nhiệm vụ của từng lớp
  + Employee: Nhập thông tin giờ làm vào hệ thống.
  + PayrollSystem: Xử lý dữ liệu nhập vào và lưu vào bảng chấm công.
  + Timecard: Lớp lưu trữ các thông tin chấm công của nhân viên theo thời gian.
5. Hợp nhất kết quả phân tích
- Tổng quan
  + Trong hệ thống Payroll System của Acme, có hai ca sử dụng quan trọng cần phân tích là Select Payment Method và Maintain Timecard. Hai ca sử dụng này phục vụ cho nhu cầu quản lý thông tin thanh toán và ghi nhận thời gian làm việc của nhân viên. Sau khi phân tích chi tiết từng ca sử dụng, chúng ta tiến hành hợp nhất các lớp, quan hệ và chức năng để tạo nên một kiến trúc chung, nhất quán cho hệ thống. Việc hợp nhất giúp đảm bảo rằng hệ thống có thể vận hành một cách mạch lạc và giảm thiểu sự trùng lặp trong thiết kế.
- Mối quan hệ giữa các lớp
  + Quan hệ giữa Employee và PaymentMethod: Mỗi Employee có thể có một PaymentMethod nhất định để nhận thanh toán. Đây là quan hệ một-nhiều, nơi một nhân viên có một phương thức thanh toán, nhưng các phương thức thanh toán có thể khác nhau tùy nhân viên.
  + Quan hệ giữa Employee và Timecard: Mỗi nhân viên sẽ có nhiều bản ghi Timecard trong hệ thống để quản lý thời gian làm việc. Quan hệ này là một-nhiều, vì mỗi nhân viên có thể ghi nhận nhiều bản Timecard khác nhau.
  + Quan hệ giữa PayrollSystem với Employee và Timecard: Lớp PayrollSystem quản lý các thao tác liên quan đến nhân viên và Timecard, bao gồm việc ghi nhận thời gian làm việc và xử lý thanh toán.
- Biểu đồ lớp hợp nhất của 2 ca sử dụng Select Payment và Maintain Timecard
![Diagram](https://www.planttext.com/api/plantuml/svg/V57DIiGm4BxdAOQULEY2rvxse0SFBeA2vzbqQ6KpcJ993aLyCWy-agzWcxQh4V6KuUFx9P_l7_iGKMDYPunr60BSyk1a989N0r03yN1tao-FJFaOSBods4jhtZRH0uvCFYxmgkI5CvzehIGV3ucFf1aveZyTPiEpnTCBaqNTr2t69QsNfE5Pz4IBb-rHEvgiYdGLvnx748bNVHfcXxNNnMN6d7HRoeHCylFMwhe2gUlybbiQw36KnCpRxQwgxyuDA5dHzYzczQjV0obGC2LOiejyHe_TVu8VBQQ5mPWz-NR-qIy0003__mC0)
- Chức năng của từng lớp trong hợp nhất
  + Employee: Đóng vai trò là thực thể trung tâm, nơi lưu trữ thông tin cá nhân và phương thức thanh toán của nhân viên. Nhân viên có thể cập nhật thông tin Timecard hoặc chọn phương thức thanh toán.
  + PaymentMethod: Lưu trữ chi tiết về cách thức thanh toán cho nhân viên. Có thể được cập nhật khi nhân viên thay đổi phương thức nhận tiền.
  + Timecard: Giúp quản lý thời gian làm việc của nhân viên, để hệ thống có thể tính toán mức lương dựa trên giờ làm việc và các thông tin liên quan.
  + PayrollSystem: Đóng vai trò là hệ thống quản lý toàn bộ các hoạt động liên quan đến Payroll. Lớp này chịu trách nhiệm thực hiện các chức năng như cập nhật PaymentMethod và ghi nhận Timecard của nhân viên. PayrollSystem cũng sẽ là nơi liên kết với các thành phần khác để tạo báo cáo và thực hiện tính toán lương.
- Lợi ích của việc hợp nhất
  + Giảm thiểu sự trùng lặp: Các lớp và mối quan hệ được hợp nhất, giúp tránh lặp lại thông tin và logic nghiệp vụ.
  + Dễ dàng bảo trì và mở rộng: Kiến trúc này dễ dàng bảo trì khi cần thay đổi yêu cầu hoặc mở rộng thêm chức năng mới.
  + Tính nhất quán: Việc quản lý các thông tin và quy trình liên quan đến Payroll trở nên mạch lạc hơn khi tất cả đều được tích hợp trong một hệ thống hợp nhất.
-  Kết luận: việc hợp nhất kết quả phân tích của hai ca sử dụng giúp xây dựng một hệ thống Payroll nhất quán, đáp ứng yêu cầu của Acme, Inc. Kiến trúc hợp nhất không chỉ giúp hệ thống đáp ứng nhu cầu hiện tại mà còn có khả năng mở rộng và bảo trì trong tương lai.
