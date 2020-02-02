**How to test**

1.  ใช้ google operator search ที่เกี่ยวข้องกับข้อมูลที่ต้องการค้นหา เช่น

•  ต้องการค้นหา Network diagrams and configurations
site:cophone.com
filetype:pdf vsd txt

•  ต้องการค้นหา โพสต์ และ email ที่ admin ได้เคยโพสต์ไว้Archived posts and emails by administrators and other key staff
for social network
@facebook pentest01
@twitter pentest01

•  ค้นหาวิธีการ Log on เข้าใช้งานเป้าหมาย และรูปแบบของ username 
ในกรณีที่ได้รับ username จากลูกค้ามาเพื่อทำการทดสอบแบบ grey-box

•  Usernames and passwords
inurl:"/root/etc/passwd" intext:"home/*:"
inurl:admin inurl:userlist

ตัวอย่างการค้นหา

![image](https://user-images.githubusercontent.com/60565002/73606412-913c6f00-45dc-11ea-9f21-c7ac98f51ee3.png)

•  ค้นหาจาก Error message 
inurl:".php?id=" "You have an error in your SQL syntax"

•  Development, test, UAT and staging versions of the website

2. ลองทำการค้นหาด้วย search engine อื่นๆ

Ref : https://github.com/OWASP/wstg/blob/master/document/4_Web_Application_Security_Testing/4.2_Information_Gathering/4.2.1_Conduct_Search_Engine_Discovery_Reconnaissance_for_Information_Leakage_OTG-INFO-001.md

update : 01/2563
