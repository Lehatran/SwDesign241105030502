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
## 3. Phân tích ca sử dụng Payment
## 4. Phân tích ca sử dụng Maintain Timecard
## 5. Hợp nhất kết quả phân tích
