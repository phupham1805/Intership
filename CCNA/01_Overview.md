# Mục lục   
[1. Tổng quan](#1)    

## [Tham khảo](#4)    
----    

<a name='1'></a>      

## 1.Tổng quan    
- Mạng là gì ?   
   - `Mạng (network)` là tập hợp các thiết bị dùng để truyền dữ liệu và hệ thống các thiết bị đầu cuối (máy tính, máy server,...) được kết nối để giao tiếp và truyền thông với nhau.       

- Các thành phần cơ bản:     
   - Các PC đầu cuối  
   - Các kết nối    
       - `Card mạng` (NIC_Network Interface Card): chuyển dữ liệu được tạo ra bởi ứng dụng trên PC thành định dạng dữ liệu có thể truyền được trên kết nối mạng.   
       - `Phương tiện truyền dẫn (network media)`: như cáp mạng hoặc sóng không giây cho phép truyền đi các tín hiệu từ một thiết bị này đến một thiết bị khác.    
       - `Các đầu nối (Connector)`:kết nối một đường truyền có dây, cho phép giao tiếp giữa đường truyền với NIC card của PC.    

- `Switch`: Các thiết bị đầu cuối như PC được kết nối về một thiết bị tập trung được gọi là switch.   

- `Router`: Các swith được kết nối về một thiết bị tập trung được gọi là `router`.      

### Chức năng chia sẻ tài nguyên    

- Kết nối mạng dùng để chia sẻ dữ liệu và các tài nguyên mạng như là: 
   - Dữ liệu và các ứng dụng   
   - Chia sẻ các tài nguyên phần cứng   
   - Các hệ thống lưu trữ và backup dữ liệu     

- Các ứng dụng người dùng:   
   - Thư điện tử   
   - Truy cập web   
   - Chia sẻ và download các file dữ liệu    
- Các ứng dụng qua mạng   
   - Ứng dụng truyền file  
   - Ứng dụng tương tác   
   - Ứng dụng thời gian thực (real time): VoIP, Video         

### Các đặc tính kỹ thuật   
- Speed (tốc độ của mạng)   
- Cost (chi phí)     
- Tính bảo mật (Security)    
- Độ sẵn sàng (Availability): Tính liên tục để đảm bảo truy nhập và truyền dữ liệu qua mạng.    
- Tính tin cậy (reliability): tránh gây lỗi trong việc truyền dữ liệu qua mạng    
- Sơ đồ mạng (Topology)      

### Mô hình OSI (Open System Interconnection)      

![image](image1/m%C3%B4hinhOSI.png)   

- `Lớp Physical`: có nhiệm vụ đảm bảo truyền được bit nhị phân qua một môi trường cụ thể nào đó.   
- `Lớp Data Link`: dùng để đóng gói dữ liệu thành các frame phù hợp với từng loại đường truyền.   
- `Lớp Network`: dùng để định tuyến tìm đường đi tối ưu từ điểm này đến điểm kia của mạng.   `router`
- `Lớp Transport`: dùng để quản lý và truyền dữ liệu từ đầu cuối đến đầu cuối (end-to-end or host-to-host) đảm bảo hoạt động này diễn ra hiệu quả nhất.      
- `Lớp Session`: dùng để thiết lập, duy trì và giải phóng các phiên trao đổi dữ liệu.       
- `Lớp Presentation`: dùng để thông dịch sao cho hai ứng dụng có thể truyền thông và hiểu được nhau.   
- `Lớp Application`: dùng để tương tác trực tiếp và các dịch vụ mạng đến người dùng.      

- Các lớp Application, Session, Presentation: `Data`    
- Lớp Transport: `Segment`      
- Lớp Network: `Packet`  
- Lớp Data Link: `Frame`   
- Lớp Physical: `Bit`      

### Protocol 

- `Giao thức (Protocol)`:là tập hợp các quy tắc, quy ước để đảm bảo các máy tính trên mạng có thể giao tiếp được với nhau.    

### PDU (Protocol Data Unit)   
- PDU (Protocol Data Unit) gồm 2 thành phần: `header` và `data`    
   - `header` chính là phần thông tin quản lý của gói tin.   
   - `data` chính là phần dữ liệu thực sự của gói tin.    

### Địa chỉ IP      

### Quy tắc   
- Các bit phần mạng không được phép đồng thời bằng 0    
- Nếu các bit phần host đồng thời bằng 0, ta có địa chỉ `network` mạng.         
- Nếu các bit phần host đồng thời bằng 1, ta có địa chỉ `broadcast`    

- Lớp A: `1 -> 126`    
   - `127.0.0.0` là địa chỉ loopback      
- Lớp B: `128 -> 191` 
- Lớp C: `192 -> 223`  
- Lớp D: `224 -> 239` 
- Lớp E: `240 -> 255` được sử dụng cho mục đích dự phòng.        

- Các subnet-mask chuẩn của các địa chỉ lớp A, B và C   
   - `Lớp A`: 255.0.0.0 
   - `Lớp B`: 255.255.0.0  
   - `Lớp C`: 255.255.255.0   

- Địa chỉ IP: 192.168.1.1/24   
   - `/24` là prefix-length.   
   - `Prefix-length` là số bit mạng trong một địa chỉ IP       

### Default gateway   
- Default gateway là địa chỉ IP của router mà kết nối đến mạng chứa máy nguồn.      
- Khi một máy tính muốn truyền thông đến máy tính khác mạng, thì nó phải gửi gói tin ra default gateway.    
- Tất cả máy tính có trong cùng một mạng có cùng một địa chỉ default gateway.     
- Đối với hai máy tính trong cùng một mạng thì việc gửi gói tin cho nhau là điều vô cùng dễ dàng. Nhưng đối với các máy tính có địa chỉ IP khác nhau thì khi đó bạn cần phải có sự hỗ trợ bởi router và trao đổi thông tin qua `default gateway`.    

- Lệnh `ping`: dùng để kiểm tra kết nối mạng của 2 máy tính.  
- Lệnh `tracert`: dùng để kiểm tra đường đi của các gói tin của lệnh `ping` (tìm đường đi đến đích) 




