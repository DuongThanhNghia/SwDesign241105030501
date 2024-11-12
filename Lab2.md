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

- EmployeeService

  **Phương thức**

      - createEmployee(employee: Employee): Xử lý việc tạo mới nhân viên
      - validateEmployee(employeee: Employee): Kiểm tra tính hợp lệ của thông tin nhân viên trước khi lưu

- EmployeeRepository:

  **Phương thức**

      - saveEmployee(employee: Employee): Lưu thông tin nhân viên vào cơ sở dữ liệu
      - findEmployeeById(maNhanVien: String): Tìm kiếm thông tin nhân viên dựa trên mã nhân viên

- Department

  **Thuộc tính**

      - maPhongBan: Mã phòng ban
      - tenPhongBan: Tên phòng ban

  **Phương thức**

      - addEmployee(employee: Employee): Thêm nhân viên vào phòng ban

  - Payroll
 
  **Thuộc tính**

      - maNhanVien: Mã nhân viên
      - luongCoBan: Lương cơ bản của nhân viên

  **Phương thức**

      - calculateInitialSalary(employee: Employee): Tính lương ban đầu cho nhân viên
#### 1.2 biểu đồ Sequence cho ca sử dụng Create Employee
![Sequence](https://www.planttext.com/api/plantuml/png/Z9BDJiCm3CVlUOeSLucz00Uq0uXnGQYhk5k9jrfoaoeVbV9i77WaNW5NexHCAz13L3ls_sSx_dXxtyK48UME5PZaWzxNIkrhlRtJ3rtFlY0UC0naKDzg4n0IJlvD1yyjk5T2TwCJkjbW3pHRVPkzEpLjDetusiQ3EDq9oYED0dsbBaaBk507OBB2tLGAE9rDZTEzt83IylqYKcFl8qbtHUGY37CBqq_rGs8HlxqwYE_gHZ6xXh_7NaRReKkI0jQkK1TXVz14Ovts0YLuvl6PW4rccTYJeqJ01s08vO8wXLz7VcLAVsFghBX25mtPcKMbvqsnEcPZCCPZPYuAEQ8cz-y7lAvAtkaZ44ijwApQoJ5kxoS0003__mC0)
#### 1.3 Nhiệm vụ của các lớp phân tích
- Employee: Lưu trữ thông tin cá nhân của nhân viên
- EmployeeService: Xử lý yêu cầu tạo mới nhân viên
- EmployeeRepository: Lưu trữ thông tin nhân viên vào cở sở dữ liệu, tìm kiếm thông tin nhân viên dụa trên mã nhân viên
- Department: Quản lý phòng ban, liên kết nhân viên mới với phòng ban tương ứng
- Payroll: Lưu trữ thông tin phòng ban, tính  toán lương ban đầu cho nhân viên mới
#### 1.4 Biểu đồ lớp (Class Diagram) cho các lớp phân tích
![Diagram](https://www.planttext.com/api/plantuml/png/Z5D1Ri8m4Bpd5Jx2WG_uK25ALN6fK46zB_P2B6tio7OYMLLVraEVr2_K1foG4BNDATgPtPdTIRu_lvREW_LDHOKWS8uzLJMPWCZU2vQUdRTAdrW5BoNeDuLwKFQe9-jaG4q2TTaOVTgNZTX7kDmRkE9hyCZq2SApIbBrfTe2AHcHsPopbJ64cUwWFHTResJnKOpCxz2sIdGx28jnHWPdU7tX7NyyFSjcF9g3tzlkBBnYRPponeRi8bd-tSDvcJFtgBJCm2fivAo_Fx-USjwtzkfhh6EQ5Mf_bz-sZ8TVmLr-mpf8-G-FdTuMWZL4VtmiQzCS21cbw1zDfoM0H4Fnp1kjl0BQ0O4DqxAN4KbudF5YyJ1rTCuQXswIVNCapfJsQ47uQMhUZ_TcU-90EdTn5bUNX98TGf7RRuc3MV6ZI3kpex75ZQqHFuRYc3V54hLCV-eF0000__y30000)
### 2. Phân tích ca sử dụng Maintain Puschase Order
#### 2.1 Xác định các lớp phân tích cho ca sử dụng
##### Mục đích
- Duy trì và cập nhật thông tin đơn hàng mua (Purchase Order) trong hệ thống
- PurchaseOrder:

  **Thuộc tính**

      - maDonHang: Mã đơn hàng
      - ngayDatHang: Ngày đặt hàng
      - soTienDonHang: Tổng giá trị đơn hàng
      - trangThaiDonHang: Trạng thái của đơn hàng

  **Phương thức**

      - validate(): Xác minh tính hợp lệ của thông tin đơn hàng
      - updateOrderDetails(): Cập nhật chi tiết đơn hàng

- PurchaseOrderService:
 
  **Phương thức**

      - maintainOrder(order: PurchaseOrder): Xử lý việc duy trì và cập nhật đơn hàng
      - validateOrderData(order: PurchaseOrder): Kiểm tra tính hợp lệ của thông tin đơn hàng trước khi lưu

- PurchaseOrderRepository:

  **Phương thức**

      - saveOrder(order: PurchaseOrder): Lưu thông tin đơn hàng vào cơ sở dữ liệu
      - findOrderById(maDonHang: String): Tìm kiếm thông tin đơn hàng dựa trên mã đơn hàng
      - updateOrder(order: PurchaseOrder): Cập nhật thông tin đơn hàng trong cơ sở dữ liệu

- Supplier:

  **Thuộc tính**

      - maNhaCungCap: Mã nhà cung cấp
      - tenNhaCungCap: Tên nhà cung cấp

  **Phương thức**

      - linkOrder(order: PurchaseOrder): Liên kết đơn hàng với nhà cung cấp
#### 2.2 Biểu đồ Sequence cho ca sử dụng Maintain Puschase Order
![Sequence](https://www.planttext.com/api/plantuml/png/b9DTJiCm3CVVSme_hj9s0HxGXFO0Jw1j7C1gt2qYTQfyJFHiF70aha2ITeLLPIkHaZPs_FlRaVFryRbs7gqFjHPOUcFXrP4L8gsmkeUNOCiZEdgsakoEx4cL17TGes8VPpOlQjmOVaG-B84Fs6xGTnjdzefuy7aRF_iZgjvIY4dwM7LBZN4gfjP6uKgnpDQ7zad-28zGlq9MVnTnOHO2jGUJVe7UbVDEG1opCeoi4sebqTEYo669bKqzCRemEsOpBweEJM9tbtrngfY6pgk_oxrZovlPxKBJQ9MBrOhVhYOpdBsfdb0tnICaz-CvwDnz9C65iYJdgg1rcoca7O7YVrx-f08nSdHMg3J9vG0TSCHIPBbUnf03DhvhdolTCnPBCPK9YHQdMCSrFSTl0000__y30000)
#### 2.3 Nhiệm vụ của các lớp phân tích
- PurchaseOrder: Lưu trữ và quản lý thông tin đơn hàng. Đảm bảo rằng thông tin được nhập vào là hợp lệ và có thể được cập nhật khi cần
- PurchaseOrderService: Xử lý các nghiệp vụ liên quan đến duy trì và cập nhật đơn hàng, bao gồm xác minh dữ liệu và lưu thông tin đơn hàng vào cơ sở dữ liệu
- PurchaseOrderRepository: Tương tác với cơ sở dữ liệu để lưu trữ và truy xuất thông tin đơn hàng. Đảm bảo rằng dữ liệu được lưu trữ an toàn và có thể truy xuất khi cần
- Supplier: Quản lý thông tin nhà cung cấp và liên kết đơn hàng với nhà cung cấp tương ứng
#### 2.4 Biểu đồ lớp (Class Diagram) cho các lớp phân tích
![Diagram](https://www.planttext.com/api/plantuml/png/Z5DBJiCm4Dtd55wcYruW2rIrMS064Ea5XcH8HZZZo9-W274o5Xo9As0dJKH2Mkg5PRsPD-_DZFpz-RKp5hHrjOno2SQ8HwVp2Wm-w0ArU8z4E9dLnAMe8LLy2rmEQ0eM1PVG-SSlLBbdYSAe8o7FyazLhFR8iGAQ1LkGLFY2yIOHUwKa0Wy1rmIujvEY1P8cfBIAYkWZMZETeMufnz5x3SIUndqiLk5EveIbucXbq0GB_x7MVJnXemnPfRlHYe4MBzhek-fJNuYB7jrtTqKy3Juv3N6puFuPrKM5oM_ccaRIofxlApWuBW_Gp5U7l8n8ujUh55TtjDtUd1rQ8fn1SvutcK-4tp1goAqHRsIhAwKyhmQ6qcjCfTQIGeScsY4NuPVy0000__y30000)
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
#### 5.1 Xác định các lớp phân tích cho ca sử dụng
##### Mục đích:
- Duy trì và cập nhật thông tin cá nhân của nhân viên trong hệ thống
- Employee:

  **Thuộc tính**

      - maNhanVien: Mã nhân viên
      - tenNhanVien: Tên nhân viên
      - loaiNhanVien: Loại nhân viên
      - phuongThucThanhToan: Phương thức thanh toán
      - ngayGiaNhap: Ngày gia nhập công ty
      - diaChi: Địa chỉ của nhân viên
      - soDienThoai: Số điện thoại của nhân viên
      - email: Địa chỉ email của nhân viên
  
  **Phương thức**

      - updatePersonalInfo(): Cập nhật thông tin cá nhân của nhân viên
      - validate(): Xác minh tính hợp lệ của thông tin nhân viên

- EmployeeService:

  **Phương thức**

      - maintainEmployee(employee: Employee): Xử lý việc duy trì và cập nhật thông tin nhân viên
      - validateEmployeeData(employee: Employee): Kiểm tra tính hợp lệ của thông tin nhân viên trước khi lưu

- EmployeeRepository:

  **Phương thức**

      - saveEmployee(employee: Employee): Lưu thông tin nhân viên vào cơ sở dữ liệu
      - findEmployeeById(maNhanVien: String): Tìm kiếm thông tin nhân viên dựa trên mã nhân viên
      - updateEmployee(employee: Employee): Cập nhật thông tin nhân viên trong cơ sở dữ liệu

- Department

  **Thuộc tính**

      - maPhongBan: Mã phòng ban
      - tenPhongBan: Tên phòng ban

  **Phương thức**

      - linkEmployee(employee: Employee): Liên kết nhân viên với phòng ban
#### 5.2 Biểu đồ Sequence cho ca sử dụng Maintain Employee Infomation
![Sequence](https://www.planttext.com/api/plantuml/png/b5DBJiCm4Dtx55vIARq02rH14MB30WBxKJnfHZZZABOhSZOM78ahC4x91wZI4ibMvlC-jiQVxnyR7w0DiROAYk1Q_UonLIhjUdsbR-l6kWxn2Tiz5QWlTGt4GTPGkQZXeG9-8UHC1-Gfi0veYfegEjxbLInooLMv0qdo3hexIWHDfWt1JKMPzcuhYBmIUAPHzEnA_VOni_Q8ZVCarZjnLnAReN3TtPkPkubaXbWVFUEGKGfi40k7IECR-U2Lbc_1Z-3tOCb0m8jLtvn8-jH49LNeQoV8VXmkDebqlFZXP_M7wEm3VbEQ9IjRR6H0QkGWG4lykc1Wrdj2E14jwGgwdy4PXBXqRGs178zJY4RxM1JeVHcjxNe-j3ur_-l6pv531fRUKWOIJJOgZCJ8HlNQawP3hzc5m-GS7vmZoWbHkfZePAcDxEbzVW400F__0m00)
#### 5.3 Nhiệm vụ của các lớp phân tích
- Employee: Lưu trữ và quản lý thông tin cá nhân của nhân viên. Đảm bảo rằng thông tin được nhập vào là hợp lệ và có thể được cập nhật khi cần.
- EmployeeService: Xử lý các nghiệp vụ liên quan đến duy trì và cập nhật thông tin nhân viên, bao gồm xác minh dữ liệu và lưu thông tin nhân viên vào cơ sở dữ liệu.
- EmployeeRepository: Tương tác với cơ sở dữ liệu để lưu trữ và truy xuất thông tin nhân viên. Đảm bảo rằng dữ liệu được lưu trữ an toàn và có thể truy xuất khi cần.
- Department: Quản lý thông tin phòng ban và liên kết nhân viên với các phòng ban tương ứng.
#### 5.4 Biểu đồ lớp (Class Diagram) mô tả các lớp phân tích
![Diagram](https://www.planttext.com/api/plantuml/png/Z5DBQeH04DrxYbuwYxc0Yp0OGvXD63AIVQ4rTf6sMkpM824doo97oXNIJjJnXumWo7jLxzNFt--VWx5GsYfNNgB06F6K5qetYEBJ4-rpjYLn9d9uaS1lX3o1BV8ghZJGAb78IdCMoog97IrZ3HqVWKN16JJFr5eLawoKu57I138wSjgnT4OJ77CWzO_Ke2Xriluk4A7M2dklgcZX4vP6CwWZNtGRKcjAlIzlDeSpbZKbmpYSEbltzhIFtKSmPCpT-Z9wtdKAsscB8bwnq8QiBfk-3WCrRjTmRUSQUo5EUo9iZgb_MsRGZMrtInsFw0w7eTO82tT8ER9TdCv9kfs7i3YTAQw8t-ypdEzcltzO6rKWAeDcDNfKR23SHh64n1hnGLPkghle71Wo9pkIc4MqZHZlW9oslzKV0000__y30000)
### 6. Phân tích ca sử dụng Run Payroll
#### 6.1 Xác định các lớp phân tích cho ca sử dụng
##### Mục đích:
- Tính toán và thực hiện thanh toán lương cho nhân viên trong hệ thống

- Employee:

  **Thuộc tính**

      - maNhanVien: Mã nhân viên
      - tenNhanVien: Tên nhân viên
      - loaiNhanVien: Loại nhân viên
      - phuongThucThanhToan: Phương thức thanh toán
      - ngayGiaNhap: Ngày gia nhập công ty
      - luongCoBan: Lương cơ bản của nhân viên

  **Phương thức**

      - getPaymentDetails(): Lấy chi tiết thanh toán của nhân viên

  - TimeCard:
 
    **Thuộc tính**

        - ngayLamViec: Ngày làm việc
        - soGioLam: Số giờ làm việc của nhân viên
        - maDuAn: Mã dự án mà nhân viên đã làm

    **Phương thức**

        - getHoursWorked(): Lấy số giờ làm việc của nhân viên trong khoảng thời gian cụ thể
 - SalesOrder:

    **Thuộc tính**

       - ngayDatHang: Ngày đặt hàng
       - soTienDonHang: Tổng giá trị của đơn hàng
       - hoaHong: Tỷ lệ hoa hồng mà nhân viên được nhận

   **Phương thức**

       - getCommission(): Lấy thông tin về hoa hồng của đơn hàng
- Payroll:

  **Thuộc tính**

      - maNhanVien: Mã nhân viên
      - tongLuong: Tổng lương của nhân viên

  **Phương thức**

      - calculatePayroll(employee: Employee, timecards: List<TimeCard>, salesOrders: List<SalesOrder>): Tính toán lương của nhân viên dựa trên thông tin cá nhân và các thẻ chấm công, đơn hàng
      - executePayroll(employee: Employee): Thực hiện thanh toán lương cho nhân viên

- PayrollService
  **Phương thức**

      - runPayroll(): Xử lý việc tính toán và thanh toán lương cho tất cả nhân viên
      - validatePayrollData(employee: Employee): Kiểm tra tính hợp lệ của thông tin lương

- PayrollRepository:

  **Phương thức**

      - savePayroll(payroll: Payroll): Lưu thông tin về lương đã được tính toán
      - getPayrollByEmployee(maNhanVien: String): Truy xuất thông tin lương của một nhân viên cụ thể
#### 6.2 Biểu đồ Sequence cho ca sử dụng Run Payroll
![Sequence](https://www.planttext.com/api/plantuml/png/V9F1JiCm38RlUOeSLsbxWGbLsn0t18WXxbRgiWWdcP9qKf-D0u_4As1AqqARhfT8zl_RdnFtw-Dp5oBus1WIeABpSbyPRONe3hafvHEqtX4TqL-qGhcLlh5zR5M8IPRrT-PChaLynhCBcYksx7d3k2TAgS36Z6oJwtQlGxn9ub88e2XhnaHGfw6NaFpDKLwqmLlmrHGbnSEXJHLM1XvEO5yrsgAhbl4kyoLnkG1o1CBmw2lqKvGnSmqcwr_66ULBG7s43Gf8DGGHqvicYFLajFMiTd6z-BzH0ro63lrP2BILo6pG0UpxE57qO4EDdXk3rxmx7KRlOeQ_wkoLf09IELjhRo1gPsTjsVcxyjlXSdZHPMYKmX3gXgWLOiV4Ft_ADm000F__0m00)
#### 6.3 Nhiệm vụ của các lớp phân tích
- Employee: Lưu trữ và quản lý thông tin cá nhân và lương cơ bản của nhân viên. Cung cấp chi tiết thanh toán để tính toán lương.
- TimeCard: Lưu trữ thông tin về số giờ làm việc của nhân viên. Cung cấp dữ liệu về số giờ làm việc để tính toán lương.
- SalesOrder: Lưu trữ thông tin về các đơn hàng và hoa hồng của nhân viên. Cung cấp dữ liệu về hoa hồng để tính toán lương.
- Payroll: Xử lý việc tính toán và thực hiện thanh toán lương cho nhân viên.
- PayrollService: Xử lý các nghiệp vụ liên quan đến tính toán và thanh toán lương. Kiểm tra tính hợp lệ của dữ liệu lương và thực hiện thanh toán.
- PayrollRepository: Tương tác với cơ sở dữ liệu để lưu trữ và truy xuất thông tin lương.
#### 6.4 Biểu đồ lớp (Class Diagram) mô tả các lớp phân tích
![Diagram](https://www.planttext.com/api/plantuml/png/Z5HBZjim3Dtx55fcW9aB64KmJL9C5a5RD4QxPcLEB8mi6g8Kr2XwiYvwf5wXSY9PTX9CnniRv2CV7p_--_lF8pkmphUwa1gOnOUsqzGZYf-569wziyeSH0iV6p1V5PgPsQ6vQTS4wgQZQpoPGzLuMGLtKn54_mOS2dE0_aaDL5sqal-kKUWXQ4sh13wW-mnzYyPjq87IlBWhnTnI_2gYeagrk0PR9qKZqmxQK9yyMvLnWkb9KR1UAD_uzvbtIzxoDx8lM0-a8ImpxK4ZVx8rsYkkyB45SvYfOgf2UpPahZmDmPQIBP2kgMqLio8pS9v1cJO8jwJrVoOMKxkGT-V7v1Aqz3fK6PCiCCw_73VXNhZGGHawoANOANRlKaUNzu97oScPcx3CjPwuy0TA_nfJm1z9rLVAzcYFIeuhQRr9ELB4oNu4hUei9RGSRfEiY3I6NRha-O8TiN9a-qJ5S1phxSxlCg5dtEUD7CohFZ4jyWZAE9MxCJgJXwr-kL3eB1X-HXjw2LOXBqwTZP7BIPik6lJmi1nrJiIKmZFoBN2Qv9l0UR9lWgUrBFEIlOQRvUJmpkYPhiWewdZdKynuwX7J3CSwGqnED6BaU5jSJ4SnAIsPIj5PaiX3M1eH5uzewk7_-Gy00F__0m00)
