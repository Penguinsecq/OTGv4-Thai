Testing for Encryption & Reuse of Session Tokens vulnerabilities

ตัวระบบต้องมีการป้องกันตัว session id หรือ token ไม่ให้ถูกดักฟังได้จากผู้ไม่ประสงค์ดี เพราะฉะนั้นตัว session id ควรต้องถูกส่งผ่าน encryption tunnel เช่น https 

เราอาจจะทดสอบโดยการใช้ burp ดักการส่งผ่าน http requrest แล้ว ทำการแทนที่ https ด้วย http ว่าสามารถทำได้หรือไม่ รวมถึงเวลามีการดาวน์โหลดไฟล์ ซึ่งตัวไฟล์อาจจะสามารถเข้าถึงได้ด้วย http ทีนี้เวลา user เข้ามาทำการดาวน์โหลดก็จะมีการ switch จาก https เป็น http ซึ่งตัว application server ควรจะมีการ monitor ตัว session id ของผู้ใช้งานเพื่อให้แน่ใจว่ามีการเปลี่ยน session id ก่อนทำการเข้าถึงไฟล์ที่จะดาวน์โหลด กล่าวง่ายๆ คือไม่ได้ใช้ session id ตัวเดียวกันกับตอนใช้งานหน้าเวปที่เป็น https

ซึ่งผลลัพธ์ที่ตัว application ควรจะทำคือ 
	* 
ทุกครั้งที่มีการ authenticate สำเร็จต้องมีการแจก session id , token ตัวใหม่ให้ผู้ใช้งาน และ
	* 
ตัว session id, token ต้องส่งผ่าน https หรือ encrypted channel เท่านั้น



Testing for Proxies & Caching vulnerabilities:

ในหลายๆองค์กรจะมีการเข้าใช้งาน web application ผ่านทางอุปกรณ์ประเภท proxy ทีนี้ ตัว proxy ก็จะมีการเก็บ cache ในแต่ละ connection อยู่แล้ว เป็นที่มาของการ test นี้ คือ ถ้าตัว session id ไม่มีการตั้งค่าเพื่อให้ค่าของ session id ไม่ถูกเก็บไว้ตาม cache ในที่ต่างๆ ก็ ก็มีความเสี่ยงว่าจะสามารถนำค่า session id ที่ถูก cache ไว้ไปใช้งานต่อ (reuse) ได้

การทดสอบทำได้โดยสังเกตการตั้งค่า "Expires: 0" หรือ Cache-Control: max-age=0 ให้กับตัว cookie ซึ่งควรจะถูกใช้เพื่อป้องการการ cache "session id" เก็บไว้ 


ซึ่งมิใช่ว่าการที่ค่า cache-control กับ expires เป็นดังรูปด้านบนแล้วจะเป็นสิ่งที่ผิด ผู้ทดสอบต้องดู environment อื่นๆร่วมด้วยเช่นเป็น application ที่จำเป็นต้องใช้หรือไม่


Testing for GET & POST vulnerabilities:

โดยทางปฏิบัติแล้วไม่ควรมีการส่งค่า session id ผ่านทาง GET request อยู่แล้วเพราะมันจะไปโผล่ใน log ของพวก web proxy หรือ firewall ซึ่งทำให้มีความเสี่ยงที่ผู้เป็น admin ของอุปกรณ์เหล่านั้นหรือคนอื่นๆ ที่เข้าถึงได้สามารถรู้ค่า session id ของผู้ใช้งาน จึงควรส่งค่า cookie หรือ session id ใน POST  ผู้ทดสอบจึงต้องลองเปลี่ยน POST request แทนที่ด้วย GET ดูว่ายังสามารถส่ง request ไปทำงานได้ปกติไหม ซึ่งไม่ควรจะทำงานได้ ยกตัวอย่างจากใน owasp ดังนี้ครับ 



ตัว POST request ตามภาพด้านบนนี้ ถ้า login.asp มีการจัดการที่ไม่ดี ผู้ทดสอบจะสามารถทำการ login โดยใช้ GET ดังนี้

http://test.com/login.asp?Login=Username&password=Password&SessionID=12345678

Testing for Transport vulnerabilities:
เวลาที่มีการส่งผ่านข้อมูลระหว่าง server-client ผู้ทดสอบควรทดสอบดังต่อไปนี้เป็นอย่างน้อย (ไม่แปลนะครับ)
	* 
How are Session IDs transferred? e.g., GET, POST, Form Field (including hidden fields)
	* 
Are Session IDs always sent over encrypted transport by default?
	* 
Is it possible to manipulate the application to send Session IDs unencrypted? e.g., by changing HTTP to HTTPS?
	* 
What cache-control directives are applied to requests/responses passing Session IDs?
	* 
Are these directives always present? If not, where are the exceptions?
	* 
Are GET requests incorporating the Session ID used?
	* 
If POST is used, can it be interchanged with GET?


