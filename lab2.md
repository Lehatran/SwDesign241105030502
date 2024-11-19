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
  ![Diagram](https://www.planttext.com/api/plantuml/png/d9F1JiCm38RlUGgBytW13cXeW_C4J-0rHaHgu-6ua_fi77WaNW4dNTfjJDf43sqI_uv_Vqb_lhwNIL6qxrg7ZRB01WVXjdtoNOWXgQ0jEhVbFdgK0UuEyLVQiUWBItS7c20FNCDHBNQcMOshBKbHpbD7KOFQbgEkHCVX57dkTYqFH2LM9ywZuXOJrSmrSX7OrxbB_k7-iJY41olmsLDIK8P629L0nf8bRhgB-NFUg0OTThG0Cq9f0HWzqC4SHEmeNNEn4Tu7NskRaw0a0ISJCwGinfGcIJP-XF18Q6cLKF6h4cXFix5CxKm_uZFrwXW5PBOUECw-JjCcbDfBd8WmzCaStSu_eTdJZt-UGEPSoBVSe0QEjpB_crWBs_qntTkfhP5R3fqgvhRhTRpMW45y3wOuPERslNFOQZs7o7KLxBdIpZga1iLNU1HjhwMzyv_y2m00__y30000)
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
  ### 2. Create Employee Report
  #### 2.1 Xác định các lớp phân tích
  - **Boundary class**:
      - **EmployeeReportForm:** Quản lý giao diện và tương tác với nhân viên khi họ yêu cầu tạo báo cáo.
  - **Control class**:
      - **EmployeeReportController:** Xử lý logic nghiệp vụ cho việc tạo báo cáo nhân viên. Nhận yêu cầu từ nhân viên, xử lý thông tin, và tương tác với các lớp khác để tạo và lưu báo cáo.
  - **Entity class**:
      - **Report:** Đại diện cho báo cáo đã được tạo ra. Chứa các thuộc tính và phương thức liên quan đến dữ liệu của báo cáo.
      - **Employee:** Đại diện cho nhân viên trong hệ thống. Cung cấp các thông tin cần thiết cho báo cáo như giờ làm việc, dự án, hoặc kỳ nghỉ.
      - **ChargeNumber:** Đại diện cho mã số dự án trong hệ thống quản lý dự án. Sử dụng khi nhân viên chọn báo cáo "Total Hours Worked for a Project".
  - **Data Access Object (DAO):**
      - **ReportDao:** Quản lý việc lưu trữ và truy xuất dữ liệu báo cáo từ cơ sở dữ liệu.
      - **ProjectDatabaseDao:** Lấy danh sách các mã số dự án từ cơ sở dữ liệu quản lý dự án khi nhân viên yêu cầu báo cáo theo dự án.   
  #### 2.2 Nhiệm vụ của các lóp phân tích
  - **EmployeeReportForm:**
     - Hiển thị các tùy chọn và tiêu chí để nhân viên chọn loại báo cáo.
     - Yêu cầu nhân viên nhập thông tin về ngày bắt đầu và ngày kết thúc của báo cáo.
  - **EmployeeReportController:**
     -  Xử lý logic nghiệp vụ cho việc tạo báo cáo dựa trên loại báo cáo và các tiêu chí đã nhập.
     - Kiểm tra và điều phối việc lấy thông tin về nhân viên hoặc dự án khi cần thiết.
  - **Report:**
     - Chứa các phương thức tạo và lưu trữ thông tin báo cáo như "Total Hours Worked", "Vacation/Sick Leave", "Total Pay Year-to-Date".
  - **Employee:**
     - Cung cấp dữ liệu về thời gian làm việc, dự án tham gia, và các kỳ nghỉ của nhân viên.
  - **ChargeNumber:**
     - Lấy và cung cấp danh sách mã số dự án từ ProjectDatabaseDao khi báo cáo theo dự án được yêu cầu.
  - **ReportDao:**
     - Truy xuất và lưu dữ liệu báo cáo vào cơ sở dữ liệu khi nhân viên chọn lưu báo cáo.
  - **ProjectDatabaseDao:**
     - Lấy thông tin mã số dự án từ cơ sở dữ liệu quản lý dự án khi cần hiển thị các mã số dự án có sẵn cho nhân viên.
  #### 2.3 Biểu đồ Sequence
  ![Diagram](https://www.planttext.com/api/plantuml/png/b5HBRjH04DttAKgp0YbS06bGn0GK2HGXG69TOzTaJDhTfhizaa_0YZCW5YWI6rYm6Y-o68bx-0Iv0jLjjpyJ9u9PUEogLrslNZtxjhuvjGwDAtCfC77Qm8kyaBeY4cAjIvMYgM0HOs-fqCQzr2PV05hmDoBHoXajZq6hDYp91EZmA4YvpF6XBIvaszi-4qyAkPvFpAwsQ2xfeipNyUnHGAJeS8sMulbdg0E8_qUvDqP_f8IJRI22OlYv4CiblDeszTSCNBF_fg4w_2WXQVRNPHTO7_YI-CjoAI99UF8ig09FUQPF9La7Zb66q16OTigGPrnVCs1R1BYge1DWjcHF05KAZtJXCgrGFeQYfGX961fKE_LCVvvbbwMnAtF879aC-_R3HZmOhUqXdl9eNrwAryt-UmLfK_y4cJNrvt8wFae75yt-XXLYpRueMBpN3YMSwz9O-A3D5QMmONDXb7WXW7yZ3ioeLpyeuan6EvhEQKFLW3iUWwjAevWYQwatSxNJZfrKPvaj95P7U2z3RpvVEoFoEv9tb-6nzwjiGmdhCIqYbGenPJSnI2S7nPZtyX6-DJoZLsE_WJTu2beD5dXGXEZ1qV310Nz-bV_ZUOkxVt6ymfo2nQLEq7iysAIhUy3LT-hw9lmk-yKCxLkfV7WsorpZTs6EA6kroJZQeVrOQH3alAclgv4YAlZ_QdluhIv1UhMw5wDRYzAn-XulyG8ID6aSFXZYbA_-q_mN003__mC0)
  #### 2.4 Biểu đồ lớp
   ![Diagram](https://www.planttext.com/api/plantuml/png/b5J1Ri8m3BttAonEGu8Vg2Q4nBRJXAQ1j7FMMf2jRJed8A5fNxR3Fcc_iBX9Q5eAOXTG7FizlsUdlzy_Ssq4cLrP95aXj8RxiYxK0V4PQqNcGL49dma047xiK1iNNXzgl1cdi5SoZoxlX44z45zi1MrmkIjVaUBhsX8kI1eaATPgeIf3gYYwERdKTI4EZdS0UoNsU7ffgp91UU_YAnaKsH87gOOaxZ5aMLc2CSAPSp92AzRZPrv32XxGdySX4AF6PZHcFKfjRkFeZDDrgukQlu0rWKgKcCBAmbMR2HGg4qQgAaHEnBgoHjgKZkCBwHnjLe27bmB_SWYhl1VmuZisJBEexHHY4QnXWnLIQrCqdmtwJRf38sJH-E3xEHcIwrpcSSUn1NpUgXtf5qNlQDDaPJn7Vu9zYhXXHzCLr1BKfDumCyikBtF461VKUBb2kHrhnxjMtDshqDWRT6VNtUu44AV6xzQHuidr6E2ENF_PF0isy0MOJcVdtqmA8tx845x1A3cRoZX-7MsLUqFWL5zLnP9i8PjtNTc09RO-609ksb0vIqP9ozBjj4CuWCdPdLswH3AtRuk_jty0003__mC0)
  #### 2.5 Giải thích về biểu đồ lớp
  - **EmployeeReportForm**:
    - Phương thức:
        - requestReportType(): Phương thức này yêu cầu người dùng chọn loại báo cáo cần tạo, ví dụ: báo cáo về tổng số giờ làm việc hoặc báo cáo về lương trong năm.
        - requestDates(): Phương thức này yêu cầu người dùng nhập khoảng thời gian báo cáo, gồm ngày bắt đầu và kết thúc.
        - requestChargeNumber(): Nếu loại báo cáo yêu cầu thông tin dự án, phương thức này yêu cầu người dùng nhập số charge dự án.
        - passCriteriaToController(): Chuyển các tiêu chí đã nhập từ người dùng (loại báo cáo, thời gian, số charge dự án) đến controller để xử lý.
        - displayReport(): Phương thức này hiển thị báo cáo đã được tạo từ controller trên giao diện người dùng.
        - requestSaveReport(): Yêu cầu người dùng cung cấp tên và vị trí lưu báo cáo.
        - discardReport(): Nếu người dùng quyết định không lưu báo cáo, phương thức này hủy bỏ báo cáo và không lưu vào cơ sở dữ liệu.
- **EmployeeReportController**:
    - Phương thức:
        - retrieveEmployeeData(): Lấy dữ liệu về nhân viên từ hệ thống (ví dụ: tên, giờ làm việc, v.v.) để sử dụng trong báo cáo.
        - createReport(criteria): Tạo báo cáo dựa trên các tiêu chí đã cung cấp (loại báo cáo, khoảng thời gian, nhân viên, số charge dự án). Sau khi tạo báo cáo, gửi lại kết quả cho form để hiển thị cho người dùng.
        - retrieveChargeNumbers(): Lấy danh sách số charge của các dự án từ cơ sở dữ liệu nếu báo cáo yêu cầu thông tin về các dự án.
- **Report**:
    - Phương thức:
        - `generateReport()`: Tạo nội dung báo cáo dựa trên các tiêu chí đã nhập từ người dùng (ví dụ: tổng số giờ làm việc cho một dự án hoặc tổng số giờ làm việc của nhân viên).
        - `getReportDetails()`: Trả về chi tiết của báo cáo (có thể bao gồm thông tin về nhân viên, số giờ làm việc, lương, dự án, v.v.).
- **Employee**:
    - Phương thức:
        - getEmployeeData(): Lấy thông tin về nhân viên, ví dụ: tên nhân viên, số giờ làm việc, v.v., để báo cáo có thể tính toán và hiển thị các thông tin liên quan đến nhân viên trong báo cáo.

- **ChargeNumber**:
    - Phương thức:
        - getChargeNumberDetails(): Lấy thông tin chi tiết về số charge của dự án mà nhân viên tham gia. Thông tin này sẽ được sử dụng trong báo cáo nếu báo cáo yêu cầu thông tin liên quan đến các dự án.
- **ReportDao**:
    - Phương thức:
        - saveReportToDatabase(report): Lưu báo cáo vào cơ sở dữ liệu. Khi người dùng yêu cầu lưu báo cáo, phương thức này sẽ lưu dữ liệu báo cáo vào hệ thống lưu trữ.
        - retrieveReportData(): Lấy dữ liệu báo cáo từ cơ sở dữ liệu, ví dụ khi cần truy xuất lại báo cáo đã lưu.
- **ProjectDatabaseDao**:
    - Phương thức:
        - retrieveChargeNumbers(): Lấy danh sách các số charge dự án từ cơ sở dữ liệu để phục vụ cho việc tạo báo cáo nếu báo cáo yêu cầu dữ liệu về các dự án.
  ### 3. Close Registration
  #### 3.1 Xác định các lớp phân tích
- **Boundary class**:
    - **CloseRegistrationForm :** Quản lý giao diện người dùng cho Registrar, cho phép Registrar yêu cầu đóng đăng ký và hiển thị các thông báo về tình trạng các khóa học (đủ số sinh viên hoặc bị hủy).
    - **BillingSystemForm:** Quản lý giao diện người dùng cho hệ thống thanh toán, cho phép hệ thống thanh toán nhận thông tin về học phí của các sinh viên và xử lý giao dịch thanh toán cho các khóa học không bị hủy.
- **Control class**:
    - **CloseRegistrationController:** Xử lý logic nghiệp vụ cho việc đóng đăng ký, kiểm tra xem mỗi khóa học có đủ số lượng sinh viên và giảng viên hay không, xử lý việc hủy các khóa học không đủ sinh viên và thông báo cho hệ thống thanh toán về các sinh viên trong các khóa học hợp lệ.
- **Entity class**:
    - **CourseOffering (Entity):** Đại diện cho khóa học và thông tin liên quan như giảng viên và số lượng sinh viên đăng ký.
    - **Student (Entity):** Đại diện cho sinh viên đăng ký và lưu trữ thông tin học phí.
- **Data Access Object (DAO):**
    - **CourseOfferingDao:** Truy cập cơ sở dữ liệu để lấy thông tin các khóa học, bao gồm việc kiểm tra số lượng sinh viên, giảng viên, và trạng thái của khóa học.
    - **BillingDao:** Truy cập cơ sở dữ liệu để tính toán học phí cho sinh viên trong các khóa học hợp lệ và gửi giao dịch thanh toán cho hệ thống thanh toán.
     
  #### 3.2 Nhiệm vụ của các lóp phân tích
- **CloseRegistrationForm:** Hiển thị giao diện yêu cầu đóng đăng ký và thông báo tình trạng các khóa học.
- **BillingSystemForm:** Hiển thị giao diện thanh toán và xử lý giao dịch học phí cho các khóa học không bị hủy.
- **CloseRegistrationController:** Xử lý logic đóng đăng ký, kiểm tra khóa học hợp lệ, hủy khóa học không đủ sinh viên, và thông báo cho hệ thống thanh toán.
- **CourseOffering:** Đại diện cho khóa học, kiểm tra tính hợp lệ của khóa học.
- **Student:** Lưu trữ thông tin sinh viên và học phí cho các khóa học hợp lệ.
- **CourseOfferingDao:** Truy xuất và cập nhật thông tin khóa học trong cơ sở dữ liệu.
- **BillingDao:** Tính toán học phí và gửi giao dịch thanh toán cho sinh viên.
  #### 3.3 Biểu đồ Sequence
  ![Diagram](https://www.planttext.com/api/plantuml/png/X5HBJWCn3Dtd5DQiO85OiEi2LHGXiG69di3DUDg8D874KzIpiU18N05F9lFfz4CtpUUz-FdPdj_ldtba35nlhKBDFi0RhKtaW04mGj7lYdpzOAmrRhtSHwPjWkGJQ8yAfLQ-TYM6FHGBwoDrJx3nxic7RT6mceNItd7mzWHkqTvO2WazR1KvDjmyxUiGwRMgA4ZmZ1eVzSWbrwMi4oIlLOcCAumqVUSH_Ocdv7J4oFbsq66hrE3TpNrA4MRYvsTDaO4zw2PD2ACyLG89UCXGA4jofS0kyKRun9x8JN4v6DeHw7G9Fjz6TOoU2X1k7Tmnys9OuIqsfD_1L1rp8_uWWoMKHEuWjkvF5VmJVeVMb4qbhzBgrhZqVwqKMeRdFfY9BLI1_0w53ZNgtCrIO9MRrxZA9-88UaPMHv5Ik2X38UM0aXYDZUT3vtcPmOjdK-q1PKXugc8i81Ec6cHJ6McPJaGWJMP7fI8h5XoOaNqweUcuRkWqsSpDX8iLwcJaQ3hnRTkQOk-qKV8eB8xw63w2rnHZFmV314cXDlxh4DqCGXr8V4EkevfBgER3zGS00F__0m00)
  #### 3.4 Biểu đồ lớp
  ![Diagram](https://www.planttext.com/api/plantuml/png/d5LBRjim4Dth50DjQXV9ebkZ29BOBH2Wg8kuw7vCZMos56cGmmP6cvDrqIFr2gN-egmOHhJJl3U_Dnpotv-_juxHiYzKyWPMb4jDm7i2eT0vSe0wA_-b1KiAMHhjzlBWai2-DrvdQ8yjDpcW-84xWhH5KlYLG0t3KXb7ZxIJZcqLvwEnHOMNdnYZitc3kBrv6W8RHlQkWf-JBlgzL4hgtURec8eeSkdVe2jYbCfreG_M27Bk2nuBqjo4V2vRMnhDrgWwUDzNOpxRLiDHP2zexYSgcI7JqdZhQ9tdP4ET7QmDo_mOzTPX0hKWLJiEI_-WMVB4J6fxL7gKjA-sCZza2v2Q8zjdB6W1eOb0RolqnJhViC-2W6xeKG4FEf2zO6CZp5KZ74MIxbifnco-WAqnAXvlaw4VQlqV5zaO9wfaBwiJHm78ZDygQW3IrQYoMefGqgSme_UnC3UzjYjaX3jH7XfORx-JO9YjxjRpKxK7p9SbNw7fEjeHnw0hbNYXdFBpX_xWD3iHJUvg9FFqmWnB4AY43pjENpkvPh7Gyv5yemMAoLU0HRW7kFKPdD77uLK2M-8d8js9E7rJN5__lZcxRGlmfVVfJL1vHkQMUovSdUzaNfTw3lHzNRBWrjuEbwSRT5tDW2mA3kudRKmdB527qzjfs17RzLl0Fhm7YiOH8NsN1YQaRzC1jrukbzoIpihtvJy0003__mC0)
  #### 3.5 Giải thích về biểu đồ lớp
  - **CloseRegistrationForm**:
    - Phương thức:
        - closeRegistration(): Đóng đăng ký cho các khóa học, kiểm tra điều kiện để xác nhận khóa học hợp lệ hoặc bị hủy.
        - showRegistrationStatus(): Hiển thị trạng thái của các khóa học, bao gồm việc khóa học có đủ sinh viên và giảng viên hay không.

- **BillingSystemForm**:
    - Phương thức:
        - showBillingDetails(): Hiển thị thông tin về học phí của sinh viên trong các khóa học hợp lệ.
        - processPayment(): Xử lý giao dịch thanh toán cho sinh viên, truyền thông tin học phí và nhận phản hồi từ hệ thống thanh toán.

- **CloseRegistrationController**:
    - Phương thức:
        - closeRegistration(): Điều phối quá trình đóng đăng ký, kiểm tra tính hợp lệ của các khóa học và hủy các khóa học không hợp lệ.
        - validateCourseOffering(): Kiểm tra các khóa học xem có đủ số sinh viên và giảng viên không, nếu không đủ sẽ hủy khóa học.
        - notifyBillingSystem(): Thông báo cho hệ thống thanh toán về các khóa học hợp lệ và gửi thông tin học phí của sinh viên để thanh toán.
        - cancelCourse(): Hủy các khóa học không đủ số sinh viên và giảng viên, và cập nhật trạng thái khóa học trong cơ sở dữ liệu.

- **CourseOffering (Entity)**:
    - Phương thức:
        - isValid(): Kiểm tra tính hợp lệ của khóa học, xác nhận số lượng sinh viên và giảng viên có đủ để giữ khóa học mở.
- **Student (Entity)**:
    - Phương thức:
        - getTuitionFee(): Tính toán học phí của sinh viên dựa trên các khóa học mà họ tham gia, bao gồm việc áp dụng các khoản giảm giá hoặc tăng thêm.
- **CourseOfferingDao (DAO)**:
    - Phương thức:
        - getCourseOfferings(): Truy xuất danh sách các khóa học từ cơ sở dữ liệu, bao gồm thông tin về số lượng sinh viên và giảng viên.
        - updateCourseStatus(courseId, status): Cập nhật trạng thái của khóa học trong cơ sở dữ liệu (ví dụ: "đã đóng" hoặc "bị hủy").
- **BillingDao (DAO)**:
    - Phương thức:
        - calculateTuitionFee(studentId): Tính toán học phí mà sinh viên phải trả cho các khóa học hợp lệ mà họ đã đăng ký.
        - processPayment(studentId, amount): Xử lý giao dịch thanh toán học phí cho sinh viên, bao gồm việc gửi thông tin thanh toán và cập nhật trạng thái giao dịch.

  ### 4. Maintaiin Employee info
  #### 4.1 Xác định các lớp phân tích
  - **Boundary class**:
       - **EmployeeUI:** Giao diện duy nhất cho Quản trị viên, hiển thị các chức năng Thêm, Sửa, Xóa nhân viên và thu thập thông tin từ người dùng.
  - **Control class**:
      - **EmployeeController**: EmployeeController: Điều khiển các thao tác thêm, sửa, xóa nhân viên.
  - **Entity class**:
      - **Employee:** Lớp cơ bản chứa thông tin chung của nhân viên (mã, tên, địa chỉ, số an sinh xã hội,...).
  - **Data Access Object (DAO):**
      - **EmployeeDatabase: Lưu trữ và quản lý dữ liệu nhân viên, thực hiện thêm, lấy, cập nhật và đánh dấu xóa.
  #### 4.2 Nhiệm vụ của các lóp phân tích
  - **MaintainEmployeeBoundary:** Giao diện để Payroll Administrator tương tác với hệ thống nhằm thực hiện các chức năng thêm, sửa, và xóa thông tin nhân viên.
  - **EmployeeController:** Xử lý logic nghiệp vụ cho các yêu cầu từ Payroll Administrator về thêm, cập nhật, và xóa thông tin nhân viên.
  - **Employee:**Đại diện cho một nhân viên, lưu trữ thông tin chung như mã nhân viên, tên, địa chỉ, số an sinh xã hội, v.v.
  - **EmployeeDatabase (DAO)**: Lớp quản lý dữ liệu nhân viên. Nhiệm vụ chính của EmployeeDatabase là:Thêm, lấy, cập nhật và đánh dấu xóa các bản ghi nhân viên trong hệ thống.
  #### 4.3 Biểu đồ Sequence
  ![Diagram](https://www.planttext.com/api/plantuml/png/p5LBJiCm4Dtx55PN8D4BH0egQa3g1Y6g7c0QJwk0OnVR0ULiB3WILy3Enp5fsWGa93PHCddFR-RDY_Bv_h7G1fGfSauWDLBH1oYLvFo6vPd8j57WYg1fLI1aAml1G9NqDZzmMI9kLYILmbYEBothPuwAe32PwS24WO4jQFILf2aG4iTMW_aND8u9gKJf_3fGY-WQEQQ6paBqZ7I84D-r4b5Wh2rVk3ukoJ4gv4PqgH0CKe5lNLjo-sJLFJKajBD4LCChUYriRZgz5aZdt-JkhKuBhevWLrIXAPJGlhvYWVI9GGUmuOGzEmVGpaEBgjoFQ9Bf0uUoiY40kuLj3imPD7rdFSAKjHKLvSZDbJMdViMI2SliThD7Ct3Oo7B2XloqcTX9bOF9f1YDKjyf5y2H49qOV3H6ZPJzAdTPlxsJGpKaXRhWPafiraMQejOqjnVOuqXsT0_jmfFOJFmeF3t2bF2mYd9st_ynBsxgHtmfK9jw14iPNcWzUkFsUSgWjyiQuIaJF3r96NCo1_Ly9rNIy7xdPdBMZhyBx085St_9Bm000F__0m00)
  #### 4.4 Biểu đồ lớp
  ![Diagram](https://www.planttext.com/api/plantuml/png/n5HBJiCm4Dtd5DvH97g1B50b0X8IOa7X0DDusbZu4tacBH7YP2mu4bTWaZPfKafXHrRnlEVdcNbZVxv_p8WXSkLiafof39V6e-82LMw124c1rytQH1M3bRNnBKmrCRf4lfQehbrfGutuTAjU4wKKQDs59XeOqfwHoUeyLUjWT4EiIe6nv-BkvrQdSXHVx72TdTBGQF5dZOxuTfZhLV0iHLcCVynPnFuvvJRHgJgWjp4F3bCrvsZyQaHwhCin87L691h5AEG6x1ppAXgkxoktm3WYCBnagAkSJV2oTMa3RCyDCWxnE5GMmUCHhI9KqTOFqgGXcy12h8UHF3XdY4JsaDiet1bdU5j_qz4LydNVbidUBObdo60iDS6X7NilEyAlpdqpf04NG5jZf8JrTq_tIgEaJdZVGIU6RIJQ3PM3-7mJn0oPBMdQYQdghtf42wrlXIb9BP0tY7xu0CWD7zpjwVJosFL9MwigRtB9bP8ZZE56eJlmi1emHtZVqrGHXuXQalzDSx17AiK8EPFQ62wIP8PUo_ls1G00__y30000)
  #### 4.5 Giải thích về biểu đồ lớp
  - **EmployeeUI**
      - Phương thức:
          -  addEmployee(data: EmployeeData): void: Nhận dữ liệu thêm nhân viên từ người dùng và chuyển cho EmployeeController.
          -  updateEmployee(employeeId, updatedData): Nhận yêu cầu cập nhật thông tin nhân viên và chuyển cho EmployeeController.
          -  deleteEmployee(employeeId): Nhận yêu cầu xóa nhân viên và chuyển cho EmployeeController.
  - **EmployeeController**:
      - Phương thức:
          - addEmployee(data): Tạo nhân viên mới từ dữ liệu, lưu vào EmployeeDatabase, và trả về employeeId.
          - updateEmployee(employeeId, updatedData): Lấy thông tin, cập nhật nhân viên từ updatedData, và lưu vào EmployeeDatabase.
          - deleteEmployee(employeeId): Lấy thông tin nhân viên, xác nhận xóa và đánh dấu xóa trong EmployeeDatabase.
  - **Employee**:
      - Phương thức:
          - getEmployeeId(): Trả về mã nhân viên.
          - getDetails(): Trả về thông tin chi tiết của nhân viên.
          - updateDetails(updatedData): Cập nhật thông tin nhân viên.
  - **EmployeeDatabase**:
      - Phương thức:
          - saveEmployee(employee): Lưu nhân viên mới và trả về employeeId.
          - getEmployee(employeeId): Lấy thông tin nhân viên theo employeeId.
          - updateEmployee(employee): Cập nhật thông tin nhân viên trong cơ sở dữ liệu.
          - markForDeletion(employeeId): Đánh dấu nhân viên để xóa.
  ### 5. Run Payroll
  #### 5.1 Xác định các lớp phân tích
  - **Boundary class**:
      - **SystemClock:** Kích hoạt quá trình chạy lương theo lịch (vào mỗi Thứ Sáu và ngày làm việc cuối của tháng).
      - **Printer:** Chịu trách nhiệm in phiếu lương cho nhân viên có phương thức nhận lương là qua thư hoặc nhận trực tiếp.
      - **BankSystem:** Thực hiện các giao dịch chuyển khoản trực tiếp cho nhân viên có phương thức nhận lương là chuyển khoản ngân hàng.
  - **Control class**:
      - PayrollController:
      - Điều phối quy trình chạy lương bao gồm:
         - Lấy danh sách nhân viên cần được trả lương vào ngày hiện tại.
         - Tính toán lương của từng nhân viên dựa trên phiếu chấm công, thông tin nhân viên, đơn hàng mua, và các khoản khấu trừ hợp pháp.
         - Gửi phiếu lương đến Printer nếu phương thức nhận lương là thư hoặc nhận trực tiếp.
         - Gửi yêu cầu giao dịch đến BankSystem nếu phương thức nhận lương là chuyển khoản.
  - **Entity class**:
      - Employee: Đại diện cho nhân viên, chứa thông tin cần thiết để tính lương như mức lương, loại nhân viên, các khoản lợi ích, và phương thức nhận lương (thư, nhận trực tiếp, hoặc chuyển khoản).
      - TimeCard: Đại diện cho phiếu chấm công, chứa thông tin về số giờ làm việc của nhân viên trong kỳ lương (áp dụng cho nhân viên trả lương theo giờ).
      - PurchaseOrder: Đại diện cho đơn hàng mua (áp dụng cho nhân viên hưởng lương theo hoa hồng), chứa thông tin về các đơn hàng mà nhân viên được hưởng hoa hồng.
      - Paycheck: Lớp này đại diện cho phiếu lương cuối cùng của nhân viên sau khi tính toán xong, bao gồm tổng lương và các khoản khấu trừ.
  - **Data Access Object (DAO)**
      - EmployeeDatabase: Quản lý dữ liệu nhân viên và cung cấp thông tin về nhân viên, bao gồm phiếu chấm công và đơn hàng, từ cơ sở dữ liệu phục vụ cho việc tính lương.
  #### 5.2 Nhiệm vụ của các lóp phân tích
  - **SystemClock (Boundary)**: Tự động kích hoạt PayrollController để bắt đầu chạy lương vào thời gian đã được lên lịch.
  - **Printer (Boundary)**: In phiếu lương cho các nhân viên có phương thức nhận lương là qua thư hoặc nhận trực tiếp.
  - **BankSystem (Boundary)**: Thực hiện giao dịch chuyển khoản khi nhân viên chọn phương thức nhận lương qua chuyển khoản.
  - **PayrollController (Control)**: Điều phối toàn bộ quy trình chạy lương, từ lấy thông tin nhân viên, tính toán lương đến xử lý thanh toán qua in phiếu hoặc chuyển khoản ngân hàng.
  - **Employee (Entity)**: Cung cấp thông tin nhân viên để tính lương, bao gồm mức lương, lợi ích, và phương thức nhận lương.
  - **TimeCard (Entity)**: Cung cấp thông tin giờ làm việc của nhân viên (dành cho nhân viên hưởng lương theo giờ).
  - **PurchaseOrder (Entity)**: Cung cấp thông tin về đơn hàng cho nhân viên hưởng lương theo hoa hồng.
  - **Paycheck (Entity)**: Lưu trữ thông tin phiếu lương sau khi tính toán xong.
  - **EmployeeDatabase (DAO)**: Truy cập và quản lý dữ liệu nhân viên từ cơ sở dữ liệu để phục vụ cho việc tính lương.
  #### 5.3 Biểu đồ Sequence
  ![Diagram](https://www.planttext.com/api/plantuml/png/n5HBJiCm4Dtd5DvH97g1B50b0X8IOa7X0DDusbZu4tacBH7YP2mu4bTWaZPfKafXHrRnlEVdcNbZVxv_p8WXSkLiafof39V6e-82LMw124c1rytQH1M3bRNnBKmrCRf4lfQehbrfGutuTAjU4wKKQDs59XeOqfwHoUeyLUjWT4EiIe6nv-BkvrQdSXHVx72TdTBGQF5dZOxuTfZhLV0iHLcCVynPnFuvvJRHgJgWjp4F3bCrvsZyQaHwhCin87L691h5AEG6x1ppAXgkxoktm3WYCBnagAkSJV2oTMa3RCyDCWxnE5GMmUCHhI9KqTOFqgGXcy12h8UHF3XdY4JsaDiet1bdU5j_qz4LydNVbidUBObdo60iDS6X7NilEyAlpdqpf04NG5jZf8JrTq_tIgEaJdZVGIU6RIJQ3PM3-7mJn0oPBMdQYQdghtf42wrlXIb9BP0tY7xu0CWD7zpjwVJosFL9MwigRtB9bP8ZZE56eJlmi1emHtZVqrGHXuXQalzDSx17AiK8EPFQ62wIP8PUo_ls1G00__y30000)
  #### 5.4 Biểu đồ lớp
  ![Diagram](https://www.planttext.com/api/plantuml/png/Z5JDRjim3BxxANHCWVO5XA5ecsp0W1KjrW4zApAN294bWwG314EVR8SzqbvXj6FMzlBN71oBuiVl8qtox-y_TyGEkQbYKVZeYCpBZXYgUSn-OtuLflqnXjKAy7kJdjqESuopg-9D_Pyn90PKtxezYfjVWz_Cwlx56ZMDa0ykRVPi0pXx85e41CyBg3C5FX-Z5pJFYTl_GSSnpTt52lXpLSUy0w0l6VNMDuYGUE4Oh6cVlRjtqJTHpk8uur31t65fpO_-xThK3Vgr8tZ24b0qZe_N1degQvJqQiXZI4ClLRt2lWgLr7DlJAwIE2-IMLhjBUIYmvqrPMwM4VQs9IJu6PYcdbB4Ij9x15xdSderAiW2s8L8Cz6upQ4Sz6cwP_MjSuFqcd43Owk4LxI6_mzzm3QfuLbAdwig48MSxglS99wMGgWdeJxCttyVfNP7OfTGDfw5cARs16ttJssJ7ZfWUo--OxSKgShwuKQrvbiW_gJEjzeRMpWtXuECySJVtDmUcIchuqJ5uMKBESZ16kVRKOPB2F54aEYm1PAYTX_e1EIz2SUGTYGluARjD0Rdpd81hSrWZKUGUfzqx1UXDGIf9ACrF-4-sdwAABkz9tgwnLSKTs9jD_C_0000__y30000)
  #### 5.5 Giải thích về biểu đồ lớp
- **SystemClock:**
    - Phương thức:
        - triggerRunPayroll(): là phương thức khởi động quy trình tính lương, kích hoạt lớp PayrollController.
- **Printer:**
    - Phương thức:
        - printPaycheck(paycheck: Paycheck): Nhận thông tin phiếu lương từ PayrollController và in phiếu lương theo yêu cầu.
- **BankSystem:**
    - Phương thức:
        - processDirectDeposit(paycheck: Paycheck): Nhận yêu cầu giao dịch từ PayrollController và xử lý thanh toán qua ngân hàng.
- **PayrollController:**
    - Phương thức:
        - triggerRunPayroll() được kích hoạt bởi SystemClock, và từ đó lớp này sẽ bắt đầu quá trình tính lương.
        - getEmployeesForPayroll(currentDate: Date): Truy xuất danh sách các nhân viên cần được trả lương vào ngày hiện tại từ EmployeeDatabase.
        - calculatePay(timeCard: TimeCard, purchaseOrder: PurchaseOrder, employee: Employee): Paycheck: Tính toán lương dựa trên thông tin từ các phiếu chấm công (TimeCard), đơn hàng mua (PurchaseOrder), và thông tin nhân viên (Employee). Kết quả là một đối tượng Paycheck.
- **Employee:**
    - Phương thức:
        - getEmployeeDetails(): Cung cấp chi tiết thông tin về nhân viên, như mức lương, các khoản khấu trừ, và phương thức thanh toán
- **TimeCard:**
    - Phương thức:
        - getTimeCardDetails(employeeId: int): Cung cấp thông tin về thời gian làm việc của nhân viên dựa trên mã nhân viên.
- **PurchaseOrder:**
    - Phương thức:
        - getPurchaseOrderDetails(employeeId: int): Cung cấp chi tiết về đơn hàng liên quan đến mã nhân viên.
- **Paycheck:**
    - Phương thức:
        - calculatePay(): Tính toán phiếu lương cuối cùng cho nhân viên, bao gồm tổng số tiền lương, các khoản khấu trừ, và lương ròng.
- **EmployeeDatabase:**
    - Phương thức:
        - getEmployeesForPayroll(currentDate: Date): Lấy danh sách các nhân viên cần trả lương trong ngày hiện tại.
        - savePaycheck(paycheck: Paycheck): Lưu phiếu lương đã tính vào cơ sở dữ liệu.
              
  ### 6. Login
  #### 6.1 Xác định các lớp phân tích
  - **Boundary class**:
      - **LoginUI:**: Đây là giao diện người dùng để thực hiện chức năng đăng nhập.
  - **Control class**:
      - **LoginController:** Đây là lớp điều khiển, chịu trách nhiệm điều phối quá trình xác thực đăng nhập.
  - **Entity class**:
      - **User:** Lớp này đại diện cho người dùng trong hệ thống và chứa các thông tin cần thiết để xác thực.
  -  **Data Access Object (DAO)**
      - **UserDatabase**: Đây là lớp truy cập cơ sở dữ liệu, chịu trách nhiệm truy xuất và xác nhận thông tin người dùng.
  #### 6.2 Nhiệm vụ của các lóp phân tích
  - **LoginForm:**
    - Hiển thị các trường để nhập tên người dùng và mật khẩu.
    - Thu thập thông tin đăng nhập từ người dùng và chuyển tiếp chúng cho lớp điều khiển.
  - **LoginController:**
    - Nhận tên người dùng và mật khẩu từ LoginUI.
    - Tương tác với UserDatabase để xác nhận thông tin đăng nhập.
    - Gửi thông báo đến LoginUI về kết quả xác thực (thành công hoặc thất bại).
  - **User:**
    - Chứa thuộc tính username và password (được mã hóa) của người dùng.
    - Cung cấp phương thức xác minh thông tin đăng nhập.
  - **UserDatabase**
     - Cung cấp phương thức để kiểm tra tên người dùng và mật khẩu.
     - Lấy thông tin người dùng từ cơ sở dữ liệu để hỗ trợ quá trình xác thực của LoginController.
  #### 6.3 Biểu đồ Sequence
  ![Diagram](https://www.planttext.com/api/plantuml/png/b991JiGm34NtFeMN834N6AbefCAiM216i7SRCrIuoSX9G3qR2ux45KZIJgT2tT15r3Z-to-__Vdwtlb06c8l0DG6f_ZiMQ5nqHhI0H_SiRDxfpsqpWPrCbRgSIEfbMtemb1az-KL30Lgo7EftKqRWAh2GvurEk2ZkfQznwg2t8URsykmBIRNL8lfm5BFIDRWYRp_T6fWRfir5vmj-jZqNK39zQkpmSsilYuWBoHTmXmHiLOs-Hea1UUFPPwolCaMFoRrGhSwQQd2pHgiSeXg5-5X-W8sYXJA-etRzock9_PHGiOZEKTuY6sEy3KAO7fMk1U9ciwVX8QKJn5XdnOwCh0akD5lJvsm-OSNgoRUsSaQW5rQyz_q2m00__y30000)
  #### 6.4 Biểu đồ lớp
  ![Diagram](https://www.planttext.com/api/plantuml/png/b991JWGX44NtdAAMFObz0HPcaZ76XGkZyG0rKFQGq32XeCt4U38N7iah2DrDc-bneQoWUFK_7_Zw-Dnon11JRuLG5fdXcId0cu0yMaXvuR0d2Kyn6DVDvMC6NttGTyY7ios0WO9vEJtCG5F9IcqaxBstX4wyLyTxtnbtwqC_smAvI64NIEU9GSlD-XXNSA4xTMh3HukdKV6HEDdOS5AAc1VVpSfuvrqCtjebDM2AX-AiCD9Vh7-9L2xn1YFkaQdA3cYDpfB_32P7iKcYerWM5sqLolvdpcrxFRsdX42Pf85Oh5DNQEcIWEELLNPycaAjEoKmESsWVX89iSsbyfs-0G00__y30000)
  #### 6.5 Giải thích về biểu đồ lớp
  - **User:**
     - Phương thức:
         - verifyPassword(password: String): boolean: Kiểm tra xem mật khẩu người dùng nhập vào có khớp với mật khẩu đã lưu (mã hóa) không.
  - **LoginForm:**
     - Phương thức:
         - enterCredentials(username: String, password: String): Thu thập tên đăng nhập và mật khẩu từ người dùng rồi gửi đến LoginController.
         - displayLoginResult(success: boolean): Hiển thị kết quả đăng nhập (thành công hoặc thất bại) cho người dùng.
  - **LoginController:**
     - Phương thức:
         - authenticate(username: String, password: String): boolean: Nhận thông tin đăng nhập từ LoginUI, xác thực qua UserDatabase, và trả về kết quả (đúng/sai).
  - **UserDatabase:**
     - Phương thức:
         - validateCredentials(username: String, password: String): User: Tìm và xác minh thông tin đăng nhập của người dùng; nếu hợp lệ, trả về đối tượng User.
## II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.
- ### **Lớp Boundary**
  - **TimecardUIHandler.java** 

public class TimecardUIHandler {
    private TimecardService timecardService;

    public TimecardUIHandler(TimecardService timecardService) {
        this.timecardService = timecardService;
    }

    public void start() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the Timecard System");

        System.out.print("Enter Employee ID: ");
        String employeeId = scanner.nextLine();

        List<ChargeNumber> chargeNumbers = timecardService.getAvailableChargeNumbers();
        System.out.println("Available Charge Numbers:");
        for (ChargeNumber cn : chargeNumbers) {
            System.out.println(cn.getChargeNumber());
        }

        System.out.print("Enter Charge Number: ");
        String chargeNumberInput = scanner.nextLine();

        System.out.print("Enter Hours Worked: ");
        double hoursWorked = scanner.nextDouble();

        timecardService.createTimecard(employeeId, chargeNumberInput, hoursWorked);
        System.out.println("Timecard created successfully!");

        // Save or submit the timecard
        System.out.println("Do you want to save or submit the timecard? (save/submit): ");
        String action = scanner.next();
        if ("submit".equalsIgnoreCase(action)) {
            timecardService.submitTimecard(employeeId);
            System.out.println("Timecard submitted successfully!");
        } else {
            System.out.println("Timecard saved successfully!");
        }

        scanner.close();
    }
}
  - ** ProjectDatabase.java


public class ProjectDatabase {
    public List<ChargeNumber> getChargeNumbers() {
        // For demonstration, return some dummy charge numbers
        List<ChargeNumber> chargeNumbers = new ArrayList<>();
        chargeNumbers.add(new ChargeNumber("CN001"));
        chargeNumbers.add(new ChargeNumber("CN002"));
        chargeNumbers.add(new ChargeNumber("CN003"));
        return chargeNumbers;
    }
}
- ###  Lớp Control
  - **TimecardService.java**
    import java.util.List;

public class TimecardService {
    private TimecardDAO timecardDAO;
    private ProjectDatabase projectDatabase;

    public TimecardService(TimecardDAO timecardDAO, ProjectDatabase projectDatabase) {
        this.timecardDAO = timecardDAO;
        this.projectDatabase = projectDatabase;
    }

    public List<ChargeNumber> getAvailableChargeNumbers() {
        return projectDatabase.getChargeNumbers();
    }

    public void createTimecard(String employeeId, String chargeNumber, double hoursWorked) {
        Employee employee = new Employee(employeeId);
        Timecard timecard = new Timecard(employee, new ChargeNumber(chargeNumber), hoursWorked);
        timecardDAO.saveTimecard(timecard);
    }

    public void submitTimecard(String employeeId) {
        timecardDAO.submitTimecard(employeeId);
    }
}
- ### Lớp Entity
  - **Employee.java**
    public class Employee {
    private String employeeId;

    public Employee(String employeeId) {
        this.employeeId = employeeId;
    }

    public String getEmployeeId() {
        return employeeId;
    }
}
  - **Timecard.java**
    public class Timecard {
    private Employee employee;
    private ChargeNumber chargeNumber;
    private double hoursWorked;
    private boolean isSubmitted;

    public Timecard(Employee employee, ChargeNumber chargeNumber, double hoursWorked) {
        this.employee = employee;
        this.chargeNumber = chargeNumber;
        this.hoursWorked = hoursWorked;
        this.isSubmitted = false;
    }

    public Employee getEmployee() {
        return employee;
    }

    public ChargeNumber getChargeNumber() {
        return chargeNumber;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    public boolean isSubmitted() {
        return isSubmitted;
    }

    public void submit() {
        this.isSubmitted = true;
    }

- **ChargeNumber.java**
  public class ChargeNumber {
    private String chargeNumber;

    public ChargeNumber(String chargeNumber) {
        this.chargeNumber = chargeNumber;
    }

    public String getChargeNumber() {
        return chargeNumber;
    }

}

- ### Lớp TimecardDAO
    - **TimecardDAO.java**
public class TimecardDAO {
    private Map<String, Timecard> timecardDatabase = new HashMap<>();

    public void saveTimecard(Timecard timecard) {
        timecardDatabase.put(timecard.getEmployee().getEmployeeId(), timecard);
        System.out.println("Timecard saved for Employee ID: " + timecard.getEmployee().getEmployeeId());
    }

    public void submitTimecard(String employeeId) {
        Timecard timecard = timecardDatabase.get(employeeId);
        if (timecard != null) {
            timecard.submit();
            System.out.println("Timecard submitted for Employee ID: " + employeeId);
        } else {
            System.out.println("No timecard found for Employee ID: " + employeeId);
        }
    }

- ### Main.java
  public class Main {
    public static void main(String[] args) {
        ProjectDatabase projectDatabase = new ProjectDatabase();
        TimecardDAO timecardDAO = new TimecardDAO();
        TimecardService timecardService = new TimecardService(timecardDAO, projectDatabase);

        TimecardUIHandler uiHandler = new TimecardUIHandler(timecardService);
        uiHandler.start();
    }
}





 

