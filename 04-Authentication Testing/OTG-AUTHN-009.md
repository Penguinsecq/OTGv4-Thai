Testing for weak password change or reset functionalities (OTG-AUTHN-009)

How to test

1. หาวิธีการที่จะสามารถเปลี่ยน หรือ reset password ของคนอื่นได้ โดยไม่ใช้สิทธิ์ administrator
2. ทดสอบเปลี่ยน หรือ reset password ด้วยช่องโหว่ csrf

test password reset ซึ่งเป็นเรื่องของ logic
- มี secret question ที่ต้องตอบก่อนทำการ reset หรือไม่ และเป็น secret question ที่ดีไหม

- reset password ต้องถูกสร้างขึ้นมาแบบ random และเก็บในรูปแบบ hash

- app ควรส่ง email link ที่มี random token แก่ user ที่ต้องการเปลี่ยน password

- test ว่า สามารถแก้ไข email ที่ password reset function จะส่ง link ไปเป็นของ attacker ได้หรือไม่

test password change
- ต้องมี old password ใน request สำหรับการเปลี่ยน password หรือไม่
	* 
ในหัวข้อนี้ให้ลองหาวิธีที่จะไม่ต้องใช้ old password ในการเปลี่ยน password


https://www.owasp.org/index.php/Testing_for_weak_password_change_or_reset_functionalities_(OTG-AUTHN-009)
