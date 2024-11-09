# Lab 02
## I. Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
  ### 1. Create Administrative Report
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
  ![Diagram](https://www.planttext.com/api/plantuml/png/d9DDJiD038NtEONLTRa02rJKmhg24vYC4ICbu-1nAkLiB3WILy0pwIGDLBGYYsH-lZT-Vac-FZutKL6qRviAQsM1FGx2JNFlMXzyL45Rh3f3VEqx30gh8_547Oi-ihGhm0Xfy0UtvQ1fHfBfURhKZ716nk5o-w7j6Xw8Cb0cvqxO8MV6dbLrhYMukSkMuTOAlVSK5PIX5a8baB5qtZVkh7xMZJJeqD4QdEdZ6Z0ueAC_2DXIlEHYBtpmhjGs9rv9F4ucviGIZ35EI39-akS9QB8IKlQhukb0ip4pYp_uCJwZjwTHm0j6Si1XzhMKJL5gBs5AXA6FvkZw_2EQFNtxvnj8EUVa6wvHFOThC_yjB8Nj-p7kUMbhp2rjBOcvxGIao2urO26-UYEEojI-gofijBo7m6KLxBhGpix76iMLy2ZOMHkxfv_x6m00__y30000)
  #### 1.4 Biểu đồ lớp
  ![Diagram](https://www.planttext.com/api/plantuml/png/V5D1JiCm4Bpx5LPFSEW7ScgLmWaX17nW5M-BfTWRrjkW2F4o3Zo9Bv34Jj8cBTVTcTdP7Vlt-sSJ15YEhbH52I7erHCqJ6MvDSvw6uH1Y5VwKscj6T-F62Hd1C5dh8ZbvhPhL4orDQcKinLa2x6LE2zGNsSyWiEjDmzKW5ZoBU9BpUn4u3snE_ToQMJL4eVAA-NafLD0ZbrZGrL2SshcJ6jffaKKvFUMNKHqkvXHh00sezWLtvE7qRsmnHhlN5LIWxW3IUQBy-DEWh6K-0VqoBCG0gODajX47QQCP9dDdK_P0ILicELsM0wvz63qUdqnkanRt-O2XGJzOULDBJ1BvkdniZvS3EsPOhvQI5r1zqhJwjbuzA1DQrxlcTo_tE7YMGebg5WvQVQ7MYobDkXDzwN-0000__y30000)
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
