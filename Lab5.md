# Lab 5
### Thiết kế hệ thống con Run Payroll
#### 1.  Distribute subsystem behavior to subsystem elements
- EmployeeSubsystem:
  - Cung cấp thông tin chi tiết của nhân viên, bao gồm tên, mã nhân vien và lương cơ bản
- TimeCardSubsystem:
  - Cung cấp dữ liệu làm việc, bao gồm số giờ làm việc hàng tuần hoặc hàng tháng của nhân viên
- SaleOrderSubsystem:
  - Cung cấp dữ liệu đơn hàng, bao gồm tổng doanh số và hoa hồng của nhân viên làm việc theo doanh số.
- PayrollService:
  - Xử lý toàn bộ quy trình tính toán lương, kết hợp các dữ liệu từ EmployeeSubsystem, TimeCardSubsystem và SalesOrderSubsystem
  - Thực hiện kiểm tra tính hợp lệ của dữ liệu trước khi lưu
  - Quản lý lưu thông tin lương thông qua PayrollRepository
- PayrollRepository
  - Lưu trữ thông tin tổng lương của nhân viên sau khi tính toán
  - Truy xuất thông tin lương của nhân viên dựa trên mã nhân viên
#### 2. Document subsystem elements
- EmployeeSubsystem
  - Chức năng:
    - getEmployee(employeeId): Lấy thông tin nhân viên theo mã nhân viên
- TimeCardSubsystem
  - Chức năng:
    - getTimeCard(employeeId): Lấy dữ liệu giờ làm việc của nhân viên.
- SalesOrderSubsystem
  - Chức năng:
    - getSalesData(employeeId): Lấy thông tin doanh số và hoa hồng của nhân viên.
- PayrollService
  - Chức năng:
    - calculatePayroll(employeeId): Tính toán tổng lương của nhân viên dựa trên lương cơ bản, giờ làm, và hoa hồng.
    - savePayroll(payroll): Lưu thông tin lương vào hệ thống.
- PayrollRepository
  - Chức năng:
    - savePayroll(payroll): Lưu thông tin tổng lương đã tính vào cơ sở dữ liệu.
    - getPayrollByEmployee(employeeId): Truy xuất thông tin lương theo mã nhân viên.
#### 3. Describe Subsystem Dependencies
- EmployeeSubsystem:
  - Phụ thuộc vào cơ sở dữ liệu nhân viên để truy xuất thông tin cơ bản
- TimeCardSubsystem:
  - Phụ thuộc vào cơ sở dữ liệu thẻ chấm công để truy xuất số giờ làm việc
- SalesOrderSubsystem:
  - Phụ thuộc vào cơ sở dữ liệu đơn hàng để lấy thông tin doanh số và hoa hồng
- PayrollService:
  - Phụ thuộc vào EmployeeSubsystem để lấy thông tin nhân viên
  - Phụ thuộc vào TimeCardSubsystem để lấy dữ liệu giờ làm việc.
  - Phụ thuộc vào SalesOrderSubsystem để lấy thông tin doanh số và hoa hồng.
  - Phụ thuộc vào PayrollRepository để lưu và truy xuất dữ liệu lương.
- PayrollRepository:
  - Phụ thuộc vào cơ sở dữ liệu lưu trữ lương để quản lý thông tin lương của nhân viên.
### Thiết kế hệ thống con Maintain Timecard
#### 1. Distribute subsystem behavior to subsystem elements
- Employee Subsystem: Xử lý tương tác của người dùng và gửi yêu cầu
- TimeCard Subsystem: Xác minh và lưu trữ dữ liệu thẻ chấm công
- TimeCardService Subsystem: Xử lý logic nghiệp vụ và điều phối giữa nhân viên và repository
- TimecardRepository Subsystem: Quản lý lưu trữ và truy xuất dữ liệu từ cơ sở dữ liệu.
#### 2. Document subsystem elements
- Employee:
  - Gửi yêu cầu thêm hoặc chỉnh sửa thẻ chấm công
  - Nhận phản hồi
- Timecard:
  - Lưu trữ thông tin thời gian làm việc.
  - Cung cấp phương thức validate() để đảm bảo tính hợp lệ của dữ liệu.
- TimecardService:
  - Xử lý logic nghiệp vụ liên quan đến thêm và chỉnh sửa thẻ chấm công.
  - Gọi repository để thao tác dữ liệu.
- TimecardRepository:
  - Cung cấp các phương thức (save(), findByEmployee()) để tương tác với cơ sở dữ liệu.
#### 3. Describe Subsystem Dependencies
### Thiết kế hệ thông con Login
