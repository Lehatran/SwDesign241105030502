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
## 2. Cơ chế phân tích
## 3. Phân tích ca sử dụng Payment
## 4. Phân tích ca sử dụng Maintain Timecard
## 5. Hợp nhất kết quả phân tích
