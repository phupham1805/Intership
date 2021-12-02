# Mục lục    
[1. Log là gì, để làm gì?](#1)    
[2. Giao thức Syslog là gì?](#2)    
[3. Rsyslog là gì?](#3)      
[4. Logrotate là gì?](#4)     
[5. Journal](#5)     

## [Tham Khảo](#6)   

----  

<a name='1'></a>    
### 1. Log là gì, để làm gì?    

*VD: Khi quản lý một server chứa nhiều dữ liệu hoặc đã cài đặt rất nhiều ứng dụng, tính năng. Server tự nhiên mất dữ liệu, muốn điều tra xử lý và tìm nguyên nhân khắc phục hậu quả xảy ra thì `log` sẽ giúp việc này.*    

- 1.1 Log là gì?             
   - `log` là dữ liệu sinh ra khi hệ thống hoạt động ghi lại liên tục các thông báo về hoạt động của cả hệ thống hoặc các dịch vụ được triển khai trên hệ thống và file tương ứng.       

![image](image/4.0.png)     

- 1.2 Công dụng của Log    
   - Phân tích nguyên nhân và khắc phục nhanh hơn khi có sự cố xảy ra.   
   - Phát hiện và dự đoán vấn đề có thể xảy ra đối với hệ thống.
   
- Các file log sẽ xuất log cho bạn biết tất cả các tiến trình diễn ra trong hệ thống.      
- Hệ điều hành Linux cung cấp một kho lưu trữ tập trung các file log trong thư mục `/var/log`     

![image](image/3.9.png)           
- 1.3 File Log:   
     **Ví dụ**  
   - Syslog: Log hệ thống thông thường chứa các thông tin mặc định của hệ thống, thường được lưu trong /var/log/syslog hoặc /var/log/messages.  

![image](image/4.1.png)     

   - Auth.log: Chứa thông tin xác thực trên hệ thống. Khi chúng ta tìm kiếm vấn đề liên quan đến cơ chế ủy quyền của người dùng thì file log này sẽ làm điều đó.   
      - Thông qua file log này giúp cho chúng ta xác định được:  
         - Các lần thử đăng nhập thất bại.   
         - Điều tra các cuộc tấn công và các lỗ hổng liên quan đến cơ chế ủy quyền của người dùng.        
- Một số file log có trong thư mục /var/log    
    - /var/log/boot.log: log trong quá trình khởi động hệ thống.      
    ![image](image/4.3.png)   
    - /var/log/cron: các hoạt động của crond.       
    ![image](image/4.2.png)   
    - /var/log/dmesg: chứa thông tin bộ đệm vòng kernel.    
    - /var/log/yum.log: các log của yum.    
    - /var/log/secure: log xác thực     
    - /var/log/wtmp: chứa thông tin lịch sử về các lần đăng nhập và đăng xuất.    
    ![image](image/4.4.png)
    - /var/log/btmp: chứa thông tin đăng nhập không thành công.   

<a name='2'></a>    
### 2. Giao thức Syslog      

- 2.1 Syslog là gì?   
    - Syslog là một giao thức client/server là giao thức dùng để chuyển log và thông điệp đến máy nhận log. Máy nhận log thường được gọi là `syslogd, syslog daemon hoặc syslog server.`        
    - Syslog có thể gửi qua UDP hoặc TCP.   
    - Syslog dùng `port 514`.   
    - Trong chuẩn syslog, mỗi thông báo đều được dán nhãn và được gán các mức độ nghiêm trọng khác nhau.      
- 2.2 Mục đích của syslog ?    
    - Syslog xác định mức độ nghiêm trọng (severity levels) cũng như mức độ cơ sở (facility levels) giúp người dùng hiểu rõ hơn về log được sinh ra ở máy.  

**Cấp độ cơ sở Syslog (Syslog Facility levels)**:    
- Dùng để xác định chương trình
- Xác định Log được tạo ra từ đâu   
- Xác định mục đích Log sinh ra    
- Nếu một máy khác muốn sinh ra log thì sẽ là một tập hợp các cấp độ facility được bảo lưu từ 16-23 được gọi là "local use" facility levels.     

|Facility|Nguồn tạo log|Ý nghĩa|   
|----|----|----|    
|0|kernel|Những log mà do kernel sinh ra|   
|1|user|Log ghi lại cấp độ người dùng|   
|2|mail|Log của hệ thống mail|    
|3|daemon|Log của các tiến trình trên hệ thống|    
|4|auth|Log từ quá trình đăng nhập hệ thống hoặc xác thực hệ thống|    
|5|syslog|Log từ chương trình syslogd|   
|6|lpr|Log từ quá trình in ấn|    
|7|news|Thông tin từ hệ thống|    
|8|uucp|Log UUCP sybsystem|    
|9||Clock daemon|    
|10|authpriv|Quá trình đăng nhập hoặc xác thực hệ thống|    
|11|ftp|Log của FTP daemon|    
|12||Log từ dịch vụ NTP của các subserver|    
|13||Kiểm tra đăng nhập|   
|14||Log cảnh báo hệ thống|   
|15|cron|Log từ clock daemon|    
|16-23|local 0-local 7|Log dự trữ cho sử dụng nội bộ|     

**Cấp độ cảnh báo**    
- Dựa vào mức cảnh báo để biết và khắc phục sự cố.   
- Có 8 cấp độ từ 0-7, 0 là cấp độ khẩn cấp quan trọng nhất.    

|Value|Severity|Keyword|    
|----|----|----|  
|0|Emergency|`emerg`-Thông báo tình trạng khẩn cấp|   
|1|Alert|`alert`-Hệ thống cần can thiệp ngay|    
|2|Critical|`crit`-Tình trạng nguy kịch|    
|3|Error|`err`-Thông báo lỗi đối với hệ thống|    
|4|Warning|`warning`-Mức cảnh báo đối với hệ thống|    
|5|Notice|`notice`-Chú ý đối với hệ thống|   
|6|Informational|`info`-Thông tin của hệ thống|   
|7|Debug|`debug`-Quá trình kiểm tra hệ thống|     

**Định dạng chung của một gói tin syslog**    
- Định dạng của một thông báo syslog gồm 3 phần chính.   
   `<PRI> HEADER MSG`      

Trong đó:   
  - `PRI` hay `Priority` thể hiện cơ sở sinh ra log hoặc mức độ nghiêm trọng, là một số gồm 8 bit:     
       - 3 bit đầu thể hiện tính nghiêm trọng của thông báo.(severity levels)
       - 5 bit còn lại đại diện cho cơ sở sinh ra thông báo. (facility levels)     

- Giá trị PRI được tính như sau:  
    - `Facility levels x 8 + Severity levels`      

VD: Thông báo từ kernel (Facility=0) với mức độ nghiêm trọng (Severity=0) thì giá trị Priority = 0x8+0 =0     
Trường hợp khác, với "local use 4" (Facility=20) mức độ nghiêm trọng (Severity=5) thì số Priority là 20 x 8 + 5 = 165      
Ngược lại: 
Nếu biết Priority = 191 thì xác định `Facility` và `Severity` là bao nhiêu ?  
- Lấy 191:8=23.875 -> Facility =23 ("local 7") -> Severity =191-(23*8)=7 (debug).     

`HEADER`    
- Phần HEADER thì gồm các phần chính sau:   
    - Time stamp -Thời gian mà thông báo được tạo ra. Thời gian này được lấy từ thời gian hệ thống    
    *Note: thời gian của server và thời gian của client khác nhau thì thông báo ghi trên log được gửi lên server là thời gian của client*      
    - Hostname hoặc IP      
   
`MSG`   
- Phần Message hay MSG chứa một số thông tin về quá trình tạo ra thông điệp đó. Gồm 2 phần chính: 
   - Tag field: tên chương trình tạo ra thông báo.   
   - Content field: chứa các chi tiết của thông báo.      
          




<a name='6'></a> 
## Tham khảo   
[1]https://levanphu.info/tim-hieu-co-ban-ve-cac-loai-log-tren-linux-unix   
[2]  


