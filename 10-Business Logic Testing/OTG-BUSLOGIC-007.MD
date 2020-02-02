เป็นบทที่จะทดสอบการป้องกันตัวเองของ application เมื่อมีการใช้งานจากฝั่ง user ที่ผิดปกติ

โดยตัวอย่างจากทาง owasp ก็จะมีเคส เช่น
	1. 
พยายามเข้าถึงไฟล์ ที่ผู้ใช้ไม่มีสิทธิ์จะ download
	2. 
ลองใส่ single quote ( ' ) แทน id no.
	3. 
เปลี่ยน method จาก GET ให้เป็น POST
	4. 
ใส่ parameter ที่ไม่ปกติลงไปเพิ่ม
	5. 
ใส่ parameter ซ้ำๆ  เป็นต้น



ซึ่งตัว application ก็ควรจะมีการ monitor และทำการ
	* 
disable ฟังก์ชั่นที่มีความสำคัญและมีความเสี่ยง
	* 
มีการให้ทำการ authentication เพิ่มเติม เช่น 2FA ในการโอนเงิน
	* 
ให้มีการ delay สำหรับ request จาก user ที่ผิดปกติ
	* 
ทำการเก็บข้อมูลการใช้งานของ user ที่ดูผิดปกตินั้น


เหล่นนี้เป็นแค่ตัวอย่างที่ทาง owasp ยกมาว่า เป็นสิ่งที่ application ควรมีเพื่อป้องกันการโจมตี

How to Test
ในการทดสอบบทนี้จริงๆแล้ว ผลอาจจะได้มาจากการทำการทดสอบบทอื่นๆ ที่ผ่านมาก่อนหน้านี้แล้วก็ได้ ซึ่งถ้ามีการตอบสนองดังต่อไปนี้จาก application ก็แสดงว่ามีการป้องกันตัวเองของ application เช่น

	* 
changed response
	* 
ทำการ block request ที่ดูไม่ปกติ เหล่านั้น
	* 
ทำการ log out ผู้ใช้งานคนนั้นออกจากระบบทันทีหรือ lock ให้ไม่สามารถใช้งานได้
	* 
ปฏิเสธรับ input ที่ประกอบด้วย character บางตัว
	* 
ทำการ lock ผู้ใช้งานเป็นการชั่วคราวเมื่อพบว่ามีการ authen ผิดซ้ำๆกันหลายครั้ง


ข้างต้นจะเป็นการป้องกันแบบเหมือน จำกัดความประพฤติ ไม่ให้ทำเพิ่ม ไม่ให้ทำต่อไป อะไรประมาณนั้น ซึ่งในการโจมตี หรือใช้งานที่ผิดปกติบางประเภทนั้น การป้องกันแบบด้านบนจะไม่สามารถป้องกันได้ เช่น (ไม่แปลละกันครับ)
	* 
Forced browsing
	* 
Bypassing presentation layer input validation
	* 
Multiple access control errors
	* 
Additional, duplicated or missing parameter names
	* 
Multiple input validation or business logic verification failures with values that cannot be the result user mistakes or typos
	* 
Structured data (e.g. JSON, XML) of an invalid format is received
	* 
Blatant cross-site scripting or SQL injection payloads are received
	* 
Utilising the application faster than would be possible without automation tools
	* 
Change in continental geo-location of a user
	* 
Change of user agent
	* 
Accessing a multi-stage business process in the wrong order
	* 
Large number of, or high rate of use of, application-specific functionality (e.g. voucher code submission, failed credit card payments, file uploads, file downloads, log outs, etc).



ในการทดสอบ ถ้าผู้ทดสอบเจอว่าไม่มีการป้องกันในรูปแบบใดก็จะถือว่าเป็นช่องโหว่ที่ควรใส่ในรายงาน ซึ่งในการทดสอบ บางครั้งระหว่างลองทำการทดสอบด้วยการโจมตีต่างๆ บาง action ของฝั่ง application อาจจะไม่ได้แสดงหรือ response ให้ผู้ใช้งานหรือผู้ทดสอบเห็นเช่น
	* 
การ logging
	* 
การ monitor ที่เพิ่มระดับความเข้มข้นขึ้น
	* 
การแจ้งเตือนไปยังผู้ดูแลระบบ



