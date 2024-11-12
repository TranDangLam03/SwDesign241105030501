1. Phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
   * Phân tích ca sử dụng Create Administrative Report
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/R9112i8m44NtEKMMBTGBT268uauHFS7G3YMG9dKo2aKycGkFv1LCJ6i3RHR9y9Dv_qy-htUbmJbvWfwirfkwLKOv9c1B8bubchhZ6JjBB1z2XiLzXwMyC2dJHCKn4E-0lHpsAAAf4-avW2DgQmq7QwGHsg11RpPOPS6ZcBZ5IFD5ssdR8nwXnVoFtIkD1p3GJ4G7O_2CVaSXjQtyFDQ4Fh4qlLojvmbBINYzeUE1belP4z-s-6Ebh0YdgPOxq-nb6ZiNNm000F__0m00)
       - Nhiệm vụ của từng lớp
         + PayrollAdministrator: Yêu cầu hệ thống tạo báo cáo và quyết định lưu báo cáo.
         + ReportController: Nhận yêu cầu tạo báo cáo, gọi lớp xử lý báo cáo và lớp lưu trữ nếu cần.
         + AdministrativeReport: Lưu trữ dữ liệu về loại báo cáo và thời gian báo cáo.
         + FileManager: Chịu trách nhiệm lưu báo cáo vào hệ thống.
   * Phân tích ca sử dụng Create Employee Report
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/UhzxVt9EOd6nWcjkGKv-PMeg5oetABKWlwX4ePfB0GHAAWjIhHI2Iueoyz8X8iKbYKKbBeabG64G2H5CpKj14gg56WanoZa_hwGeFoSdjGWgx9QPa-gRc9UO3XJXWbche6k7eLx1Ig4ejR0qjRW48gEXoOMX1AWDpULM2ib5gK1duDM3v0QWXkB4CeHo00000F__0m00)
     - Nhiệm vụ của từng lớp
       + Employee: Tạo yêu cầu báo cáo.
       + ReportController: Xử lý yêu cầu từ nhân viên, tương tác với lớp báo cáo và lưu trữ nếu cần.
       + EmployeeReport: Lưu trữ thông tin về loại và thời gian báo cáo của nhân viên.
       + FileManager: Xử lý lưu trữ báo cáo.
   * Phân tích ca sử dụng Login
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/UhzxVt9EOd6nGcXnQX4NXEbOMfAHcbUIcPnOafcVvvoVLrAKdvEJMgHGpQK00ZdvwPbv6gL03Nc9kQaw2WL0JUNvHIcQNBLS2CE2KukBWTfXcefB4ejAe69WlI3LN2252hfskAsqWjgcoOLJ2L0xidrMg5PfSW40003__mC0)
     - Nhiệm vụ của từng lớp
       + User: Nhập thông tin đăng nhập.
       + AuthenticationController: Xác thực thông tin đăng nhập và khởi tạo phiên làm việc.
       + UserSession: Quản lý phiên đăng nhập của người dùng.
   * Phân tích ca sử dụng Maintain Employee Information
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/UhzxVt9EOd6nGa1YPL5-JevZIcvcNcPnIL5YINuH5qJADRSW9xyoDTKtCIynFRL8ePfB0GGIKr9WCXgQ4A7IWfJ4abHqqPJKd5GKqLeqWxcuiDcke6k7ORMLGYwOXMGOkX8aNI3b-IcPQPKkgIM9cJd5GDK00000__y30000)
     - Nhiệm vụ của từng lớp
       + PayrollAdministrator: Yêu cầu hệ thống quản lý thông tin nhân viên.
       + EmployeeManager: Thực hiện thêm, cập nhật hoặc xóa nhân viên.
       + Employee: Đối tượng lưu trữ thông tin nhân viên.
   * Phân tích ca sử dụng Maintain Purchase Order
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/UhzxVt9EOd6nWcjkGKv-PMeg5uGRK5gKd95OdEfVb99Qf53DfG02AOabgLOABa0Ima_CpI_DAx5IICl9JopXgiMcrJa_hwGeFoS7OKXoKIhG0B2aHYhKKayN7OLya0ZGx4HDe4bSCESewDhXDD0AnInDBbpgq8q0QYnEB8Dh0m000F__0m00)
     - Nhiệm vụ của từng lớp
       + Employee: Tạo yêu cầu đặt hàng.
       + PurchaseOrderController: Xử lý yêu cầu tạo đơn hàng mới.
       + PurchaseOrder: Lưu thông tin đơn hàng.
   * Phân tích ca sử dụng Ca sử dụng Run Payroll
     - Biểu đồ lớp
       ![Diagram](https://www.planttext.com/api/plantuml/svg/P8vD2i9038NtSueiMz0BTE52wbxG2uGGP71-IXA5eNWo5nx9A-YWOgjPXPVttfVxzKO1LM6BHN88kwB6qRsqJHn2Bimz6iBeeCw1xMcDdAndGn-qQTtbxLzZEku5aoAPp-aJ8M4qdXmQZFcKR058L9VQu6OFm78rftSWREBvp5_iN-ANty4WcLXrocxT0m00__y30000)
     - Nhiệm vụ của từng lớp
       + PayrollSystem: Quản lý tính toán lương và thực hiện giao dịch.
       + EmployeeData: Lấy dữ liệu thanh toán của nhân viên.
       + BankTransaction: Tạo và xử lý giao dịch ngân hàng.
2. Code Java mô phỏng ca sử dụng Maintain Timecard.
package MaintainTimecard;

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

class Timecard {
	private String employeeId;
	private String startDate;
	private String endDate;
	private boolean submitted = false;
	private Map<String, Integer> hoursWorked = new HashMap<>();
	private String submittedDate;

	public Timecard(String employeeId, String startDate, String endDate) {
		this.employeeId = employeeId;
		this.startDate = startDate;
		this.endDate = endDate;
	}


	public void addHours(String chargeNumber, int hours) throws Exception {
		if (submitted) {
			throw new Exception("Không thể thêm giờ: Timecard đã được gửi.");
		}
		if (hours > 24) {
			throw new Exception("Mục nhập không hợp lệ: Không thể làm việc quá 24 giờ trong một ngày.");
		}
		hoursWorked.put(chargeNumber, hoursWorked.getOrDefault(chargeNumber, 0) + hours);
	}


	public void submitTimecard() throws Exception {
		if (submitted) {
			throw new Exception("Thẻ thời gian đã được gửi.");
		}
		submitted = true;
		submittedDate = java.time.LocalDate.now().toString();
		System.out.println("Timecard được gửi vào ngày: " + submittedDate);
	}


	public void displayTimecard() {
		System.out.println("Timecard cho ID nhân viên: " + employeeId);
		System.out.println("Ngày bắt đầu: " + startDate + " | Ngày kết thúc: " + endDate);
		System.out.println("Đã gửi: " + (submitted ? "Yes, on " + submittedDate : "No"));
		System.out.println("Số giờ đã làm việc: ");
		for (Map.Entry<String, Integer> entry : hoursWorked.entrySet()) {
			System.out.println(" - Số phí: " + entry.getKey() + ", Giờ: " + entry.getValue());
		}
	}


	public boolean isSubmitted() {
		return submitted;
	}
}


public class MaintainTimecard {
	private static Scanner scanner = new Scanner(System.in);

	public static void main(String[] args) {
		try {
			System.out.print("Nhập ID nhân viên: ");
			String employeeId = scanner.nextLine();
			Timecard timecard = new Timecard(employeeId, "2024-11-01", "2024-11-07");

			boolean running = true;
			while (running) {
				System.out.println("\n1. Xem Timecard\n2. Thêm giờ\n3.  Timecard\n4. Thoát");
				System.out.print("Chọn một tùy chọn: ");
				int choice = scanner.nextInt();
				scanner.nextLine();

				switch (choice) {
				case 1:
					timecard.displayTimecard();
					break;
				case 2:
					if (timecard.isSubmitted()) {
						System.out.println("Không thể sửa đổi: Timecard đã được gửi.");
						break;
					}
					System.out.print("Nhập số phí: ");
					String chargeNumber = scanner.nextLine();
					System.out.print("Nhập số giờ đã làm việc: ");
					int hours = scanner.nextInt();
					scanner.nextLine();
					try {
						timecard.addHours(chargeNumber, hours);
						System.out.println("Đã thêm giờ thành công.");
					} catch (Exception e) {
						System.out.println(e.getMessage());
					}
					break;
				case 3:
					try {
						timecard.submitTimecard();
						System.out.println("Timecard đã được gửi thành công.");
					} catch (Exception e) {
						System.out.println(e.getMessage());
					}
					break;
				case 4:
					running = false;
					System.out.println("Thoát khỏi hệ thống.");
					break;
				default:
					System.out.println("Lựa chọn không hợp lệ. Vui lòng chọn lại.");
				}
			}
		} catch (Exception e) {
			System.out.println("Lỗi: " + e.getMessage());
		}
	}
}
