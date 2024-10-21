## Báo cáo phân tích kiến trúc và ca sử dụng hệ thống "Paroll System"

### 1. Phân tích kiến trúc

#### 1.1. Đề xuất kiến trúc

- **Kiến trúc đa tầng (N-tier) kết hợp với kiến trúc hướng dịch vụ (SOA)**

#### 1.2. Lý do lựa chọn

- **Kiến trúc đa tầng (N-tier)** giúp hệ thống được phân tách thành các tầng khác nhau như Presentation Layer, Service Layer, Data Layer và Security Layer. Điều này giúp hệ thống dễ bảo trì và quản lý
- **Kiến trúc hướng dịch vụ (SOA)** Bằng cách chia nhỏ các chức năng thành các dịch vụ độc lập, các module có thể dễ dàng mở rộng hoặc thay đổi mà không ảnh hưởng đến toàn bộ hệ thống.

#### 1.3. Ý nghĩa thành phần trong kiến trúc

- **Tầng trình bày (Presentation Layer)**: Đây là tầng giao diện dành cho nhân viên và quản trị viên. Giao diện người dùng được triển khai dưới dạn deskop giúp thuận tiện cho nhân viên và quản lý trong việc truy cập, nhập dữ liệu
- **Tầng dịch vụ (Service Layer)**: Xử lý các nghiệp vụ quan trọng như tính lương, thanh toán, chấm công
- **Tầng dữ liệu (Data Layer)**: Lưu trữ và truy xuất thông tin liên quan đến nhân viên, timecard. Đảm bảo việc tương tác cơ sở dữ liệu như DB2 và Payroll Database mà không cần thay đổi các hệ thống
- **Tầng bảo mật (Security Layer)**: Đảm bảo hệ thống chỉ cho phép người được ủy quyền truy cập vào các chức năng tương tự

  #### 1.4. Biểu đồ package mô tả kiến trúc
  ![Diagram](https://www.planttext.com/api/plantuml/png/b5GzIyD06DxpArwwg4CH71saj84gbg8IY-kHXjnXUWdv48euEJY8e8E3OvKkGh3WraCSJle_xXVu5xnhwSSbLr4e1Evvdu_tWtwpprgIeZZDUe4L8VSS-HvKzWMx0GSBza1zE4BzE0o22bnQ0FAtg6hoTm9DWaAmYIHGs3mzs9gL0RW1If8fQXEFjZ6Y7VarGCSPeavC979bbTJF1CkXnJ-WxMFb4K57iA7kOGjswsBrtiRyMThmLsg47PvJt9gC9WFgcmj8ptDHt3M3iWNiX7n0pL6TEEj3GuppI97UeANoPdhKGnmgR0OPt7HyrT1OeVLhYiHp5uDSvakavwWBzjJ0ML-mQ_frBzWZiUixSuqDEF42b9AG9fX4YNmfRX6grJt3s60N4hMlhdoRJhYmuW9jcRv4DEzilQqls1tvCsynr_yojSHbvWgiUCOXIsAg3iLLXwBxpjjHNEEXI6um6MNRKu4BCHvINM3PLrbYjUVVH0ezh3ateuWbhwVcqQxw9_a1003__mC0)

  ### 2. Cơ chế phân tích
