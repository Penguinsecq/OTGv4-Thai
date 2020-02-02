ทดสอบ idle timeout หรือการที่ตัว application ทำการ logout user เมื่อไม่มีการส่ง http request จาก user ที่มี session id นึง ซึ่งควรเป็นค่าที่เหมาะสมกับทั้งทางด้านความปลอดภัยและการใช้งาน ซึ่งค่าที่เหมาะสมนี้ขึ้นอยู่กับลักษณะ ประเภทของข้อมูลในตัว application นั้นๆ เช่น ถ้าเป็น public forum ก็อาจจะมีระยะเวลาที่ 60 นาที แต่ถ้าเป็น internet banking ก็อยู่ที่ 15 นาทีเป็นต้น 

Black Box testing

วิธีการทดสอบก็จะคล้ายกับของ OTG-SESS-006 คือ 
	* 
ทดสอบว่ามี timeout หรือป่าว 
	* 
นานเท่าไหร่ถึงจะ timeout 


ซึ่งเมื่อ timeout แล้ว session นั้นควรจะไม่สามารถนำกลับมาใช้ได้อีก ซึ่งในการทดสอบผู้ทดสอบต้องดูว่าเป็นการ timeout ที่เกิดจากฝั่ง client หรือ server ที่ดีควรจะเป็นการ check จาก server-side หรือทั้งสองฝั่งไปเลย 

กรณี session cookie มีค่าเรื่องของเวลาอยู่ในตัว cookie เอง เป็นไปได้ว่าจะถูกเช็ค timeout จากฝั่ง client ซึ่งผู้ทดสอบอาจจะลองทำการแก้ไขค่าดูว่าจะทำการ manipulate เพื่อให้ค่า timeout หรือ session expiration มันยืดออกไปได้หรือไม่ และค่าของ session cookie ไม่ควรนำกลับมาใช้ได้ใหม่เมื่อมีการ expired ไปแล้ว

Grey Box testing  ทดสอบดังต่อไปนี้

	* 
ฟังก์ชั่น logout มีการทำลาย session token ทั้งหมดไม่ให้ใช้ได้อีก
	* 
มีการเช็ค session state จากฝั่ง server เพื่อป้องกันไม่ให้ attacker ใช้งาน session ที่ถูกทำลายไปแล้ว
	* 
การ timeout ต้องเป็นการสั่งจากฝั่ง server ในกรณีที่ตัว server ต้องมีการอ่านค่าจากฝั่ง client (ซึ่งไม่ควร) ตัว session token ควรมีการ encrypt เพื่อให้ยากแก่การ tamper





