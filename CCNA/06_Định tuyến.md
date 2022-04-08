# Mục lục   
[1. Routing là gì? ](#1)   
[2. ](#2)    

-----   

<a name='1'></a>   

## 1. Routing  là gì ?  
- `Định tuyến (Routing)` là quá trình xác định đường đi tối ưu đi đến một đích đến nào đó trên mạng.    
- Thông tin về các mạng đích đến (Destination networks) và đường đi tối ưu để đi đến mạng này được router lưu lại trong `table routing`.    
- Routing:   
   - Static Routing   
   - Dynamic Routing     
       - `EGP(Exterior Gateway Protocol)`: BGP (Border Gateway Protocol)      
       - `IGP (Interior Gateway Protocol)`: RIP, OSPF, EIGRP       
            - `Distance-Vector`: RIP  
            - `Link - State`: OSPF, IS-IS   
            - `Hybrid (advance distance-vector)`: EIGRP(Enhanced Interior Gateway Routing Protocol)    
            - Classful: RIPv1   
            - Classless: RIPv2, OSPF, EIGRP    
- `AS (Autonomous System)` tạm dịch là ` Hệ tự trị ` là tập hợp các router thuộc cùng một sự quản lý về kỹ thuật và sở hữu của một doanh nghiệp.    
- `Distance-Vector`: mỗi router sẽ gửi cho láng giềng của nó toàn bộ bảng định tuyến của nó theo định kỳ.    
- `Link - State`: mỗi router sẽ gửi bản tin trạng thái đường link (LSA) cho các router khác. Việc tính toán định tuyến được thực hiện bằng thuật toán Dijkstra.     
- `Hybrid`: kết hợp đặc điểm của hai loại trên. Nhưng EIGRP vẫn là giao thức loại Distance-Vector nhưng đã được cải thiện nhằm `tăng tốc độ hội tụ` và `quy mô hoạt động`.

- `Classful`: router sẽ không gửi kèm theo subnet - mask trong bản tin định tuyến của mình.     
- `Classless`: ngược với classful, router sẽ gửi kèm theo subnet - mask trong bản tin định tuyến. Có hỗ trợ VLSM và mạng gián đoạn. `(RIPv2, OSPF, EIGRP)`

### Adminitrative Distance 
- AD là giá trị được sử dụng để đo đạc mức độ ưu tiên giữa các kỹ thuật định tuyến.     

|Kỹ thuật định tuyến|Giá trị AD|   
|-----|-----|   
|Định tuyến tĩnh (Static)|0 hoặc 1, tùy theo cách thức cấu hình|   
|EIGRP|90|  
|OSPF|110|    
|RIP|120|      

### Metric
- Metric là giá trị dùng để `định lượng mức độ tối ưu` của một đường đi trong tính toán định tuyến.    
- Trong các đường đi đến đích, đường đi nào có `metric nhỏ hơn` thì đường đi đó được xem là `tối ưu nhất`       
- `RIP`: tính metric dựa vào số router trên đường đi đến đích.  
- `OSPF`: tính metric dựa vào `băng thông (bandwidth)` của đường truyền.    
- `EIRGP`: tính metric dựa vào `bandwidth, relibility, load, delay` của đường truyền.   

### Sự hội tụ      
- Sự hội tụ (convergence) là quá trình router thay đổi và update thông tin định tuyến tương ứng với những sự thay đổi diễn ra trên system network.     

|Kỹ thuật định tuyến|Convergence|  
|----|----|   
|Static Routing|No convergence except status up/down của port primary được config static router|   
|RIP|Convergence low|  
|OSPF|Convergence fast|  
|EIGRP|Convergence very fast|    

