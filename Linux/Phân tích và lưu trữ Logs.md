# Mục lục    
[1. Mô tả kiến trúc Log hệ thống](#1)    
[2. Reviewing Syslog Files](#2)    
[3. Reviewing System Journal Entries](#3)    
[4. Preserving The System Journal](#4)     
[5. Duy trì thời gian chính xác](#5)     

## [Tham Khảo](#6)   

----  

<a name='1'></a>    
### 1. Mô tả kiến trúc Log hệ thống   
- Hầu hết các hệ thống ghi lại logs of events trong tệp văn bản, có thể được tìm thấy trong thư mục `/var/log` và thư mục con.     

  ![image](image/3.7.png)  
- Một `logging system` tiêu chuẩn dựa trên giao thức `syslog` thì đã được xây dựng trong Linux. Nhiều chương trình sử dụng hệ thống này để ghi lại events và sắp xếp chúng thành files log. Dịch vụ `systemd-journald` và `rsyslog` xử lý `syslog messages` trong Linux.   
      
|Log File|Chức năng|   
|----|----|  
|/var/log/messages|Most syslog messages are logged here. Ngoại trừ thông tin liên quan authentication và email processing, scheduled job execution and debug.|   
|/var/log/secure|Syslog messages được liên quan đến bảo mật và xác thực events.|   
|/var/log/maillog|Syslog messages được liên quan mail server |   
|/var/log/cron| Syslog messages được liên quan đến scheduled job execution |   
|/var/log/boot.log|Non-syslog console messages được liên quan đến hệ thống khởi động.|



