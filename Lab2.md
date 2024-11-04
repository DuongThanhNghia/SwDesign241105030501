# Lab 2
## I. Phân tích các ca sử dụng còn lại
### 1. Phân tích ca sử dụng Create Employee 
### 2. Phân tích ca sử dụng Maintain Puschase Order
### 3. Phân tích ca sử dụng Login
### 4. Phân tích ca sử dụng Create AdminiStrative Report
#### 4.1 Xác định các lớp phân tích cho ca sử dụng
##### Các lớp phân tích chính
PayrollAdministrator: Là người tương tác với hệ thống để tạo và lưu báo cáo hành chính, Payroll Administrator tạo cáo
**Phương thức**: 

    - requestReport(criteria: ReportCriteria): Phương thức để Payroll Administrator yêu cầu tạo báo cáo theo các tiêu chí cụ thể
    - saveReport(report: Report, fileName: String, location: String): Phương thức để Payroll Administrator lưu báo cáo vào vị trí chỉ định nếu muốn
    
#### 5. Phân tích ca sử dụng Maintain Employee Infomation
#### 6. Phân tích ca sử dụng Run Payroll
