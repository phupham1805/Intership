# Mục lục    
[1. Log để làm gì?](#1)    
[2. Syslog là gì?](#2)    
[3. Rsyslog là gì?](#3)    
[4. Logroation](#4)     
[5. Journal](#5)     

## [Tham Khảo](#6)   

----  

<a name='1'></a>    
### 1. Log là gì, để làm gì? 
VD: Khi quản lý một server chứa nhiều dữ liệu hoặc đã cài đặt rất nhiều ứng dụng, tính năng. Server tự nhiên mất dữ liệu, muốn điều tra xử lý và tìm nguyên nhân khắc phục hậu quả xảy ra thì `log` sẽ giúp việc này.   
  -  1.1 Log là gì?          
     - `log` là dữ liệu sinh ra khi hệ thống hoạt động ghi lại liên tục các thông báo về hoạt động của cả hệ thống hoặc các dịch vụ được triển khai trên hệ thống và file tương ứng.   
     - Các file log sẽ xuất log cho bạn biết tất cả các tiến trình diễn ra trong hệ thống.   
     - Hệ điều hành Linux cung cấp một kho lưu trữ tập trung các file log trong thư mục `/var/log`   

  ![image](image/3.9.png)  

|Log File|Loại messages được lưu trữ|   
|----|----|  
|/var/log/messages|Most syslog messages are logged here. Ngoại trừ thông tin liên quan authentication và email processing, scheduled job execution and debug.|   
|/var/log/secure|Files log lưu trữ syslog messages liên quan đến bảo mật và xác thực events.|   
|/var/log/maillog|Files lưu trữ syslog messages liên quan mail server |   
|/var/log/cron|Files lưu trữ syslog messages liên quan đến scheduled job execution |   
|/var/log/boot.log|Non-syslog console messages liên quan đến hệ thống khởi động.|     

<a name='2'></a>    
### 2. Syslog       
- Logging events to the system   
   - Nhiều chương trình sử dụng giao thức syslog để log events đến hệ thống. Mỗi log messages thì được phân phối bởi 1 cơ sở (kiểu của messages) và độ ưu tiên (mức độ nghiệm trọng của messages).    

   |code|Priority|Severity|   
   |----|----|----|   
   |0|emerg|Hệ thống thì không thể sử dụng được|    
   |1|alert|Hành động phải được thực hiện ngay lập tức|    
   |2|crit|Tình trạng nguy hiểm|   
   |3|err|Tình trạng lỗi không nguy hiểm|   
   |4|warning|Tình trạng cảnh báo|   
   |5|notice|Event bình thường nhưng quan trọng|   
   |6|info|Thông tin event|    
   |7|debug|Debugging-level messages|   






