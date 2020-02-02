Testing for Browser cache weakness (OTG-AUTHN-006)

How to test

Black box Testing

Browser History

1. ทำการ login เข้า web application แล้วกรอก sensitive information ลงในหน้าใดหน้านึง แล้ว
2. logout ออกมา แล้วกด Back กลับ กรณีที่ sensitive information ยังแสดงให้เห็นอยู่ ถือว่าเป็นช่องโหว่

หรือ ไม่จำเป็นต้อง login ก็ได้เช่น เป็นหน้า sign up ซึ่งต้องกรอก email address เมื่อกรอกแล้วให้ลองกด Back ถ้ายังแสดงให้เห็นก็เป็นช่องโหว่

Browser Cache

1. เช็คโดยให้ทดสอบ web application จนครบทุกหน้า ผ่าน Burp หรือ intercept proxy อื่นๆ แล้วทำการ search ใน history ของ burp ว่าทุกๆ server response ในหน้าที่มี sensitive data นั้น ไม่มีการเก็บ cache โดยสามารถดูได้จาก
	* 
Cache-Control: no-cache, no-store
	* 
Expires: 0
	* 
Pragma: no-cache



2. เช็คใน local storage ของ browser ยกตัวอย่างเช่น
	* 
Mozilla Firefox:

		* 
Unix/Linux: ~/.mozilla/firefox/<profile-id>/Cache/
		* 
Windows: C:\Documents and Settings\<user_name>\Local Settings\Application Data\Mozilla\Firefox\Profiles\<profile-id>\Cache
	* 
Internet Explorer:

		* 
C:\Documents and Settings\<user_name>\Local Settings\Temporary Internet Files



ซึ่งในแต่ละ OS และ browser ก็จะแตกต่างกันไป

Grey Box testing

วิธีการเดียวกับ black box แต่ให้ดูรวมถึงหน้าที่มี sensitive data ที่ผ่านการ authentication แล้วด้วย
