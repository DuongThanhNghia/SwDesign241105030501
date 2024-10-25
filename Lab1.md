## Báo cáo phân tích kiến trúc và ca sử dụng hệ thống "Paroll System"

### 1 Phân tích kiến trúc

#### 1.1 Đề xuất kiến trúc

- **Kiến trúc đa tầng (N-tier)**

#### 1.2 Lý do lựa chọn

- **Kiến trúc đa tầng (N-tier)** giúp hệ thống được phân tách thành các tầng khác nhau như Presentation Layer, Service Layer, Data Layer và Security Layer. Điều này giúp hệ thống dễ bảo trì và quản lý

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
 ![Sequence](https://www.planttext.com/api/plantuml/png/X9D1ReCm54JtFiLNzhq04bMgfAgoQ5e5vG2_vZUnQcpBDaIShOiUgLTe425W6zGbrhoPOGo_tpzhvz7wkf8CkTSMLi-LaRebMW4weDi3CrUHuCAWygC4Zhj0TTo5kdTiArA-8Di8tXkQu6ZUza16Et4jqmRktJ5ZUGxt-88aSU_WbWElvC-wX3ndR83WuN5IBuCtG-gkxtcX5HJS4YasAgTS5vp1WRmLrD0OFzXioQEGZatrAVz2FaNxnX4PLRu6rrR5o4BN3BR26OajR6fhE_qI5o_JZm5xkYorwvF26ypWQ4hqoHk5gdID0fj_LeY9sHmG2hReyGCTfIl6LP_ubz8NIUKfyUdTazhHHXkjFeMjOdXpHdMYy4fcxwIeEIVd1X_ilZt6rgJAxWVy0m00__y30000)

 #### 3.3 Nhiệm vụ của các lớp phân tích
  - Lớp NhanVien (Employee): Lớp này lưu trữ và quản lý thông tin cá nhân của nhân viên, bao gồm loại nhân viên và phương thức thanh toán
  - Lớp ThanhToan (Payment): Quản lý quá trình thanh toán, bao gồm việc tính toán lương và thực hiện thanh toán cho nhân viên dựa trên thông tin từ các lớp khác như TheChamCong và DonHang
  - Lớp QuanLyThanhToan (PaymentManager): Điều phối toàn bố quá trình tính lương và thanh toán cho tất cả các nhân viên
  - Lớp TheChamCong (Timecard): Lưu trữ và quản lý dữ liệu chấm công của nhân viên, bao gồm ngày làm việc và số giờ làm việc
  - Lớp DonHang (SalesOrder): Được dùng cho nhân viên nhận hoa hồng để lưu thông tin về các đơn hàng và tính toán hoa hồng dựa trên doanh số
  - Lớp DuLieuThanhToan (PaymentData): Đảm bảo lưu trữ và truy xuất thông tin thanh toán từ cơ sở dữ liệu
  - Lớp DuLieuNhanVien (EmployeeData): Quản lý và cung cấp thông tin về nhân viên từ cơ sở dữ liệu
  - Lớp TichHopCSDLDB2 (DB2Integration): Tích hợp hệ thống với cơ sở dữ liệu DB2 hiện tại để truy xuất mã dự án, đảm bảo rằng không có sự thay đổi dữ liệu DB2.

#### 3.4 Biểu đồ lớp (Class Diagram) mô tả các lớp phân tích
![ClassDiagram](https://www.planttext.com/api/plantuml/png/Z5913i8W4Bpp2eusqG_qO3peKMFKU2TqKaaeaBBLDCQNUV19Vi6qOXLCZ9nWM6PdPhbVRpDFegQcqanguJrVL4xR5k1dnlkrfLgPabTYTH1chs1Yd62IYxLeAnXQWWwsuExp52eyD2H5TIE3qtENnmGPkx0WBU1Rr4Sbtm8RLmX2p8RW8X_yZFaV7Lx56pZh5Tcw7RgKI0I_0yb35bb2_4FVz-E_zCNHfXFgqLth4ED2IjiOceE4qhuZ6sOycKmJoKd6NS5tA7dm5CnaZCrWYkuFFG000F__0m00)

### 4. Phân tích ca sử dụng Maintain Timecard
#### 4.1 Xác định các lớp phân tích cho ca sử dụng Maintain Timecard
##### Các lớp phân tích chính
  Employee (Nhân viên): Đại diện cho mỗi nhân viên trong hệ thống, chịu trách nhiệm quản lý và cung cấp thông tin về cá nhân và thông tin liên quan đến thẻ công

  **Thuộc tính**:

    - maNhanVien: Mã nhân viên
    - tenNhanVien: Tên nhân viên
    - loaiNhanVien: Loại nhân viên
    - timeCard: Danh sách các thẻ chấm công

  **Phương thức**

    - addTimecard(): Thêm mới thẻ chấm công
    - editTimecard(): Chỉnh sửa thẻ chấm công đã nhập

  Timecard (Thẻ chấm công): Lớp này lưu trữ thông tin thời gian làm việc của nhân viên. Mỗi thẻ chấm công có các thuộc tính về ngày, số giờ làm việc và mã dự án

  **Thuộc tính**:

    - ngay: Ngày làm việc
    - soGioLamViec: Số giờ làm việc
    - maDuAn: Mã dự án mà nhân viên đã làm việc

  **Phương thức**

    - save(): Lưu thông tin thẻ chấm công vào cơ sở dữ liệu
    - validate(): Xác minh thông tin hợp lệ

  TimecardService (Dịch vụ quản lý thẻ chấm công): Lớp dịch vụ chịu các nghiệp vụ như thêm, chỉnh sửa và lưu thẻ chấm công vào hệ thống
  
  **Phương thức**

    - save(timecard): Lưu trữ thẻ chấm công mới
    - update(timecard): Cập nhật thông tin thẻ chấm công
    - findByEmployee(maNhanVien): Lấy danh sách thẻ chấm công của nhân viên
#### 4.2 Biểu đồ Sequence cho ca sử dụng Maintain Timecard
![Sequence Maintain](https://www.planttext.com/api/plantuml/png/Z95D3e8m48NtFKMNcE05N1YC6FVY1SPsD9FGdxG5mzbSU2IlO34YX3JgTbw_zsPU7xTxuGEuqAYQWGZ6yPsojUaG6RDnJe8iwC2Ff520anMwbWGcjGDQuobwT4cPiS6QBzTpGxxYmY447EQPla2NSs_sP7Ake6msUi7crCGeEcYyyl_uz0Ojr2JZ3jdNeF7CY7XeCGjlPSGcRo9PGe0J-3w2j4SNVXA9Tem-arDLdvTSxrFkQgna-wfKiWArx7_u2G00__y30000)

#### 4.3 Nhiệm vụ của từng lớp phân tích

- Employee: Nhập và gửi yêu cầu tạo, chỉnh sửa thông tin chấm công
- Timecard: Đại dienj cho từng thẻ chấm công, lưu trữ thông tin về ngày làm viêc, số giờ và mã dự án. Nó cũng chịu trách nhiệm xác minh tính hợp lệ của thông tin
- TimecardService: Xử lý nghiệp vụ liên quan đến việc tạo mới hoặc chỉnh sửa thẻ chấm công và liên lạc với cơ sở dữ liệu thông qua TimecardRepository.
- TimecardRepository: Tương tác với cơ sở dữ liệu, chịu trách nhiệm lưu trữ hoặc truy xuất thẻ chấm công

#### 4.4 Biểu đồ Class Diagram cho ca sử dụng Maintain Timecard
![Class Maintain](https://www.planttext.com/api/plantuml/png/X9B1JiCm38RlUOgefuAw0zSAJGCDSPbss11tAp73KfjMYLkfGZmP1nw9Lw3jaXIw8dAA_Jlsbp_v-lZSE0RBJLa8LO1pyg6iYwf3b6z2Zkl8bin9bh1_1VDCQ7xd6SrCs97ZsoSgKO7LQyb-vxmCMWSnPPNB45nv7JNn7mNlmaE6L8JS0gCq9-XyJ8Qbgnwfsa7PewdvNRRDNS1jeI3T7qy3W8Ds22w67T6sf2PZbCN-M4H5RrmUBSn6edo4oyuu-K2MUO3SyuJ1JQr_DlpdxWUiAqTSsIuIZUHBdfuxBqelPFHz5v3JwPadkdvq_1N9JI9NgxLChfFOIimT6WekCHVBGcCXDcZqy0s_0G00__y30000)

### 5. Hợp nhất kết quả phân tích
#### 5.1 Tóm tắt các lớp chính
##### Các lớp phân tích được xác định qua hai ca sử dụng: 

  Emloyee: Quản lý thông tin của nhân viên, bao gồm mã nhân viên, ten, phương thức thanh toán, loại nhân viên và các thông tin liên quan.
  Timecard: Đại diện cho thông tin về số giờ làm việc của nhân viên, được sử dụng để tính toán lương
  Payment: Xử lý việc thanh toán cho nhân viên dựa trên loại nhân viên và thông tin được ghi nhận từ thẻ chấm công hoặc hoa hồng
  TiemcardService: Quản lý trình tạo, cập nhật và lưu trữ thẻ chấm công cho nhân viên
  PaymentService: Chịu trách nhiệm thực hiện các thao tác liên quan đến tính toán và thực hiện thanh toán cho nhân viên
  PurchaseOrder: Đại diện cho các đơn hàng được thực hiện bởi nhân viên nhận hoa hồng, được sử dụng để tính toán hoa hồng
  
  #### 5.2 Mối quan hệ giữa các lớp
  ###### Qua hai ca sử dụng, Chúng ta thấy rằng các lớp có mối quan hệ qua lại với nhau để hoàn thành các nhiệm vụ trong hệ thống:
  - Employee tương tác với các đối tượng khác nhau (Timecard, PurchaseOrder, Payment) để ghi nhận công việc và các giao dịch của họ.
  - PaymentService đóng vai trò trung tâm trong việc xử lý thanh toán, lấy dữ liệu từ TimecardService và PurchaseOrder để tính toán và thực hiện thanh toán cho nhân viên
  - Các Repositry đóng vai trò lưu trữ và cung cấp dữ liệu cho quá trình xử lý, đảm bảo rằng mọi thông tin đều được cập nhật và truy xuất khi cần thiết

#### 5.3 Biều đồ lớp hợp nhất
![ClassDiagram](https://www.planttext.com/api/plantuml/png/b5GxJiCm6Dvp2gjJAn6nPq150j6XF4GZTYinYQN4ZXox8a8SXe6n4WDJEp0WSO-SW2lWaDX9R4SLtUB__nx_gp-7psN98UCYppmloc1PWikyo6Y547ZsWFpvERn98Nd0Y0HWmnacIVlE4N47YbHGaeIfY48PJqCAZOICGcn1NvH-Y7CKGHOhVPB0AW0NaAFskwHNcAvXBj5H033XokQ5E7VGtS4gHuGFsGQsXhJXdvr7wQwb15oMi9AFEd--2C2MudZ0BbYKmXBTiXYneSQrW2j8aca5q-06iIsELDS1nwtakkdbdEXkgUae9nD6fm5MdmtXJ0WLSR2SI6DjCD048okPREyqVD6ZUYCgU8yAMc9EMQMzDBDgTWdhLPlRwxZe-UtgtAJAePDCExJwCLsxEKs7hEJfQkd7LBJPWO9PhRGGJiSTkd6XhzVt-qiAm2of3pkiXpSRvQaJaMaahVSx0ZfVHjfersKoh_Ul51JTCw3D-nZY6At4PT_lGkxirmT9cZsVUSO9-FxP198pKO4dKU_V-342Un1AMHVdG9b7qM2aMZNed9aoXDbgftAAHy3_AzLR8X8tVzU_0000__y30000)

#### 5.4 Hợp nhất luồng hoạt động
##### Khi hợp nhất hai ca sử dụng Select Payment và Maintain Timecard, hệ thống sẽ hoạt động theo luồng sau:
 - Nhân viên ghi nhân thời gian làm việc:
   - Nhân viên sửu dụng hệ thống để nhập thẻ chấm công (Timecard), bao gồm thông tin ngày làm việc, số giờ làm việc và mã dự án (charge number) để ghi nhận các giờ làm việc thực tế.
   - Hệ thống thông qua dịch vụ chấm công (TimecardService) để lưu thẻ chấm công vào kho thẻ chấm công (TimecardRepository). Mỗi thẻ chấm công được liên kết với mã nhân viên và lưu trữ để phục vụ tính toán lương.
 - Lưu thông tin thẻ chấm công:
   - Hệ thống gửi yêu cầu tới TimecardRepository để lưu thẻ chấm công vào cơ sở dữ liệu, đảm bảo dữ liệu được lưu trữ cho tính toán lương cũng như các báo cáo sau này.
 - Tính toán và xử lý thanh toán (Payment):
   - Vào ngày thanh toán được chỉ định, dịch vụ thanh toán (PaymentService) sẽ truy vấn thông tin từ các thẻ chấm công đã lưu vào thông tin nhân viên để thực hiện thanh toán cho từng nhân viên.
   - Đối với nhân viên làm theo giờ. hệ thống sẽ tính toán số giờ làm việc trong tuần hoặc tháng, bao gồm giờ làm thêm và mức lương tương ứng
   - Đối với nhân viên hưởng lương cố định, dịch vụ thanh toán sẽ tự động tính toán dựa trên mức lương cố định, tuy nhiên vẫn sử dụng thẻ chấm công để theo dõi các dự án làm việc và giờ làm việc thực tế.
 - Ghi nhận thông tin thanh toán:
   - Sau khi tính toán lương, PaymentService lưu trũ thông tin thanh toán vào PaymentRepository, bao gồm ngày thanh toán, số tiền và phương thức thanh toán đã chọn của nhân viên.
 - Chọn phương thức thanh toán và thực hiện thanh toán:
   - Nhân viên có thể lựa chọn các nhận lương trong hồ sơ cá nhân.
   - Hệ thống thực hiện thanh toán theo phương thức nhân viên đẫ chọn, đảm bảo quy trình thanh toán tự động và không cần can thiệp thủ công.
 - Truy vấn báo cáo cá nhân:
   - Nhân viên có thể sử dụng hệ thống để truy vấn số giờ làm việc, tổng thu nhập năm hoặc các giờ làm cho từng dự án
   - Hệ thống dữ liệu TimecardRepository và PaymentRepository để hiện thị các báo cáo
#### 5.5 Tài liệu mô tả
Qua quá trình và hợp nhất, hệ thống quản lý payroll của Acme Inc. sẽ bao gồm các chứ năng
 - Ghi nhận thời gian làm việc (Maintain Timecard): Ghi lại số giờ làm việc hàng ngày để lưu trữ trong hệ thống và tính toán lương
 - Xử lý thanh toán (Payment): Tự động tính toán và thực hiện than toán dựa trên thông tin từ thẻ chấm công và dữ liệu nhân viên, bao gồm thanh toán theo giờ, lương cố định và hoa hồng
 - Chọn phương thức thanh toán: Nhân viên chọn cách nhận lương và hệ thống thực hiện thanh toán theo phương thức đã chọn vào thời điểm quy định
 - Quản lý thông tin nhân viên: Quản trị viên thêm, sửa, xóa thông tin nhân viên và thay đổi phân loại thanh toán
 - Báo cáo cá nhân: Nhân viên xem báo cáo tổng số giờ làm, tổng lương và các khoản thanh toán đã nhận.
