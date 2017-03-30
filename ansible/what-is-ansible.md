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

Tất cả điều này không xảy ra cùng lúc trên tất cả các server. Ansible có thể làm việc trên một tập con của các server tại một thời điểm để cung cấp các triển khai không có thời gian chết. Ví dụ tại một thời điểm duy nhất nó có thể triển khai trên 5 server cùng lúc, và sau đó nó có thể triển khai tới 5 server tiếp theo khi kết thúc.

### Giao hàng liên tục (Continuous delivery)
Mục tiêu của giao hàng liên tục là thường xuyên - nhanh chóng triển khai phiên bản cập nhật đã kiểm thử tự động lên môi trường sản xuất. Để đạt được mục tiêu này, cần sử dụng các công cụ tốt nhất cho phép phát hành thường xuyên mà không ngưng hoạt động và yêu cầu ít nhất sự can thiệp của con người. Ansible thực hiện các triển khai mà không có thời gian chết. Yêu cầu khác của giao hàng liên tục là giảm tối đa xử lý thủ công và chuyển qua tự động hóa. Ansible tự động hóa nhiệm vụ từ chuẩn bị máy chủ ảo, cài đặt phần mềm đến cấu hình dịch vụ cho đến khi hệ thống vận hành được. Sau khi kịch bản (playbook) được tạo và kiểm tra, việc còn lại đặt playbook trong hệ thống tích hợp liên tục và để Ansible thực thi.

### Bảo mật và tuân thủ (Security and Compliance)
Bảo mật là cực kỳ quan trọng. Giữ hệ thống an toàn là một điều khó đạt được nhất. Để đảm bảo tính bảo mật cho hệ thống, định nghĩa bảo mật là không đủ, phải áp dụng các cơ chế bảo mật và giám sát liên tục hệ thống để chắc rằng chúng liên tục tuân thủ bảo mật.

Ansible tự động hóa cấu hình các tập luật đóng mở cổng tường lửa, cấp phép tùy chỉnh theo từng người dùng hoặc nhóm. Ansible tin cậy vì các lệnh cấu hình bảo mật được lập trình thành kịch bản trong playbook. Playbook có thể quản lý phiên bản ví dụ dùng Git. Quản trị hệ thống có thể điều chỉnh và chạy lại trên nhiều máy chủ.

### Điều phối (Orchestration)
Ansible đảm bảo rằng tất cả các nhiệm vụ được cung cấp theo thứ tự thích hợp và thiết lập một sự hài hòa giữa tất cả các tài nguyên mà nó quản lý. Tính năng quản lý cấu hình và triển khai của Ansible giúp điều phối dễ dàng các đợt triển khai nhiều tầng. Ví dụ khi triển khai một ngăn xếp phần mềm, làm sao cơ sở dữ liệu sẵn sàng trước application server hoặc phải cấu hình mạng thông suốt trước khi bổ xung máy chủ vào nhóm máy chủ cân bằng tải.

Ansible phối hợp tốt với các công cụ điều phối CloudFormation của Amazon, Heat của OpenStack, Swarm của Docker ...Theo các này, thay vì học các nền tảng, ngôn ngữ, quy tắc khác nhau, thì tập trung vào việc viết kịch bản cú pháp YAML và gọi các tác vụ từ các module có sẵn.
