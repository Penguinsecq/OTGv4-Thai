Testing for default credentials

Black box testing

1. ถ้าเป็น application หรือ อุปกรณ์ที่ค้นหาได้ใน internet เช่น tomcat, cisco router ก็ให้ค้นหา default credential หรือ credential ที่มักจะใช้กันมาใช้ลองดู

2. ถ้าเป็น application ที่ไม่มี default and common user เช่น ลูกค้า dev ขึ้นมาเอง tester สามารถเดา credential ที่มักมีการใช้งานบ่อยๆ แต่ต้องระวังเรื่อง lockout policy ที่อาจจะเกิดขึ้น

ในอีกทางหนึ่งแต่ละ application อาจจะมี error message ที่บ่งชี้หรือช่วยให้เราทราบว่ามี username นั้นจริงหรือไม่ ตามการทดสอบ OTG-IDENT-005 และเมื่อเราทราบ username แล้วก็สามารถเดาเฉพาะ password ได้ต่อไป

- username ที่มีการใช้บ่อย เช่น "admin", "administrator", "root", "system", "guest", "operator", or "super" หรืออาจจะเป็น "qa", "test", "test1", "testing" ประมาณนี้ (ลองหา list ของ username ที่คาดว่าจะใช้บ่อยเพิ่มเติมได้)

ส่วน password ก็จะมี เช่น "password", "pass123", "password123", "admin", or "guest" หรือใช้ค่าว่าง อันนี้เป็นศิลปะแต่ละคน

- ใช้ชื่อระบบนำหน้าเช่น bank/security

- ใช้ชื่อ ของผู้ที่เป็น contact ให้เราเป็น username หรือใช้ email

- ลองค้นหาใน page source หรือ javascript ว่ามี credential ทิ้งไว้หรือไม่

3. ลองใช้ default password หรือ password ที่ถูกกำหนดขึ้นสำหรับ new account เผื่อในกรณีที่ user จะยังไม่ได้เปลี่ยน หรือไม่ได้ใช้งาน

- สามารถหาได้จาก user registration page หรือพวก manual guide ของ app นั้นๆ อาจจะเจอวิธีการตั้ง username, password

- ลองดูว่า app มีการ gen username ให้หรือไม่ เพราะเราสามารถรู้ถึง pattern ของ username ในระบบได้ หรือ gen username ที่เป็นค่าที่เป็นลำดับเช่น user7811, user7812

- ลองดูว่า app มีการ gen password ให้เหมือนกรณี username ไหม ที่ predict ได้

- ถ้าได้ username มาแล้ว ลอง brute-force ดู และใช้ blank password ดูเะช่นกัน
