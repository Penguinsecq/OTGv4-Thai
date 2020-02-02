เพื่อทดสอบกระบวนการลงทะเบียน (registration) ของ application ว่าเป็นไปตามความต้องการที่ได้ออกแบบไว้ และมีความปลอดภัยหรือไม่

How to Test

ใช้ Browser และ Burp suite ในการทดสอบตามหัวข้อต่อไปนี้ (ไม่แปล)

	* 
ทุกคนสามารถทำการ register ได้ไหม ?
	* 
ในกระบวนการ register ผู้ที่ทำการ register แล้วต้องมีการรอให้ admin หรือผู้มีอำนาจตรวจสอบและอนุญาตก่อนไหม หรือได้รับสิทธิ์ในการเข้าใช้งานเลยถ้าเงื่อนไขต่างๆครบถ้วน ?
	* 
คนเดียวกันสามารถจะทำการ register ได้หลายครั้งหรือไม่ โดยใช้ข้อมูลเดียวกัน ?
	* 
ผู้ใช้งานสามารถ register ตัวเองเป็นผู้ใช้ใน role อื่นๆ ที่มี permission ต่างกันได้ไหม ?
	* 
มีเงื่อนไขหรือสิ่งใดที่จำเป็นในการทำการ register ให้สำเร็จเรียบร้อย ?
	* 
แล้วมีวิธีการ identify ผู้ที่เข้ามาทำการ register ไหม ?



Validate the registration process:
	* 
ข้อมูลส่วนบุคคลของผู้ที่เข้ามาทำ register ปลอมแปลงได้ง่ายหรือไม่ ?
	* 
การแลกเปลี่ยนข้อมูลในระหว่าง register ถูกแก้ไขได้ง่ายหรือไม่ ?


ให้ดูรูปภาพได้ใน owasp

https://github.com/OWASP/wstg/blob/master/document/4_Web_Application_Security_Testing/4.4_Identity_Management_Testing/4.4.2_Test_User_Registration_Process_OTG-IDENT-002.md
