บทนี้เป็นเรื่องของ stack trace ซึ่งในเอกสาร owasp ก็จะกล่าวว่าตัว stack trace เนี่ย โดยตัวมันเองจะไม่ใช่ช่องโหว่ แต่มักจะเปิดเผยข้อมูลที่สำคัญให้แก่ผู้โจมตี หรือผู้ทดสอบทางด้าน security โดยที่ผู้ทดสอบก็จะพยายามทำให้เกิด error โดยการแก้ไขค่า input ที่ใส่ลงไปในระบบ เหมือนกับบทที่แล้ว เช่น relative path ที่ใช้ install ของตัว application  

Black Box Testing

ในการทดสอบจะมีเทคนิคมากมายในการทำให้เกิด error message ซึ่ง owasp ก็ยกตัวอย่างวิธีการทดสอบมาดังนี้

	* 
invalid input (such as input that is not consistent with application logic).
	* 
input that contains non alphanumeric characters or query syntax.
	* 
empty inputs.
	* 
inputs that are too long.
	* 
access to internal pages without authentication.
	* 
bypassing application flow.



โดย tools พวก owasp zap หรือ burp suite จะมีความสามารถในการ detect พวก exceptions message หรือ error message เหล่านี้โดยอัตโนมัติ

Grey Box Testing

ในการทำ source code review เราจะทำการค้นหา code ที่จะเรียก exception message ให้แสดงออกมา เช่นใน Java ก็จะมี code ใน JSP แบบนี้ 



ตัวอย่าง error เอามาจาก stackoverflow นะครับ

 



