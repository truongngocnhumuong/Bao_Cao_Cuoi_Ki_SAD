# BÁO CÁO CUỐI KÌ Mentcare: A mental health support system

## 1. Mô tả tóm tắt bài toán

Cơ quan y tế khu vực Mid-Scotland muốn mua một hệ thống thông tin để giúp quản lý việc chăm sóc bệnh nhân mắc các vấn đề về sức khỏe tâm thần. Mục tiêu chung của hệ thống là:

- Cung cấp thông tin quản lý tốt hơn về chăm sóc sức khỏe tâm thần trong khu vực.
- Cung cấp hệ thống hồ sơ được cải thiện cho đội ngũ nhân viên lâm sàng tham gia chẩn đoán và điều trị.
- *Chú ý: Hệ thống không nhằm mục đích là hệ thống hồ sơ y tế hoàn chỉnh, nơi lưu giữ mọi thông tin về quá trình điều trị y tế của bệnh nhân. Hệ thống chỉ nhằm mục đích hỗ trợ chăm sóc sức khỏe tâm thần (ví dụ: nếu bệnh nhân mắc một số tình trạng không liên quan khác, chẳng hạn như huyết áp cao, tình trạng này sẽ không được ghi nhận chính thức trong hệ thống). Do đó, hệ thống phải tương tác và chia sẻ thông tin với các hệ thống hồ sơ bệnh nhân khác đang được sử dụng.*

### Sự cần thiết

1. **Quản lý thông tin hiệu quả:** Hệ thống giúp quản lý thông tin bệnh nhân, từ thông tin cá nhân đến lịch sử điều trị, một cách hiệu quả và có tổ chức.
2. **Theo dõi điều trị:** Hỗ trợ theo dõi tình trạng điều trị của bệnh nhân, đảm bảo rằng không có bệnh nhân nào bị bỏ sót hay quên lịch hẹn.
3. **Quản lý giam giữ:** Đặc biệt quan trọng trong việc quản lý những bệnh nhân cần giam giữ bắt buộc vì lý do an toàn.

### Lợi ích khi giải quyết bài toán

1. **Cải thiện chất lượng chăm sóc:** Tăng cường khả năng cung cấp dịch vụ chăm sóc sức khỏe tâm thần chất lượng cao thông qua việc quản lý và theo dõi bệnh nhân hiệu quả.
2. **Tiết kiệm thời gian:** Giảm bớt thời gian tìm kiếm và cập nhật thông tin bệnh nhân cho các bác sĩ và nhân viên y tế.
3. **Đáp ứng pháp lý:** Đảm bảo tuân thủ các yêu cầu pháp lý về an toàn và quyền riêng tư của bệnh nhân.

### Các yêu cầu chức năng

1. **Quản lý chăm sóc cá nhân:**
   - Tạo, chỉnh sửa và xem hồ sơ bệnh nhân.
   - Ghi nhận các buổi tư vấn, tình trạng và phương pháp điều trị.
2. **Theo dõi bệnh nhân:**
   - Theo dõi thường xuyên tình trạng bệnh nhân.
   - Cảnh báo khi phát hiện các vấn đề có thể xảy ra hoặc khi bệnh nhân không gặp bác sĩ theo lịch hẹn.
3. **Quản lý giam giữ bắt buộc:**
   - Quản lý thông tin và tình trạng của những bệnh nhân bị giam giữ.
   - Đảm bảo tuân thủ quy trình pháp lý liên quan đến việc giam giữ.
4. **Báo cáo hành chính:**
   - Tạo các báo cáo quản lý hàng tháng.
   - Báo cáo về số lượng bệnh nhân, tình trạng bệnh, chi phí điều trị.

### Các yêu cầu phi chức năng

1. **An toàn:**
   - Cảnh báo cho nhân viên y tế về những bệnh nhân có nguy cơ tự tử hoặc gây nguy hiểm.
   - Đảm bảo hệ thống luôn khả dụng và có thể truy cập khi cần.
2. **Quyền riêng tư:**
   - Bảo mật thông tin bệnh nhân, chỉ cho phép nhân viên y tế được ủy quyền truy cập.
   - Ngăn chặn việc truy cập không hợp pháp vào thông tin cá nhân của bệnh nhân.
3. **Hiệu suất:**
   - Đảm bảo hệ thống hoạt động mượt mà với thời gian phản hồi nhanh chóng.
   - Khả năng xử lý lượng lớn dữ liệu và nhiều truy vấn cùng lúc.

## 2. Phân tích các ca sử dụng

### Kiến trúc đề xuất: Mô hình triển khai

Kiến trúc máy khách-máy chủ.

- **Máy khách:** Các nhân viên y tế và quản trị viên sẽ truy cập hệ thống qua trình duyệt web (Firefox) trên giao diện tương tác dạng biểu mẫu.
- **Máy chủ:** Lưu trữ hồ sơ bệnh nhân và xử lý yêu cầu từ máy khách, được vận hành trên các máy chủ Linux.

#### Lí do lựa chọn kiến trúc này

- **Phân quyền và bảo mật:** Nhân viên y tế và quản trị viên cần quyền truy cập khác nhau vào dữ liệu; máy chủ quản lý quyền này.
- **Tích hợp dễ dàng:** Hệ thống phải tích hợp với các hệ thống bên ngoài như PRESCRIPTION và hồ sơ bệnh án quốc gia.
- **Độ tin cậy cao:** Các yêu cầu về tính khả dụng trong giờ làm việc và tính bảo mật phù hợp với kiến trúc máy khách-máy chủ.

#### Biểu đồ package mô tả kiến trúc

![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWf9pJcPgNecIGZMNWa9qU6gIWbDHVdbnQb4iLoqNGbLmQb5PQX5KbME0Poo8TYejpinBBIvMyCbFpqn6rU2IM9AOb5YS2jKIa5W2iaOXA3KvloYb6ApTEISpBpCvCKS1f1Qi6yL-1LrTEwXTO1B2HxSJNG2Y2iCwxChGNE2GcfTIcfi30000__y30000)

### Các cơ chế phân tích

#### Yêu cầu hệ thống

- **Tính khả dụng:**
  - Hệ thống phải hoạt động liên tục trong giờ làm việc từ 08:00 - 18:30, từ Thứ Hai đến Thứ Sáu.
  - Bảo trì được sắp xếp ngoài giờ làm việc (21:00 - nửa đêm, hoặc Chủ Nhật 08:00 - 12:00).
- **Hiệu suất:**
  - Hệ thống phải phản hồi trong vòng 2 giây cho các truy vấn bệnh nhân thông thường.
  - Nếu phản hồi mất hơn 2 giây, hệ thống hiển thị trạng thái xử lý để tránh bực bội cho người dùng.

#### Cơ chế bảo mật

- Hệ thống phải đảm bảo quyền riêng tư dữ liệu bệnh nhân, chỉ cho phép nhân viên được ủy quyền truy cập.
- Tích hợp hệ thống xác thực đa yếu tố.

#### Cơ chế quản lý dữ liệu

- Dữ liệu được xác thực trước khi lưu, đặc biệt đối với các mục không chọn từ menu.
- Tất cả thông tin được lưu giữ tuân thủ các tiêu chuẩn bảo mật và quy định của hệ thống y tế Mid-Scotland.

### Kết quả phân tích từng ca sử dụng

#### **Quản lý chăm sóc cá nhân**

1. **Xác định các lớp phân tích**

Dựa trên yêu cầu của hệ thống Mentcare, các lớp phân tích cho ca sử dụng "Quản lý chăm sóc cá nhân" bao gồm:

- **BenhNhan:** Lớp đại diện cho bệnh nhân.
- **NhanVienLamSang:** Lớp đại diện cho nhân viên lâm sàng.
- **BuoiTuVan:** Lớp đại diện cho buổi tư vấn.
- **HoSoBenhNhan:** Lớp đại diện cho hồ sơ bệnh nhân.
- **ChanDoan:** Lớp đại diện cho chẩn đoán.
- **DieuTri:** Lớp đại diện cho phương pháp điều trị.
- **ThuocKeDon:** Lớp đại diện cho thuốc được kê đơn.
- **GioiThieu:** Lớp đại diện cho việc giới thiệu bệnh nhân đến các bộ phận khác.

2. **Mô tả hành vi thông qua biểu đồ sequence**

Dưới đây là biểu đồ sequence mô tả hành vi của ca sử dụng "Quản lý chăm sóc cá nhân":

![diagram](https://www.planttext.com/plantuml/png/d9AnQXj148RxVOeVztu15S7e13742a9UZDlp9MWNwLR7QK-zAnTk94mgDpw7514ngBujLEonxp5Fu5S8ksU13ya6gPvlvlzdvdyr6tOsqt6kYtJ2uaHFStmNzbbTIRjI5_OvlRHFQiIoEDSoaLciD4xEoJnSkh9Bvaw9G9yWdc4mR6FTWimloTtwYge_3HArYKXGzLVLYwajctglNQyNainjmNCozw7EstKk2ZBBv9jTrGltDgBVHhvACe-I2qdchWZ0aB4z6-Bq2mR33hZzbs8igTga46GUC7CbRiAcKBwD3OQUtJEY0vvJzHjpChSVz7wa77N0gIgdk0atWtPhpFtLa7hxBDhQk_2j65ErqRlitBC7AlSwuCAkKYJX5wYN_XcijnMCg7h9e0HLBxhDO6wVfWUgyQrQ9jpQbMg4JDWoGxqCZuRsdsPyh_XdBSTuwM-zw2P56DiLwgKh5UllDR33uGXL7x6WEWh1X6wIoKAeTYJRq35w8JHkNHmUvcjR9eqFXSdx2Upif_fHf9F_0000__y30000)

3. **Xác định nhiệm vụ của từng lớp phân tích**
   
- **BenhNhan:** Lưu trữ thông tin cá nhân của bệnh nhân như tên, địa chỉ, ngày sinh, liên hệ gia đình.
- **NhanVienLamSang:** Quản lý thông tin nhân viên lâm sàng và thực hiện các thao tác trên hồ sơ bệnh nhân.
- **BuoiTuVan:** Quản lý thông tin về buổi tư vấn, bao gồm ngày giờ, nhân viên lâm sàng tham gia, và các ghi chú tư vấn.
- **HoSoBenhNhan:** Lưu trữ toàn bộ thông tin về bệnh nhân, bao gồm chẩn đoán, phương pháp điều trị, thuốc kê đơn, và giới thiệu.
- **ChanDoan:** Quản lý thông tin về các chẩn đoán bệnh của bệnh nhân.
- **DieuTri:** Quản lý thông tin về các phương pháp điều trị được áp dụng cho bệnh nhân.
- **ThuocKeDon:** Quản lý thông tin về các loại thuốc được kê đơn cho bệnh nhân.
- **GioiThieu:** Quản lý thông tin về việc giới thiệu bệnh nhân đến các bộ phận khác.

4. **Xác định một số thuộc tính và quan hệ giữa các lớp phân tích**

- **BenhNhan**
  - Thuộc tính: `maBenhNhan`, `ten`, `diaChi`, `ngaySinh`, `thongTinLienHe`, `nguoiThan`
  - Quan hệ: 1 BenhNhan có nhiều HoSoBenhNhan

- **NhanVienLamSang**
  - Thuộc tính: `maNhanVien`, `ten`, `vaiTro`, `thongTinLienHe`
  - Quan hệ: 1 NhanVienLamSang có nhiều BuoiTuVan

- **BuoiTuVan**
  - Thuộc tính: `maBuoiTuVan`, `ngay`, `gio`, `ghiChu`
  - Quan hệ: 1 BuoiTuVan thuộc về 1 HoSoBenhNhan, 1 BuoiTuVan có nhiều NhanVienLamSang

- **HoSoBenhNhan**
  - Thuộc tính: `maHoSo`, `maBenhNhan`, `danhGiaRuiRo`
  - Quan hệ: 1 HoSoBenhNhan có nhiều ChanDoan, DieuTri, ThuocKeDon, GioiThieu

- **ChanDoan**
  - Thuộc tính: `maChanDoan`, `tinhTrang`, `ngay`, `ghiChu`
  - Quan hệ: 1 ChanDoan thuộc về 1 HoSoBenhNhan

- **DieuTri**
  - Thuộc tính: `maDieuTri`, `phuongPhap`, `ngay`, `ghiChu`
  - Quan hệ: 1 DieuTri thuộc về 1 HoSoBenhNhan

- **ThuocKeDon**
  - Thuộc tính: `maThuoc`, `tenThuoc`, `lieuLuong`, `ngay`, `ghiChu`
  - Quan hệ: 1 ThuocKeDon thuộc về 1 HoSoBenhNhan

- **GioiThieu**
  - Thuộc tính: `maGioiThieu`, `boPhan`, `ngay`, `ghiChu`
  - Quan hệ: 1 GioiThieu thuộc về 1 HoSoBenhNhan
5. **Biểu đồ lớp mô tả lớp phân tích và giải thích**

![diagram](https://www.planttext.com/plantuml/png/b591QiCm4Bph5SB7Ga9xzId4XWHgIeX5xjj4Q1ViLR2jGYbzMGzzKhzGd4QsvIGkEUumcftLpC_Nzw9ke6fSMOXz0NKjbvhn1O7bXv1Ibk3dMEPDHMnQjD71U218a8O86tZFYJ6MAJJwz0Gj6qMSaUQr3hdEaXfk-1HdB-tU7MdEeCo1ZRVauGbBRq2giW7Xke5krx9ruNQ3mpqmFgm_of2DfQBoRq1Aq5qAhsrknv_QOaFPwzzy0COLmTRHrbxg9WYSsbxJpy7HnAWgO3DnmmtRAMcdAlBgvt6eSqHdsMmGZlUhAtHs_wnJsza_8QD4Bx22jClQhVTlN57RCjBEB-o0UA3rQZUZ4FvJxwADdY8vcydeSJv_Y8BKnRZ7KK3jYYRw3eQCqNiHLEgMs0J9LsMASmvyYjA7ECNg_baiD1zSMVm2003__mC0)

#### **Theo dõi bệnh nhân**

1. **Xác định các lớp phân tích**

- **Hồ sơ bệnh nhân:** Quản lý thông tin cá nhân, lịch sử điều trị, và lịch hẹn của bệnh nhân.
  - Thuộc tính:
    - `ID bệnh nhân`: String
    - `Tên`: String
    - `Lịch sử điều trị`: List<DieuTri>
    - `Cuộc hẹn`: List<CuocHen>
  - Nhiệm vụ: Cung cấp thông tin về lịch sử điều trị và lịch hẹn để kiểm tra tuân thủ.
- **Trình theo dõi điều trị:** Kiểm tra và phát hiện các vấn đề liên quan đến tuân thủ điều trị.
  - Thuộc tính: `Tần suất kiểm tra`: int
  - Nhiệm vụ: Tự động kiểm tra hồ sơ bệnh nhân để phát hiện các vấn đề.
- **Cảnh báo:** Quản lý thông tin cảnh báo khi phát hiện vấn đề.
  - Thuộc tính:
    - `ID cảnh báo`: String
    - `Loại cảnh báo`: String
    - `Tin nhắn cảnh báo`: String
  - Nhiệm vụ: Ghi nhận và gửi cảnh báo cho nhân viên lâm sàng.
- **Nhân viên lâm sàn:** Người nhận cảnh báo và thực hiện hành động cần thiết.
  - Thuộc tính:
    - `ID nhân viên`: String
    - `Email`: String
  - Nhiệm vụ: Nhận cảnh báo và phản hồi.
- **Hệ thống lịch hẹn:** Tích hợp với hệ thống lịch hẹn bên ngoài để đối chiếu dữ liệu.
  - Thuộc tính: `Dữ liệu cuộc hẹn`: List<CuocHen>
  - Nhiệm vụ: Cung cấp thông tin lịch hẹn để kiểm tra tuân thủ.

2. **Biểu đồ sequence**

![PlantText](https://www.planttext.com/plantuml/png/ZLE_IiD06DyFxXq-EkdW2sIGqWeMMefWSRzUGkyWlIl9jU0e3XsSYfERgRY88g8E9eF3YUznR-ANDCMaLJJRST_lxtrfneP5PZeEAM7Sw0WQVM6N2cRItYa8xN8CiRrMemQm6Fg2gHCPA4ec299SJfWoq1X4zbu9C2BGuDjN2HyBwRApAPZ8PHS5SX199GOuSA3b1hhZiak8FnCOkcoED2hNBq0TVQnRWHAvx3PeZe8kMwWHXAZ21GYNlgs0FSb5PyjcswKto3-qYIwcsao95jEK5D7bZ9bWmsVr17lxDKCUz5nwUuecx0jwC5AXWH-IK595mHxIL6azFA4lc65XuBli4KBiRZxTuDZsKcRqe8lpvsFicjMAeAIS-Bza7OwjX0QEX4qCY7m0bm8JAtnT1582-6sQAYj51PSc6lXtux33XSIMNFfkgZoxAw8Ic7Eibyo3GvSzo7N11Kc5a98WZ0FehcwvVVxRNRs44falqHDV9nIuwwBWk58Zb50-9NxmoteqyRhuSxu0)

3. **Biểu đồ lớp**

![Diagram](https://www.planttext.com/plantuml/png/XLEzJiCm4DuhzHsiJa6qBn2XgYePEaGiYTXDOiKd4XibDX92p0myHK6CY8M5PkoJv4suf7RpKw9ck_k-ptVVtMLLA9ehdQNJIPJIeY0R6SWr4_o6Kq6UfnE2toN9gCsv950vYCGYYfsaKeXue3rWEip19JuKwif4oovdKqiRr3z4BKgV_EuZpiNOCmSYQe-KzgsNwSIwGetW8MVIaz2wKbG4cYgJTma8PQ5xO5cOqr3ltqN8jSDnB6vlEBRUDHLyJMM_dabs1sXIms492PuMoGYQIWeZaABI84x48GIcB6FUo6o4VHgULIRQlkd4zGfgDxV0X4-pW3Q2Hmbnpy-0qlLbeM5_BAEGdhX5yh5hwyia_gkxOI6N8Z4xRSl6siTByCyTaTUbZLr8x-8NYsN_M5moYt0_9AfsdmyahifllDsgVDKpLFQxEwDDg_8jueHNkr-1uXwpbjgRGPMgTbjPopu49tVxhKI-XMlgS1qeIQho2uZY-n-CZMJ5HDpysdy0)


4. Giải thích:
   - Hồ sơ bệnh nhân: Là nguồn dữ liệu chính, cung cấp lịch sử điều trị và lịch hẹn để kiểm tra tuân thủ.
   - Trình theo dõi điều trị:
     + Lớp chính thực hiện chức năng kiểm tra hồ sơ bệnh nhân.
     + Tương tác với Hồ sơ bệnh nhân và Hệ thống lịch hẹn để lấy dữ liệu cần thiết.
     + Tạo cảnh báo thông qua lớp Alert.
   - Cảnh báo: Quản lý thông tin cảnh báo và gửi đến Nhân viên lâm sàng.
   - Nhân viên lâm sàng: Nhận thông báo và thực hiện các hành động cần thiết.
   - Hệ thống lịch hẹn: Hỗ trợ đối chiếu lịch hẹn, đảm bảo kiểm tra đầy đủ thông tin.
6. Mối quan hệ giữa các lớp:
   - Hồ sơ bệnh nhân và Trình theo dõi điều trị: Quan hệ kết hợp: Trình theo dõi điều trị sử dụng dữ liệu từ Hồ sơ bệnh nhân.
   - Trình theo dõi điều trị và Cảnh báo: Quan hệ tạo: Trình theo dõi điều trị tạo cảnh báo thông qua Cảnh báo.
   - Cảnh báo và Nhân viên lâm sàng: Quan hệ giao tiếp: Cảnh báo gửi thông báo đến Nhân viên lâm sàng.
   - Trình theo dõi điều trị và Hệ thống lịch hẹn: Quan hệ tích hợp: Trình theo dõi điều trị lấy dữ liệu lịch hẹn từ Hệ thống lịch hẹn. 
### **Quản lý giam giữ bắt buộc:**
   1. Xác định các lớp phân tích:
      - Hồ sơ giam giữ: Quản lý thông tin về giam giữ của bệnh nhân.
        + Thuộc tính:
          - maGiamGiu: String 
          - ngayGiamGiu: Date 
          - lyDo: String 
          - trangThai: String
        + Nhiệm vụ: Lưu trữ và quản lý thông tin giam giữ.
      - Quản lý giam giữ: Điều phối quá trình ghi nhận và cập nhật thông tin giam giữ.
        + Thuộc tính: danhSachGiamGiu: List(HosoGiamGiu)
        + Nhiệm vụ:
          - Xác minh tính hợp lệ của thông tin nhập vào.
          - Lưu trữ thông tin giam giữ vào cơ sở dữ liệu.
          - Gửi nhắc nhở về các cuộc kiểm tra định kỳ.
      - Nhân viên lâm sàng: Người cập nhật thông tin giam giữ của bệnh nhân.
        + Thuộc tính:
          - maNhanVien: String
          - ten: String
        + Nhiệm vụ: Nhập thông tin giam giữ và gửi yêu cầu cập nhật.
       
      - Thông báo: Quản lý các thông báo nhắc nhở kiểm tra định kỳ.
        + Thuộc tính:
          - maThongBao: String 
          - noiDungThongBao: String 
          - ngayThongBao: Date 
        + Nhiệm vụ: Gửi thông báo đến nhân viên lâm sàng.
       
      - Tuân thủ pháp luật: Đảm bảo hệ thống tuân thủ các quy định pháp lý.
        + Thuộc tính: quyDinhHienHanh: String
        + Nhiệm vụ: Kiểm tra tính hợp lệ của thông tin theo các quy định pháp luật.
   3. Biểu đồ sequence:

   ![PlantText](https://www.planttext.com/plantuml/png/XPAxQiCm58PtWz_X9tjUm4C9xP10GcXewAwwnX9nP3UM0faxTCXKEdHiBaCW459efvZIGINleJUfvE3MkPHwa8Kvtw_l7BcM2Z8GiX-v3l55F42bJTMCOyZKaYDIipvIDU5X1IH5cn9-pGBkEec1cCyImWKg7QatSrlyWP2Hlbbqjiw1ZYIyDQgRZtKc3wY6pfwGRgU7J2E-YayJNQhUUOWRDOtpoYwDUNXEuiCoQHiGL6SB95HD4qH6S2LovfAIf2M9S1tNATf1zMpVrCE50H9mQZaJbPyh62-vkiuUOZEAR0zDKt7VXnWG2BNY54PcRZnqzk0wHHcgn-SszUPJuCuE5BsV42jB8e7khqWv4EOvaYcDqKDh-oh_QkCaNOpMGrrdAvPFOktRL_PI4iFNeyx6fh-UpjvS9uZIe2pPsst_TIqkmaF3HkykRso9PuQXcc2abXA-tYmaKkDZ1XBmMzUfcJN_TRy1)


   
   4. Biểu đồ lớp:


   ![Diagram](https://www.planttext.com/plantuml/png/XPF1Qi9048RlWk-mUB8KNq2AI17CGOHYw7rDmkvYCXkJNK5AJts4Fa2hFHGAugKdGq-1laVUf9FWQff4p6LX_vdPR-QV36D58wK3lzroV1h7nCgIr_XtmmGDcCYIFNbgjmX-joIWOxmS2zqdCnK9O4O0HjSdQKILPmH_FPBLO1LHO3QdeYhuMbjo9hitVRAImZNN3WsddAh_qdExPNWVT7Ru03_zQI1sAV0PTVW9RY9YTLVjS6325y8Bx8ZQN2AXW2xZ25cDHeQvbBv7mQGnBOgKUzfCEENf5bOY_KBARH2dxy3AGyNku55uK1jK_Geu3GtTiQUBa3KCcwVVmERfHfPVD-IrfwGOwToe2p9QVjRAdfUduUOjDBJVYASnJF4i-GnvkWbzj7MdpgHBlHu9u1OEoa9Ngpn7womPJhphlXNFDYnEhpUext-VT9P5AC7OpiMyPdvCNc38Iv3lFIcKAsNEBc4kovATGDkpmzx9Z-GDCvlsAKzjg8Wb7EG8YnA8euhgH0d0EaCFtEB7_mC0)


   
   5. Giải thích:
      - Hồ sơ giam giữ: Lưu trữ thông tin chi tiết về giam giữ của bệnh nhân.
      - Quản lý giam giữ: Điều phối toàn bộ quy trình ghi nhận và quản lý giam giữ.
      - Nhân viên lâm sàng: Tương tác với hệ thống để nhập thông tin giam giữ.
      - Thông báo: Quản lý và gửi thông báo nhắc nhở.
      - Tuân thủ pháp luật: Đảm bảo thông tin giam giữ tuân thủ các quy định pháp lý.
   7. Mối quan hệ giữa các lớp:
      - Nhân viên lâm sàng và Quản lý giam giữ: Quan hệ gọi: Nhân viên lâm sàng gửi thông tin giam giữ đến trình quản lý.
      - Quản lý giam giữ và Tuân thủ pháp luật: Quan hệ kết hợp: Quản lý giam giữ kiểm tra thông tin giam giữ qua Tuân thủ pháp luật.
      - Quản lý giam giữ và Hồ sơ giam giữ: Quan hệ tạo: Quản lý giam giữ tạo hoặc cập nhật hồ sơ giam giữ.
      - Quản lý giam giữ và Thông báo: Quan hệ gọi: Gửi nhắc nhở kiểm tra định kỳ qua Thông báo.
   
      
       
        
        
     
### **Báo cáo hành chính:**
 1. Xác định các lớp phân tích:
    - **Quản lý báo cáo**: Chịu trách nhiệm điều phối quá trình tạo báo cáo.
      + Thuộc tính: loaiBaoCao: String
      + Nhiệm vụ:
        - Thu thập dữ liệu liên quan.
        - Gọi các lớp hỗ trợ để xử lý và lưu trữ báo cáo.
    - **Thu thập dữ liệu**: Chịu trách nhiệm thu thập dữ liệu từ cơ sở dữ liệu.
      + Thuộc tính: duLieuLienQuan: List<Object>
      + Nhiệm vụ: Lấy dữ liệu từ các bảng cần thiết trong cơ sở dữ liệu.
    - **Báo cáo:** Lưu trữ thông tin báo cáo đã tạo.
      + Thuộc tính:
        - maBaoCao: String
        - noiDungBaoCao: String
        - thoiGianTao: Date
      + Nhiệm vụ:
        - Lưu trữ thông tin báo cáo.
        - Cho phép tải xuống hoặc in.  
    - **Quản trị viên**: Người khởi tạo quá trình tạo báo cáo.
      + Thuộc tính: maQuanTri: String
      + Nhiệm vụ: Chọn loại báo cáo và khởi chạy quy trình tạo báo cáo.
    - **Ghi nhật ký**: Ghi lại lịch sử tạo báo cáo.
      + Thuộc tính: lichSuTaoBaoCao: List<String>
      + Nhiệm vụ: Lưu thông tin về báo cáo đã được tạo.
     
 2. Biểu đồ sequence:


![PlantText](https://www.planttext.com/plantuml/png/RP8nQiCm68LtWUxmo9uBP2WXANHeA0Hy0TKEaQWhEROKoDYfG-aT6Zgr4BgqYqKcdKGtgUmaTknaiOtyllU_zzlZGhDSc-UK4XPhbMCmDxxybD2vjszO2_Sj1s05veR9A1UKP44lOf4ngHjnwlPuT5k5E5mQ-MmpOMhAL8-9k87cljnbIBpzGIgyVJKr5Lv5d6MtPYOMfeTDElvNdU-uWAoSDPxSljQ5emVEzFs64agE7J2ywUGROSgzVGyrb2-tecro84wo2ki47E5wbN0BMyCgi9Hq20mlHaTvs23MthwSMvpIdizkY11IjI7Xoo-9X4b-YJJjHzKZqhfU6Zvip55ukuFkUlKTZcd3pggkxbSk3zfsUE7BFud2VSWb9UE5JEfVwHy0)

 3. Biểu đồ lớp:


![Diagram](https://www.planttext.com/plantuml/png/VL8zJyCm4DqZvJzOdOfG_q24ga8ZTQ20e1rOhqaK7tLjbDX84M9cu4SW1aR4tepy4lyJhirt6x1aB_VklNVlF4ar9DfiXEi40jAKtKMFAj5N826E4lRiEepEAHCAy0BK59J75Zf16LSL3Qee38yn9rx9vpelhbD9-A1XgeI80grQ4g6POxIxyjQ0zDWSKtrsiteWsBYs0Pc_X_MBTLjQaeMBHci3_SD8XRwHyH-JSeKp1BdSbMY8g7PbJ1a1UNXI63RPuBrH5LzJRJax3pSesyPsmoyJF1HVa_Zo_wYFkKs8UgxYxYOnu0jJKvMX5IHrpZ77QmxwCXiU9jNLwVwMqMXyi5oF3OJTVcOijFatITlyrGpwsie54LxRxOTYgnzw0dfwqUt1g8NSCc7pju2prEPVr5AasX1NpGHUSvk_8miuwMG4dKGotF__Nm00)

4. Giải thích biểu đồ lớp:
   - Quản lý báo cáo:
     + Lớp chính điều phối việc tạo báo cáo.
     + Tương tác với lớp Thu thập dữ liệu để thu thập dữ liệu và Report để tạo báo cáo.
   - Thu thập dữ liệu:
     + Lấy dữ liệu liên quan từ cơ sở dữ liệu.
     + Đảm bảo dữ liệu đầy đủ để tạo báo cáo.
   - Báo cáo:
     + Lưu trữ thông tin báo cáo ẩn danh.
     + Cung cấp các phương thức tải xuống và lưu báo cáo.
   - Quản trị viên:
     + Người khởi tạo quy trình tạo báo cáo.
     + Tương tác với Quản lý báo cáo để yêu cầu tạo báo cáo.
   - Ghi nhật ký: Ghi lại các hoạt động tạo báo cáo để phục vụ kiểm tra và truy vết.
5. Mối quan hệ giữa các lớp:
   - Quản trị viên và Quản lý báo cáo: Quan hệ gọi: Quản trị viên khởi chạy quá trình tạo báo cáo thông qua Quản lý báo cáo.
   - Quản lý báo cáo và Thu thập dữ liệu: Quan hệ kết hợp: Quản lý báo cáo yêu cầu Thu thập dữ liệu thu thập dữ liệu.
   - Quản lý báo cáo và Báo cáo: Quan hệ tạo: Quản lý báo cáo chịu trách nhiệm tạo và quản lý đối tượng Báo cáo.
   - Quản lý báo cáo và Ghi nhật ký: Quan hệ gọi: Quản lý báo cáo ghi lịch sử vào Ghi nhật ký.

     

## 3. Xác định các phần tử thiết kế
   1. Các phần tử thiết kế trong hệ thống:
      - Giao diện người dùng:
        + Phần tử thiết kế:
          - Các biểu mẫu nhập liệu (Forms): Quản lý hồ sơ bệnh nhân, giam giữ bắt buộc, và lịch hẹn.
          - Màn hình báo cáo: Hiển thị báo cáo hành chính và cảnh báo.
          - Menu điều hướng: Giúp nhân viên lâm sàng và quản trị viên truy cập các chức năng dễ dàng.
          - Thông báo trạng thái: Hiển thị thông báo lỗi hoặc thành công cho người dùng.
        + Tổ chức:
          - Giao diện tập trung vào sự đơn giản, giảm thiểu lỗi nhập liệu.
          - Phân quyền hiển thị: Nhân viên lâm sàng, quản trị viên chỉ thấy các chức năng phù hợp.
      - Lớp logic nghiệp vụ:
        + Phần tử thiết kế:
          - Trình quản lý bệnh nhân: Quản lý thông tin bệnh nhân, lịch sử điều trị, và tích hợp lịch hẹn.
          - Trình theo dõi bệnh nhân: Theo dõi tuân thủ điều trị, phát hiện và gửi cảnh báo.
          - Trình quản lý giam giữ: Ghi nhận và kiểm tra thông tin giam giữ.
          - Trình quản lý báo cáo: Xử lý báo cáo hành chính, lưu trữ và truy xuất dữ liệu.
        + Tổ chức:
          - Chia lớp nghiệp vụ thành các module độc lập, mỗi module xử lý một nhóm chức năng:
            + Quản lý bệnh nhân
            + Báo cáo hành chính.
            + Theo dõi điều trị.
          - Áp dụng nguyên tắc Separation of Concerns (SoC): Mỗi module chỉ thực hiện một nhiệm vụ cụ thể.
      - Lớp phân tích:
        + Phần tử thiết kế:
          - Tích hợp hệ thống kê đơn thuốc: Gửi và nhận thông tin kê đơn.
          - Tích hợp hệ thống hồ sơ bệnh án quốc gia: Đồng bộ thông tin bệnh nhân.
          - Tích hợp hệ thống lịch hẹn: Kiểm tra lịch hẹn và lên kế hoạch nhắc nhở.
        + Tổ chức:
          - Sử dụng API hoặc giao thức tiêu chuẩn (REST hoặc SOAP) để tích hợp.
          - Đảm bảo bảo mật dữ liệu khi trao đổi giữa các hệ thống.
      - Lớp dữ liệu:
        + Phần tử thiết kế:
          - Cơ sở dữ liệu bệnh nhân: Lưu trữ thông tin cá nhân, lịch sử điều trị, và trạng thái giam giữ.
          - Cơ sở dữ liệu báo cáo: Lưu trữ các báo cáo đã tạo và lịch sử truy cập.
          - Cơ sở dữ liệu nhật ký: Theo dõi các hành động thực hiện trên hệ thống để kiểm tra và truy vết.
        + Tổ chức:
          - Thiết kế cơ sở dữ liệu quan hệ với các bảng: Thông tin bệnh nhân, Lịch hẹn, Thông tin giam giữ , Báo cáo hành chính.
          - Sử dụng ORM (Object-Relational Mapping) để giảm độ phức tạp khi truy vấn dữ liệu.
         
   2. Cách tổ chức các phần tử:
      - Kiến trúc 3 tầng:
        + Tầng giao diện:
          - Tương tác với người dùng qua trình duyệt web.
          - Gửi yêu cầu đến tầng logic nghiệp vụ.
        + Tầng nghiệp vụ:
          - Xử lý tất cả các logic nghiệp vụ.
          - Tương tác với tầng dữ liệu để lấy hoặc lưu thông tin.
        + Tầng dữ liệu: Lưu trữ và truy xuất dữ liệu từ cơ sở dữ liệu.
   3. Các cơ chế thiết kế được sử dụng:
      - Cơ chế bảo mật:
        + Xác thực người dùng bằng mật khẩu và phân quyền.
        + Xác thực người dùng bằng mật khẩu và phân quyền.
        + Ứng dụng: Đảm bảo chỉ nhân viên được ủy quyền mới có thể truy cập thông tin giam giữ hoặc báo cáo.
      - Cơ chế tích hợp:
        + Sử dụng API tiêu chuẩn để giao tiếp với hệ thống bên ngoài.
        + Cơ chế retry để xử lý lỗi khi kết nối bị gián đoạn.
        + Ứng dụng: Tích hợp hệ thống kê đơn thuốc và lịch hẹn.
      - Cơ chế xử lý lỗi:
        + Hiển thị thông báo lỗi rõ ràng cho người dùng (ví dụ: "Dữ liệu không hợp lệ").
        + Ghi lại lỗi trong nhật ký để phân tích và xử lý.
        + Ứng dụng: Xử lý lỗi khi dữ liệu nhập không hợp lệ trong quản lý giam giữ.
      - Cơ chế nhắc nhở tự động:
        + ên lịch nhắc nhở kiểm tra định kỳ dựa trên thông tin giam giữ hoặc lịch hẹn.
        + Ứng dụng: Tự động gửi thông báo qua email hoặc hệ thống UI.
          
## 4. Thiết kế hệ thống con :

### **1. Quản lý bệnh nhân**: Thêm mới, cập nhật, tìm kiếm, hoặc xóa bệnh nhân.
   **1.1 Mô tả chức năng**
   - Chức năng :
      + Quản lý thông tin bệnh nhân (thêm, sửa, xóa, tìm kiếm).
      + Quản lý lịch sử điều trị của từng bệnh nhân.
   - Yêu cầu giao diện:
      + Biểu mẫu nhập liệu (Forms) để thêm/sửa thông tin bệnh nhân.
      + Màn hình hiển thị danh sách bệnh nhân kèm chức năng tìm kiếm.
   
   **1.2 Sơ đồ lớp**
   
   ![diagram](https://www.planttext.com/plantuml/png/Z591Ri8m4Bpx5Nii4dp0GWYrELGYfQh8fSV5hE8jyPeIMof2lAo7FgbVg1AI4A9MvROUp-xChFRxysjU1jo7w0grGxF5dE2HCkibVuaewU6Un2ujob6P0iiIhb4uAW20OCcrqDswAJIqq4Z3slk2K6gsmTtIOkWQ77RZDB24CVmxuiFZd-q3Qk2BjS0K7onhoCv5nkGMJ6wa8UKoJ5lYJ9rKa_SgwL1A0LYVKVLQXJrBhW0anyEAnOA610EfQZjUyembPP8KJPzSiB6h-9eHD0xI5kXP69YjdTmWQz0qdGjRgpxXRdhcZ-5v_KOcz4GwuNgyiH4byNNEJcB35BCzzw5WepS99b7oDi7vhvuyk9N9P7PPfuRtY58SVYCD0si8J6xBvDGLx-9PW_7LBikeJcfEigdk-GS00F__0m00)
   
  **1.3 Sơ đồ tuần tự** 
  
  ![diagram](https://www.planttext.com/plantuml/png/T98nIWD168NxESLZAoroWIr2s2p4O1353TZ9P7V936x-bTrPCQLOfB0IBw2c2mOiKcKGYn7lCIVm2Z8ROjIGzkTzxtzl_ldIxwrIyK9LeupnMEK5ZeHvflChQMO4Ng9VfWKRv1Kbl1Z3wqYU8v5MJmWdbLrE2Pbvmy0D1CYndiCw_IwBSr95di6B2lD20X_tqkgR2XT2MdrBsr1x1MHfmL9IKetXzVAXZBULzPWbNF41BrDuxTEmjwqA0yPSVZIQBf2FI9ZPw8yEUv4m2nf6ae9wNDVVPvr-rr6RH3xEh9xNPLNjiWDi_n2EhtFwE7I5Hr05Xx1wUedCwiakXrNbHXDXuAFt-LgvXGiQGicTSSC0ZSswI9X74eYTSctthyong6ydh7wGpd-Z_rrW_Mu7guCfOVKThirJ319sEIVMIYbnN-SR003__mC0)
  
### **2. Theo dõi điều trị**: Gửi cảnh báo, kiểm tra tuân thủ điều trị.
   **2.1 Mô tả chức năng**
      - Chức năng:
         + Theo dõi tình trạng tuân thủ điều trị của bệnh nhân.
         + Gửi cảnh báo khi phát hiện vi phạm.
      - Yêu cầu giao diện:
         + Màn hình theo dõi lịch sử điều trị.
         + Thông báo trạng thái tuân thủ (đạt/không đạt).
         
   **2.2 Sơ đồ lớp**
   
   ![diagram](https://www.planttext.com/plantuml/png/R991Ri8m44NtSufPjWikO5K8GHQL6h715nZSKMoHZ55YBn3AoRhWIBr2vH1Cah9zV_x_7jk_FxTD5wWDiQdXJEP45UCdQ-kbqfPzuLtXEEhMNS7Kr7KuftW5HCIJuqQtf2E9jl6jeIsBtLiIXKx2kqBTKWeaDuuChYgw7OdTad_XE7fVCmdqC1O_1eRAnJmWMgzP51v2wwG2nDePUuZZCHMMhWiVvPIjdz4pFkPdvprUAhfaL51WG0msUbFG5qzgmsBH5wldsgKoDEU0IQYXyzvIA4bsqJ_wUu35MwnMw-SjAGnt5J9A-dnLXSRF2CprvFXtocJA47hOi7odx_C7003__mC0)
   
   **2.3 Sơ đồ tuần tự** 

  ![diagram](https://www.planttext.com/plantuml/png/V991Qi9068NtSuf7Lkt22sGX4WEsQBjfXEvaJ88p62TqCX6oB5rquQf7K952QUcgcmp5HNgHEK6lK4QnqIhT3k_xttl_FzzwtSeKbIgV98I6AfMuPjL23AQyUX63Og1CkGRDqCzYIOPfBY8g2pWTJbD4tEX7WO35AQBgW-FhYHjzdqD9esUEnJhzInAcGiaqWHF8wbMmNzMOSQCVn0cglIMIM99OAAuAEBrqnCCJqiqxYQYYGvh5SDetVk-4pFS8iHNGQDfCBhhMUm8bALHUBGGKC_ePPrVLqhEjs6ODvwJJlxHCdSZ5hT5lIAfFZEiPHrmDM7oJqaNFbAi2aT7lIEpkyl-zjvqRJVYUYq3c1QQcN0aaHiz2XipcEAXwFCBtqAZzkwPSAzpbfbpk3zaP_UaPI5FEnGYALNE-d_IWt6wX5zjZMi7CfgbHqef5PF_N3m000F__0m00)
  
### **3. Quản lý báo cáo hành chính**: Tạo, lưu trữ, truy vấn báo cáo.
   **3.1 Mô tả chức năng**
      - Chức năng:
         + Tạo, lưu trữ và truy xuất báo cáo hành chính.
         + Xuất báo cáo tổng hợp và chi tiết.
         
   **3.2 Sơ đồ lớp**
   
   ![diagram](https://www.planttext.com/plantuml/png/R96n2i8m48RtFCMDEeXx1X4jwE0Y1XTn-D6G1jjBiSbGn2Tpy95y1Qc9OgsPVhxS_VzTyhZTfxN7sOUo4AB2uGIZQQbLxjYi0tZLpE3cS7GHH4I70dLDVoxQu-4Y6tYhmpotabGK4GybHV7fA91S1YMYa6JPTmkluYlw9xHCRVJgIx1DppH9slYpPPCeEvi5DZriqAYNGGQl-u6T3JwvXSCR_VXLESgjLRcp2mjEjhjzChwApjkDHfFtHf8Kt7Y5fb_H7K7I9Xm36o6cce_jlpq1003__mC0)
   
   **3.3 Sơ đồ tuần tự** 
   
  ![diagram](https://www.planttext.com/plantuml/png/Z98nQiCm58PtdUBXgHro0GyXs0OtD4kf3Ts2OfjQr9MeB0KybWuTCkK89dG93TqjIWRb8Zf1hn1aDtLhEcGL__U__tzFNse_AGNcGZuM22U2SRYHfjdGkU16hUPBehSKS0bncN6qO9Acc5VWX0GpI8bHh_GRW49_maBN319TCySoOJn52QE2imASYEjtciDXJOnwbl2G4wDUw83mEtMHSPHHGKG5pepTasGWQzzGYWLUu383nxyDPWD9u25aCyDeR7Eu49ccPhq8BYAYjzBFzSxJDVDrpIvH64-jla_XmfrHkxQQE8FtVq1hqwOyRt1NSZI6m7CXuhA2fMdUAAH6VK1Xrop_vG8FHlsaQzFi1JpPS_mcJ-w3PjQbItHOwqtNxq-3q-Qkkak9tAXLtmDDCfhQNtC4003__mC0)
  
### **4. Quản lý giam giữ**: Xác thực, lưu trữ, kiểm tra thông tin giam giữ.
   **4.1 Mô tả chức năng**
      - Chức năng:
         + Lưu trữ và kiểm tra thông tin giam giữ bắt buộc của bệnh nhân.
         + Gửi thông báo khi có thay đổi về trạng thái giam giữ.

   **4.2 Sơ đồ lớp**
   
   ![diagram](https://www.planttext.com/plantuml/png/N591QiCm4Bph5KjE2JGVqA44OqYX8L2g3spTHHALLwczFfZYb_NG9_KBnKPHPUkc6StE3AlVxvzJBzZ9q0QbRjXye2NOFP5naUtBW7mPpnxRinzsyAK009g0VGyhAZ7p4KVjeZMU4xkNTDUGa8E6jnW38MTTm74hQx4YTbU7hC6p7B8yYngyNHsAwP2jSUZtBQOdY-81vCveU9NEizquJqMZRPSy2vPX6QrIg1KSnZh2tIHXsNnBiCMnGgbn7bsZK84_anWtD2KngI9bTl-FkGhYeg4vMc4ugKcfzRwEnyVSLyFdW1n6LP95oU29PtLDhDI9-7t-Ady0003__mC0)
   
   **4.3 Sơ đồ tuần tự** 
   
  ![diagram](https://www.planttext.com/plantuml/png/T951IiD068NtSuf7Lhhe1R8efGr4COXY2-xAD0cPmMGYoKJiKbnquKgyWDfTiTI5gmxInOZtc1Du1PcKsXBgzkTzxt_l_t_KgbDAMiWgImaDPLxWbEbNCRpXUYQ6uw4qonLeYK4P5sIKLoAYnHYEpscEY1ir4JYlp78gaEfF99ncIBXH2yT2_k2OXBcGHPx2wHVwJJ1yFNAZxYfSCMxKlMWYlRKyZGiI2ydb64wG9pniwkeXYQYa8rh6S7eNNj3KU5r2R6wqsZQAYpxJimoIwG-HGFBTvJZmZ5e4jb7bSvhvTdX8_C6nfRUfN5mQDQ_BojfjFzVx0onUXtLnOXjda0K5CsfwZTIeoJy6wzAjDhokY-3xlTgDlH_nkcXjb_MPVXOCeOKsReqcPwn-73FgYLlxhNut_kPuH-j_IMRK0sxrImZ1p78kI2SMKPMblm000F__0m00)
  
### **5. Hệ thống tích hợp**: Đồng bộ hóa với các hệ thống kê đơn thuốc, lịch hẹn và hồ sơ bệnh án
 **5.1 Mô tả chức năng**
   - Chức năng:
     + Đồng bộ dữ liệu với các hệ thống bên ngoài như kê đơn thuốc, hồ sơ bệnh án quốc         gia và lịch hẹn.
     + Gửi và nhận dữ liệu từ API.
       
   **5.2 Sơ đồ lớp**
       
   ![diagram](https://www.planttext.com/plantuml/png/Z59B2i8m4Dtd58Eh2dg1BgGM5m551Nk1QHgIQ9qHswp4axdmI5v1RAEKKjIiafdt6oQFspsfQZpN_bWASK9rGADX97LccKpcb9Ly6i55002e4giAGZ50Gkjr2YQJicHS-9NJFYePNNkDOLUV7Pa95E6zoVTQrUCOSkPI8tr4o2ArfCm7YxLXT0DguxTCGxwAJiR0NEe5KsOzgqvCurqOZff-z5UchKMIxABVff9td6goSnesRNl_kVOuVVFUAgRJsS3aSLZC5tGdyWTz5OcculKjdW000F__0m00)
   
   **5.3 Sơ đồ tuần tự** 
   
  ![diagram](https://www.planttext.com/plantuml/png/R9AnQYf158RxUOgVhN8BNs0B4RD19HO13TnEndNP6UvwDeop8PRX5jPYTJk3X0lXIbAasY6ac93tE4zmNo5i9AZHTlY_Cz_vEV_TQsDYfR75E1Cojhb1czriO1MxEQM3eN-W0QMvNsh82SvkR698Phtfn2PZCSmB6aapHT3ICiT8iviH-duTAoXsgwkWWbgN7H7dP4sU8UWR_uyKtkQQtMs1Nqgp-tt8d6xoMM94GbRRAO9kdkhu8FZvAaRIog6S90XEUr7t81GrXTXNHwrUUOLeiLjhJFr3WPZBlmNUvkmMb6B8xWzE8dQFtMgjeirkqNk_-o5QbvsAtXg6-CbkZSo_xCuvXcwPQiAdUeZpge4nh94ROsJiPaVnJGErEg9cYExxKm5hs3qUpKPDrBP_z9LVaaBidodz6lDjXml5vOegXOM6tStlMd_LrZTShd3DxXOt_Yu6AIxNjEccLlzs9o7QkLyIB9VtTgzWqKXeL8op3m000F__0m00)

## 5. Thiết kế các lớp
   ### 5.1 Ca sử dụng Quản lý chăm sóc cá nhân
   #### 5.1.1 Xác dịnh các operations :
   ![PlantTexxt](https://www.planttext.com/plantuml/png/Z90nYi9G54NxlufRpY_SWCKWMDWCLXRJXaJoFYOFqP_2siB2GYmiBRGKn42c6LynnHVtyLRW5cH84v202xZd7Ev3_dfp7yryaMUcEqplfShU8Gc_d7RHwNpYOqJXb2DJMSU4c6xB7FDGnOZ30KpXoBPbsDVhUGeclPuzF8KVJk4TDnXjo-zGHQz6QymRCJLXGAusSyDipJjDDU3hNXRm52rmswhid3LjLOtaHEM2pAci2an8PUD0AYjuKjboQarlpCd_qyOy0G00__y30000)
   #### 5.1.2 Xác định các trạng thái : 
   ![PlantText](https://www.planttext.com/plantuml/png/P94nQiD044NxESMWCk0Bg0W6fKWXL8aWC2a6nMWMx5bZhmgV88IGmaLwfGqO0acLBL9io3ts1Bb2M2aMmbl_jt_UplpQh_dEqDQqwnKiBcvnDhl4SalIPAo4CSKRrsbaR-_HiBS7QG0cUO_pSfshEi0PU_iac9JiNjUuylQnvWH68D1vsvQifIcLO8e5-y_Z1Wsx3sdGA85f7ibSQzT9e3lXo2EZJS5a9kqddQmV8c6McSnAuFp9A4ZxAwt-6nw4SUVjaIBDWOeiyv-t5WtJ7hyFtZwhoBJITBQmohtJkAzJtADK5qnIQS8KA_TI3zyGc0IHGDysR0dhe0ppfTo54mF07m000F__0m00)
   #### 5.1.3 Xác định các thuộc tính :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9FPdA6SqPYRd1-ia8rbuA2ha9cYfM2Prv9Qdfg4PYVbvvOQQNWabYI2kQMPEJdfOTavbaf19SKPUQbSzLoGOtoIo_DpyHlLaagGX-8NvQO6LAKZsmKYY6wkdOe3hHIK0eiVRXhSPv2pk6zIbmEgNaf89zmSN5n0G000F__0m00)
   #### 5.1.4 Xác định các phụ thuộc , quan hệ kết hợp
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bTgNabcIQM2NtffVgPpHc9kS7woGZMNWeAMGcQAbO9dNabgUceHc5-IccUb45nIb9cN3kQN9MQ65EN3XMgvO6RvP2Pdu3SgBpsnqah19R4a5M9oHdvUUaWcmlXQBYuK1zNKwEhcLwCORAMWvFDmrze2XPo7kxkJCvIu75BpKa0UukBYuW80003__mC0)
   ### 5.2 Ca sử dụng Theo dõi bệnh nhân
   #### 5.2.1 Xác định các operations :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3fULN_gn3GztpyrKI3cyCo_TIa5Nrqv18oJZyAfSXPACmrloqXLAClCKaXxkRi_BKCZBEBmeJnE79kU7kzOMAEHbFDorjaGXu-7koGh5nnOIfJCYDLUXvF2Ql0o5agA7knRcfQFfuYBW88WfFiSsbCBjrUGYnZr86aio4YiLZanyk7jgfYON8HT1z7baFjpTdATGal5mTpUIspIv75BpKa21oyN5nGK0003__mC0)
   #### 5.2.2 Xác định các trạng thái :
   ![PlantText](https://www.planttext.com/plantuml/png/V94nQiCm58PtdUB7Oo4Ny512tI53yH9J0gM3cXezG_KSR7de2J8LMaftfsDefdQAXWuglOTEq2iKcHYS6gf5eF-J_k-X7_ivhOsiJAFlnDN9DIQJKsILP9LGmOGObwujGTwkOSZR9rP23F8EfroVvKmfIKQCXBnzO4GPkQt6ZRTh9Z2vLux44HhkNZJDh9oNY96It-zMCEG-MC4KBFfif3GhNSk1R9d2jjKZfqIkKfBcy7Qlb7GL79fCcEaPzVSc4aFu89MHl3yl2yIOUxkJVxJwz7-pvQ1j9BZ8TLOmTQS3mqMkOTnRcAlo-mshI1oHeyQlH_VE2ilEilRsHKnplWs_sQrV0000__y30000)
   #### 5.2.3 Xác định các thuộc tính : 
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9JQbw6NqPYda8rbuA2ha9cYfM2Prv9Qdfg4PXVaffdfH1SKfIPbmxXb-Pdegd8pCi8AKhCIuUhg-M2cksH7vmFCjyHb-bv-PakfKWwmMBfYPNEYGL-6OabLWekYIMf8FFWhjJLjKCsraf1oVdmPYKkXzIy592V8000003__mC0)
   #### 5.2.4 Xác định các phụ thuộc , quan hệ kế hợp :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bTgNabcIQM2KsfUXbz6Ofv2DPU2WfP2PegLWcTUIMfwQX6ONvAQPwKGN5AKcPSEuPVcPwAfoCpB22bAp4k7gwlbWXdkaH-S3xB04PVnUVcPBgL8Mi5YwOcLpea5VXc99LOABeabgI03uSwigT7LpQz6DjbAGSdds8PIXPACmrloqa7kKU9oICrB0NaI2W00003__mC0)
   ### 5.3 Ca sử dụng Quản Lý Giam Giữ Bắt Buộc :
   #### 5.3.1 Xác định các operations :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3fULN_gn3GztpyrKA2nzk6jndaBEuRrM2hgwTWeQ8Hc7L-Kgv3pStPwNeP2UcPYha9xvSFTwJNnwd1_kMbkWa9VnSDVQ4eMIZCDRyj8LIZBpYDKUSNXp8ZORkN0w1gBFvzY6KbpM4UCc55CIAnMEJ7ouUsgc9XSk1o6vDkNXxlKAEPaFTxUNAcHdFDpTdwcGyN1tkq99niFT4_FIDRaSKlDIG24D0m00003__mC0)
   #### 5.3.2 Xác định các trạng thái :
   ![PlantText](https://www.planttext.com/plantuml/png/T96nIWD154Nx-OhBba9-O0i9h62pf76H1R5uhCk-WUpR46V1V44gYnJsiHM2GgoSmcB4_vWly1TaDXesRfpstllkUM--xFlurj3SjFLKNPrSOpGwHJOdgHBMmeXnwTODsDib37kxaagfdjxPkQpJKlXSKuqO2NjxBuWoTayrfjukXL45hTBUFaVgm1y6f6sRSIDLfWKn9kpVDZCOTgzImMXHVNt0btw-jC6y5aOH8WE-X6OJ9dC4CUcQ91IQNc6a_aRsbBGuQpHYN7YxeG7ZJlqFaHRuM7dxe0U4UKD7w7AtfP_xHQflwI9KJ9WaRmWnSlTOxDOGtBajgPuweEd67XniNCfD-F_Vzmq00F__0m00)
   #### 5.3.3 Xác định các thuộc tính :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9FQbw6UsPYhdjcgK8rbuA2ha9cYfM2Prv9Qdfg4PXVafhdbrwQd-cK2L9dfH1SKfIPbmwMoajFhFH9BB1IS4aiIOKepipB22bAp4k7gwlbWjeKM9gOvrD9q2uK2yeICqEAyf7DGZL5LzSEnGTM2ag1fGztBSvJo3cyLudB8JKl1UHL6000003__mC0)
   #### 5.3.4 Xác định các phụ thuộc , quan hệ kết hợp :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bTgNabcIQL2O6bYda-bUsPYhdjcgK8rbuA2ba9cYfM2Prv9Qdfg4PXVaffdfH1SKfIPbmxcboLcXXJbmuLgkM26-QJcPH0qoY-zD3_JAHEa3iNKlFJ4If_40Yi5byIIL8ZYpBoCaAB4l7Hagr0TN5EZgvjVZMAnbOAIUqQcGbx6mrrhyvIu75BpKa3-XG400000__y30000)
   ### 5.4 Ca sử dụng Báo Cáo Hành chính :
   #### 5.4.1 Xác dịnh các operations :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3fULN_gn3GztpyrKI3cyCo_TIa5Nrqv18-JXheNv2ac75-Oh91zUcA-9Gvdpmrrh2nJoCXxkMbj2MBNxmzrhCv6LSM7O0r7e1pAmG27luUwPcGeffNdfcbouh8Aw8-FXxiwy38NYXxlN9gBgGxSKeY7YyC9aY65v2kbW5KScPcfoEQJcfO021Ge00000__y30000)
   #### 5.4.2 Xác định các trạng thái : 
   ![PlantText](https://www.planttext.com/plantuml/png/X9AnQiCm48PtFSMHiU0No5127F0IlCIKGEbmTOebI4ycbOOyGQSE7ZfqgybiyD0f6Zee-3tq17s5ehgfLGojrl__x_xlq8Tvdpqet2bzlsNN5pSGHPUGxP2Ac0lYC8Kh-og1E_C8YZjJKS5Oe7_PKSvHnYXX2Z5tvebWahbZBU7MrX9oMyi96qm-ad8iKoaMcWgOGihTiIc1d7aHiD5Ki53t_gNMFokMNQj1SVj61IX1RD16tUVd_N2gx06sNQj7xMCiKuvgH13tdNmr5OByzli9Auq3oygP1aEKG8rwaepZVY75W89xE5NEF0lFSbR_XEbQPmuvv4774LYYnGWgSQOH8SrWyf4rvYb7IhGljxPrtiycA7oE1V9_f-u3iplQ-8_r_Ju1003__mC0)
   #### 5.4.3 Xác định các thuộc tính :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9JOhvpOhv2DPU2Wgv2PegLWcTUIMfwQX6ONvAPMkgIQgKGN5AKcPSE5ihBptGfpKj75KjFh7GlpRHIS4aiIUMgvO8QxPTU2b6Co_JKF1HZoX8pGuhouKArN5m84tHrxM1EjL9GydcuQss14fT3QbuAo2Sm00000F__0m00)
   #### 5.4.4 Xác định các phụ thuộc , quan hệ kết hợp :
   ![PlantText](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bTgNabcIQM2NtffVgPBQLwwGZMNWeAMGcQAbO9dNabgUceHc5-IccUb45nIb9cN3kQN9MQ65EN3XMgvO0Ov9UOx9-RZCYKpjTGb5SMWF8Yrg6BfYPNkfPbM2Yw99QaWin6kgwdHrSslXjbYfQ0Kyd3Nmdo5eaGbBeVKl1IGZs000000__y30000)
## 6. Kết luận
   #### 6.1.Mô tả tóm tắt bài toán:
   - Mục tiêu của hệ thống là hỗ trợ quản lý bệnh nhân mắc các vấn đề về sức khỏe tâm thần trong khu vực Mid-Scotland.
   - Hệ thống cung cấp thông tin quản lý, theo dõi điều trị, và quản lý giam giữ bắt buộc.
   #### 6.2.Phân tích các ca sử dụng:
   - Kiến trúc đề xuất là mô hình triển khai máy khách-máy chủ.
   - Các cơ chế bảo mật, quản lý dữ liệu, và phân tích từng ca sử dụng được mô tả chi tiết.
   #### 6.3.Xác định các phần tử thiết kế:
   - Phân tích chi tiết các phần tử trong hệ thống như giao diện người dùng, lớp logic nghiệp vụ, lớp phân tích, và lớp dữ liệu.
   #### 6.4.Thiết kế hệ thống con:
   - Mô tả các chức năng quản lý bệnh nhân, theo dõi điều trị, quản lý báo cáo hành chính, quản lý giam giữ, và hệ thống tích hợp.
   - Sơ đồ lớp và sơ đồ tuần tự cho từng hệ thống con.
   #### 6.5.Thiết kế các lớp:
   - Xác định các operations, trạng thái, thuộc tính, và quan hệ kết hợp cho từng ca sử dụng.
   - Ca sử dụng "Quản lý chăm sóc cá nhân": Thêm, xóa, cập nhật, và tìm kiếm bệnh nhân. Các trạng thái bao gồm bệnh nhân mới, đã cập nhật, đã xóa. Các thuộc tính như mã bệnh nhân, tên, địa chỉ, ngày sinh, thông tin liên hệ.
   - Ca sử dụng "Theo dõi bệnh nhân": Gửi cảnh báo, kiểm tra tuân thủ điều trị, cập nhật trạng thái điều trị. Các trạng thái bao gồm đang điều trị, không tuân thủ, đã gửi cảnh báo. Các thuộc tính như mã cảnh báo, mã bệnh nhân, nội dung cảnh báo, trạng thái điều trị.
   - Ca sử dụng "Quản lý giam giữ bắt buộc": Thêm, cập nhật, xóa thông tin giam giữ. Các trạng thái bao gồm đang giam giữ, đã thả. Các thuộc tính như mã giam giữ, mã bệnh nhân, ngày giam giữ, ngày thả, lý do giam giữ.
   - Ca sử dụng "Báo cáo hành chính": Tạo, lưu trữ, truy xuất báo cáo. Các trạng thái bao gồm báo cáo mới, đã lưu, đã truy xuất. Các thuộc tính như mã báo cáo, nội dung báo cáo, thời gian tạo.
