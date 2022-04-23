# Mục lục    
[1. KVM là gì ? ](#1)    
[2. ](#2)    

## [Tham khảo](#5)    
-----    

<a name='1'></a>   

## 1. KVM là gì ?
- KVM là một nền tảng áo hóa mã nguồn mở và free cho nhân kernel Linux.   
- `KVM_Kernel based Virtual Machine` chỉ có thể được sử dụng trong một bộ xử lý với mở rộng ảo hóa phần cứng, như là `Intel-VT or AMD-V`.     
-KVM đáp ứng sự ổn định và nhanh cho workloads (khối lượng công việc) nhiều, dùng để tạo và chạy VM trong KVM.        
- Dưới KVM, mỗi VM là một process được lên kế hoạch và được điều khiển bởi kernel và có phần cứng ảo hóa riêng (CPU, Network Interface, disk,...). Nó hỗ trợ nested virtualization (ảo hóa lồng nhau), cái mà người dùng bật để chạy 1 VM bên trong VM khác.    


### Đặc tính của KVM      
- KVM hypervisor hỗ trợ các đặc tính sau:     
   - `over - committing`: Phân bổ nhiều CPU hoặc memory ảo hơn resource có sẵn trong hệ thống.    
   - `thin provisioning`: Phân bổ storage linh hoạt và tối ưu space có sẵn cho mỗi VM guest.   
   - `Disk I/O throttling`: Cung cấp khả năng set giới hạn trên disk I/O được yêu cầu từ VM đến máy host.      
   - `Automatic NUMA balancing`: Cải tiến hiệu suất của ứng dụng đang chạy trong hệ thống hardware NUMA.     
   - `Virtual CPU hot add capability`: Cung cấp khả năng tăng sức mạng xử lý khi cần thiết trong khi chạy VM, không có thời gian chết (downtime).        

- 
