เป็นช่องโหว่ที่เกี่ยวกับการที่ตัว application มีการใช้ค่า session ค่าเดียวกันสำหรับหลายๆวัตถุประสงค์ ทำให้ผู้โจมตีเข้าถึงหน้า page ที่ไม่ควรจะเข้าถึงได้ เช่น การที่ attacker สามารถ bypass authentication  สำหรับ application ตัวนึงที่ไม่ได้ public บน internet โดยการใช้ค่า session ที่ได้รับจากการเข้าหน้า password recovery ที่อยู่บน internet

Black Box Testing

วิธีการทดสอบให้ลองดูจากรูปด้านล่างนี้ ซึ่งถ้าทราบ concept ของ session ใน web application แล้วก็ให้ข้ามไปดูภาพต่อไป



จากภาพด้านบนจะอธิบายวิธีการทำงานของ session 

ทีนี้มาถึงตัวอย่างของการทำ bypass authentication ที่เกิดจากช่องโหว่ session puzzling จากที่ได้กล่าวไปข้างต้น จะเป็นตามรูปด้านล่างนี้ คือ 
	1. 
user เข้าไปยังหน้า password recovery ที่ถูกวางอยู่บน public internet ใครๆสามารถเข้าถึงได้ ซึ่ง หน้านี้จะให้ user กรอกพวก username หรือ email ทีนี้เมื่อ 
	2. 
ฝั่งตัว application server ก็จะส่ง recovery link ไปยัง email ที่ให้ไว้ซึ่งจะมีการฝัง token ชั่วคราว ซึ่งผูกอยู่กับ account ของ user รายนี้
	3. 
เมื่อ user รายนี้ทำการ click link ในข้อ 2 ก็จะเจอกับ challenge question ตามปกติ ซึ่งในบางครั้ง ค่า session ที่ user ใช้ในการเข้าถึงหน้า challenge นี้ กับ token-to-account จะมีการสร้างและเก็บไว้ใน session memory ด้วยข้อมูลพวก username หรือ email ที่ client ส่งมา ใน step แรก ซึ่งเป็นกลุ่มของ identity objects ดังภาพด้านล่างลงไปอีก
	4. 
ตัว identity objects ใน session memory เหล่านี้เองที่ทำให้ user อาจจะสามารถเอาค่า session นี้มาใช้ในการเข้าหน้า login ที่อยู่ภายในองค์กร ที่ไม่สามารถเข้าถึงได้จาก public internet









Grey-Box Testing
ใช้วิธีการทำ source code review จะดีที่สุด


มีเอกสารที่ให้ความรู้เพิ่ม และมีเคสให้ดูอีกตามด้านล่าง หรือเปิดจาก owasp testing guide ใน github ก็ได้เช่นกัน
ref : https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/puzzlemall/Session%20Puzzles%20-%20Indirect%20Application%20Attack%20Vectors%20-%20May%202011%20-%20Whitepaper.pdf
