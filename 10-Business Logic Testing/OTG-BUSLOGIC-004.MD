บทนี้ เกี่ยวข้องกับเรื่องการเล่นกับเงื่อนไขที่แตกต่างกันตามช่วงเวลา ดูตัวอย่างที่ owasp ยกมา เช่น

บาง application ในหน้า logon ที่ให้กรอก username และ password ถ้า 


Username
Password
Response Time
Error Message
ผิด
ผิด
5 วินาที
user or password is incorrect.
ถูก
ผิด
3 วินาที
user or password is incorrect.
กรณีตามตารางด้านบนนี้ทำให้ผู้โจมตีรู้โดยไม่ต้องดู error message ที่ server ตอบกลับมาว่ามี username อันไหนบ้างที่มีอยู่จริงในระบบ

อีกตัวอย่างนึง เช่น เวปไซต์ให้จองตั๋วเครื่องบิน ตั๋วหนัง แล้วเราเข้าไปจองตั๋วไว้ แต่ไม่ทำการจ่ายเงินแล้วให้ระบบค้าง status ว่าจองไปเรื่อยๆ ถ้าทำแบบนี้ก็จะทำให้คนอื่นไม่สามารถจองตั๋วที่เรา hold ไว้เรื่อยๆ ได้

How to Test

ให้ค้นหา function การทำงานที่มีโอกาสจะเกิดช่องโหว่ด้วยเงื่อนไขด้านเวลา เช่น ที่ยกตัวอย่างมาข้างต้น แล้วลอง ทำให้มันผิดเงื่อนไข หรือให้เราได้ประโยชน์ หรือผู้ใช้คนอื่นและเจ้าของระบบเสียประโยชน์อันไม่สมควรจากการกระทำของผู้ทดสอบ ซึ่งเกี่ยวข้องกับเวลาครับ
