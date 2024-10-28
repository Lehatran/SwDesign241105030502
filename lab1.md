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
   ![Diagram]([https://www.planttext.com/api/plantuml/png/T99FIWCn58VtESMZ-xb05wNLKZjOi3ZEGiH59XFQq3If-LCTn9KB5nx00nGH177VGRheIN82hs1c1kgCjLaaaE_zlhm7-SutNMsmCdRE4T8p9a19JH4op70AOvmfoJdq59aoGucnohC59ZCyeT0QAwgfCDWmAM24CwfQS8_0BoBd2oayWwiul0Qi8Gx_WcCfJ66dgYmWXgE7clm8QmhdrFhzeDempam60oj8qOEkNXe0D4rMCq6rXf6SC5BP_jD5L2qPeQKaQXZws63e4L9A3ZJJxvsLIN_k8HzF_3WbJvD27OT1Acz5qF5Zj-74vHyCKfT_0cSkVxB8NmTs4NJYi0r3V_Kem4nT_WmpjzuOkB5klK9bLQM9sd2vVRT0tFhDmftt0Tz-eQYGL8-SreFnO9SRklm5Z7Bvgghk-04QidfRdks25ygh6hI6qyHpcy7IhLy5IfDVytwiIqNg_zyF0000__y30000](https://www.planttext.com/api/plantuml/png/T99FIWCn58VtESMZ-xb05wNLKZjOi3ZEGiH59XFQq3If-LCTn9KB5nx00nGH177VGRheIN82hs1c1kgCjLaaaE_zlhm7-SutNMsmCdRE4T8p9a19JH4op70AOvmfoJdq59aoGucnohC59ZCyeT0QAwgfCDWmAM24CwfQS8_0BoBd2oayWwiul0Qi8Gx_WcCfJ66dgYmWXgE7clm8QmhdrFhzeDempam60oj8qOEkNXe0D4rMCq6rXf6SC5BP_jD5L2qPeQKaQXZws63e4L9A3ZJJxvsLIN_k8HzF_3WbJvD27OT1Acz5qF5Zj-74vHyCKfT_0cSkVxB8NmTs4NJYi0r3V_Kem4nT_WmpjzuOkB5klK9bLQM9sd2vVRT0tFhDmftt0Tz-eQYGL8-SreFnO9SRklm5Z7Bvgghk-04QidfRdks25ygh6hI6qyHpcy7IhLy5IfDVytwiIqNg_zyF0000__y30000))
  
## 2. Cơ chế phân tích
- **Persistency** *(Cơ chế bền vững)*: Đảm bảo rằng dữ liệu về thông tin nhân viên, thời gian làm việc, thông tin lương được lưu trữ bền vững trong cơ sở dữ liệu để có thể truy cập và sử dụng về sau.
- **Communication** *(Cơ chế trao đổi thông tin)*: Ngoài việc giao tiếp giữa các thành phần trong hệ thống, cần có khả năng liên kết và trao đổi dữ liệu với các hệ thống bên ngoài, ví dụ như ngân hàng để thực hiện các giao dịch chuyển khoản lương cho nhân viên.
- **Information Exchange and Format Conversion** *(Trao đổi dữ liệu và đổi định dạng)*: Hệ thống phải có khả năng tương tác với các phần mềm khác và có khả năng chuyển đổi giữa các định dạng dữ liệu khác nhau. Điều này sẽ nâng cao khả năng tích hợp và giao lưu thông tin của hệ thống.
- **Security** *(Cơ chế bảo mật)*: Cần phải bảo vệ thông tin nhạy cảm của nhân viên, chẳng hạn như thông tin lương và thông tin tài khoản ngân hàng, khỏi các sự cố xâm nhập và đảm bảo quyền truy cập hợp lệ. Các biện pháp này có thể bao gồm xác thực đa yếu tố, mã hóa dữ liệu và kiểm soát quyền truy cập.
- **Error Detection/Handling/Reporting** *(Cơ chế phát hiện, xử lý và thông báo lỗi)*: Hệ thống nên có chức năng phát hiện lỗi trong quá trình tính toán lương hoặc trong giao tiếp dữ liệu, và cung cấp các thông báo lỗi rõ ràng để hỗ trợ việc kiểm soát và khắc phục vấn đề. 
- **Legacy Interface** *(Cơ chế kết nối với hệ thống cũ)*: Tích hợp với hệ thống cơ sở dữ liệu quản lý dự án hiện có (DB2) để truy xuất thông tin mà không làm thay đổi nó. Điều này sẽ giúp tiết kiệm chi phí và thời gian cho việc triển khai hệ thống mới.
## 3. Phân tích ca sử dụng Payment
- **Xác định các lớp phân tích**:
  - **PaymentUIHandler**: Lớp này quản lý giao diện và tương tác với người dùng.
  - **PaymentService**: Xử lý logic nghiệp vụ liên quan đến việc thay đổi phương thức thanh toán.
  - **Employee**: Đại diện cho thông tin của nhân viên, bao gồm phương thức thanh toán hiện tại.
  - **PaymentMethod**: Đại diện cho thông tin thanh toán
  - **PaymentDao**: Truy cập và tương tác với cơ sở dữ liệu.
- **Nhiệm vụ của các lớp phân tích**:
    - **PaymentView**: Nhận lựa chọn từ nhân viên, hiển thị kết quả hoặc thông báo lỗi.
    - **PaymentService**: Điều phối quá trình lựa chọn phương thức thanh toán, kiểm tra dữ liệu hợp lệ, và chuyển thông tin đến lớp truy cập dữ liệu.
    - **Employee**: Đại diện cho thông tin của nhân viên, bao gồm phương thức thanh toán hiện tại.
    - **PaymentMethod**: Lưu thông tin về phương thức thanh toán đã chọn.
    - **PaymentDAO**: Truy xuất và lưu thông tin về nhân viên và phương thức thanh toán vào cơ sở dữ liệu.
- **Biểu đồ Sequence**:
  ![Diagram](https://www.planttext.com/api/plantuml/png/f5CnJiCm5DrzYgzEPU027L218hL32n8mC9haWwscTXIxaJeY9bGnz0Of30Wa90QcPEXWr7lu15m1Dsb4YagfX0VB_zll_VUVxSzirbIQHdeu28ZgSm6HL4YefsK4HuCma2D4GaYvXDqzEA6Z0GfztcbJuGSODU2GsUnUb1lGHSsaJtwUgs1FCOgvXmrG6A2dbza2Lozow1VX3bd5L5XQ-ySDkEB2BzKTZ3f-7PT1vnlg3guhVXRPz15YczrKMgM1XfvDPqFmYgv2Dd-RJyKrQ1S_Ur3hKXxK2BZngxAADnVcnL7Pz6a8WjdqDOIFYSt6DAU_osasczjRWqBXRwEqnIFd9BGmb8hh_sWMr-P103E9OuzD0ifc4z0cuT1dqhaejc_aRwgykysthcYCgw-chBtXlLIqjBdDRaLkrDZDvjs9kJHJkLWdWe6to92cKxBu65y0003__mC0)
- **Biểu đồ lớp**:
  ![Diagram](https://www.planttext.com/api/plantuml/png/V59BJiCm4Dtd55PNxI8BjbbK1O545hI8mW6cyT1Qs1FBdw08SJ8M78ahqAQnavWARwnvytbldltpzRso3eppIcPP9S5QTgUqh5j4zf6nuycPu0KJvFg8G671jiu8slSGS6xGsWJLq2eazu3kK1ydF8x3x3EmJU18gRhmkTKfrGxeRNr1GLNLdjpQgnsQc4j9jcWQKON56BCeiN8J1VD5dsj02WuEIzBUHTJh4vPsf3otrvl8yIg81qTlsfBFiG_AiwkB8XeUL46JC8IMeVGlvqjv3yGbcc6xG_s-qKxKPAD-BgoMq3wXzTATbSVddbtDM9vtr_HH2kOjMhRC4XlpV3dUE2qR58qAG-z_CwEYWYaWs7TrsGg9dtxfBm000F__0m00)
- **Giải thích về biểu đồ lớp:**
    - Employee: Đại diện cho thông tin của nhân viên, bao gồm ID, tên, địa chỉ, và phương thức thanh toán.
    - PaymentMethod: Lưu trữ thông tin về phương thức thanh toán mà nhân viên chọn, bao gồm loại phương thức, tên ngân hàng và số tài khoản.
    - PaymentService: Chịu trách nhiệm về các hoạt động liên quan đến thanh toán, như chọn phương thức thanh toán và cập nhật thông tin.
    - PaymentDAO: Đảm nhận việc truy xuất và lưu thông tin nhân viên và phương thức thanh toán từ cơ sở dữ liệu.
    - PaymentUIHandler: Quản lý giao diện người dùng, hiển thị các lựa chọn và thông báo kết quả.
    
## 4. Phân tích ca sử dụng Maintain Timecard
- **Xác định các lớp phân tích**:
   - **Employee**: Đại diện cho nhân viên, có trách nhiệm nhập thời gian làm việc và quản lý timecard.
   - **Timecard**: Lưu trữ thông tin về giờ làm việc của nhân viên, bao gồm thời gian bắt đầu, thời gian kết thúc, số giờ đã làm, và trạng thái (submitted, editable).
   - **ChargeNumber**: Đại diện cho các mã số dự án mà giờ làm việc được ghi lại, liên kết với timecard.
   - **TimecardService**: Chịu trách nhiệm quản lý các hoạt động liên quan đến timecard như tạo, lưu, và gửi timecard.
   - **TimecardDAO**: Đảm nhận việc truy xuất và lưu trữ thông tin timecard trong cơ sở dữ liệu.
   - **ProjectManagementDatabase**: Cung cấp danh sách các charge number cho nhân viên.
- **Nhiệm vụ của các lớp phân tích**:
- **Biểu đồ Sequence**:
  ![Diagram](https://www.planttext.com/api/plantuml/png/d5CzJiCm5DvzYZVIWGjaG0LQgGm49Ce17EUHcCPEPJj17H430sT0AcBk15CpTCX9V0AkWDiqKLJw0sI8dlpUz-Nv-xvy5OkkDbIPJ2H4ZxW4bMeab9bKGL-CatI2I4XTmV493Bb0HbLuUp6WCanGUU37TZuRGyHjyGf9EHMGk_APaH-pRO8RL3bdw464vZnJ2gMfMqUu_k15s24RyssAtkcL1tTSXlN1sQJV8BUIECJM7ORApjyXjyLZqoE49WPyErzaC8hBJna1Ap_0r6rmpvxTF60AgK4V7vfhTGXAnxi5TQtIUsJcaaeQeN1IzAYX0TLhUMAg8lGp4Q3IZcNdzA6xLKImPjedRSlUWJFpIOA9RV6ooV3VQ41UJe5LN7B5zSkmQ9fZesVjHQVjLMIB6V-3JJeB13SjZmuWLg7RiSO1w2vHJHMle7nBb_LKnYvgxgIAIzUzb__dDm000F__0m00)
- **Biểu đồ lớp**:
  ![Diagram](https://www.planttext.com/api/plantuml/png/h5FBJiCm4BpdArOzjOWSk5eeAhILg4G1gKYSNNj93RLJsUjA5UBBEF19_09k6hj9gt8YXpmsuzdP6VldwtleY5loUfLbOiMTWubUhwej8dna4AuSb6IW33LVXcjaC2UhJ5cN0D0GshlAM_TIsNUK_K7s6TcUbKR1hKniTRinfq2okpTLDFAajZmmCfZnzVLeoMs93rulq5x2D7GjqHO7NlBkI9dp2wsehQVDaJI9IdPdoa6Y4rQjILKc_JaPQevseqHq2g146dbhWnyHqSV6pUdUn05BYwD4li64fkRbW1fq9laJU29lVFEOfBqg8sFzTZj9glv1OEhxPAit53JZXfUeWmiXJBxWhcjGAm3N3-tkbQDEjCMECUt2tbKFyhn-fBt4GDSz71HPAaRWHQyRCWln6kBAjD4nkJmlEdOny0xF0S_Fnu0BWMw_D1k6tRmxKBy0003__mC0)
- **Giải thích về biểu đồ lớp:**
    - Employee: Lớp này lưu trữ thông tin nhân viên và có trách nhiệm nhập giờ làm việc.
    - Timecard: Lớp này lưu trữ thông tin liên quan đến giờ làm việc, bao gồm thời gian bắt đầu, thời gian kết thúc, và trạng thái.
    - ChargeNumber: Đại diện cho các mã số dự án, cho phép nhân viên ghi lại giờ làm việc cho từng dự án.
    - TimecardService: Lớp này quản lý các chức năng liên quan đến timecard, bao gồm việc lấy timecard hiện tại, lưu timecard, và gửi timecard.
    - TimecardDAO: Chịu trách nhiệm truy xuất và lưu trữ thông tin timecard trong cơ sở dữ liệu.
    - ProjectManagementDatabase: Cung cấp danh sách charge numbers cho nhân viên để họ có thể nhập thông tin giờ làm việc cho các dự án cụ thể.
## 5. Hợp nhất kết quả phân tích
