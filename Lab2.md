# Lab 2
## I. Phân tích các ca sử dụng còn lại
### 1. Phân tích ca sử dụng Create Employee 
#### 1.1 Xác định các lớp phân tích ca sử dụng
##### Mục đích:
- Tạo mới thông tin nhân viên
- Employee

**Thuộc tính**

    - maNhanVien: Mã nhân viên
    - tenNhanVien: Tên nhân viên
    - loaiNhanVien: Loại nhân viên
    - phuongThucThanhToan: Phương thức thanh toán
    - ngayGiaNhap: Ngày gia nhập công ty
**Phương thức**

    - save(): Lưu thông tin  nhân viên vào cơ sở dữ liệu
    - validate(): Xác minh tính hợp lệ của thông tin nhân viên
#### 1.2 biểu đồ Sequence cho ca sử dụng Create Employee
![Sequence](https://www.planttext.com/api/plantuml/png/Z9BDJiCm3CVlUOeSLucz00Uq0uXnGQYhk5k9jrfoaoeVbV9i77WaNW5NexHCAz13L3ls_sSx_dXxtyK48UME5PZaWzxNIkrhlRtJ3rtFlY0UC0naKDzg4n0IJlvD1yyjk5T2TwCJkjbW3pHRVPkzEpLjDetusiQ3EDq9oYED0dsbBaaBk507OBB2tLGAE9rDZTEzt83IylqYKcFl8qbtHUGY37CBqq_rGs8HlxqwYE_gHZ6xXh_7NaRReKkI0jQkK1TXVz14Ovts0YLuvl6PW4rccTYJeqJ01s08vO8wXLz7VcLAVsFghBX25mtPcKMbvqsnEcPZCCPZPYuAEQ8cz-y7lAvAtkaZ44ijwApQoJ5kxoS0003__mC0)
#### 1.3 Nhiệm vụ của các lớp phân tích
- Employee: Lưu trữ thông tin cá nhân của nhân viên
- EmployeeService: Xử lý yêu cầu tạo mới nhân viên
- EmployeeRepository: Lưu trữ thông tin nhân viên vào cở sở dữ liệu, tìm kiếm thông tin nhân viên dụa trên mã nhân viên
- Department: Quản lý phòng ban, liên kết nhân viên mới với phòng ban tương ứng
- Payroll: Lưu trữ thông tin phòng ban, tính  toán lương ban đầu cho nhân viên mới
#### 1.4 Biểu đồ lớp (Class Diagram) cho các lớp phân tích
### 2. Phân tích ca sử dụng Maintain Puschase Order
### 3. Phân tích ca sử dụng Login
#### 3.1 Xác định các lớp phân tích cho ca sử dụng
##### Mục đích
- Ca sử dụng này xác thực người dùng và cấp quyền truy cập vào hệ thống
##### Các lớp phân tích chính
- User: Lớp này đại diện cho người dùng hệ thống
**Thuộc tính**

      - username: Tên đăng nhập của người dùng. Đây là thông tin định danh để truy cập vào hệ thống
      - password: Mật khẩu của người dung. Đây là thông tin bảo mật cần thiết để xác thực người dùng
      - role: Vai trò của người dùng. Vai trò này xác định quyền hạn và chức năng người dùng có thẻ truy cập trong hệ thống

  **Phương thức**

      - authenticate(): Xác thực người dùng dựa trên tên đăng nhập và mật khẩu. Phương thức này kiểm tra xem thông tin đăng nhập có hợp lệ hay không
      - authorize(): Cấp quyền truy cập cho người dùng dựa trên vai trò của họ. Phương thức này quyết định những gì người dùng có thể làm sau khi đã đăng nhập

- AuthService: Lớp này xử lý các nghiệp vụ liên quan đến xác thực và cấp quyền truy cập

  **Phương thức**

      - login(user: User): Xử lý đăng nhập cho người dùng. Phương thức này sử dụng thông tin từ lớp user để xác thực và tọa nên phiên làm việc mới nếu thông tin hợp lệ.
      - logout(user: User): Xử lý đăng xuất cho người dùng. Kết thức phiên làm việc của người dùng và đảm bảo rằng họ không thể truy xuất các chức năng yêu cầu đăng nhập
      - validateCredentials(usename: String, password: String): Kiểm tra thông tin đăng nhập. Xác thực tên đăng nhập và mật khẩu của người dùng

  - SessionManager: Lớp này quản lý các phiên làm việc của người dùng.

  **Thuộc tính**

       - currentSessions: Danh sách các phiên làm việc hiện tại. Đây là danh sách chứa thông tin về các phiên làm việc đang hoạt động của tất cả người dùng đã đăng nhập

  **Phương thức**

      - createSessions(user: User): Tạo một phiên làm việc mới khi người dùng đăng nhập thành công. Phương thức này lưu trữ thông tin phiên làm việc
      - terminateSession(user: User): Kết thức phiên làm việc của người dùng khi họ đăng xuất
      - isSessionActive(user: User): Kiểm tra xem phiên làm việc của người đùng có đang hoạt động hay không. Phương thức này giúp xác định xem người dùng có cần phải đăng nhập lại hay không

  - UserRepository: Lớp này tương tác với cơ sở dữ liệu để truy xuất thông tin người dùng
 
    **Phương thức**

        - findUserByUserName(username: String): Truy xuất thông tin người dùng từ cơ sở dữ liệu dựa trên tên đăng nhập. Phương thức này trả về đối tượng User nếu tìm thấy thông tin tương ứng
        - updateUser(user: User): Cập nhật thông tin người dùng trong cơ sở dữ liệu. Phương thức này lưu các thay đổi thông tin của người dùng (như mật khẩu mới) vào cơ sở dữ liệu
#### 3.2 Biểu đồ Sequence cho ca sử dụng Login
![Sequence](https://www.planttext.com/api/plantuml/png/Z5DBReCm4Dtx5BC4YLoWYogjkkcYcqOvmCWUKal6Zln9bRDrqIFr2Xr3W0Y352Ipc7dlpPk7-VlvtOU8FgRE29JHUJW6yaBaD-oUuIN5hmFvYvO4Js3SITigSSzYHmsSCOHlvrKjxd5Co_HFEhkWMVBAp5PRbOklr-EDFSdKOe7U5NC7JsWYND1e1TAJ8XircY20dvNfp4AkPfJ4IDLiDHEor5rREmiXIKbXq5lHF72FOHzeyTIhimVMlPMhFBAUk0jmkL0O0Ezlw-Fc7Vh4Hs_DWaScq7AD5hL9dXxJpM1I3MWxv3g6DAXR9Ve9OtVyO6NaMxgP0TP5Q5tAQdosRvPBiIekKX5x9DzfMoJ_QE8pNudj5TZAT1_4dctdt-CV003__mC0)
#### 3.3 Nhiệm vụ của các lớp phân tích
- User: Lưu trữ thông tin đăng nhập (tên đăng nhập, mật khẩu) và vai trò của người dùng. Thực hiện xác thực và cấp quyền dựa trên vai trò
- AuthService: Xử lý các nghiệp vụ liên quan đến xác thực và cấp quyền truy cập
- SessionManager: Quản lý các phiên làm việc của người dùng
- UserRepository: Tương tác với cơ sở dữ liệu để truy xuất và cập nhật thông tin người dùng
#### 3.4 Biểu đồ lớp (Class Diagram) mô tả cho các lớp phân tích
![Sequence](https://www.planttext.com/api/plantuml/png/b9DDJiCm48NtEOMNhKGlO5LLMxQmQLJsLZ9DHqhiQCO9AeYJiU18N04xiSaV296L_URpp9kny_d-iMUho3PLcMIbOXPd1XAlYV1VQWbr8HedQLN1HAmT_6meduXaoa2fnbv1MyoKXLLaPU3MKXoDGvKUO4Fu0YiNEVaSRqcmSt2X5AZ53AAhqXIeLz5Kp7ad_ghYpfd6TWTbrwO3dWo63bfLOkxCtXFathWg-NyrlYsdm8n6FogjYc6MMKFayeOWI_60RBTXkmiCWNCGjAdH8FQS1QfG_uOEFI47u91PR66ABNnx_GIrORI6Rj7t1NNk8yVREKnZCPPrdxFdczfFqUz_SELgpQfiDhl-oKbn0PjTWPFnbSVmw8Jqxt59pQOkHTMjE9a5HWNZbNEo1vtxN-0B003__mC0)
### 4. Phân tích ca sử dụng Create AdminiStrative Report
#### 4.1 Xác định các lớp phân tích cho ca sử dụng
##### Mục đích
- Ca sử dụng này nhằm cung cấp chức năng PayrollAdministrator tạo báo cáo hành chính, bao gồm hai loại:
    - Total Hour Worked: Báo cáo tổng số giờ làm việc của nhân viên
    - Pay Year-to-Date: Báo cáo tổng lương tính đến thời điểm hiện tại trong năm
##### Các lớp phân tích chính
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
- ErrorLogger: Quản lý thông báo lỗi và hiển thị lỗi cho Payroll Administrator
#### 4.4 Biểu đồ lớp (Class Diagram) mô tả các lớp phân tích
![Diagram](https://www.planttext.com/api/plantuml/png/V9An3i8W48RtFWMZ3hv01zD11nS7RTnFUXOI2WtG9etnoHny95_18fRQIcJZkml__z_nl3yoOq7RfX895M0CEM2jj2NNXBXpj9hBakWtt1KHc7SrJd015ZmeKQ86Y_x9nTBJ5WGllkajcKWVKRUSuk20QXoRF-QySlIzJQy-Rmi2sweMgaESfQjWpq2UECe9jYYZN2ZWqKBD6YNBd3KqxyiiLo17RMVi32Pe6sZ_fRgWfMpm-mxrOtQPXa1EPZgzrMezh3BzpD14MeAhb3IcxmXtLmpZIhqTD7wv6Sh2VPWN0000__y30000)

### 5. Phân tích ca sử dụng Maintain Employee Infomation
### 6. Phân tích ca sử dụng Run Payroll
