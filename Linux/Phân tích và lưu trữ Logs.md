# Mục lục    
[1. Log là gì, để làm gì?](#1)    
[2. Syslog là gì?](#2)    
[3. Rsyslog là gì?](#3)      
[4. Logroation](#4)     
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
### 2. Syslog       
       

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



<a name='6'></a> 
## Tham khảo   
[1]https://levanphu.info/tim-hieu-co-ban-ve-cac-loai-log-tren-linux-unix   
[2]  


