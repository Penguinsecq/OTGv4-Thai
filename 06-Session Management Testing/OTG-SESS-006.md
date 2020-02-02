Secure session termination มี requirement 3 อย่างเป็นอย่างน้อย ดังนี้ครับ
	* มี UI ให้ ผู้ใช้งานทำการ logout ได้ด้วยตัวเอง
	* มี session timeout เมื่อไม่มีการใช้งานระยะนึง
	* มีการตรวจสอบ session จากฝั่ง server ที่ถูกต้อง

Testing for log out user interface:ข้อนี้จะเป็นเรื่องเกี่ยวกับมีปุ่ม มี function ให้กด logout ได้ ประมาณนั้น สิ่งที่ควรมีคือ
	* ปุ่ม logout ต้องมีในทุกๆ หน้าของ web app
	* ปุ่ม logout หาเจอง่าย อยาก logout เมื่อไหร่ก็เห็น
	* หลังจากโหลด page ไหนขึ้นมาควรจะเห็นปุ่ม logout ทันทีโดยไม่ต้อง scroll mouse
	* ปุ่ม logout ควรอยู่ในที่เดียวกันตลอด

Testing for server-side session termination:เมื่อใช้งาน page หลัง authentication แล้ว ก็ลองกด logout ดู หลังจากนั้น
	* ลองกด back ว่าสามารถกลับมาใช้งานได้ไหม 
	* ลอง reload ดูว่าใช้งานได้ไหม
	* ถ้าได้ session id ใหม่ หลัง logout ให้ลองเอา session id อันเก่ามาแทนที่ดูแล้วใช้หน้า page หลัง authentication ดู ตามรูป 

ข้อมูลที่ผู้ใช้งานมองเห็น หรือเข้าถึงได้หลังการ authentication ไม่ควรเข้าถึงได้หลังจากกดปุ่ม logout ไปแล้ว ค่า session id ควรจะถูก assign ให้กับ client side ใหม่ และอันเดิมก็ต้องใช้ไม่ได้ด้วย หลักการประมาณนี้


Testing for session timeout:

เพื่อทดสอบว่า ตัว application มีการตั้งเวลาในการ timeout อยู่ที่เท่าไหร่ โดยปกติการทดสอบข้อนี้ให้ลองถามทาง business หรือ dev ก็ได้ดูว่ากำหนดไว้ที่เท่าไหร่ ซึ่งต้องเป็นค่าที่เหมาะสมกับลักษณะ ประเภทของ application นั้นๆ ซึ่งต้องมีการตัดสินใจจากฝั่ง business มาเกี่ยวข้อง


Testing for session termination in single sign-on environments (single sign-off):
ในบางระบบ จะมีการใช้ SSO (single sign-on) คือ ทำ authentication ครั้งเดียว จากระบบๆ นึง แล้วสามารถเข้าไปใช้งาน application อื่นๆในระบบเครือข่ายเดียวกันได้ทั้งหมดโดยไม่ต้องมีการทำ authentication ซ้ำอีก ซึ่งในการทดสอบ เราก็ต้องทำการทดสอบดูว่า ถ้าเราลอง logout ออกจาก application แล้ว มี portal หรือ path อะไรหรือไม่ที่อนุญาตให้ user สามารถกลับเข้าไปใช้งานตัว application หลัง authenticate ได้ โดยไม่มีการ authenticate อีกครั้ง 

ในทางที่ควรเป็นคือ ถ้า logout จาก application ที่อยู่ในระบบ SSO แล้วนั้น ต้องทำให้ session มันถูก terminate ไปเลย รวมถึง SSO global ด้วย ถ้าต้องการใช้งาน application นั้นใหม่ก็ต้องทำการ authenticate ใหม่
