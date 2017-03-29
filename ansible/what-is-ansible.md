## Ansible là gì và nó hoạt động như thế nào? 
Tiêu chí của Ansible là "Công cụ tự động hóa triển khai, mã nguồn mở, cấu hình đơn giản, không cần agent (phần mềm đại lý) và mạnh mẽ".
Ansible có những tính năng cơ bản sau:
- Dự phòng tài nguyên (provisioning)
- Quản lý cấu hình (configuration management)
- Triển khai ứng dụng (app deployment)
- Giao hàng liên tục (continous delivery)
- Bảo mật và tuân thủ (security and compliance)
- Điều phối (orchestration).

Ansible kết hợp tốt với các công nghệ:

1. AWS (Amazon Web Service - dịch vụ điện toán đám mấy của Amazon)
2. Docker (công nghệ đóng gói các phần mềm cài đặt)
3. OpenStack (công nghệ vận hành nền tảng như là dịch vụ - infrastructure as service)
4. Red Hat
5. Windows

### Dự phòng tài nguyên (Provisioning)
Ansible là công cụ quản lý tự động hệ thống mà không cần phải cài đặt phần mềm trên máy tính bị điều khiển (agentless). Nó có thể quản lý máy chủ, thiết bị cân bằng tải, switch, tường lửa nhờ SSH (secure shell). Dù hệ thống là máy chủ vật lý (bare-metal) hay là máy chủ dịch vụ đám mây, Ansible giúp chúng ta quản lý, cấu hình hệ thống rất đơn giản.

### Quản lý cấu hình (Configuration management)
Ansible là công cụ giúp chuyên viên quản lý hệ thống tự động hóa các tác vụ buồn tẻ, lặp đi lặp lại (thường phải gõ các câu lệnh dài khó nhớ qua màn hình terminal).
Với Ansible ta có thể viết một playbooks đơn giản trên ngôn ngữ Python 2.x sử dụng lại các module viết sẵn chất lượng cao, đã kiểm thử trên nhiều môi trường khác nhau. Các module thường là mã nguồn mở (chẳng hạn như AWS, Nagios, PostgreSQL, SSH, APT, File Folder IO) gồm nhiều tác vụ có tham số để lập trình viên tùy biến theo yêu cầu cụ thể.

### Triển khai ứng dụng (App deployment)
Trong Ansible, artifact là những thay đổi nhóm phát triển tạo ra để triển khai tới các server. Số lượng server có thể chỉ một hoặc nhiều đến hàng trăm máy chủ. Ansible kết nối thông qua SSH, không cần kéo từ một kho respository về mỗi server hoặc theo cách cổ điển là copy các file kiểu FTP rất chậm chạp. Ansible đồng bộ các artifact bằng cách cập nhật file mới hoặc  bỏ qua những file không sửa đổi. Cách này cũng tăng tốc độ truyền file và tiết kiệm một lượng lớn băng thông.
Bên cạnh việc truyền file, Ansible cũng giúp cho các server luôn sẵn sàng phục vụ ở chế độ production. Trước khi triển khai ứng dụng lên máy chủ X, Ansible tạm dừng việc các tiến trình giám sát X, tạm loại bỏ X ra khỏi tập máy chủ cân bằng tải, tạm tắt các dịch vụ đang chạy trên X. Sau khi triển khai xong, nó có thể bắt đầu các dịch vụ, gán X vào tập máy chủ cân bằng tải, và giám sát trở lại.

