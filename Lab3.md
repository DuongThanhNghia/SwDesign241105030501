### Lab 3. Identify design elements
#### 1. Subsystem context diagram
##### Mô tả hệ thống và Interface của hệ thống con BankSystem
- Mô tả: Hệ thống con BankSystem chịu trách nhiệm xử lý các giao dịch liên quan đến việc chuyển tiền lương trực tiếp vào tài khoản ngân hàng của nhân viên
- Interface:
  - sendDirectDepositDetails(): Gửi thông tin chi tiết về chuyển tiền trực tiếp đến hệ thống ngân hàng.
  - confirmTransaction(): Nhận xác nhận từ hệ thống ngân hàng về việc giao dịch chuyển tiền đã được thực hiện thành công
- Biểu đồ ngữ cảnh:
  ![Diagram](https://www.planttext.com/api/plantuml/png/h55B3e8m4Dtt51DNc0ZHBI64w8gTYIUefSG6Q4cd68bwCXSUoIj8GGYVhLsqqxutRzvCFwztX8PgKnKv8IodY72ajLPvVb3Is9Dhk1EmIrSIoWvqrkH9Y926wvGo3l6UoknKe-55pqvugL0OXpPwxC9PvaCVRQ39L3R51xl7CbMwe4OesUeEFbfsVvynny-_oa60rHcxkDJgLeVX7zmivx7QUjvk1QuRJXht8H6QCzCNGsZr4Qw2aZ4nUBZkoFS4iw93vtDWCOA8oyH-tHS00F__0m00)
##### Mô tả hệ thống và Interface của hệ thống con PrintService
- Mô tả: Hệ thognos con này được xử lý việc in báo cáo, phiếu lương và các tài liệu liên quan khác
- Interface
  - printPayrollReport(): In báo cáo lương
  - confirmPrint(): Nhận xác nhận từ dịch vụ in rằng báo cáo đã được in thành công
- Biểu đồ ngữ cảnh
  ![Diagram]()

##### Mô tả hệ thống và Interce của hệ thống con ProjectManagementDatabase
- Mô tả: Hệ thống con ProjectManagementDatabase là cơ sở dữ liệu cũ chứa tất cả thông tin vaeef các dự án và số hiệu cùng lúc
- Interface:
  - getProjectDetails(chảgeNumber): Lấy thông tin chi tiết về dự án dựa trên số hiệu công việc
  - sendProjectDetails(): Gửi thông tin chi tiết về dự án đến hệ thống Payroll
- Biểu đồ ngữ cảnh
  ![Diagram]()
