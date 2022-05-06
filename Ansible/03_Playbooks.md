# Mục lục   
[1. Tại sao lại sử dụng Playbooks ?](#1)    
[2. Tạo một playbooks ](#2)       
[3. ](#3)     

## [Tham khảo](#4)    
-----   

<a name='1'></a>          

***Như thế nào để sử dụng Ansible Playbooks để Automation Complex Tasks trong Multiple Remote Servers***     

## 1. Tại sao lại sử dụng Playbooks ?     
***Mục đích của Ansible: Bạn đứng trên một Node Controll và ra lệnh cho các server mà bạn quản lý.***       
- Vấn đề: Số lượng thao tác cần thực hiện trên các server kia thì nhiều, nhiều server có tác dụng, nhiệm vụ giống nhau nên cần thực hiện các thao tác giống nhau.   
- Không lẽ bạn định ngồi gõ hàng trăm hoặc hàng nghìn lệnh. Để rồi khi có các server mới bạn lại ngồi gõ tay lại, chưa kể việc sai sót khi thực hiện.   
- Giải quyết vấn đề: Lúc này bạn cần phải viết một playbooks.       
- Trong một playbooks sẽ chứa một tập hợp các actitives (hoạt động) hay các tasks (nhiệm vụ) sẽ được chạy trên một hoặc một nhóm servers. Trong đó `task` là một hành động duy nhất được thực hiện trên server, ví dụ như cài gói service nào đó, hay bật/tắt service.    

### Một số thuật ngữ cơ bản     
- Playbooks thì được viết dưới định dạng văn bản `YAML`, chứa một list các mục với một hoặc nhiều cặp key/value (biết như một "hash" or một "dictionary").       
- `hosts` có một danh sách machine (chứa trong file `/etc/ansible/hosts`) các tasks sẽ được thực thi lên list machine này.  
- `remote_user` account remote sẽ được sử dụng để thực hiện các tasks này.     
- `vars` variables được sử dụng để biến đổi trạng thái của remote system(s).  
- `tasks` được thực hiện theo thứ tự, tất cả các máy phù hợp với host. Trong một `play`, tất cả hosts được chỉ thị cùng task.   

***Nếu bạn cần thực hiện một set khác của task liên quan cho một host riêng, tạo play khác trong `Playbook` hiện tại***   

<a name='2'></a>   

## 2. Tạo một playbook    
- Tạo một file định dạng `.yml`, ví dụ playbook1.yml      
- Chỉnh sửa nội dung file playbook1.yml        

```   
---        
- host: webservers  
  become: true  
  tasks: 
        - name: Install lastest version of chrony  
          apt: name=chrony update_cache=yes state=latest   
        - name:show status chronyd  
          command: systemctl status chronyd   

```        
- Trong đó:   
  - `host`: là hostname được bạn chỉ định trong file `/etc/ansible/host`      
  - `become`: `true` nói với Ansible rằng nó sẽ `sử dụng leo thang đặc quyền (sudo)` để chạy tất cả các task trong playbook.      
  - `tasks`: nơi các task được khai báo. 
  - `name`: tên của task   
  - `apt, command`: module của Ansible được sử dụng.       




 

 


