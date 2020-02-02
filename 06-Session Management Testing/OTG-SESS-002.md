
Black Box Testing

จาก owasp จะแบ่งเป็น 2 หมวดหลักๆ คือ

Test ช่องโหว่ที่เกี่ยวกับ cookie attribute 

จากการทำงานระหว่าง web app - client เราได้รู้มาจากบทที่แล้วว่า web app จะเป็นคน assign cookie ให้กับ client เพราะฉะนั้นเวลาเราจะทำการ test ในส่วน cookie attribute เราจึงต้องดูที่ HTTP response ที่มาจากฝั่ง web application ว่า cookie attribute มีการตั้งค่าที่ถูกต้องหรือไม่ ดังต่อไปนี้

Secure Attribute - ตัว cookie ควรจะถูกส่งผ่าน encrypted tunnel เท่านั้น เช่น HTTPS โดยวิธีการตรวจสอบก็ดูที่ HTTP response ว่า หลัง cookie มีการ tag ตัว "secure" flag ติดมาด้วยหรือไม่ เพราะถ้าไม่มีการ tag secure flag ติดมานั่นคือ browser ยินยอมให้มีการส่ง cookie ผ่านทาง unencrypted channel เช่น HTTP ยกตัวอย่างการ set cookie จากฝั่ง server ที่มีการ secure flag set





HttpOnly Attribute - เมื่อมีการใช้ cookie ควรจะมีการ set tag HttpOnly เสมอไม่ว่า browser จะ support หรือไม่ก็ตาม เป็นตัวช่วยป้องกัน cookie ไม่ให้ถูก client side script เข้าถึงได้ เป็นการช่วยลดความเสี่ยงในการถูกโจมตีด้วย XSS เช่น กรณีที่ web application ของเรามีช่องโหว่ XSS แล้วเราถูก attacker วาง script เพื่อขโมย cookie ของเรา ถ้ามี HttpOnly ป้องกันไว้จะทำให้เกิดผลเป็นดังเช่นด้านล่างนี้



กรณีที่ไม่มี HttpOnly จะเกิดแบบนี้ครับ



ทีนี้เรามาดูรูปที่มีการ tag "HttpOnly" 




Domain Attribute - ค่าของ domain ต้องตรง เช่น จากภาพด้านล่าง สมมติว่าถ้าเป็น cookie สำหรับของ tktboard.com ก็ควรจะ set ตามภาพด้านล่างนี้




Path Attribute - เหมือนกับเรื่อง domain attribute คือ ถ้า application อยู่บน path อะไร ก็ควร set ให้ตรงกัน ยกตัวอย่างเช่น

ถ้า application อยู่ใน /myapp/ ตัว cookie ก็ควรจะมีการ set ให้เป็น "path=/myapp/" ไม่ใช่ "path=/" 

Expires Attribute - คือค่าหมดอายุของตัว cookie ครับ คือ สมมติ ตามภาพด้านล่าง



แสดงว่า cookie ตัวนี้ที่ถูก assign มาจาก web application server จะหมดอายุการใช้งานในวันที่ 17 มกราคม 2020 ซึ่งผู้ทดสอบต้องตรวจสอบว่า cookie นี้ ไม่มี sensitive information และต้องพึงระวังว่า ตัว cookie นี้จะถูกเก็บบน local harddrive ของผู้ใช้งาน และจะยัง valid จนกว่าจะถึงวันที่ 17 มกราคม 2020 ถ้า attacker สามารถเข้าถึงและขโมย cookie ตัวนี้ไปได้จะสามารถเข้าสู่ application เสมือนผู้ใช้งานคนดังกล่าว

Test cookie authentication replay

เป็นการ test เพื่อเช็คว่า site ที่ทดสอบมีการใช้ cookie เป็น authentication token โดยไม่มีการตรวจสอบอื่นๆหรือไม่ โดยการทดสอบ

	* 
Step 1 - Use Chrome Extension Cookie Editor (i.e. Chrome EditThisCookie) to view existsng cookie name/value.
	* 
Step 2 - Use Chrome Login the target testing website
	* 
Step 3 - Use Chrome Extension Cookie Editor to view cookie again. Identify those newly added or updated cookie. These can be authentication cookie.
	* 
Step 4 - Use Firefox to visit the target testing website and manually add all previous 3 identified cookies by FireFox Cookie Editor (i.e. Firefox Extension Advanced Cookie Manager)
	* 
Step 5 - Check Firefox browser exisitng website login status to see if current web page can get authenticated and login without username and password

