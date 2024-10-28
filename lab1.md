# Lab 1: Phân tích kiến trúc và ca sử dụng hệ thống "Payroll System"

## 1. Phân tích kiến trúc
- **Đề xuất kiến trúc**: Three-tier architecture
- **Lý do lựa chọn**:
    - **Tách biệt rõ ràng các chức năng và nhiệm vụ**: Mỗi lớp thực hiện một nhiệm vụ cụ thể, giúp hệ thống dễ quản lý và bảo trì. Nếu cần sửa đổi hoặc nâng cấp, chỉ cần thao tác trên lớp tương ứng mà không ảnh hưởng đến các lớp khác.
    - **Tăng khả năng mở rộng (Scalability)**: Tầng Base Reuse Layer giúp tái sử dụng mã nguồn và thư viện, cho phép mở rộng hệ thống dễ dàng.
    - **Dễ dàng triển khai và quản lý**: Presentation Layer cung cấp giao diện thân thiện trên desktop, phù hợp với nhu cầu sử dụng hàng ngày của nhân viên. Tầng Base Reuse Layer giúp quản lý các kết nối bên ngoài (ví dụ: kết nối ngân hàng) một cách tập trung và thuận tiện.
    - **Đảm bảo tính bảo mật và phân quyền**: Base Reuse Layer cung cấp các cơ chế xác thực, phân quyền và bảo mật, giúp đảm bảo tính an toàn cho hệ thống.
- **Ý nghĩa từng thành phần**:
    - **Presentation Layer**: Là tầng giao diện người dùng, trách nhiệm của nó là giao tiếp với người dùng, hiển thị dữ liệu và nhận đầu vào từ người dùng.
    - **Business Logic Layer**: Tầng này xử lý các yêu cầu thao tác dữ liệu từ Presentation Layer và thực hiện các quy tắc và logic của doanh nghiệp trước khi truyền dữ liệu xuống Data Access Layer.
    - **Data Access Layer**: Đây là tầng quản lý việc truy cập vào cơ sở dữ liệu, nơi mà các dữ liệu thực tế được lưu trữ và xử lý.
    - **Base Reuse Layer**: Tầng này thường chứa các thành phần có thể tái sử dụng, giúp giảm thiểu mã lặp lại và tăng cường khả năng bảo trì cho ứng dụng.
- **Biểu đồ package**:
   ![Diagram](https://www.planttext.com/api/plantuml/png/T99FIWCn58VtESMZ-xb05wNLKZjOi3ZEGiH59XFQq3If-LCTn9KB5nx00nGH177VGRheIN82hs1c1kgCjLaaaE_zlhm7-SutNMsmCdRE4T8p9a19JH4op70AOvmfoJdq59aoGucnohC59ZCyeT0QAwgfCDWmAM24CwfQS8_0BoBd2oayWwiul0Qi8Gx_WcCfJ66dgYmWXgE7clm8QmhdrFhzeDempam60oj8qOEkNXe0D4rMCq6rXf6SC5BP_jD5L2qPeQKaQXZws63e4L9A3ZJJxvsLIN_k8HzF_3WbJvD27OT1Acz5qF5Zj-74vHyCKfT_0cSkVxB8NmTs4NJYi0r3V_Kem4nT_WmpjzuOkB5klK9bLQM9sd2vVRT0tFhDmftt0Tz-eQYGL8-SreFnO9SRklm5Z7Bvgghk-04QidfRdks25ygh6hI6qyHpcy7IhLy5IfDVytwiIqNg_zyF0000__y30000)
  
## 2. Cơ chế phân tích
- **Persistency** *(Cơ chế bền vững)*: Đảm bảo rằng dữ liệu về thông tin nhân viên, thời gian làm việc, thông tin lương được lưu trữ bền vững trong cơ sở dữ liệu để có thể truy cập và sử dụng về sau.
- **Communication** *(Cơ chế trao đổi thông tin)*: Ngoài việc giao tiếp giữa các thành phần trong hệ thống, cần có khả năng liên kết và trao đổi dữ liệu với các hệ thống bên ngoài, ví dụ như ngân hàng để thực hiện các giao dịch chuyển khoản lương cho nhân viên.
- **Information Exchange and Format Conversion** *(Trao đổi dữ liệu và đổi định dạng)*: Hệ thống phải có khả năng tương tác với các phần mềm khác và có khả năng chuyển đổi giữa các định dạng dữ liệu khác nhau. Điều này sẽ nâng cao khả năng tích hợp và giao lưu thông tin của hệ thống.
- **Security** *(Cơ chế bảo mật)*: Cần phải bảo vệ thông tin nhạy cảm của nhân viên, chẳng hạn như thông tin lương và thông tin tài khoản ngân hàng, khỏi các sự cố xâm nhập và đảm bảo quyền truy cập hợp lệ. Các biện pháp này có thể bao gồm xác thực đa yếu tố, mã hóa dữ liệu và kiểm soát quyền truy cập.
- **Error Detection/Handling/Reporting** *(Cơ chế phát hiện, xử lý và thông báo lỗi)*: Hệ thống nên có chức năng phát hiện lỗi trong quá trình tính toán lương hoặc trong giao tiếp dữ liệu, và cung cấp các thông báo lỗi rõ ràng để hỗ trợ việc kiểm soát và khắc phục vấn đề. 
- **Legacy Interface** *(Cơ chế kết nối với hệ thống cũ)*: Tích hợp với hệ thống cơ sở dữ liệu quản lý dự án hiện có (DB2) để truy xuất thông tin mà không làm thay đổi nó. Điều này sẽ giúp tiết kiệm chi phí và thời gian cho việc triển khai hệ thống mới.
## 3. Phân tích ca sử dụng Payment

## 4. Phân tích ca sử dụng Maintain Timecard
## 5. Hợp nhất kết quả phân tích
