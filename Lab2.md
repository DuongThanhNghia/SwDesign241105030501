# Lab 2
## I. Phân tích các ca sử dụng còn lại
### 1. Phân tích ca sử dụng Create Employee 
### 2. Phân tích ca sử dụng Maintain Puschase Order
### 3. Phân tích ca sử dụng Login
#### 3.1 Xác định các lớp phân tích cho ca sử dụng
### 4. Phân tích ca sử dụng Create AdminiStrative Report
#### 4.1 Xác định các lớp phân tích cho ca sử dụng
##### Các lớp phân tích chính
- Ca sử dụng này nhằm cung cấp chức năng PayrollAdministrator tạo báo cáo hành chính, bao gồm hai loại:
    - Total Hour Worked: Báo cáo tổng số giờ làm việc của nhân viên
    - Pay Year-to-Date: Báo cáo tổng lương tính đến thời điểm hiện tại trong năm

- PayrollAdministrator: Đại diện cho tác nhân chính, Payroll Administrator, người tương tác với hệ thống và lưu báo cáo hành chính

  **Phương thức**
  
      - requestRepost(criteria: ReportCriteria): Phương thức để Payroll Administrator yêu cầu tạo báo cáo theo các tiêu chí cụ thể.
      - saveReport(report: Report, fileName: String, location: String): Phương thức để Payroll Administrator lưu vào báo cáo vào vị trí chỉ định nếu muốn.
  
- Report: Lớp này đại diện cho báo cáo hành chính mà hệ thống tạo ra

   **Thuộc tính**

      - reportType: Loại báo cáo (Total Hours Worked hoặc Pay Year-to-Date).
      - beginDate, endDate: Khoảng thời gian cho báo cáo.
      - employeeNames: Danh sách tên các nhân viên có trong báo cáo.
      - content: Nội dung của báo cáo.

   **Phương thức**

      - generate(): Tạo báo cáo dựa trên tiêu chí đã chọn
      - save(fileName: String, location: String): Lưu báo cáo với tên vị trí chỉ định

- ReportGenerator: Lớp này chịu trách nhiệm cho việc xử lý logic tạo báo cáo theo yêu cầu từ Payroll Administrator

  **Thuộc tính**

      - dataSource: Nguồn dữ liệu dùng để tạo báo cáo, như thông tin về giờ làm và lương của nhân viên

  **Phương thức**

      - generateReport(criteria: ReportCriterial): Tạo và trả về báo cáo dựa trên tiêu chí được cung cấp

- ReportCriterial: Lớp này lưu trữ tiêu chí Payroll Administrator nhập vào để tạo báo cáo.

  **Thuộc tính**

      - reportType: Loại báo cáo (Total Hours Worked hoặc Pay Year-to-Date).
      - beginDate: Ngày bắt đầu
      - endDate: Ngày kết thúc
      - employeeNames: Dánh sách tên nhân viên cần có trong danh sách

 - ErrorLogger: Lớp này quản lý việc hiển thị và lưu lại các thông báo lỗi nếu có sự cố xảy ra trong quá trình tạo hoặc lưu báo cáo

   **Thuộc tính**

       - errorMessage: Thông điệp lỗi cuối cùng được ghi lại

   **Phương thức**

       - logError(message: String): Lưu và hiển thị thông báo lỗi
       - displayError(): Hiển thị thông báo lỗi cho Payroll Administrator
#### 4.2 Biểu đồ Sequence cho ca sử dụng Create AdminiStrative Report
![Sequence](https://www.planttext.com/api/plantuml/png/d99DJiCm48NtFeNLLIB11Rn00eJOLAZY1YOPt95SEvrCa7eCRa1LiU-2LRjW4THxz0HSWVm1QPeKYIpiU3BlpJSPVsxV9veO8qoqOpdH2_BMNiOpT9WoQVOasWdta7ZYMt0mzEqWT4FaQUoD0HAYproUNtGzbIIOPv1o7GyYGWP2hPh4w-OSYexmrqj9KmVXJmzjMLxbIo-ZSk5f_kAcnVkRCq8MJvq-GCaPkMAhkYwJJpUePAgV87X42tTw1cVI-aWpUXTMuX9al5jdnmo777r5LAk5Z-TyLIoxzNwxYgJjTGIRmdUn_UQLvSD-iyIUOgtvgOBNLETWL6rbE-XCymD6uO-y9He6ZZ5Dh5xKXhKMN2mgilOyEdWz8p_9sDo38yx_C9PyNm000F__0m00)
#### 4.3 Nhiệm vụ của các lớp phân tích
- PayrollAdministrator: Tác nhân chính yêu cầu tạo và lưu báo cáo
- Report: Đại diện cho báo cáo hành chính, chịu trách nhiệm tạo và lưu nội dung báo cáo
- ReportGenerator: Chịu trách nhiệm xử lý logic để tạo báo cáo theo tiêu chí.
- ReportCriteria: Lưu trữ các tiêu chí để tạo báo cáo
#### 4.4 Biểu đồ lớp (Class Diagram) mô tả các lớp phân tích
![Diagram]()
- ErrorLogger: Quản lý thông báo lỗi và hiển thị lỗi cho Payroll Administrator
#### 5. Phân tích ca sử dụng Maintain Employee Infomation
#### 6. Phân tích ca sử dụng Run Payroll
