Testing for Vulnerable Remember Password (OTG-AUTHN-005)

How to test

1. ค้นหา password ที่เก็บใน cookie ว่าเป็น clear text

2. ถ้า มีการ hash ตัว password ก็ให้ทดสอบว่าเป็น hash ที่แข็งแกร่งหรือไม่ เช่น md5 ไม่ควรใช้

3. ทำให้แน่ใจว่า credential มีการส่งไปยัง server ในการ login เท่านั้น ไม่ได้มีการส่ง credential ใน request อื่นๆ

4. ดูในหน้า page อื่นๆที่เกี่ยวข้องกับ credential เช่น password recovery, forgot password ว่ามีการส่ง credential ไปที่ใช้ไปด้วยหรือไม่
