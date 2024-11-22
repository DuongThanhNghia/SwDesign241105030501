# Lab 4
### Thiết kế ca sử dụng Login
#### 1. Describe interaction among design object
- User: Nhập username, password và kích hoạt login()
- AuthService: Xử lý xác thực, gọi UserRepository để kiểm tra thông tin và SessionManager để tạo phiển làm việc
- SessionManager: Quản lý phiên làm việc
- UserRepository: Truy xuất thông tin người dùng từ cơ sở dữ liệu
#### 2. Simplify Sequence Diagram Using Subsystems
- Authentication Subsystem: Gồm AuthService và UserRepository
- Session Management Subsystem: Chỉ gồm SessionManager

  ![Sequence](https://www.planttext.com/api/plantuml/png/P90n3i8m34Ntd29ZaQZO6L1HLrX07C1gh18fJP3jWZWR0qVY2ZW58TfEYUB__Eoy7i-A1KZwBXXe994zCPB1A5xkm_s0byHUAtVJf2YKWjtsSZuYNNs3lxSZCliKzn2XrGOcexRS_6VjseRK-bZqMelGuT9UWFcMo2tCVqwniLd9AmJlGB0cT7aw25mip2HMpeHPPOi1Nlaud3FNU7I56a8rVP_LCWdCBVm9r0Fdnls_osXgbvUtXDm7CHL6bp_z3G00__y30000)
#### 3. Describe persistence-related behavior
- UserRepository truy vấn thông tin qua findUserByUsername()
- Bảo mật mật khẩu với mã hóa (e.g, bcrypt)
#### 4. Refine the flow of events description
Luồng cơ bản:
- Người dùng nhập username và password
- Hệ thống gọi AuthService.login().
- AuthService xác thực thông tin qua UserRepository.
- Nếu hợp lệ, SessionManager tạo phiên làm việc.
- Trả kết quả đăng nhập thành công.
Luồng ngoại lệ:
- Sai thông tin đăng nhập: Thông báo lỗi, yêu cầu nhập lại
- Tài khoản bị khóa: Báo lỗi "Tài khoản bị khóa"
- Lỗi hệ thống: Thông báo lỗi, yêu cầu thử lại sau
#### 5. Unify classes and subsytems
- Authentication: AuthService, UserRepository xử lý xác thực và truy cập dữ liệu người dùng
- Session Management Subsystem: Đảm bảo quản lý phiên làm việc tách biệt với logic xác thực
#### Use case diagram

![Diagram](https://www.planttext.com/api/plantuml/png/V9513e8m44NtFSM4FLSm6BUw8gpDM2T80ctIcIwCuMGkF99Ni0MAeCRk_lm_lw_fy_ueMD29xrg5Mgo3Yia1CbHAETA2fcu9igsN2nbfD4fZ3PJ-n5SMwZAuAGZ7Csda4DpRkZ7PKB0x3kBBjruMWQ3MYSLLDD2aS3IYLlqAhIJco7H0WpLrOVKFtXY2QISrZzDf6EihoFFD-mLB6NcJaSOpsQUnBfuBVjkg87EE7_42003__mC0)
### Thiết kê ca sử dụng Maintain Timecard
#### 1. Describe interaction among design object
- Employee: Gửi yêu cầu thêm/chỉnh sửa thẻ công
- Timecard: Lưu thông tin thời gian làm việc, xác minh dữ liệu qua validate()
- TimecardService: Xử lý nghiệp vụ, luu/chỉnh sửa qua TimecardRepository
- TimecardRepository: Tương tác cơ sở dữ liệu để lưu hoặc truy xuất thẻ chấm công
#### 2. Simplify Sequence Diagram Using Subsystems
- Employee gọi TimecardService.addTimecard()
- TimecardService lưu trữ dữ liệu qua TimecardRepository.save().
- Phản hòi kết quả cho Employee.

  ![Sequence](https://www.planttext.com/api/plantuml/png/RD1B2i9030RWVKunIrqKzrr8Drv0lK2OYJ0mZv9a2ZsRYnx9ApY2hQLs5txo9I6lvzI98ck90T1gPdE9VSWZ4TYSb7CmTn_98hiRyU0j0INrEYxnbVeilieHOBQcEM-PQGqwDuS7_HP7sFQjw6zqrO83xR1LJxExLOgr979we0-5wNzVLSlThM6I4XGwIkxpapS0003__mC0)
#### 3. Describe persistence-related behavior
- TimecardRepository.save(): Lưu thẻ chấm công
- TimecardRepository.findByEmployee(): Lấy danh sách thẻ theo mã nhân viên
#### 4. Refine the flow of events description
Luồng cơ bản
- Nhân viên nhập thông tin thẻ chấm công
- Gửi yêu cầu thêm hoặc chỉnh sửa thẻ chấm công đến TimecardService
- TimecardService gọi TimecardRepository để lưu hoặc cập nhật thông tin
- Kết quả được trả về cho nhân viên
Luồng ngoại lệ
- Thông tin thẻ chấm công không hợp lệ: Bảo lỗi qua Timecard.validate()
- Lỗi cơ sở dữ liệu: Thông báo lỗi và yêu cầu thử lại
#### 5. Unify classes and subsytems
- Employee: Quản lý thẻ chấm công
- Timecard: Lưu thông tin và xác minh dữ liệu
- TimecardService: Xử lý nghiệp vụ thẻ chấm công
- TimecardRepository: Lưu/truy xuất dữ liệu từ DB

#### Use case diagram

![Diagram](https://www.planttext.com/api/plantuml/png/Z99DRi9038NtSmelOP4Be0hHbgeRr4L1xAsC2vRc9vfn8aM8ax7eaNg5JiCafIXKBFriFt_spDVfSn45WzJMgD9WZF1YA-DR8ZWeW08ilktHRPaSp60jWTskquNSUC9uv1ijREaPWqxgYgCyR59SfdYUiW2eTIzCffr2ckL2EgfCs6kPqEsmJPPB5EhYw5_Phz0cW3Bfx2GligmV_n01H6me3slGi4uMOuFM51ekpnV9JT8pp8QgiqzTTIutyn_iz5FR7taoSjuHW7UgV6JneRsBuSuPmqiNnNnmKDTBNoP_EVujKmjo-kT7VGC00F__0m00)
### Thiết kê ca sử dụng Run Payroll
#### 1. Describe interaction among design object
- EmployeeSubsystem: Quản lý thông tin nhân viên.
- TimeCardSubsystem: Cung cấp dữ liệu giờ làm việc.
- SalesOrderSubsystem: Cung cấp dữ liệu đơn hàng và hoa hồng.
- PayrollService: Tính toán tổng lương và xử lý thanh toán.
- PayrollRepository: Lưu và truy xuất dữ liệu lương.
#### 2. Simplify Sequence Diagram Using Subsystems
- EmployeeSubsystem: Truy xuất thông tin nhân viên
- TimeCardSubsystem: Cung cấp dữu liệu thẻ chấm công
- SalesOrderSubsystem: Lấy thông tin đơn hàng và hoa hồng
- PayrollService: Xử lý logic tính toán và lưu thông tin lương
- PayrollRepository: Lưu và truy xuất dữ liệu lương từ DB

![Sequence](https://www.planttext.com/api/plantuml/png/R98zRiCm38LtdK9ZEWJPEnGfqiufubv0bLyB0VenI2g0pfOXH-eLgiQn4qIU2F3f8nyVz7iwRraCIGvU6Ik9z6iVN5GsHQ7azOSfjVWET7GMS_iz33uLeCjVN5WGPkNJ1UmCzQtI6G_UKm-wQOZYf4nR3XWIksgYA7MneTSl3mxqiwOShxtLar8FSWKQRvNvWKpjDuXndYlReetv4PtQlC9ro1AySD-8tuJx0GiJcXWgp-Q8wTnXhFFokuVhfQGuMmlcpNSzE1FQbHKQSwwfWhCNjKNi___27m000F__0m00)
#### 3. Describe persistence-related behavior
- PayrollRepository:
  - savePayroll(payroll): Lưu thông tin tổng lương đã tính vào cơ sở dữ liệu,
  - getPayrollByEmployee(maNhanVien): Truy xuất thông tin lương theo mã nhân viên
- Data Validations: Dữ liệu lương, thời gian làm viêc và hoa hồng phải được kiểm tra hợp lệ trước khi lưu
#### 4. Refine the flow of events description
Luồng cơ bản:
- Admin khởi động quy trình tính toán lương
- Hệ thống lấy thông tin nhân viên, thẻ chấm công và đơn hàng từ cớ sở dữ liệu
- Tính lương dựa trên giờ làm, hoa hồng và lương cơ bản
- Lưu thông tin tổng lương và cơ sở dữ liệu
- Thực hiện thanh toán lương và trả kết quả cho admin
Luồng ngoại lệ:
- Thiếu dữ liệu: Báo lỗi khi không có đủ dữ liệu
- Dữ liệu không hợp lệ: Thông báo lỗi và yêu cầu kiểm tra lại
- Lỗi hệ thống: Dừng quy trình, báo lỗi và ghi log để xử lý
#### 5. Unify classes and subsytems
Classes
- Employee: Quản lý thông tin cá nhân và lương cơ bản
- TimeCard: Lưu thông tin giờ làm việc
- SalesOrder: Lưu thông tin hoa hồng
- Payroll: Tính toán tổng lương và thực hiện thanh toán
- PayrollService: Xử lý toàn bộ quy trình tính toán và thanh toán
- payrollRepository: Lưu và truy xuất thông tin lương từ cơ sở dữ liệu
Subsystems
- Payroll Processing: Xử lý nghiệp vụ tính lương
- Database Management: Lưu và quản lý thông tin lương
#### Use case diagram

![Diagram](https://www.planttext.com/api/plantuml/png/V599JiD04Bpx5QsSuE0FS41HOaGEOH69uDoCMyueCztHB14Moiiuy2I-mDZ4jk80SvigTLNrylNnEVK1NOZMP3jKMwm89ezOEp46xf3JtnA72Rnd0CgWzt1ZTqPgeXO2oC7Y_GRvMHF35Qo2qrmTcK3y5sMYS3MN6JPCAV7LKCi0L1HIWCQre83Q-8lBn1ooFi1QMvgZA_i0N66zH9jiL18hCD2Hy7Ah9J49rHm6_OL4vr_4RQaSYw_Ga7zm9RbUtiiwDL08Bv2hqxGvR0GNCePRaxbOgxtNmcEFRhwTGKW2o_YBYaAZeadz72jQeURH6wbu2f_hhyZjjUhs1E0Y_r_mH3lnEeYh-ngF-pFpdmKrqApkZc5Gx9hBy-l-L4Pmjy0HF8n-8BeU6luiPNR8fiHbSxlV0000__y30000)
