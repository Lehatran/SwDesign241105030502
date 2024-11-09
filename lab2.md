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
   - **PayrollAdministrator**:
       - Phương thức:
          - requestCreateReport(): Phương thức này được gọi khi quản trị viên bảng lương yêu cầu hệ thống tạo một báo cáo. Đây là bước đầu tiên trong quá trình tạo báo cáo.
          - provideReportCriteria(): Quản trị viên cung cấp các thông tin cần thiết cho báo cáo như loại báo cáo (tổng số giờ làm việc hoặc lương năm nay), ngày bắt đầu và kết thúc, và tên nhân viên.
          - requestSaveReport(): Phương thức này được gọi khi quản trị viên yêu cầu hệ thống lưu báo cáo đã tạo.
          - provideReportNameAndLocation(): Quản trị viên cung cấp tên và vị trí lưu báo cáo trong hệ thống.
   - **PayrollReportForm**:
       - Phương thức:
          - requestReportCriteria(): Phương thức này yêu cầu quản trị viên cung cấp các tiêu chí cần thiết để tạo báo cáo (loại báo cáo, ngày bắt đầu và kết thúc, tên nhân viên).
          - passCriteriaToController(): Sau khi quản trị viên cung cấp thông tin, phương thức này chuyển các tiêu chí đó đến PayrollReportController để xử lý.
          - displayReport(): Phương thức này hiển thị báo cáo đã được tạo trên giao diện người dùng.
          - requestReportNameAndLocation(): Phương thức này yêu cầu quản trị viên cung cấp tên và vị trí để lưu báo cáo.
          - confirmReportSaved(): Sau khi báo cáo được lưu thành công, phương thức này xác nhận với quản trị viên rằng báo cáo đã được lưu.
          - discardReport(): Nếu báo cáo không được lưu, phương thức này hủy bỏ báo cáo và không lưu vào cơ sở dữ liệu.
   - **PayrollReportController**:
       - Phương thức:
          - retrieveEmployeeData(): Phương thức này chịu trách nhiệm lấy dữ liệu về nhân viên từ hệ thống. Dữ liệu này sẽ được sử dụng để tạo báo cáo.
          - createReport(): Phương thức này tạo ra báo cáo dựa trên các tiêu chí đã được cung cấp (loại báo cáo, khoảng thời gian, nhân viên). Sau khi tạo xong, báo cáo sẽ được trả lại cho PayrollReportForm để hiển thị.
   - **Report**:
       - Phương thức:
          -  generateReport(): Phương thức này thực hiện việc tạo ra nội dung báo cáo dựa trên các tiêu chí được cung cấp (ví dụ: tổng số giờ làm việc hoặc lương năm nay).
          -  setReportData(): Phương thức này lưu trữ dữ liệu của báo cáo vào đối tượng báo cáo. Dữ liệu này có thể bao gồm thông tin về nhân viên, tổng số giờ làm việc, hoặc lương trong năm.
   - **Employee**:
       - Phương thức:
          - getEmployeeData(): Phương thức này lấy thông tin của nhân viên, như tên, số giờ làm việc, và các thông tin liên quan khác cần thiết cho báo cáo.
   - **ReportDao**:
       - Phương thức:
          - saveReport(): Phương thức này lưu báo cáo vào cơ sở dữ liệu. Nếu báo cáo được yêu cầu lưu, dữ liệu báo cáo sẽ được ghi vào một nơi lưu trữ như cơ sở dữ liệu.
          - getReportData(): Phương thức này truy xuất dữ liệu báo cáo từ cơ sở dữ liệu nếu cần thiết.
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
