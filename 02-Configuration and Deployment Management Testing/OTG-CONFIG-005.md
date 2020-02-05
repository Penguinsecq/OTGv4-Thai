enumerate admin page on the web server.

**Black box**

1. ลองพยายามคาดเดา path ที่จะเข้าไปยัง admin interface เช่น

- /admin or /administrator

2. ใช้ tools ช่วย เช่นs DIRB, DIRBuster ในการ crawling web และเมื่อได้ผลลัพธ์จาก tools แล้วสิ่งที่ขาดไม่ได้ก็คือการ verify จากผู้ทดสอบเอง

3. ตรวจหา comment ใน source code 

4. หาเอกสารพวกที่เกี่ยวกับการ configure, installation, manual หรือจาก google เพื่อค้นหา default admin path

5. ใช้ nmap ในการ scan หา port ที่เปิดอยู่อื่นๆ ซึ่งในบางครั้งผู้ทดสอบจะพบว่า admin interface ต้องเข้าผ่าน port ที่ต่างกับ web server ปกติ เช่น port 8080


**Grey box**

ได้เอกสารมาก็ตรวจสอบว่า application ไม่ได้มีการใช้ default credential หรือ configuration ที่มีผลทำให้เกิดช่องโหว่ทาง security

ในเคสของการทำ white box นั้นให้ทำการทดสอบเพื่อยืนยันว่า user ปกติ จะไม่สามารถเข้าถึง admin interface หรือ function ได้ ซึ่งอาจจะดูจากพวก authentication, authorization model ที่ขอจากลูกค้า หรือ app owner หรือพวก UAM (user access metrix) 
