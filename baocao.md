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

- **Patient:** Lớp đại diện cho bệnh nhân.
- **ClinicalStaff:** Lớp đại diện cho nhân viên lâm sàng.
- **Consultation:** Lớp đại diện cho buổi tư vấn.
- **PatientRecord:** Lớp đại diện cho hồ sơ bệnh nhân.
- **Diagnosis:** Lớp đại diện cho chẩn đoán.
- **Treatment:** Lớp đại diện cho phương pháp điều trị.
- **Medication:** Lớp đại diện cho thuốc được kê đơn.
- **Referral:** Lớp đại diện cho việc giới thiệu bệnh nhân đến các bộ phận khác.

2. **Mô tả hành vi thông qua biểu đồ sequence**

Dưới đây là biểu đồ sequence mô tả hành vi của ca sử dụng "Quản lý chăm sóc cá nhân":

![diagram](https://www.planttext.com/plantuml/png/b98nJiD044NxFSM8dWkaG4XEIQJ8kA3TE4vs5NjihSVfgIYe8aH5Wq4KH22bzXOfDl8zvWHS0SKeWYM0IFtVznjh_vjTdvOa3LLPAcHCkO4WrQXZcPwJd4n48GtfM1SI2Ow6adI252PnRiP784iOXZuHv5XMAKdIENP0uETzBQUObxhimhuVHYQHb2L8NHZvuI0Pw_ZpkmC_3PD9OenCkomKmli9E3w1OTY3oBraCDFSh3DGR6-WR6iOiRr21QZS0ufXk6MzSWyYmyqZpDbU_jBQjmKzYBYfSnXLR6yrKBk2EJTF21dREos2tKbdsYqHPjoiQP-TRzb_E_izY9HRPX0hRfuHDelSrIZwErN0pMi1gBXv9P-1kRlF_-s9Tfv2jQksnYaKojK5R1QQxMK5PDXUY-X7xL-LmwuOxAuWLR5Tn31pIzWisXh5u4SrVUSEystdq_cckdiLKfhjLIMwmUp9VEWmKpUBTbKTCj4BLySVReJqQrUS9ZYkilGT003__mC0)

3. **Xác định nhiệm vụ của từng lớp phân tích**

- **Patient:** Lưu trữ thông tin cá nhân của bệnh nhân như tên, địa chỉ, ngày sinh, liên hệ gia đình.
- **ClinicalStaff:** Quản lý thông tin nhân viên lâm sàng và thực hiện các thao tác trên hồ sơ bệnh nhân.
- **Consultation:** Quản lý thông tin về buổi tư vấn, bao gồm ngày giờ, nhân viên lâm sàng tham gia, và các ghi chú tư vấn.
- **PatientRecord:** Lưu trữ toàn bộ thông tin về bệnh nhân, bao gồm chẩn đoán, phương pháp điều trị, thuốc kê đơn, và giới thiệu.
- **Diagnosis:** Quản lý thông tin về các chẩn đoán bệnh của bệnh nhân.
- **Treatment:** Quản lý thông tin về các phương pháp điều trị được áp dụng cho bệnh nhân.
- **Medication:** Quản lý thông tin về các loại thuốc được kê đơn cho bệnh nhân.
- **Referral:** Quản lý thông tin về việc giới thiệu bệnh nhân đến các bộ phận khác.

4. **Xác định một số thuộc tính và quan hệ giữa các lớp phân tích**

- **Patient**
  - Thuộc tính: `patientID`, `name`, `address`, `dateOfBirth`, `contactDetails`, `familyContacts`
  - Quan hệ: 1 Patient có nhiều PatientRecord

- **ClinicalStaff**
  - Thuộc tính: `staffID`, `name`, `role`, `contactDetails`
  - Quan hệ: 1 ClinicalStaff có nhiều Consultation

- **Consultation**
  - Thuộc tính: `consultationID`, `date`, `time`, `notes`
  - Quan hệ: 1 Consultation thuộc về 1 PatientRecord, 1 Consultation có nhiều ClinicalStaff

- **PatientRecord**
  - Thuộc tính: `recordID`, `patientID`, `riskAssessment`
  - Quan hệ: 1 PatientRecord có nhiều Diagnosis, Treatment, Medication, Referral

- **Diagnosis**
  - Thuộc tính: `diagnosisID`, `condition`, `date`, `comments`
  - Quan hệ: 1 Diagnosis thuộc về 1 PatientRecord

- **Treatment**
  - Thuộc tính: `treatmentID`, `method`, `date`, `comments`
  - Quan hệ: 1 Treatment thuộc về 1 PatientRecord

- **Medication**
  - Thuộc tính: `medicationID`, `drugName`, `dosage`, `date`, `comments`
  - Quan hệ: 1 Medication thuộc về 1 PatientRecord

- **Referral**
  - Thuộc tính: `referralID`, `department`, `date`, `comments`
  - Quan hệ: 1 Referral thuộc về 1 PatientRecord

5. **Biểu đồ lớp mô tả lớp phân tích và giải thích**

![diagram](https://www.planttext.com/plantuml/png/d5CvRiCm4Epr2a9b01j9wyg9rQJ80TiVM90hcGWFWxigWY0lIv4dvGi1JSiI5Lj0t6cMWvazHZzVtqjY2DnQKqW3HE8LMADZyL488VO9F5OBiU6WNHEB3YmECIWLa6XOKi3uKZ_emBk5g80n5gLt398hPD0cezTWjNbVfVV-vRCuzhGosca9PiDGrwapYf_JVGLlCdp1ltVnZbh3mDgxP287bTmh3jXFnZewRxKz8ESPpyWV5xj6wODA-k7mdIkVNNdGz7PFX4GM7V_LhZGqpfEcfAiwcAj8xvIEiroUH7eR7Swqlmq87D-I1NSmjx38Ew-kqNz2fULWz_Q4HviFRVCykhJo10rUuxh66aC0qzqZeP4ZxY4SPlsVG_SdbNUbcCr4UJkVtvHv38eysJbpDKXVaOLpn1jgTAx7c4qeJX5FUPfadI8noUeFEqdhBb4iqQdMcby0003__mC0)

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
       
 + ### **Quản lý giam giữ bắt buộc:**
   - Key Abstractions :
     
       ![PlantText](https://www.planttext.com/plantuml/png/N8v12i9034NtESKSfL8HbyMU8Cn43Cma9KaNHJoPYnx9AuWe2BFzxpzuh-S-UA35sYhaYkvfmc2II7T82HxmMy-4DMuZ6ascLt9d5QpTwKX14gnomioLO-lul2wBMinVlOCZEbqegvNUsZoe7KhZlm83IVaq0y0R003__mC0)
     
       - Key Abstraction Definitions :
         Patient (Bệnh nhân): Đại diện cho cá nhân được quản lý trong hệ thống.
         HealthCareProfessional (Nhân viên y tế): Người thực hiện các đánh giá và hỗ trợ.
         DetentionFacility (Cơ sở giam giữ): Thông tin về địa điểm và điều kiện giam giữ.
         SupportSession (Phiên hỗ trợ): Các buổi hỗ trợ tâm lý/điều trị.
         CaseRecord (Hồ sơ vụ việc): Quản lý thông tin chi tiết về trường hợp của bệnh nhân.
         SystemAdmin (Quản trị viên hệ thống): Người quản lý và giám sát hệ thống.
         
       - Upper-Level layers and their dependentcies :
         
        ![PlantText](https://www.planttext.com/plantuml/png/V9F1Qjmm54Nt-efBLkqYFv15IDf2EYIK5ZBGhU8nigX7urhIqA5aKRAOHLTPXzAMOGXjCPD5DxKeMJZCVxmlw2yKQUpKpfXwPQ5xzSvzJ_hZRW-quRcnuvHbF7h3HOoTbtciOsMuaHE54pwBSpmwado2aIGtLuzty9u1KSgrnd0G5lvxBibTA9Y4t4UCoAsGUhsjjryaL1OATvTKNbjCgoyJ678_eCJwXjmdYL7rIma6dBDpzW_cCCjI6TKi4o6ZXcYp8FTD2LzjgKG7x8dLKiLQRsGDusjo1TBgDvH8F5o6ARbblNdi0unXSWvJ5If1GcwH8IKtxydpoivWg5n549AF8IIvrHRzCsuu3gCerhhXFitj316LHTO-jCFkNRMf0G-kAPLBXMZz5PhSvnwcC2KZgRmDmQwaXx_g5Ef5FECwRlYUzXo_HHSC3Tl9-iR2v5xUyi0arS_xNb6vKA7nP_vF-FdZhUNAztZUC0q7sDtTVp2wFHoHAoHcrNVh-tPjMLVWBQsERUlHZjzIDiOGPg_TOa-t6P7ojzO4Lv1j5JlDgLpuPd_uNvc7aVfTkBki5dXNtz6UcCF1VRokZTm5_8LktXyxYDN8Fsh66FiB003__mC0)
     
       - Layer Definitions :
           + Lớp giao diện (Presentation Layer - UI/UX):
              - Mục đích: Cung cấp giao diện người dùng để các nhân viên y tế, quản trị viên hệ thống và nhân viên hỗ trợ tương 
                tác với hệ thống.
              - Phụ thuộc:
                + Phụ thuộc vào Lớp logic ứng dụng để lấy dữ liệu và hiển thị.
                + Phụ thuộc vào API để xử lý dữ liệu đầu vào và đầu ra.
              - Ví dụ các thành phần:
                + Bảng điều khiển quản lý bệnh nhân.
                + Giao diện tạo và xem hồ sơ vụ việc.
                + Giao diện lên lịch các phiên hỗ trợ.
           + Lớp logic ứng dụng (Application Logic Layer):
              - Mục đích: Xử lý các logic nghiệp vụ chính, như quy tắc giam giữ, kiểm tra tính hợp lệ dữ liệu và quy trình làm việc.
              - Phụ thuộc:
                + Phụ thuộc vào Lớp truy cập dữ liệu để lấy và lưu trữ dữ liệu.
                + Cung cấp dữ liệu đã xử lý cho Lớp giao diện.
              - Ví dụ các thành phần:
                + Quy tắc quản lý hồ sơ (liên kết bệnh nhân với cơ sở giam giữ).
                + Logic lên lịch các phiên hỗ trợ.
                + Logic kiểm tra chứng chỉ của nhân viên y tế.
            + Lớp truy cập dữ liệu (Data Access Layer):
              - Mục đích: Cung cấp giao diện có cấu trúc để truy vấn, cập nhật và quản lý cơ sở dữ liệu.
              - Phụ thuộc:
                + Phụ thuộc vào Lớp cơ sở dữ liệu để lưu trữ và truy xuất dữ liệu thực tế.
                + Hỗ trợ Lớp logic ứng dụng với các thực thể và thao tác dữ liệu.
              - Ví dụ các thành phần:
                + ORM (Object-Relational Mapping) cho các thực thể như Patient, CaseRecord, SupportSession.
                + Các phương pháp đồng bộ dữ liệu (như quản lý bộ nhớ đệm - cache).
            + Lớp cơ sở dữ liệu (Database Layer):
              - Mục đích: Lưu trữ tất cả dữ liệu thô, bao gồm thông tin bệnh nhân, hồ sơ vụ việc và nhật ký các phiên hỗ trợ.
              - Phụ thuộc:
                + Không phụ thuộc vào bất kỳ lớp nào khác (lớp nền tảng).
                + Phục vụ dữ liệu cho Lớp truy cập dữ liệu.
              - Ví dụ các thành phần:
                + Bảng dữ liệu cho Patients, HealthCareProfessionals, CaseRecords, v.v.
                + Chiến lược sao lưu và đồng bộ hóa.
                  
        - Biểu đồ sequence :
          
      ![PlantText](https://www.planttext.com/plantuml/png/h9J1Qjim6CVlUee_FMs7la0Wet4CIy2Cm1hOLLKzIyoHKqiUv0bws6LZXnrNjuT1MEaEFTcC7bJo7dg2lSAGab2xYJiAkndq-_xwlfy-_AU-ErAQvhgOfOGodUKOnJJLV4ZpU99dxsEbH2Pf2gem6ax8dEPQC36dKkFWxKBfU8ONq_7B0mTCn-tpe512naeXoXB1F194RIIaccB0cAVe8iuz5GxsO2TKnUlJW91-7u6jRZJklzZgHu6pOW6Tcv-Iezyde-44Xwym7VVmXjlgUWxDpQrCe8N4YQtF9OVavbAIwTY1GTJ3QrjV2opCiW3paTfMPGPkwwzGgx9T5aIkB1n4FKIhNqLdV3XOWq4FnzmiPrqWFfgB36nLGjdwEqvjVODKsFgy8660m-rTxqp98Dr44kdctWl9mLpe-hBDDCUvhQxmmLPt6cU5-tQyxtiZffdrQDHMgbDz_zcKaYCHfeJsadLkgr8cso7QpeTUkSzs3zHHk-E-GUu8RgPuL_lVfU6xrSJ3Q7aca-U9PesWVpXkeHsk_RirHtM28xEKI6tzYN7NwpVdgBw2DfSpfERt8x_xwQTsENse84_ixcvcbz0v5owoqUlpDxXfQzlSV_3RaDDUvADOdhh_727aBm000F__0m00)
     
     + ### **Báo cáo hành chính:**
       - Brief Description: Tạo các báo cáo ẩn danh hàng tháng về số lượng bệnh nhân, chi phí điều trị, và các chỉ số quản lý.
       - Flow of Events:
         + Basic Flow:
           - Quản trị viên chọn loại báo cáo cần tạo.
           - Hệ thống thu thập dữ liệu liên quan và tạo báo cáo.
           - Báo cáo được lưu trữ và sẵn sàng để tải xuống hoặc in.
         + Alternative Flows: AF1: Không đủ dữ liệu:
           - Nếu không đủ dữ liệu để tạo báo cáo, hệ thống hiển thị thông báo và yêu cầu kiểm tra lại.
       - Special Requirements:
         + Báo cáo phải ẩn danh để bảo vệ thông tin cá nhân bệnh nhân.
         + Thời gian xử lý báo cáo không quá 10 giây.
       - Pre-Conditions:
         + Dữ liệu liên quan đã được ghi nhận đầy đủ trong hệ thống.
         + Quản trị viên có quyền tạo báo cáo.
       - Post-Conditions:
         + Báo cáo được lưu trữ và sẵn sàng để sử dụng.
         + Hệ thống ghi lại lịch sử tạo báo cáo.
       - Extension Points: Tích hợp với hệ thống quản lý cấp cao: Các báo cáo có thể được chia sẻ trực tiếp với quản lý cấp cao qua email.
      
+ ### **Quản lý dịch vụ y tế (Health Service Management):**     
   1 **Xác định các lớp phân tích**
      - **HealthServiceManager:** Đại diện cho quản lý dịch vụ y tế, yêu cầu và nhận báo cáo.
      - **ReportGenerator:** Xử lý yêu cầu, tạo báo cáo dựa trên dữ liệu hệ thống.
      - **PatientDataRepository:** Quản lý dữ liệu bệnh nhân, cung cấp dữ liệu cần thiết cho báo cáo.
      - **DrugDataRepository:** Quản lý dữ liệu về thuốc, cung cấp thông tin về chi phí và số lượng thuốc được kê đơn

   2 **Nhiệm vụ của từng lớp phân tích**
        **HealthServiceManager (Trình quản lý dịch vụ sức khỏe) :**  
            - Gửi yêu cầu báo cáo.  
            - Nhận và phân tích thông tin từ báo cáo để ra quyết định.  
         **ReportGenerator (Báo cáoGeneratorn) :**  
            - Xử lý yêu cầu báo cáo.  
            - Thu thập dữ liệu từ các nguồn và tổng hợp thành báo cáo.  
         **PatientDataRepository (Kho lưu trữ dữ liệu bệnh nhân)**  
            - Cung cấp thông tin tổng hợp về bệnh nhân, bao gồm số lượng bệnh nhân được điều trị.  
         **DrugDataRepository (Kho dữ liệu thuốc)**  
            - Cung cấp thông tin về loại thuốc được kê đơn, số lượng và chi phí.

   3 **Biểu đồ sequence :**

  ![Plantext](https://www.planttext.com/plantuml/png/Z951QiCm44NtEiLSm1VmmWGQI1SfbBQRBYUAi0MkPCQZGawGTO_WX13e9djhqOLFeXFq2aKbQcpQGdRIpFkyOURJVynQHcBtKWkKR0bk5TPSFIfwrLBTeS5I4M0BvwTea5XBtQ1XU52D9LueemXZ5blu-Kp0UsIj3C-HCMPQpPOs4JytOd4Ic9ChVzEn-esAD5XMN8mvF0_l3cJeZmvMGsT13fqLb_6oOkpBOHdwmmRMmP-Wri5l7Qo2tveAJ3NiZ1Yna4r5JnJwFTIXx_J_-OauZVwNbIiN_9iKYRdMbd8ZKLQaG-LmuqmPjt5eHjkOAREEn_u2003__mC0)

  4 **Thuộc tính và mối quan hệ giữa các lớp :**
   - Thuộc tính:
     **Trình quản lý dịch vụ sức khỏe**  
        - `managerID`: ID của người quản lý.  
        - `name`: Tên của người quản lý.
     **Trình tạo báo cáo**  
      - `reportID': ID báo cáo. 
      - `date`: Ngày tạo báo cáo.
     **Kho lưu trữ dữ liệu bệnh nhân**  
      - `patientID`: ID bệnh nhân.  
      - `visitDate`: Ngày khám.
     **Kho dữ liệu thuốc**  
      - `drugID': ID thuốc. 
      - `cost`: Chi phí thuốc.
   - Mối quan hệ giữa các lớp
      - **HealthServiceManager** gửi yêu cầu đến **ReportGenerator**.  
      - **ReportGenerator** truy xuất dữ liệu từ **PatientDataRepository** và **DrugDataRepository**.  
      - **ReportGenerator** trả kết quả cho **HealthServiceManager**.

   5 **Biểu đồ Lớp :**     
   ![PlanText](https://www.planttext.com/plantuml/png/RDAzIWGn40VmFaynfHRx0YdaYiKFK12liXnsnrmWcxsRJ0uEiVP9HB2nloqiV99z0bz1OaxPzLBEn_y76V8rV2o284lid6eSXW2NX4vMI-AjRUW6FHfYU5G0LPUBgrh3KjXwaveUEvhKmBI95EIErZtBoQbwKWStTox84wFq1v9_cdEnHI4DDGebp-G07OEtA9Qyr2YOXi5ApxlChlDexcvji6bxWZ-GDAk9C-LhZgPajnpD76xw81hENO_oX_wcirYyQLMT7Hr5tt--HMZ6_MjK_sTfl_nc3TVZ_cK7xJYyWxFZy5nE5vvKYYx8j-a_V0C00F__0m00)
  
4. Xác định các phần tử thiết kế
5. Thiết kế hệ thống con
6. Thiết kế các lớp
7. Kết luận
   
