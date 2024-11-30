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

![Subsytem](https://www.planttext.com/api/plantuml/png/V5HBJiCm5Dpx55OtmA8No09LK1OiAb331LwTHsNXn97jH8fGJyQ28t45yh7T1B-GJIBFJEPbtYW_Nzyxwy2ufbJCIQUGvyt9TjPXoVTOOrLW9IHQ_guDFpOLVuNEQAKOgq5ym1dvvgcibUuGet33FnddGe6rF057RBZEw09uY_xXkRZBegJdNTXbPlGcItm4Kv162JWt2k3IA9mcHZaej2-cG4DQ4V3SR8Jtu63f5eyJEnzfZgQL0kTEIoIQ252YKU3GuqkZiA69Qw6Dj7gwzvnMo_IpFUs8jRRIQTCHerp1ECs_3ZuJZpzqzCgl8uyJtIogn_waiDtU4xNArWf5oTEoP6ireUHK0RBLrLDlIDFCo1nPIXpaWyK9BFQg0rJ3yZnlH5YQ3YqAl4cLXaAh0czIKLdGkf4vYTYkt-xmos6_0000__y30000)
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
- Employee Subsystem:
  - Subsystem Employee sẽ gửi yêu cầu thêm mới hoặc chỉnh sửa thẻ chấm công đến Subsystem TimeCardService
  - Sau khi xử lý yêu cầu, TimecardService sẽ gửi phản hồi (success/failure) trở lại cho Employee.
- TimecardService Subsystem:
  - TimecardService sử dụng đối tượng Timecard để thực hiện các thao tác nghiệp vụ như thêm mới, chỉnh sửa hoặc xác thực dữ liệu thẻ chấm công.
  - TimecardService gọi phương thức validate() của Timecard để đảm bảo dữ liệu hợp lệ trước khi lưu trữ.
- TimecardService Subsystem:
  - TimecardService phụ thuộc vào TimecardRepository để lưu trữ hoặc truy xuất dữ liệu từ cơ sở dữ liệu.
  - Các phương thức như save() hoặc findByEmployee() của TimecardRepository được sử dụng để thực hiện các thao tác CRUD (Create, Read, Update, Delete) với dữ liệu thẻ chấm công
- TimecardRepository Subsystem:
  - TimecardRepository tương tác trực tiếp với cơ sở dữ liệu để lưu trữ hoặc truy xuất thông tin thẻ chấm công.
  - Dữ liệu được lưu trữ trong cơ sở dữ liệu ở dạng bảng hoặc các cấu trúc dữ liệu tương tự

![Subsystem](https://www.planttext.com/api/plantuml/png/b5DTQiCm37xtAKnVri5wWJ9ADzg7mSgWxGMKM2rcZfrPQY2CdcmFEzAkC7l4cTS_ka0WMFh-9EVhutDA39vtbH6isQ1SxGfgYR6ICwpHAhIbHf8Rv-K2jENmohMki0IlXAYXV8Kjoi6ygerhCSCFvBkGiZH09FjgF8gFnxST4ZyezUBdIdDY77BtCGE6sx5S8jNE4WRONkmplGGuhTTNaru3HYjW70REmZc3OBlA5dc68PMXM5jdycSrL-WRNPw9UjYK7C1HLEo6ygJkv7zZBx5sfDdvzhABh2yP8MYm7tFGQfnMNMcZhNfiqx8oWw7jMHFV9zf9CdRpvvQ8Vi-ZqUHe4kChjouEWJbPOFdTvSNEBFhu8FJrkFCJ4IVw8qsCK035k0kmSMczzPzB9QPXNF5t-mO00F__0m00)
### Thiết kế hệ thông con Login
#### 1. Distribute subsystem behavior to subsystem elements
- Authentication Subsystem:
  - AuthService:
    - Xử lý logic xác thực người dùng
    - Gọi UserRepository để truy vấn thông tin người dùng từ cơ sở dữ liệu
    - Kiểm tra thông tin username và password (so sánh mật khẩu đã mã hóa).
  - UserRepository:
    - Quản lý việc truy xuất dữ liệu người dùng từ cơ sở dữ liệu.
    - Cung cấp phương thức findUserByUsername() để lấy thông tin người dùng dựa trên username.
- Session Management Subsystem:
  - SessionManager:
    - Tạo phiên làm việc cho người dùng sau khi xác thực thành công.
    - Quản lý thông tin phiên (session), bao gồm việc lưu trữ hoặc hủy bỏ phiên khi cần thiết.
#### 2. Document subsystem elements
- Authentication Subsystem:
  - AuthService:
     - Xử lý logic đăng nhập người dùng
     - Gọi UserRepository để lấy thông tin người dùng.
     - Xác thực mật khẩu (so sánh mật khẩu đã mã hóa).
     - Gọi SessionManager để tạo phiên làm việc khi đăng nhập thành công.
  - UserRepository:
     - Truy xuất thông tin người dùng từ cơ sở dữ liệu.
- Session Management Subsystem:
  - SessionManager:
     - Tạo và quản lý phiên làm việc của người dùng.
     - Lưu trữ thông tin phiên làm việc (session token, thời gian hết hạn, thông tin người dùng...).
#### 3. Describe Subsystem Dependencies
- User:
  - Người dùng tương tác với hệ thống thông qua giao diện người dùng (UI) để gửi yêu cầu đăng nhập (username và password).
  - AuthService xử lý logic xác thực.
- AuthService:
  - AuthService gọi UserRepository để truy vấn thông tin người dùng từ cơ sở dữ liệu.
  - Phụ thuộc vào phương thức findUserByUsername() để tìm kiếm người dùng.
- AuthService:
  - Sau khi xác thực thành công, AuthService gọi SessionManager để tạo phiên làm việc mới.
- UserRepository:
  - UserRepository phụ thuộc vào cơ sở dữ liệu để truy vấn thông tin người dùng.

![Subsystem](https://www.planttext.com/api/plantuml/png/Z5D1Ri8m4Bpx5Iik1Qda0JbKjE9GfFPGA0zOaWMi9dRaTQXGnSjww9FwXNf9GaAWLNE9l3ixCvbrlZ-_9kpH-JBFbDS-8rYKAzwpfnocL919oIIQ6DRMmPFTQADKWSaRRWW6IoO7C-F9hJ4X62vdem5yA80aGsOujkKeJoQpmpAK3EPq2qL0l5kNZcAO4nVMC0NaGHqw_FUbtvBnEa6lhMcTTKK4io2tqy50euNj7Fr3yipmd0hBsbktFz6jjKcbzR1Vrbmdqa0bjGld2s8MoyzemZaFPgwxht4Lh0qhSHIirysZM12gZpL4cnrcEkt0k7hFvFjsLgSNfgReSOLC_HszuYfhmsi-BGXwfyscBZVXFI9lUoqRqdP2908nH57KID-StI5rl13ZyTtPqkBVhuRgucIkjw3upzLSJFV2Zg_5h7eIZMgLKGml9OMgG25aZwh7AV0cPf2Oh2Ee5rCDg4d8G_ws7m000F__0m00)
