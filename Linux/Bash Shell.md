  # Bash Shell
   
  [1. Different types of Shells](#1)   
  [2. Bash shell features  ](#2)   
  [3. Bash environment variables](#3)   
  [4. Path variables](#4)   
  [5. Customize Bash Prompt](#5)  

  ## [Tham khảo](#6)   
  
  ----    

<a name ='1'></a>
### 1.Different types of Shells   

- Có các loại shells khác nhau trong linux, nhưng một số loại shell phổ biến đó là:    
    - Bourne Shell (sh)  
    - C Shell (csh or tsh)    
    - Korn Shell (ksh)    
    - Z Shell (zsh)   
    - Bourne again shell (Bash)           

- Lệnh `echo $SHELL`: để check shell đang được sử dụng.    
![image](image/6.2.png)     

- Lệnh `chsh`: dùng để thay đổi shell mặc định, cần sử dụng password và phải đăng nhập vào một phiên terminal mới.      


<a name='2'></a>   
### 2. Bash Shell Features     

- Trong Bash, tùy chỉnh `alias` (bí danh) cho lệnh dùng dễ dàng hơn.      
    - Tạo `alias`:  
       - Cấu trúc: `alias alias_name='alias_command --options'`   
       - VD: `alias date='dt'`       
    - Lưu `alias`:   `source ~/.bashrc or ~/.bash_profile`: để khi reboot hệ thống không bị mất alias vừa tạo.        
    - Xóa `alias`: `unalias alias_name`       

![image](image/6.3.png)    

- Lệnh `history`: để hiện thị danh sách  các lệnh chạy trước.    

![image](image/6.4.png)    

<a name='3'></a>   
### 3. Bash environment variables.  

- Lệnh `echo $SHELL`: để in `SHELL`.        

![image](image/6.5.png)    

- Lệnh `env`: để xem danh sách tất cả các enviroment variable.    

![image](image/6.6.png)     

- Lệnh `export`: để set một enviroment variables.    
- Lệnh `echo "export Environment_name" >> ~/.profile or ~/.pam_environment`: để tạo environment variables và lưu lại tại file ~/.bashrc or ~/.bash_profile.     

- Lệnh `echo $LOGNAME`: hiện thị tên đăng nhập ra screen.    

<a name='4'></a>    
### 4.Path variables    

- `Path variables` là khi một người sử dụng lệnh external trong shell, thì shell sẽ sử dụng path variables để tìm kiếm lệnh external đó.    

- Lệnh `echo $PATH`: để xem các thư mục được xác định trong `path variables`.    

![image](image/6.7.png)      

- Lệnh `which [command]`: để xác định vị trí của command.    
- VD: `which pwd`      

![image](image/6.8.png)     

<a name='5'></a>  
### 5. Customize Bash Prompt   

![image](image/6.9.png)   
- Trong đó:   
   - `pdp18`: username.
   - `client1`: hostname.
   - `~`:Thư mục làm việc hiện tại (Presenting Working Directory)  
   - `$`: biểu tượng của người sử dụng.    
   - `#`: biểu tượng của người quản trị hệ thống.      

- Bash Prompt thì được đặt trong một biến môi trường shell riêng. Đó là variable `PS1`:    
- Lệnh `echo $PS1`: để xem các giá trị được gán cho `PS1`      

![image](image/7.0.png)   
- Lệnh `PS1="Centos8"` để thay đổi lời nhắc hiện thị word "Centos8"         
![image](image/7.2.png)            

- Các `[Options]`    

![image](image/7.1.png)    

- Lệnh `PS1="[\d \t \u@\h \w] $ "`: Để thay đổi bash prompt hiện thị `date`, `time`, `username of the current user`, `hostname`, và `current working  directory`.    

<a name ='6'></a>
## Tham khảo    
  [1]https://github.com/phupham1805/linux-basics-course/blob/master/docs/02-Working-With-Shell-Part-I/05-Bash-Shell.md









