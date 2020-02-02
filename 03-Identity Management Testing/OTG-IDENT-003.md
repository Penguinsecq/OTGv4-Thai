Verify which accounts may provision other accounts and of what type.How to Testmanual test onlyทดสอบว่า role ใดใน application เป้าหมาย ที่มีสิทธิ์ในการ provision ผู้ใช้งานอื่นๆ  ตามหัวข้อ ดังต่อไปนี้เป็นตัวอย่าง
	* Is there any verification, vetting and authorization of provisioning requests?
	* Is there any verification, vetting and authorization of de-provisioning requests?
	* Can an administrator provision other administrators or just users?
	* Can an administrator or other user provision accounts with privileges greater than their own?
	* Can an administrator or user de-provision themselves?
	* How are the files or resources owned by the de-provisioned user managed? Are they deleted? Is access transferred?

ตัวอย่างจาก owasp คือ ใน wordpress ข้อมูลที่จำเป็นในการ add user ก็จะมีแค่ username กับ email 


ในการ de-provision จำเป็นต้องให้ admin เท่านั้นในการทำ


