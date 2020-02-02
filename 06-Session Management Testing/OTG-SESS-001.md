
ดูเรื่องของ cookie ก่อน ครับ หลักการทำงานคร่าวๆ ของ http cookie ตามภาพ




จากภาพจะเห็นว่า cookie จะเป็นเสมือนตัวที่บ่งบอกว่าเป็นใครมากกว่านั้นยังอาจบอกถึงว่า user คนนั้น ทำอะไรมา และมีสถานะเป็นแบบไหน จะเห็นว่า cookie มีความสำคัญมากในระบบ web application ซึ่งก็จะมาเกี่ยวเนื่องกับเรื่อง security จะเห็นได้ว่าถ้า user cookie ของใครคนใดคนนึง หลุดไปอยู่ในมือของ attacker ก็เปรียบเสมือนว่า attacker คนนั้นมีสิทธิ์ได้เทียบเท่า user คนดังกล่าว (hijacking) 


Black Box Testing 

จาก owasp จะ list สิ่งที่ควรทำการ test เกี่ยวกับ cookie มาอย่างน้อย ดังต่อไปนี้

	* 
Are all Set-Cookie directives tagged as Secure?
	* 
Do any Cookie operations take place over unencrypted transport?
	* 
Can the Cookie be forced over unencrypted transport?
	* 
If so, how does the application maintain security?
	* 
Are any Cookies persistent?
	* 
What Expires= times are used on persistent cookies, and are they reasonable?
	* 
Are cookies that are expected to be transient configured as such?
	* 
What HTTP/1.1 Cache-Control settings are used to protect Cookies?
	* 
What HTTP/1.0 Cache-Control settings are used to protect Cookies?



ละไว้ตรงนี้ 


มาถึงเรื่อง การ test 

Cookie collection 

สิ่งแรกในการที่เราจะทำการ manipulate cookie ได้ คือต้องเข้าใจว่า cookie ถูกสร้างขึ้นมาและมีการจัดการกับ cookie นั้นๆ อย่างไร โดย
	* 
มี cookie อะไรบ้างที่ถูกใช้ใน application นี้ โดยผู้ทดสอบควรจะลองใช้งาน application นั้นๆ แล้ว สังเกตเวลามีการสร้าง cookie เกิดขึ้นมา จดบันทึกว่าเกิดตอนไหน ยังไง หน้า page ไหน สร้าง ฯลฯ
	* 
เล่น application แล้วสังเกตว่า cookie เป็นค่าตายตัวหรือ เปลี่ยนแปลง หรือไม่อย่างไร อะไรทำให้มีการเปลี่ยนแปลงค่า cookie นั้นๆ
	* 
ส่วนไหนของ application ที่สามารถเข้าถึงได้เมื่อมี cookie เท่านั้น ลองเข้าโดยไม่ใช้ cookie ดู




Session Analysis

ค่า session tokens ในทีนี้หมายถึง ค่า cookie, session id หรือ ค่าอื่นๆที่คล้ายคลึงกันนั้น ควรจะถูกทดสอบว่า มีการสร้างด้วยวิธีการ random หรือไม่, เป็นค่าเฉพาะตัว (uniqueness) หรือไม่ , คาดเดาได้หรือไม่ และการเข้ารหัส cookie นั้นดีเพียงพอหรือไม่  ยกตัวอย่างตาม owasp เช่น เรื่อง 

token structure & information leakage  
คือ ตัว structure ของ session id นั้นไม่ควรจะมีการเอาค่าเฉพาะเจาะจงต่างๆ มาใส่ไว้ หรือเป็นค่าที่สามารถอ้างอิงถึงข้อมูลในฝั่ง server side ได้ เช่น ค่า session id ต่อไปนี้ ซึ่งอยู่ในรูปแบบที่อ่านได้ (clear-text)

192.168.100.1:owaspuser:password:15:58

เป็นรูปแบบที่ไม่สมควร ถึงแมัว่าบางครั้งตัว application นำไป เข้ารหัสด้วยการ encode หรือ hash ก็แล้วแต่ เป็นข้อความดังต่อไปนี้

Hex 3139322E3136382E3130302E313A6F77617370757365723A70617373776F72643A31353A3538
Base64 MTkyLjE2OC4xMDAuMTpvd2FzcHVzZXI6cGFzc3dvcmQ6MTU6NTg=
MD5 01c2fc4f0a817afd8366689bd29dd40a

ผู้ทดสอบยังสามารถลองทำการ decode ด้วยเทคนิคต่างๆ ลองดู และจะพบว่าสามารถได้ credential จากข้อมูลนี้ จึงเป็นรูปแบบที่ไม่เหมาะสม

ในระหว่างการวิเคราะห์ตัว structure ของ session token ผู้ทดสอบควรจะทำการทดสอบในเรื่องต่อไปนี้ด้วย

	* 
มีส่วนไหนของ session id ที่เป็นค่าตายตัวหรือไม่
	* 
มีข้อมูล clear-text ที่เป็น confidential ถูกเก็บไว้ในตัว session id หรือไม่เช่น username/ UID, IP address
	* 
ข้อมูล confidential ที่ถูกถอดรหัสออกมานั้นมีอะไรบ้าง สำคัญหรือไม่อย่างไร
	* 
มีข้อมูลอะไรที่เราสามารถอนุมานได้จาก structure ของ session id หรือไม่
	* 
What portions of the Session ID are static for the same log in conditions?
	* 
What obvious patterns are present in the Session ID as a whole, or individual portions?


Session ID Predictability and Randomness
ผู้ทดสอบ สามารถคาดเดาค่า session id ได้หรือไม่ ด้วยข้อมูลต่างๆ จากตัว application ดูเพิ่มเติมจากใน owasp ครับ https://www.owasp.org/index.php/Testing_for_Session_Management_Schema_(OTG-SESS-001)

ในการทำการวิเคราะลำดับ หรือความต่อเนื่องของ session id , รูปแบบและการหมุนเวียนของ session id เราควรต้องทดสอบเรื่องดังต่อไปนี้ด้วย
	* 
Session id มีการ random จริงๆ หรือไม่ 
	* 
มีเงื่อนไขอะไรไหม ที่เวลาเราใส่ input ลงไปแล้วสามารถทำให้ได้ session id เดิม หรือ เป็น ลำดับที่คาดเดาได้
	* 
session id มีการเข้ารหัสที่แกะได้ยากจริงๆหรือไม่
	* 
มีส่วนไหนของ session id ที่เกี่ยวข้องกับเรื่องของเวลาไหม
	* 
มีส่วนไหนของ session id ที่สามารถคาดเดาล่วงหน้าได้ไหม
	* 
เราสามารถอนุมานวิธีการสร้าง session id ได้ จาก session id เก่าๆ ไหม


ดูเพิ่มเติมใน owasp ในหัวข้อต่อไปนี้ครับCookie reverse engineeringBrute Force Attacks
Gray Box testing and example
กรณี Grey Box ผู้ทดสอบต้องเช็คเรื่องดังต่อไปนี้
	* 
Session id มีการ random จริงหรือไม่ คาดเดาได้ด้วยวิธีต่างๆ หรือไม่ ต้องมีการเข้ารหัสด้วย key ที่ความยาว 256 bits 
	* 
ความยาวของ session id อย่างน้อยควรมี 50 คัวอักษร
	* 
Session time-out ต้องมีการกำหนดไว้ขึ้นอยู่กับลักษณะของ application และ business
	* 
cookie configuration

		* 
ต้องไม่มีการเก็บใน memory อื่นๆ นอกจาก ram
		* 
มีการ set secure attribute ให้กับ cookie

			* 
Set Cookie: cookie=data; path=/; domain=.aaa.it; secure
		* 
มีการ set HTTPOnly ให้กับ cookie

			* 
Set Cookie: cookie=data; path=/; domain=.aaa.it; HTTPOnly






