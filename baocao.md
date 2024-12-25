# BÁO CÁO CUỐI KÌ 
## Mentcare: A mental health support system
1. Mô tả tóm tắt bài toán: Cơ quan y tế khu vực Mid-Scotland muốn mua một hệ thống thông tin để giúp quản lý việc chăm sóc bệnh nhân mắc các vấn đề về sức khỏe tâm thần. Mục tiêu chung của hệ thống là:
   - Cung cấp thông tin quản lý tốt hơn về chăm sóc sức khỏe tâm thần trong khu vực.
   - Cung cấp hệ thống hồ sơ được cải thiện cho đội ngũ nhân viên lâm sàng tham gia chẩn đoán và điều trị.
   - *Chú ý: Hệ thống không nhằm mục đích là hệ thống hồ sơ y tế hoàn chỉnh, nơi lưu giữ mọi thông tin về quá trình điều trị y tế của bệnh nhân. Hệ thống chỉ nhằm mục đích hỗ trợ chăm sóc sức khỏe tâm thần (ví dụ:nếu bệnh nhân mắc một số tình trạng không liên quan khác, chẳng hạn như huyết áp cao, tình trạng này sẽ không được ghi nhận chính thức trong hệ thống). Do đó, hệ thống phải tương tác và chia sẻ thông tin với các hệ thống hồ sơ bệnh nhân khác đang được sử dụng.*(ở phần 1.Introduction)
   - Sự cần thiết:(1.1 system overview)
     + Quản lý thông tin hiệu quả: Hệ thống giúp quản lý thông tin bệnh nhân, từ thông tin cá nhân đến lịch sử điều trị, một cách hiệu quả và có tổ chức.
     + Theo dõi điều trị: Hỗ trợ theo dõi tình trạng điều trị của bệnh nhân, đảm bảo rằng không có bệnh nhân nào bị bỏ sót hay quên lịch hẹn.
     + Quản lý giam giữ: Đặc biệt quan trọng trong việc quản lý những bệnh nhân cần giam giữ bắt buộc vì lý do an toàn.
   - Lợi ích khi giải quyết bài toán:(1.1 system overview)
     + Cải thiện chất lượng chăm sóc: Tăng cường khả năng cung cấp dịch vụ chăm sóc sức khỏe tâm thần chất lượng cao thông qua việc quản lý và theo dõi bệnh nhân hiệu quả.
     + Tiết kiệm thời gian: Giảm bớt thời gian tìm kiếm và cập nhật thông tin bệnh nhân cho các bác sĩ và nhân viên y tế.
     + Đáp ứng pháp lý: Đảm bảo tuân thủ các yêu cầu pháp lý về an toàn và quyền riêng tư của bệnh nhân.
   - Các yêu cầu chức năng:(1.1 system overview)
     + Quản lý chăm sóc cá nhân:
       - Tạo, chỉnh sửa và xem hồ sơ bệnh nhân.
       - Ghi nhận các buổi tư vấn, tình trạng và phương pháp điều trị.
     + Theo dõi bệnh nhân:
       - Theo dõi thường xuyên tình trạng bệnh nhân.
       - Cảnh báo khi phát hiện các vấn đề có thể xảy ra hoặc khi bệnh nhân không gặp bác sĩ theo lịch hẹn.
     + Quản lý giam giữ bắt buộc:
       - Quản lý thông tin và tình trạng của những bệnh nhân bị giam giữ.
       - Đảm bảo tuân thủ quy trình pháp lý liên quan đến việc giam giữ.
     + Báo cáo hành chính:
       - Tạo các báo cáo quản lý hàng tháng.
       - Báo cáo về số lượng bệnh nhân, tình trạng bệnh, chi phí điều trị.
   - các yêu cầu phi chức năng:(1.1 system overview)
     + An toàn:
       - Cảnh báo cho nhân viên y tế về những bệnh nhân có nguy cơ tự tử hoặc gây nguy hiểm.
       - Đảm bảo hệ thống luôn khả dụng và có thể truy cập khi cần.
     + Quyền riêng tư:
       - Bảo mật thông tin bệnh nhân, chỉ cho phép nhân viên y tế được ủy quyền truy cập.
       - Ngăn chặn việc truy cập không hợp pháp vào thông tin cá nhân của bệnh nhân.
     + Hiệu suất:
       - Đảm bảo hệ thống hoạt động mượt mà với thời gian phản hồi nhanh chóng.
       - Khả năng xử lý lượng lớn dữ liệu và nhiều truy vấn cùng lúc.
      
2. Phân tích các ca sử dụng: (Trang 4. Mục 1.1 System overview : The key features of the system are.....)
   - Kiến trúc đề xuất: Mô hình triển khai : Kiến trúc máy khách-máy chủ.
     + Máy khách: Các nhân viên y tế và quản trị viên sẽ truy cập hệ thống qua trình duyệt web (Firefox) trên giao diện tương tác dạng biểu mẫu.
     + Máy chủ: Lưu trữ hồ sơ bệnh nhân và xử lý yêu cầu từ máy khách, được vận hành trên các máy chủ Linux.
   - Các cơ chế phân tích:
     + Yêu cầu hệ thống:
       - Tính khả dụng:
         + Hệ thống phải hoạt động liên tục trong giờ làm việc từ 08:00 - 18:30, từ Thứ Hai đến Thứ Sáu.
         + Bảo trì được sắp xếp ngoài giờ làm việc (21:00 - nửa đêm, hoặc Chủ Nhật 08:00 - 12:00).
       - Hiệu suất:
         + Hệ thống phải phản hồi trong vòng 2 giây cho các truy vấn bệnh nhân thông thường.
         + Nếu phản hồi mất hơn 2 giây, hệ thống hiển thị trạng thái xử lý để tránh bực bội cho người dùng.  
     + Cơ chế bảo mật:
       - Hệ thống phải đảm bảo quyền riêng tư dữ liệu bệnh nhân, chỉ cho phép nhân viên được ủy quyền truy cập.
       - Tích hợp hệ thống xác thực đa yếu tố.
     + Cơ chế quản lý dữ liệu:
       - Dữ liệu được xác thực trước khi lưu, đặc biệt đối với các mục không chọn từ menu.
       - Tất cả thông tin được lưu giữ tuân thủ các tiêu chuẩn bảo mật và quy định của hệ thống y tế Mid-Scotland.
   - Kết quả phân tích từng ca sử dụng:
     + ### **Quản lý chắm sóc cá nhân**:
       - Brief Description: Ca sử dụng này cho phép nhân viên lâm sàng quản lý thông tin bệnh nhân, bao gồm tạo hồ sơ mới, chỉnh sửa thông tin, và xem lịch sử điều trị.
       - Flow of Events:
         + Basic Flow:
           - Nhân viên lâm sàng đăng nhập vào hệ thống.
           - Hệ thống hiển thị giao diện tìm kiếm hồ sơ bệnh nhân.
           - Nhân viên lâm sàng tìm kiếm hoặc chọn một bệnh nhân từ danh sách.
           - Nhân viên lâm sàng xem, chỉnh sửa thông tin, hoặc tạo hồ sơ bệnh nhân mới.
           - Hệ thống xác nhận thay đổi và lưu vào cơ sở dữ liệu.
         + Alternative Flows:
           - AF1: Không tìm thấy bệnh nhân: Nếu không có kết quả tìm kiếm, nhân viên lâm sàng được thông báo và có thể tạo hồ sơ bệnh nhân mới.
           - AF2: Dữ liệu không hợp lệ: Nếu thông tin nhập vào không đúng định dạng, hệ thống hiển thị thông báo lỗi và yêu cầu sửa.
       - Special Requirements:
         + Phải xác thực thông tin đăng nhập của nhân viên.
         + Dữ liệu nhập phải được kiểm tra định dạng và tính hợp lệ.
       - Pre-Conditions:
         + Nhân viên lâm sàng đã đăng nhập thành công vào hệ thống.
         + Cơ sở dữ liệu bệnh nhân khả dụng.
       - Post-Conditions:
         + Hồ sơ bệnh nhân được tạo mới hoặc cập nhật.
         + Các thay đổi được lưu trữ an toàn trong cơ sở dữ liệu.
       - Extension Points: Tích hợp hệ thống hồ sơ quốc gia: Khi tạo hoặc chỉnh sửa hồ sơ, hệ thống có thể gửi thông tin tóm tắt đến hệ thống hồ sơ bệnh án quốc gia.
     + ### **Theo dõi bệnh nhân:**
       - Brief Description: Hệ thống theo dõi hồ sơ bệnh nhân đang điều trị, phát hiện các vấn đề như bỏ lỡ cuộc hẹn hoặc nguy cơ sức khỏe, và đưa ra cảnh báo cho nhân viên lâm sàng.
       - Flow of Events:
         + Basic Flow:
           - Hệ thống tự động kiểm tra các hồ sơ bệnh nhân định kỳ.
           - Nếu phát hiện vấn đề (bỏ lỡ cuộc hẹn, không tuân thủ điều trị), hệ thống ghi nhận cảnh báo.
           - Nhân viên lâm sàng nhận được thông báo qua giao diện hoặc email.
         + Alternative Flows:
           - AF1: Không có vấn đề: Nếu không có vấn đề nào được phát hiện, hệ thống không gửi cảnh báo.
           - AF2: Sai thông tin lịch sử: Nếu dữ liệu bệnh nhân không đầy đủ, hệ thống báo lỗi đến quản trị viên.
       - Special Requirements:
         + Hệ thống phải chạy kiểm tra tự động hàng ngày.
         + Dữ liệu lịch sử phải chính xác để đưa ra cảnh báo đúng.
       - Pre-Conditions:
         + Hồ sơ bệnh nhân đầy đủ và có dữ liệu lịch sử điều trị.
         + Nhân viên lâm sàng đã được ủy quyền nhận cảnh báo.
       - Post-Conditions:
         + Cảnh báo được ghi lại và gửi đến nhân viên lâm sàng.
         + Hành động cần thiết (nếu có) được thực hiện bởi nhân viên lâm sàng.
       - Extension Points: Tích hợp hệ thống lịch hẹn: Dữ liệu lịch hẹn được đối chiếu với hồ sơ bệnh nhân để kiểm tra sự tuân thủ điều trị.
     + ### **Quản lý giam giữ bắt buộc:**
       - Brief Description: Ghi nhận và quản lý thông tin bệnh nhân bị giam giữ tại bệnh viện an ninh để đảm bảo tuân thủ các quy định pháp luật.
       - Flow of Events:
         + Basic Flow:
           - Nhân viên lâm sàng cập nhật thông tin giam giữ của bệnh nhân.
           - Hệ thống xác minh thông tin nhập vào (ngày giam giữ, lý do).
           - Thông tin được ghi nhận và lưu trữ.
           - Hệ thống gửi thông báo nhắc nhở các cuộc kiểm tra định kỳ liên quan.
         + Alternative Flows: AF1: Dữ liệu nhập không hợp lệ:
           - Hệ thống hiển thị lỗi nếu dữ liệu nhập vào không đúng định dạng.
           - Nhân viên phải sửa và gửi lại.
       - Special Requirements:
         + Hệ thống phải tuân thủ các tiêu chuẩn và quy định pháp luật về giam giữ bắt buộc.
         + Phải đảm bảo tính bảo mật cao cho dữ liệu.
       - Pre-Conditions:
         + Nhân viên lâm sàng được cấp quyền chỉnh sửa thông tin giam giữ.
         + Hệ thống phải hoạt động ổn định và truy cập được.
       - Post-Conditions:
         + Thông tin giam giữ được cập nhật chính xác trong cơ sở dữ liệu.
         + Lịch kiểm tra liên quan được lên kế hoạch và nhắc nhở.
       - Extension Points: Tích hợp với hệ thống báo cáo quản lý: Các thông tin giam giữ được tổng hợp vào báo cáo hành chính.
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
     
     
  
4. Xác định các phần tử thiết kế
5. Thiết kế hệ thống con
6. Thiết kế các lớp
7. Kết luận
   
