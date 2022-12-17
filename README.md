# SPCN-011

สร้าง vm and ct on Proxmox cluster

  create master vm (ubuntu-22.04)
  
    1.ทำการสร้าง Virtual Machine
    
    
![image](https://user-images.githubusercontent.com/109062980/208183805-60ea788c-2322-4139-9f28-2689b9a475b2.png)

    
    2.เมื่อทำการสร้าง vm เสร็จแล้ว ให้ทำการตั้งค่าเวลาให้ตรงโดยใช้คำสั่ง
        sudo time datectl set-timezone Asia/Bangkok
        
    3.ทำการเปิดใช้งาน QEMU Guest Agent โดยใช้คำสั่ง
        apt install qemu-guest-agent
        systemctl enable qemu-guest-agent
        
    4.ทำการเปลี่ยนตัว vm ให้กลายเป็น template
    
    5.clone template ที่ได้มาจากการแปลงให้เป็น vm ใหม่ 2 ครั้ง
        
    6.ทำการตั้งค่าชื่อ hostname ของเครื่องที่โคลนทั้ง 2 เครื่องด้วยคำสั่ง
         sudo hostnamectl set-hostname ชื่อ
         
    7.ทำการรีเซ็ท MachineID  ของเครื่องที่โคลนเพื่อไม่ให้เกิด ip ชนกันทั้ง 2 เครื่องด้วยคำสั่ง
          rm /var/lib/dbus/machine-id
          echo -n > /etc/machine-id
          cat /etc/machine-id
          ln -s /etc/machine-id /var/lib/dbus/machine-id
          
         
   summary screen
   
![image](https://user-images.githubusercontent.com/109062980/208189215-b4c19bd6-e28a-4406-96a9-0431e4ddbb93.png)
![image](https://user-images.githubusercontent.com/109062980/208189256-7fb6589f-00e9-4ade-8097-29d349a2dbed.png)
![image](https://user-images.githubusercontent.com/109062980/208189278-02a47124-a374-4440-839d-740ae6f2903f.png)

   watch screen
![image](https://user-images.githubusercontent.com/109062980/208236326-98f8151f-ab01-4d4d-88c5-b8c608dd5742.png)
![image](https://user-images.githubusercontent.com/109062980/208236361-a7dfb992-b0d3-499f-8c02-0b2ea9bbb0e6.png)

  create vm from other os

    1.ทำการสร้าง Virtual Machine
    
    2.เลือก ISO Image เป็น kali-linux
    
    3.ให้เลือกค่า default ทั้งหมด
    
![image](https://user-images.githubusercontent.com/109062980/208191116-33f5104e-7cd2-41bd-9fdc-d427172207aa.png)
![image](https://user-images.githubusercontent.com/109062980/208190837-67a84de0-699e-475e-b49c-d9d35c868c0d.png)

  create container template (select from CT list)
  
    1.เลือก Create CT เพื่อสร้าง
    
    2.กรอกชื่อ hostname , password เลือก Resource pool เป็น Special_CN
    
    3.เลือก Load SSH Key File 'id_rsa.pub' จากการสร้างผ่าน git
    
![image](https://user-images.githubusercontent.com/109062980/208190136-0a592087-be98-4203-b329-517f43499188.png)

    4.Network ให้เลือกเป็น SLAAC ทั้งหมด
    
  summary screen
  
![image](https://user-images.githubusercontent.com/109062980/208190407-60592133-16de-4e5c-8b58-d90774e1f1bc.png)

  watch screen
  
![image](https://user-images.githubusercontent.com/109062980/208190430-f7580a45-70bc-4b07-86e7-99742682b35c.png)




  
