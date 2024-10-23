## Báo cáo phân tích kiến trúc và ca sử dụng hệ thống "Paroll System"

### 1 Phân tích kiến trúc

#### 1.1 Đề xuất kiến trúc

- **Kiến trúc đa tầng (N-tier) kết hợp với kiến trúc hướng dịch vụ (SOA)**

#### 1.2 Lý do lựa chọn

- **Kiến trúc đa tầng (N-tier)** giúp hệ thống được phân tách thành các tầng khác nhau như Presentation Layer, Service Layer, Data Layer và Security Layer. Điều này giúp hệ thống dễ bảo trì và quản lý
- **Kiến trúc hướng dịch vụ (SOA)** Bằng cách chia nhỏ các chức năng thành các dịch vụ độc lập, các module có thể dễ dàng mở rộng hoặc thay đổi mà không ảnh hưởng đến toàn bộ hệ thống.

#### 1.3 Ý nghĩa thành phần trong kiến trúc

- **Tầng trình bày (Presentation Layer)**: Đây là tầng giao diện dành cho nhân viên và quản trị viên. Giao diện người dùng được triển khai dưới dạn deskop giúp thuận tiện cho nhân viên và quản lý trong việc truy cập, nhập dữ liệu
- **Tầng dịch vụ (Service Layer)**: Xử lý các nghiệp vụ quan trọng như tính lương, thanh toán, chấm công
- **Tầng dữ liệu (Data Layer)**: Lưu trữ và truy xuất thông tin liên quan đến nhân viên, timecard. Đảm bảo việc tương tác cơ sở dữ liệu như DB2 và Payroll Database mà không cần thay đổi các hệ thống
- **Tầng bảo mật (Security Layer)**: Đảm bảo hệ thống chỉ cho phép người được ủy quyền truy cập vào các chức năng tương tự

  #### 1.4 Biểu đồ package mô tả kiến trúc
  ![Diagram](https://www.planttext.com/api/plantuml/png/b5GzIyD06DxpArwwg4CH71saj84gbg8IY-kHXjnXUWdv48euEJY8e8E3OvKkGh3WraCSJle_xXVu5xnhwSSbLr4e1Evvdu_tWtwpprgIeZZDUe4L8VSS-HvKzWMx0GSBza1zE4BzE0o22bnQ0FAtg6hoTm9DWaAmYIHGs3mzs9gL0RW1If8fQXEFjZ6Y7VarGCSPeavC979bbTJF1CkXnJ-WxMFb4K57iA7kOGjswsBrtiRyMThmLsg47PvJt9gC9WFgcmj8ptDHt3M3iWNiX7n0pL6TEEj3GuppI97UeANoPdhKGnmgR0OPt7HyrT1OeVLhYiHp5uDSvakavwWBzjJ0ML-mQ_frBzWZiUixSuqDEF42b9AG9fX4YNmfRX6grJt3s60N4hMlhdoRJhYmuW9jcRv4DEzilQqls1tvCsynr_yojSHbvWgiUCOXIsAg3iLLXwBxpjjHNEEXI6um6MNRKu4BCHvINM3PLrbYjUVVH0ezh3ateuWbhwVcqQxw9_a1003__mC0)

  ### 2 Cơ chế phân tích
#### 2.1 Cơ chế tính lương tự động
- Tự động tính toán và xử lý thanh toán vào các ngày định sẵn
- Tính thêm lương cho giờ làm thêm và hoa hồng cho nhân viên bán hàng
#### 2.2 Cơ chế bảo mật
- Đảm bảo nhân viên chỉ có quyền truy cập và chỉnh sửa thông tin cá nhân
- Payroll Adminnistrator có quyền quản lý và cập nhật thông tin của toàn bộ nhân viên
#### 2.3 Cơ chế tích hợp với hệ thống DB2
- Hệ thống phải tích hợp với cớ sở dữ liệu cũ DB2 mà không làm thay đổi hoặc cập nhật dữ liệu trong DB2. Cơ chế này đảm bảo khả năng truy xuất thông tin dự án
#### 2.4 Cơ chế quản lý thông tin nhân viên
- Payroll Administrator có quyền thêm, xóa, sửa thông tin nhân viên
  ### 3. Phân tích ca sử dụng Payment
#### 3.1 Xác định các lớp phân tích cho ca sử dụng Payment
  Lớp NhanaViene (Employee): Lớp này đại diện cho mối nhân viên trong hệ thống và bao gồm câc thông tin cơ bản
  
**Thuộc tính**:

    - maNhanVien: Mã nhân viên
    - tenNhanVien: Tên nhân viên
    - phuongThucThanhToan: Phương thức thanh toán (chuyển khoản, bưu điện)
    - loaiNhanVien: Loại nhân viên
    - ngayTraLuongCuoi: Ngày nhận lương lần cuối
    - ngayGiaNhap: Ngày gia nhập công ty

**Phương Thức**:

    - layLoaiNhanVien(): Trả về loại nhân viên.
    - capNhatThongTin(): Cập nhật thông tin cá nhân và phương thức thanh toán

  Lớp ThanhToan (Payment): Lớp này đại diện cho mỗi khoản thanh toán thực hiện cho nhân viên
  
**Thuộc Tính**:

    - ngayThanhToan: Ngày thực hiện thanh toán
    - soTien: Số tiền thanh toán
    - phuongThucThanhToan: Phương thức thanh toán

**Phương thức**:

    - thucHienThanhToan(nhanVien: Employee): Thực hiện thanh toán cho nhân viên
    - tinhToanLuong(nhanVien: Employee): Tính toán số tiền lương dựa trên thông tin nhân viên và các thẻ chấm công

  Lớp QuanLyThanhToan(PaymentManager): Đây là lớp quản lý việc tính toán và xử lý thanh toán lương cho nhân viên

  **Thuộc tính**:
  
      - danhSachNhanVien: Danh sách các nhân viên cần được thanh toán

  **Phương thức**

      - tinhToanLuongHangTuan(): Tính toán lương cho nhân viên làm theo giờ, dựa trên thẻ chấm công
      - tinhToanLuongHangThang(): Tính toán lương cho nhân viên cố định và có hoa hồng dựa trên thẻ chấm công và đơn hàng
      - thucHienTatCaThanhToan(): Thực hiện thanh toán cho tất cả nhân viên vào các ngày lương

  Lớp TheChamCong (TimeCard): Lớp này đại deịn cho thông tin về số giờ làm việc mà nhân viên đã nhập vào hệ thống

  **Thuộc tính**:

       - ngayLamViec: Ngày làm việc
       - soGioLam: Số giờ làm việc của nhân viên trong ngày
       - maDuAn: Mã dự án mà nhân viên đã làm

  **Phương thức:

       - layThongTinGioLam: Trả về số giờ làm việc của nhân viên trong một khoảng thời gian
       - layMaDuAn: Trả về mã dự án liên quan đến thẻ chấm công

  Lớp DonHang (SalesOrder): Lớp này cho nhân viên có hoa hồng. Nó lưu trữ thông tin về các đơn hàng
  
  **Thuộc tính**:

       - ngayDatHang: Ngày mà đơn hàng được thực hiện 
       - soTienDonHang: Tổng giá trị của đơn hàng
       - hoaHong: Tỷ lệ hoa hồng mà nhân viên được nhận

  **Phương thức**:

       - layThongTinDonHang(): Trả về thông tin của đơn hàng

  Lớp DuLieuThanhToan (PaymentData): Lớp này chịu trách nhiệm lưu trữ và truy xuất thông tin thanh toán từ cơ sở dữ liệu

  **Phương thức**:

       - luuThongTinThanhToan(payment: Payment): Lưu thông tin về một lần thanh toán đã được thực hiện
       - luuThongTinThanhToan(maNhanVien: String): Truy xuất thông tin thanh toán của một nhân viên cụ thể

  Lớp DuLieuNhanVien (EmployeeData): Lớp này quản lý việc lưu trữ và truy xuất thông tin nhân viên từ cơ sở dữ liệu

  **Phương thức**: 

       - layThongTinNhanVien(maNhanVien: String): Truy xuất thông tin cá nhân và phương thức thanh toán của nhân viên
       - capNhatThongTinNhanVien(employee: Employee): Cập nhật thông tin nhân viên trong cơ sở dữ liệu

   Lớp TichHopCSDLDB2 (DB2Integration): Lớp này chịu trách nhiệm tích hợp hệ thống mới với cơ sở dữ liệu DB2 (hệ thống dự án)

   **Phương thức**

       - layThongTinDuAn(maDuAn: String): truy xuất thông tin về mã dự án từ cơ sở dữ liệu DB2 mà không thay đổi dữ liệu
#### 3.2 Biểu đồ Sequence cho ca sử dụng Select Payment
 ![Diagram](https://www.planttext.com/api/plantuml/png/X9D1ReCm54JtFiLNzhq04bMgfAgoQ5e5vG2_vZUnQcpBDaIShOiUgLTe425W6zGbrhoPOGo_tpzhvz7wkf8CkTSMLi-LaRebMW4weDi3CrUHuCAWygC4Zhj0TTo5kdTiArA-8Di8tXkQu6ZUza16Et4jqmRktJ5ZUGxt-88aSU_WbWElvC-wX3ndR83WuN5IBuCtG-gkxtcX5HJS4YasAgTS5vp1WRmLrD0OFzXioQEGZatrAVz2FaNxnX4PLRu6rrR5o4BN3BR26OajR6fhE_qI5o_JZm5xkYorwvF26ypWQ4hqoHk5gdID0fj_LeY9sHmG2hReyGCTfIl6LP_ubz8NIUKfyUdTazhHHXkjFeMjOdXpHdMYy4fcxwIeEIVd1X_ilZt6rgJAxWVy0m00__y30000)
