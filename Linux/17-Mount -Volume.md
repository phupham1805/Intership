# Mục lục      
[1. Tạo phân vùng và định dạng ổ đĩa](#1)     
[2. Cách thực hiện Mount sau khi gắn Volume mới](#2)    
[3.](#3)      

## [Tham khảo](#4)     

-----   

<a name='1'></a>      
### 1. Tạo phân vùng và định dạng ổ đĩa.           

*Trước hết ta phải add thêm một disk cho máy. Vào `VM` -> `Setting` -> `Hard Disk` -> `Add`*.   

![image](image/13.3.png)     

- Ta thấy, một harddisk sdb mới được tạo có 20G và harddisk này chưa được định dạng.      
- Với /dev/sdb mới chưa được định dạng nói trên, trước hết ta dùng lệnh fdisk.     
```  
fdisk /dev/sdb    
```     
- Sau khi dùng `fdisk /dev/sdb`, sẽ xuất hiện chế độ gõ lệnh của fdisk, ấn `m` để đưa ra các hướng dẫn về lệnh fdisk. Trong ví dụ này, ta chọn `n` để thêm một partition mới.    

![image](image/13.4.png)    

- Sau khi chọn `n`, xuất hiện các lựa chọn: lựa chọn `p` để tạo primary partition - phân vùng có thể boot được, lựa chọn `e` để tạo một phân vùng extended. Bước này chọn `p`, chương trình sẽ hỏi Partition number (1-4), gõ số 1. Chương trình sẽ cho phép bạn thay đổi First cylinder và Last cylinder. Chọn First cylinder = 2048 và Last cylinder = 41943039. Fdisk sẽ quay trở lại chế độ gõ lệnh chính của nó.    
- Gõ `w` để lưu lại bản ghi đã thay đổi.     

![image](image/13.5.png)    

- Gõ lệnh `fdisk -l` để xem những thay đổi vừa rồi.    

![image](image/13.6.png)    
- Lệnh `lsblk` để xem những thay đổi.  

![image](image/13.7.png)   

*Ta thấy volume `sdb` được gán vào máy ảo nhưng chưa được mount với bất kì thư mục nào trong hệ thống Linux*.     

<a name='2'></a>    
### 2. Cách thực hiện Mount sau khi gắn Volume mới.        

- B1: Thực hiện tạo file system cho Volume cần mount, ở đây ta sẽ dùng ext4 (hoặc có thể dùng xfs):   `mkfs.ext4 /dev/sdb`        

![image](image/13.8.png)    

- B2: Tạo thư mục mới để mount volume với thư mục này.   
`mkdir /backup`      

- B3: Thực hiện mount volume `sdb` với thư mục này.    
`mount /dev/sdb /backup`      


*Kiểm tra xem đã mount thành công chưa bằng lệnh `df -Th`      

![image](image/13.9.png)    

- Nhưng để cấu hình máy ảo tự nhận volume sau khi reboot ta phải cấu hình file `/etc/fstab`.    
- B1: Lấy uuid của volume.     `blkid`        

![image](image/14.0.png)     
- B2: Cấu hình file `/etc/fstab` thêm vào dòng cuối      

![image](image/14.1.png)     

- B3: Thực hiện mount tất cả những gì đã khai báo trong file `/etc/fstab`     
```   
mount -a
```     
- Lệnh `unmount`: để thoát ổ đĩa ra một cách an toàn mà không làm hỏng dữ liệu lưu trữ trong đó.    
