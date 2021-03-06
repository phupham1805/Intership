# Router Configuration       

## Topology     

![image](image1/configuration.png)               

## Commands   

```
Router>                          mode User   
Router>enable                    mode Privilege   
Router#configure terminal        mode Config      
Enter configuration commands, one per line. End with CNTL/Z.      
Router(config)#ip address 192.168.1.1 255.255.255.0    
Router(config-if)#no shutdown    
Router(config-if)#exit        
```      

- Cấu hình `enable password`       
    - `Router(config)#enable password vnpro`        

- Cấu hình `console password`    
    - `Router(config)#line console 0 `
    - `Router(config-line)#password cisco`      
    - `Router(config-line)#login`       `    

- Lưu cấu hình:   
   - `Router#copy running-config startup-config`    
   - `Router#write memory`      
   
### Router Security    

```   
Router(config)#enable secret cisco123   
Router(config)#do show running-config    

```     

![image](image1/EncryptionRouter.png)    

