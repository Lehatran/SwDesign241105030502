# Lab 02
## I. Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
  ### 1. Create employee
  #### 1.1 Xác định các lớp phân tích
  - **Boundary class**:
      - **PayrollReportForm:** Quản lý giao diện người dùng, cho phép Payroll Administrator nhập thông tin về loại báo cáo, khoảng thời gian và tên nhân viên.
  - **Control class**:
      - **PayrollReportController:** Xử lý logic nghiệp vụ tạo báo cáo. Nhận yêu cầu từ người dùng, kiểm tra dữ liệu và tương tác với các lớp khác để tạo báo cáo.
  - **Entity class**:
      - **Report:** Đại diện cho báo cáo đã được tạo ra, có các thuộc tính và phương thức liên quan đến dữ liệu báo cáo (loại báo cáo, khoảng thời gian, nhân viên).
      - **Employee:** Đại diện cho nhân viên, bao gồm các thông tin cần thiết về nhân viên trong báo cáo.
  - **Data Access Object (DAO):**
      - **ReportDao:** Truy cập cơ sở dữ liệu để lưu trữ và lấy thông tin báo cáo (nếu có yêu cầu lưu báo cáo).   
  #### 1.2 Nhiệm vụ của các lóp phân tích
  - **PayrollReportForm:** Thu thập thông tin từ người dùng như loại báo cáo, khoảng thời gian và nhân viên.
  - **PayrollReportController:** Xử lý yêu cầu tạo báo cáo, kiểm tra và xác nhận dữ liệu, tạo báo cáo và yêu cầu lưu trữ nếu cần.
  - **Report:** Đại diện cho báo cáo được tạo, lưu trữ thông tin như loại báo cáo và các dữ liệu liên quan.
  - **Employee:** Cung cấp thông tin về nhân viên để sử dụng trong báo cáo.
  - **ReportDao:** Lưu và truy xuất báo cáo từ cơ sở dữ liệu (nếu cần lưu báo cáo).
  #### 1.3 Biểu đồ Sequence
  #### 1.4 Biểu đồ lớp
  #### 1.5 Giải thích về biểu đồ lớp
  ### 2. Maintain Purchase Order
  #### 2.1 Xác định các lớp phân tích
   - **Boundary class**:
  - **Control class**:
  - **Entity class**:
     
  #### 2.2 Nhiệm vụ của các lóp phân tích
  #### 2.3 Biểu đồ Sequence
  #### 2.4 Biểu đồ lớp
  #### 2.5 Giải thích về biểu đồ lớp
  ### 3. Create Administrative Report
  #### 3.1 Xác định các lớp phân tích
   - **Boundary class**:
  - **Control class**:
  - **Entity class**:
     
  #### 3.2 Nhiệm vụ của các lóp phân tích
  #### 3.3 Biểu đồ Sequence
  #### 3.4 Biểu đồ lớp
  #### 3.5 Giải thích về biểu đồ lớp
  ### 4. Maintaiin Employee info
  #### 4.1 Xác định các lớp phân tích
  - **Boundary class**:
  - **Control class**:
  - **Entity class**:
     
  #### 4.2 Nhiệm vụ của các lóp phân tích
  #### 4.3 Biểu đồ Sequence
  #### 4.4 Biểu đồ lớp
  #### 4.5 Giải thích về biểu đồ lớp
  ### 5. Run Payroll
  #### 5.1 Xác định các lớp phân tích
  - **Boundary class**:
  - **Control class**:
  - **Entity class**:
     
  #### 5.2 Nhiệm vụ của các lóp phân tích
  #### 5.3 Biểu đồ Sequence
  #### 5.4 Biểu đồ lớp
  #### 5.5 Giải thích về biểu đồ lớp
  ### 6. Login
  #### 6.1 Xác định các lớp phân tích
  - **Boundary class**:
  - **Control class**:
  - **Entity class**:
     
  #### 6.2 Nhiệm vụ của các lóp phân tích
  #### 6.3 Biểu đồ Sequence
  #### 6.4 Biểu đồ lớp
  #### 6.5 Giải thích về biểu đồ lớp
## II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.
