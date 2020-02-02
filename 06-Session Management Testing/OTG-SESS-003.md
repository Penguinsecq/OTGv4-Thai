session fixation คือ การที่ user ทำการ authenticate เข้าสู่ application แต่ session id หรือ cookie ไม่มีการเปลี่ยนแปลงเป็นชุดใหม่  มีความเสี่ยงที่ทำให้เกิด session hijacking

ช่องโหว่ session fixation จะเกิดขึ้น
	* 
web application ทำการ authenticate ให้กับ user โดยปราศจากการ invalidate (ทำให้เป็นโมฆะ) ตัว session id ที่ user ใช้งานอยู่ในขณะนั้น แล้วก็ใช้ session id นั้นต่อไป
	* 
ผู้โจมตีสามารถทำให้เหยื่อนำเอา session id ของ attacker ไปใช้ในการ authenticate เมื่อ สำเร็จ attacker ก็จะสามารถเข้าถึง application นั้น เสมือนคนที่ผ่านการ authenticate มาแล้วเช่นกัน






Black Box Testing

อย่างที่อธิบายตอนต้นเรื่องการไม่ reissue session id ใหม่ให้กับ user หลังทำการ authenticate สำเร็จ ก็จะเป็นช่องโหว่ เช่นตัวอย่างใน owasp คือ ผู้ทดสอบทำการ test "www.example.com" โดยขั้นแรกคือการเข้าถึงตัว site ดังนี้




ซึ่ง response ที่ได้มาเป็นประมาณนี้



สังเกตว่า application จะมีการ แจกค่า JSESSIONID ให้กับ user ซึ่งยังไม่ได้ทำการ authenticate เป็น ดังภาพด้านบน

ทีนี้สมมติว่า user คนเดิมทำการ login เข้าไปด้วย POST HTTPS เพื่อเข้าใช้งานระบบ ตามด้านล่างนี้



เมื่อเราลองสังเกต HTTP response ที่ตอบกลับมาตามภาพด้านล่าง ซึ่งมีการ authenticate สำเร็จแต่ไม่มี JSESSIONID ตัวใหม่ตอบกลับมา แสดงว่าเป็นช่องโหว่ session fixation



ในการทดสอบแบบ grey box ก็ให้สอบถามทาง dev ว่ามีการ renew session token ให้กับ user หลังการทำ authenticate หรือไม่
