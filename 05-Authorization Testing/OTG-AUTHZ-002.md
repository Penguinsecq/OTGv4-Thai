Testing for Bypassing Authorization Schema (OTG-AUTHZ-002)

ในแต่ละ application ปกติแล้วจะมี user access matrix ที่มีการกำหนดขึ้นว่า user ในระบบ application นั้นๆ มีกี่ระดับ กี่ role และมีสิทธ์ในการเข้าถึง function หรือ หน้าไหนบ้าง resource ไหนบ้างใน web application

tester จำเป็นต้องแน่ใจว่า

- resource หรือ function ของ user ที่ผ่านการ authen แล้วสามารถเข้าถึงได้โดย user ที่ยังไม่ได้ authen หรือไม่
- resource หรือ function ของ user ที่ผ่านการ authen แล้วสามารถเข้าถึงได้โดย user ที่ log-out แล้วหรือไม่
- resource หรือ function ของ user ใน role นึง สามารถเข้าถึงได้โดย user อีก role นึงที่ไม่สมควรหรือไม่

และใน level ของ admin ก็เช่นกันให้ลองทดสอบ เช่น

- user ธรรมดาสามารถเข้าถึง function ของ admin ได้หรือไม่
- user ธรรมดาสามารถใช้งาน function ของ admin เพื่อกระทำการเช่นเดียวกับ admin ทำแก่ผู้อื่นได้หรือไม่

How to test

1. test เข้าถึง administrative function
ในตัวอย่างของ owasp จะเป็นการเข้าถึง function ชื่อ "AddUser.jsp" ซึ่งเป็นของ admin ดังนี้



ซึ่งโดยปกติ เราจะเข้าถึงได้โดยผู้ใช้งานที่อยู่ใน role ของ admin เท่านั้น ซึ่งถ้าเรา login ใน role ที่เป็น user ธรรมดา แล้วสามารถ add user ได้ด้วย function นี้ นั่นเป็นเรื่องที่ไม่ถูกต้อง

2. test เข้าถึง resource ของ role ที่แตกต่างกัน
จาก owasp จะเป็นการยกตัวอย่างเช่น

user A เพียงคนเดียวที่ สามารถเข้าถึง --> ไฟล์ docA.pdf

ให้ลองใช้ user B ซึ่งต้องเป็นคนละ role และไม่ควรมีสิทธิ์เข้าถึง ไฟล์ docA.pdf ถ้าสามารถเข้าถึงได้แสดงว่าเป็นช่องโหว่

ในการทดสอบให้กับลูกค้า เราควรที่จะคุยกับลูกค้าเพื่อขอ User Access Matrix ที่ทางลูกค้ากำหนดขึ้นไว้เป็นตัวตั้งต้นในการทดสอบ
