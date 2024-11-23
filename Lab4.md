# Thiết kế các ca sử dụng cho hệ thống "Payroll System"
## I. Ca sử dụng Maintain Timecard
### 1. Mô tả sự tương tác giữa các đối tượng thiết kế
  - Tác nhân: Employee, Project Management
### 2. Đơn giản hóa sơ đồ trình tự bằng hệ thống con
![](https://www.planttext.com/api/plantuml/png/f5F1IiCm6BxdAVwRUjWB32g3APimX-04hsaQssgJZ2Gjz2WUF8XF8CA6U7FWGH1QP8U2xv4dy1LCPLQtTegOGqZ-Fz_tV__taxTytb4QInsp2Acpa8CKYYA4YHOITjau4YcrzmtOeISXfw1YLwLAKwQGAsBkOPd2A6IKOEaTxVKnzo8g4H5SIn5LcKCgav3G1Us15AUKw7tCiKyPvHeXnu5XOBBP6FpGvBSG5HC6YJrU4d0SX3wLG6kxNgwz5ejgRxyJB5IruTZaCmjxgJAmgOi71e4msJC1RRAf06Roct0BhO1Blbe_RHYOx3u53_C0L34b0NG3B7qAmvYvL2fKWq2hITX8ckmE4fEVhn8qo6ZmfMzTkE2W0vDVhJByvcdNWgxvCWgIOWByVsOFNX_ZAlen-PwrF_polfmtZZGCJJQFmLzA8h3hXzwhAhq_mTPPfeFYYVlW5dR-zZonuoHb155kfNViNlwRTm000F__0m00)
### 3. Mô tả hành vi lưu trữ
- Employee (Người dùng) sẽ tương tác với hệ thống thông qua TimecardUIHandler để nhập thông tin giờ làm việc.
- TimecardUIHandler xử lý đầu vào từ người dùng và gửi yêu cầu đến TimecardService để tìm hoặc tạo một Timecard.
- Hành vi lưu trữ tại bước này:
  - Nếu Timecard chưa tồn tại cho nhân viên, TimecardService sẽ tạo một bản ghi Timecard mới trong cơ sở dữ liệu thông qua các thao tác nội bộ.
  - Nếu Timecard đã tồn tại, nó sẽ được tìm kiếm và lấy từ cơ sở dữ liệu thông qua TimecardDAO (hoặc các thao tác liên quan trong hệ thống).
### 4. Tinh chỉnh mô tả luồng sự kiện
- Nhập giờ làm việc:
   - Nhân viên nhập giờ làm việc qua TimecardUIHandler.
   - TimecardService xử lý Timecard (tìm hoặc tạo mới) và lấy danh sách mã chi phí từ ProjectManagement.
   - Nhân viên chọn mã chi phí và nhập giờ làm việc.
- Lưu và Gửi Timecard:
   - TimecardService lưu thông tin Timecard.
   - Nếu cần gửi Timecard, TimecardService hoàn tất việc gửi và thông báo kết quả.
### 5. Hợp nhất các lớp và hệ thống con
- Hợp nhất TimecardUIHandler và TimecardService
   - TimecardUIHandler chịu trách nhiệm giao diện và nhận dữ liệu từ nhân viên.
   - TimecardService xử lý nghiệp vụ Timecard, bao gồm tạo mới, lưu trữ và gửi.
     
Hai thành phần này có thể được hợp nhất thành một lớp duy nhất: TimecardProcessor, giúp xử lý cả giao diện và logic liên quan đến Timecard.
-  Hợp nhất tương tác với ProjectManagement
   - ProjectManagement chỉ cung cấp mã chi phí để xử lý Timecard.
     
Thay vì duy trì thành một hệ thống con riêng biệt, chức năng này có thể tích hợp vào TimecardProcessor, giảm sự phức tạp và phụ thuộc.
## II. Ca sử dụng Run Payroll
### 1. Mô tả sự tương tác giữa các đối tượng thiết kế
- Tác nhân: SystemClock, Printer và BankSystem
### 2. Đơn giản hóa sơ đồ trình tự bằng hệ thống con
![](https://www.planttext.com/api/plantuml/png/R591RiCW4BppYhsrFVG3bbn5JNAtaXTWs5XMC4JB4iblww5FoXU22pYMtHFip38xi-BnyxlpB8d3O8HKx0ZEesSSziQfAqWF_bNcXePwoqWJUKlNJ7nBUqsl9wwTAw6SPN866Zd6m-nJQRB66XHQicobHpWED-D6n4C1OZkkC27Uu82NtY8CI1rgyA5Dfk4IJMNvQDKfz5wqBbWjQIncceIxfPSP4wAkuJpjfxH3vg2knM8ryFcr3L81KzzrIATWy_FtZp_94qO6xw-47gJLitQP5MTiH1UJPfjLILUcg424bkEEC0qyJkhR1F-eH_b5hcgzlzvse5nqZOnYXrPF7-S9003__mC0)
### 3. Mô tả hành vi lưu trữ
- Lấy thông tin nhân viên từ EmployeeDatabase.
- Tính toán lương bằng cách kết hợp TimeCard và PurchaseOrder.
- Lưu trữ kết quả tính lương vào Paycheck.
- Xử lý và lưu trữ phương thức thanh toán, bao gồm việc in phiếu lương hoặc chuyển khoản qua ngân hàng.
- Cập nhật trạng thái quy trình trả lương trong cơ sở dữ liệu để theo dõi quá trình.
### 4. Tinh chỉnh mô tả luồng sự kiện
- PayrollController nhận lệnh từ SystemClock để bắt đầu trả lương.
- Lấy danh sách nhân viên từ EmployeeDatabase.
- Tính toán lương cho từng nhân viên bằng cách lấy thông tin từ TimeCard và PurchaseOrder.
- Dựa trên phương thức thanh toán, in phiếu lương qua Printer hoặc chuyển tiền qua BankSystem.
- Hoàn tất quy trình và thông báo kết quả.
### 5. Hợp nhất các lớp và hệ thống con
- PayrollController gộp các lớp và đối tượng sau:
   - Employee: Trực tiếp truy xuất và xử lý thông tin nhân viên từ EmployeeDatabase.
   - TimeCard và PurchaseOrder: Trực tiếp lấy dữ liệu và tính toán lương.
   - Paycheck: Xử lý và tạo phiếu lương sau khi tính toán.
- Printer và BankSystem: Tích hợp vào trong PayrollController, giúp xử lý phương thức thanh toán trực tiếp.
Kết quả là quy trình trả lương được đơn giản hóa và xử lý trong một lớp duy nhất (PayrollController), giảm thiểu sự phân tách giữa các lớp và giúp dễ dàng quản lý và mở rộng trong tương lai.
