## EIGRP_Enhanced Interior Gateway Route Protocol      
### Overview      
- EIGRP là một giao thức định tuyến do Cisco phát triển, chỉ chạy trên các sản phẩm của Cisco.           
- EIGRP là một giao thức dạng `Distance-Vector` được cải tiến (Advertisment Distance Vector).     
- RIP sử dụng thuật toán Bellman-Ford còn EIGRP sử dụng thuật toán DUAL (Diffusing Update Algorithym).       
- EIGRP có tốc độ hội tụ rất nhanh nhờ bảng `topology` và thuật toán DUAL.    
- `Cơ chế hoạt động`:   
   - Gửi thông tin định tuyến là các route cho láng giềng (chỉ gửi cho láng giềng) và tin tưởng tuyệt đối vào thông tin láng giềng mà nó nhận được.     
- `Khác biệt`:   
   - Chỉ gửi toàn bộ thông tin bảng định tuyến cho láng giềng lần đầu tiên, sau đó chỉ gửi cập nhật khi có sự thay đổi. Điều này sẽ tiết kiệm được tài nguyên.  
- EIGRP dựa vào nhiều thông số để tính metric: `bandwidth, delay, load và reliability và bộ tham số K tương ứng . `   

- AD của EIGRP là `90`   
- EIGRP chạy trực tiếp trên nền IP và số protocol_id là 88.     
- Địa chỉ multicast dành riêng cho EIGRP là `224.0.0.10`      

### Thiết lập quan hệ láng giềng    
- Để thiết lập quan hệ láng giềng giữa hai router thì một số thông số được trao đổi qua các gói tin hello phải khớp.    
   - Giá trị AS được cấu hình trên mỗi router.   
   - Các địa chỉ đấu nối giữa hai router phải cùng subnet.   
   - Thỏa mãn điều kiện xác thực.   
   - Cùng bộ tham số K.     
- Câu lệnh đi vào mode cấu hình EIGRP    
```   
R(config)#router eigrp số_AS(giá trị bắt buộc phải giống nhau giữa các router)  
R(config-router)#        
```    
***Note:Với định tuyến ngoài, mỗi AS là một tập hợp các router thuộc về một doanh nghiệp nào đó cùng chung một sự quản lý về kỹ thuật, sở hữu, chính sách định tuyến và sẽ cấp một giá trị định danh cho AS gọi là ASN_Autonomous System Number từ tổ chức địa chỉ Internet và số hiệu mạng quốc tế.***    
- EIGRP cho phép tạo nhiều process - domain khác nhau trong một AS  
- Các router sẽ chỉ trao đổi thông tin EIGRP với các router thuộc cùng process-domain với mình. Để hai router khác process-domain có thể biết được thông tin định tuyến của nhau, router biên giữa hai domain phải thực hiện redistribute thông tin định tuyến giữa hai domain.      

### Subnet  
- Để hai router thiết lập được quan hệ láng giềng với nhau, hai địa chỉ đấu nối giữa hai router phải cùng subnet.      

### Thỏa mãn xác thực   
- Hai router phải cấu hình xác thực thống nhất với nhau về password     

### Bảng Topology, FD, AD, Seccussor, Feasible Seccussor    
- `FD_Feasible` là giá trị metric từ router đang xét đi đến mạng đích.   
- `AD_Advertisted Distance` là giá trị metric từ router láng giềng (next hop) đi đến mạng đích.   
- `Successor` là trong tất cả các đường đi đến một đích đến, đường nào có FD nhỏ nhất, đường đó sẽ được bầu chọn làm successor.   
- `Feasible Successor` là trong tất cả các đường còn lại có FD > FD của successor, đường nào có AD < FD của successor, đường đó sẽ là feasible successor và được sử dụng để làm dự phòng cho successor.     

### Các tham số tính metric EIGRP trên cổng   

|Loại cổng|Bandwidth mặc định|Delay mặc định|  
|----|----|----|   
|Ethernet|10000|100|  
|Fast Ethernet|100000|10|  
|Serial|1544|2000|    

