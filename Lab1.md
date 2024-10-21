# 1.Phân tích kiến trúc
##### Phân tích hệ thống: 
###### Payroll System có một số chức năng chính:
- Quản lý timecard:
  * Nhân viên phải có khả năng ghi lại số giờ làm việc hàng ngày, bao gồm cả làm thêm giờ
  * Các timecard được tính toán để xác định tiền lương, với mức lương làm thêm giờ nếu vượt quá 8 giờ/ngày cho nhân viên làm theo giờ
- Quản lý thanh toán:
  * Hệ thống phải tự động tính toán và thanh toán lương theo từng phương thức khác: lương theo giờ, lương cố định và lương hoa hồng
  * Hệ thống cần thực hiện một cách tự động và các ngày định sẵn
- Báo cáo và quản lý cá nhân
  * Nhân viên có thể xem báo cáo về tổng số giờ làm việc, lương nhân được, số giờ tính theo dự án và thời gian nghỉ phép
  * Nhân viên cũng có thể tùy chọn phương thức thang toán
- Tích hợp với hệ thống hiện có:
  * Hệ thống phải truy cập cơ sở dữ liệu DB2 để lấy thông tin về charge number và dự án mà không được thay đổi
- Bảo mật và quyền truy cập
  * Nhân viên chỉ có thể truy cập và chỉnh sửa thông tin cá nhân như timecard và purchase order của họ, đảm bảo quyền riêng tư và bảo mật
- Quản lý hành chính
  * Payroll Adminnistration phải có khả năng thêm, xóa, sửa thông tin nhân viên, cũng như quản lý thông tin về lương, báo cáo hành chính
###### Phân tích kiến trúc hệ thống:
- Lớp người dùng (User Interface Layer):
  * Ứng dụng sẽ cung cấp giao diện desktop Windown để nhân viên có thể nhập thông tin timecard, tạo đơn hàng (purchase order), chọn phương thức thanh toán và xem báo cáo
  * Giao diện cần phải đảm bảo tính báo mật và thân thiện
- Lớp dịch vụ (Business Logic Layer):
  * Phần lõi của hệ thống, nơi thực hiện các chức năng tính toán phức tạp, bao gồm:
    * Tính toán lương: Lương được tính tự động dựa trên timecard, lương cố định và hoa hồng. Điều này bao gồm tính lương cho nhân viên làm thêm giờ và nhân viên hưởng hoa hồng
    * Thanh toán tự động: Lương của nhân viên sẽ được tính toán và trả lương đúng ngày
    * Quản lý quyền truy cập: Phân quyền để đảm bảo mỗi nhân viên chỉ có thể truy cập và chỉnh sửa dữ liệu của mình
    * Báo cáo: Tổng hợp dữ liệu và trả về các báo cáo về số giờ làm việc, lương nhận được
- Lớp dữ liệu (Data Layer):
  * Quản lý việc truy cập, lấy dự liệu từ cơ sở dữ liệu:
    * Cơ sở dữ liệu Payroll: Lưu trữ thông tin về nhân viên, timecards, lương và purchase order
    * Cơ sở dữ liệu: Chứa thông tin về các dự án charge numbers. Payroll System sẽ chỉ được phép đọc dữ liệu từ hệ thống này
  * Cần có cơ chế bảo mật để tránh truy cập trái phép vào cơ sở dữ liệu và đảm bảo an toàn dữ liệu
- Yêu cầu về tích hợp:
  * Tích hợp với DB2 hiện có: Payroll System mới cần tương tác với cơ sở dữ liệu DB2 để lấy thông tin về các charge numbers và dự án. Việc tích hợp phải được thực hiện một cách an toàn và không làm thay đổi bất kkyf dữ liệu nào trong hệ thống DB2 hiện có
- Tính tự đống hóa:
  * Hệ thống cần có cơ chế tự động thanh toán lương dựa trên các mốc thời gian cố định. Điều này yêu cầu việc lập lịch chạy các quy trình thanh toán mà không cần sự can thiệp thủ công.
- Bảo mật và quyền riêng tư
  * Mỗi nhân viên chỉ có thể quyền truy cập và chỉnh sửa dữ liệu cá nhân. Điều này đòi hỏi hệ thống phải có cơ chế quản lý quyền truy cập dựa trên vai trò người dùng. Payroll Administrator cần có quyền cao hơn để quản lý toàn bộ hệ thống
###### Đề xuất kiến trúc:
Kiến trúc phù hợp cho Payroll System là kiến trúc đa tầng (N-Tier) kết hợp với kiến trúc hướng dịch vụ (SOA) để đảm bảo tính linh hoạt và dễ bảo trì
##### Lý do lựa chọn:
- Tầng trình bày (Presentation Layer): Được triển khai dưới dạng giao diện người dùng trên desktop, giúp nhân viên thông tin thẻ chấm công, đơn hàng và truy vấn báo cáo.
- Tầng dịch vụ (Service Layer): Xử lý logic nghiệp vụ liên quan đến việc tính toán lương, xử lý thẻ chấm công, đơn hnagf và quản lý thanh toán. Các dịch vụ này có thể được chia nhỏ theo chức năng
- Tầng dữ liệu (Data Layer): Tích hợp với hệ thống cơ sở dữ liệu DB2 để truy xuất thông tin dự án và các cơ sở dữ liệu quản lý nhân viên
- Tầng bảo mật (Security Layer): Đảm bảo chỉ những người được ủy quyền mới có thể truy cập và chỉnh sửa thông tin nhạy cảm
##### Ý nghĩa từng thành phần: 
- Presentation Layer: Cung cấp giao diện trực quan, dễ sử dụng, giúp nhân viên nhập dữ liệu và quản trị viên thực hiện các báo cáo
- Service Layer: Đảm bảo tách biệt logic nghiệp vụ khỏi tầng giao diện, giúp hệ thống dễ bảo trì và nâng cấp
- Data Layer: Đảm bảo việc lưu trữ dữ liệu an toàn và hiệu quả, đặc biệt sau khi tịch hợp với hệ thống cũ
- Security Layer: Cung cấp các cơ chế bảo mật dữ liệu, bảo vệ hệ thống khỏi truy cập trái phép
##### Biểu đồ Package mô tả kiến trúc
![Package](https://www.planttext.com/api/plantuml/png/T95DJiCm44RtFiMe-svw0DG_X2gng5HOHLuCpgYCYErgFAaKK4_6WYDnXIPj874HIp-FtlTv_FtvDK-AehMlp07T6-u99bkXH45HEGPun8Pa0Xy6eBZtXoesHF3mlB4TM9IU0oSLr2XNUZA3Q4ToP4UPOukDR-NzrSNon9uSIZbcFr5ZjehUSqfjgrywJbkZOXQrNivW4vJsSdcAxUCbLXLqmo-OwBQmguMroJIBMb_Rnkm6IuUYy7jFMaNnTsaMfjCxAB8bM7DpliuCrVyPo8jPCwTGTdzs1W00__y30000)
