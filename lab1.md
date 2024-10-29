# Lab 1: Phân tích kiến trúc và ca sử dụng hệ thống "Payroll System"

## 1. Phân tích kiến trúc
- **1.1 Đề xuất kiến trúc**: Three-tier architecture
- **1.2 Lý do lựa chọn**:
    - **Tách biệt rõ ràng các chức năng và nhiệm vụ**: Mỗi lớp thực hiện một nhiệm vụ cụ thể, giúp hệ thống dễ quản lý và bảo trì. Nếu cần sửa đổi hoặc nâng cấp, chỉ cần thao tác trên lớp tương ứng mà không ảnh hưởng đến các lớp khác.
    - **Tăng khả năng mở rộng (Scalability)**: Tầng Base Reuse Layer giúp tái sử dụng mã nguồn và thư viện, cho phép mở rộng hệ thống dễ dàng.
    - **Dễ dàng triển khai và quản lý**: Presentation Layer cung cấp giao diện thân thiện trên desktop, phù hợp với nhu cầu sử dụng hàng ngày của nhân viên. Tầng Base Reuse Layer giúp quản lý các kết nối bên ngoài (ví dụ: kết nối ngân hàng) một cách tập trung và thuận tiện.
    - **Đảm bảo tính bảo mật và phân quyền**: Base Reuse Layer cung cấp các cơ chế xác thực, phân quyền và bảo mật, giúp đảm bảo tính an toàn cho hệ thống.
 - **1.3 Ý nghĩa từng thành phần**:
    - **Presentation Layer**: Là tầng giao diện người dùng, trách nhiệm của nó là giao tiếp với người dùng, hiển thị dữ liệu và nhận đầu vào từ người dùng.
    - **Business Logic Layer**: Tầng này xử lý các yêu cầu thao tác dữ liệu từ Presentation Layer và thực hiện các quy tắc và logic của doanh nghiệp trước khi truyền dữ liệu xuống Data Access Layer.
    - **Data Access Layer**: Đây là tầng quản lý việc truy cập vào cơ sở dữ liệu, nơi mà các dữ liệu thực tế được lưu trữ và xử lý.
    - **Base Reuse Layer**: Tầng này thường chứa các thành phần có thể tái sử dụng, giúp giảm thiểu mã lặp lại và tăng cường khả năng bảo trì cho ứng dụng.
 - **1.4 Biểu đồ package**:
   ![Diagram](https://www.planttext.com/api/plantuml/png/T99FIWCn58VtESMZ-xb05wNLKZjOi3ZEGiH59XFQq3If-LCTn9KB5nx00nGH177VGRheIN82hs1c1kgCjLaaaE_zlhm7-SutNMsmCdRE4T8p9a19JH4op70AOvmfoJdq59aoGucnohC59ZCyeT0QAwgfCDWmAM24CwfQS8_0BoBd2oayWwiul0Qi8Gx_WcCfJ66dgYmWXgE7clm8QmhdrFhzeDempam60oj8qOEkNXe0D4rMCq6rXf6SC5BP_jD5L2qPeQKaQXZws63e4L9A3ZJJxvsLIN_k8HzF_3WbJvD27OT1Acz5qF5Zj-74vHyCKfT_0cSkVxB8NmTs4NJYi0r3V_Kem4nT_WmpjzuOkB5klK9bLQM9sd2vVRT0tFhDmftt0Tz-eQYGL8-SreFnO9SRklm5Z7Bvgghk-04QidfRdks25ygh6hI6qyHpcy7IhLy5IfDVytwiIqNg_zyF0000__y30000)
  
## 2. Cơ chế phân tích
- **Persistency** *(Cơ chế bền vững)*: Đảm bảo rằng dữ liệu về thông tin nhân viên, thời gian làm việc, thông tin lương được lưu trữ bền vững trong cơ sở dữ liệu để có thể truy cập và sử dụng về sau.
- **Communication** *(Cơ chế trao đổi thông tin)*: Ngoài việc giao tiếp giữa các thành phần trong hệ thống, cần có khả năng liên kết và trao đổi dữ liệu với các hệ thống bên ngoài, ví dụ như ngân hàng để thực hiện các giao dịch chuyển khoản lương cho nhân viên.
- **Information Exchange and Format Conversion** *(Trao đổi dữ liệu và đổi định dạng)*: Hệ thống phải có khả năng tương tác với các phần mềm khác và có khả năng chuyển đổi giữa các định dạng dữ liệu khác nhau. Điều này sẽ nâng cao khả năng tích hợp và giao lưu thông tin của hệ thống.
- **Security** *(Cơ chế bảo mật)*: Cần phải bảo vệ thông tin nhạy cảm của nhân viên, chẳng hạn như thông tin lương và thông tin tài khoản ngân hàng, khỏi các sự cố xâm nhập và đảm bảo quyền truy cập hợp lệ. Các biện pháp này có thể bao gồm xác thực đa yếu tố, mã hóa dữ liệu và kiểm soát quyền truy cập.
- **Error Detection/Handling/Reporting** *(Cơ chế phát hiện, xử lý và thông báo lỗi)*: Hệ thống nên có chức năng phát hiện lỗi trong quá trình tính toán lương hoặc trong giao tiếp dữ liệu, và cung cấp các thông báo lỗi rõ ràng để hỗ trợ việc kiểm soát và khắc phục vấn đề. 
- **Legacy Interface** *(Cơ chế kết nối với hệ thống cũ)*: Tích hợp với hệ thống cơ sở dữ liệu quản lý dự án hiện có (DB2) để truy xuất thông tin mà không làm thay đổi nó. Điều này sẽ giúp tiết kiệm chi phí và thời gian cho việc triển khai hệ thống mới.
## 3. Phân tích ca sử dụng Payment
- **3.1 Xác định các lớp phân tích**:
  - **Boundary class**: 
    - **PaymentUIHandler**: Lớp này quản lý giao diện và tương tác với người dùng.
  - **Control class**:
    - **PaymentService**: Xử lý logic nghiệp vụ liên quan đến việc thay đổi phương thức thanh toán.
  - **Entity class**:
    - **Employee**: Đại diện cho thông tin của nhân viên, bao gồm phương thức thanh toán hiện tại.
    - **PaymentMethod**: Đại diện cho thông tin thanh toán
  - **Data Access Object (DAO)**:
    - **PaymentDao**: Truy cập và tương tác với cơ sở dữ liệu.
- **3.2 Nhiệm vụ của các lớp phân tích**:
    - **PaymentView**: Nhận lựa chọn từ nhân viên, hiển thị kết quả hoặc thông báo lỗi.
    - **PaymentService**: Điều phối quá trình lựa chọn phương thức thanh toán, kiểm tra dữ liệu hợp lệ, và chuyển thông tin đến lớp truy cập dữ liệu.
    - **Employee**: Đại diện cho thông tin của nhân viên, bao gồm phương thức thanh toán hiện tại.
    - **PaymentMethod**: Lưu thông tin về phương thức thanh toán đã chọn.
    - **PaymentDAO**: Truy xuất và lưu thông tin về nhân viên và phương thức thanh toán vào cơ sở dữ liệu.
- **3.3 Biểu đồ Sequence**:
  
  ![Diagram](https://www.planttext.com/api/plantuml/png/f9E_JiCm4CPtFyMfKnbuWGweG97QeGK961ZTn3HMKpkodKWP4HEg6Fe6AGm892G6fcRe4DJty1Fm2ZZ_b41BgKI6AFVPzztlBlPdl6nBXONo9owIOyf0S4aGjXGNS3BnN1uIWeRSPpOM8PpXS4AOkknrCRDT8W3BDGrPd2d1tNBXd8Y0MgIsjL2GZHKUOabAlNDuMjjb8eHA1DW_M2lKWcD7n_UiN80-KGwtqHfabLjKRe4aBh5KeUPvpLmZTXxkeH_ybOiXQy4rPNP9TnJsx2OfWbwLcZQqeVY5q8j727HyKuqOOLV1G2-MFbXvLvwpUblDsGYKYPyjQFGnTHi8pFChMMqsLycBiTAB9n-OenUl7dpCT3p5cVrTPhDzk8CDMOJPkv1sg32JX0xnkAJgFynib3mmS9B8k0T915B7Cr19H67iS3D5jdiZVrjbtMt_wn87vFkfAMjlEIyrbYxLyItB1ZKrx-JTm0oJEK-_8-Q0bIgeRKZI2_a5003__mC0)
- **3.4 Biểu đồ lớp**:
  
  ![Diagram](https://www.planttext.com/api/plantuml/png/V59BJiCm4Dtd55PNxI8BjbbK1O545hI8mW6cyT1Qs1FBdw08SJ8M78ahqAQnavWARwnvytbldltpzRso3eppIcPP9S5QTgUqh5j4zf6nuycPu0KJvFg8G671jiu8slSGS6xGsWJLq2eazu3kK1ydF8x3x3EmJU18gRhmkTKfrGxeRNr1GLNLdjpQgnsQc4j9jcWQKON56BCeiN8J1VD5dsj02WuEIzBUHTJh4vPsf3otrvl8yIg81qTlsfBFiG_AiwkB8XeUL46JC8IMeVGlvqjv3yGbcc6xG_s-qKxKPAD-BgoMq3wXzTATbSVddbtDM9vtr_HH2kOjMhRC4XlpV3dUE2qR58qAG-z_CwEYWYaWs7TrsGg9dtxfBm000F__0m00)
- **3.5 Giải thích về biểu đồ lớp:**
    - Employee: Đại diện cho thông tin của nhân viên, bao gồm ID, tên, địa chỉ, và phương thức thanh toán.
    - PaymentMethod: Lưu trữ thông tin về phương thức thanh toán mà nhân viên chọn, bao gồm loại phương thức, tên ngân hàng và số tài khoản.
    - PaymentService: Chịu trách nhiệm về các hoạt động liên quan đến thanh toán, như chọn phương thức thanh toán và cập nhật thông tin.
    - PaymentDAO: Đảm nhận việc truy xuất và lưu thông tin nhân viên và phương thức thanh toán từ cơ sở dữ liệu.
    - PaymentUIHandler: Quản lý giao diện người dùng, hiển thị các lựa chọn và thông báo kết quả.
    
## 4. Phân tích ca sử dụng Maintain Timecard
 - **4.1 Xác định các lớp phân tích**:
   - **Boundary**:
     - **TimecardUIHandler**: Quản lý giao diện người dùng và nhận thông tin từ nhân viên.
     - **ProjectManagementDatabase**: Cung cấp thông tin về charge numbers cho người dùng.
    - **Control**:
     - **TimecardService**: Chịu trách nhiệm quản lý các hoạt động liên quan đến timecard như tạo, lưu, và gửi timecard.
    - **Entity**:
     - **Employee**:Đại diện cho nhân viên trong hệ thống, có khả năng nhập và cập nhật thông tin thời gian làm việc.
     - **Timecard**: Lưu trữ thông tin về số giờ làm việc của nhân viên trong một khoảng thời gian nhất định.
     - **ChargeNumber**:  Đại diện cho mã số dự án mà nhân viên ghi nhận giờ làm việc.
   - **TimecardDAO**: Cung cấp các phương thức tương tác với cơ sở dữ liệu liên quan đến timecard.
   
 - **4.2 Nhiệm vụ của các lớp phân tích**:
   - **TimecardUIHandler**: Nhận số giờ làm việc từ nhân viên, hiển thị thông báo thành công hoặc lỗi.
   - **ProjectManagementDatabase**: Cung cấp danh sách các charge number để nhân viên ghi nhận thời gian.
   - **TimecardService**: Quản lý logic nghiệp vụ liên quan đến việc tạo mới, lưu và gửi timecard, đồng thời kiểm tra tính hợp lệ của dữ liệu.
   - **Employee**: Nhập số giờ làm việc và gửi timecard cho kỳ hiện tại.
   - **Timecard**: Quản lý số giờ làm việc và trạng thái của từng kỳ.
   - **ChargeNumber**: Cung cấp thông tin mã dự án để phân bổ thời gian làm việc.
   - **TimecardDAO**: Thực hiện các truy vấn tìm kiếm và lưu trữ thông tin timecard vào cơ sở dữ liệu.
 - **4.3 Biểu đồ Sequence**:
  
  ![Diagram](https://www.planttext.com/api/plantuml/png/d5GzJiCm6DrzYc-a0nU8L5HeAzeb854Eu3WcCKtiod62EY861iGHa8gOEy7K30mvIKx05N2RtwO_GMI8R7_VUtd-tbD-ukzUeB1KeU-XOCeuI15GX31HGiBGdtbYJcc-lPRYdX8rm0fRUDrbYP3RMCvXmdnAiBHlnoFCROzAH0HNKdXbvORAY16AA5TCLO1YttUnTAWP-fR6Dde6vrS8TRjWkkbgEGE7fV4RUCd2XqWldmbqkmWLKk7qR5UDSH2BTdhh1Bbe0nog-g6KMbXHEg7v1yTs1pNwwnHQl05tZDl5mSLyM2BtacZ4NWqJcQu-84hZnsfw27iAp7Jr7SBKJRwu0oJvhCgWdoFQ322IOaLD-b1UgwEdhtdte1hkPqEfsHPeRAEdxHuP77ByiJ7Mh1nfuvuuA3UDNveC_uq1HCa2Y6PyvTkKVyn7W2DQZb3bYyucjPTfl6GbOfFLoZHdgzZkLn1QFbCrireGc_GT4DS2FJHnbUNCIjx5UhtWhiwSFiboqzFlzQ_a5m00__y30000)
  
 - **4.4 Biểu đồ lớp**:
  
  ![Diagram](https://www.planttext.com/api/plantuml/png/h5FBJiCm4BpdArOzjOWSk5eeAhILg4G1gKYSNNj93RLJsUjA5UBBEF19_09k6hj9gt8YXpmsuzdP6VldwtleY5loUfLbOiMTWubUhwej8dna4AuSb6IW33LVXcjaC2UhJ5cN0D0GshlAM_TIsNUK_K7s6TcUbKR1hKniTRinfq2okpTLDFAajZmmCfZnzVLeoMs93rulq5x2D7GjqHO7NlBkI9dp2wsehQVDaJI9IdPdoa6Y4rQjILKc_JaPQevseqHq2g146dbhWnyHqSV6pUdUn05BYwD4li64fkRbW1fq9laJU29lVFEOfBqg8sFzTZj9glv1OEhxPAit53JZXfUeWmiXJBxWhcjGAm3N3-tkbQDEjCMECUt2tbKFyhn-fBt4GDSz71HPAaRWHQyRCWln6kBAjD4nkJmlEdOny0xF0S_Fnu0BWMw_D1k6tRmxKBy0003__mC0)
 - **4.5 Giải thích về biểu đồ lớp:**
    - Employee: Lớp này lưu trữ thông tin nhân viên và có trách nhiệm nhập giờ làm việc.
    - Timecard: Lớp này lưu trữ thông tin liên quan đến giờ làm việc, bao gồm thời gian bắt đầu, thời gian kết thúc, và trạng thái.
    - ChargeNumber: Đại diện cho các mã số dự án, cho phép nhân viên ghi lại giờ làm việc cho từng dự án.
    - TimecardService: Lớp này quản lý các chức năng liên quan đến timecard, bao gồm việc lấy timecard hiện tại, lưu timecard, và gửi timecard.
    - TimecardDAO: Chịu trách nhiệm truy xuất và lưu trữ thông tin timecard trong cơ sở dữ liệu.
    - ProjectManagementDatabase: Cung cấp danh sách charge numbers cho nhân viên để họ có thể nhập thông tin giờ làm việc cho các dự án cụ thể.
## 5. Hợp nhất kết quả phân tích
