Testing for Weaker authentication in alternative channel (OTG-AUTHN-010)

เป็นการ test ที่เจาะจงไปที่ channel อื่นๆที่เกี่ยวข้องกับ application นี้ โดยปกติการโจมตีทีหน้า authentication บน web app อาจจะไม่มีช่องโหว่ ซึ่งเราอาจจะสามารถโจมตีช่องโหว่ได้จาก channel อื่นๆ เช่น หน้า mobile app, desktop app, callcenter , หน้า web ของ country or ภาษาอื่น เป็นต้น

การ test ใน category นี้ ต้องคุยกับลูกค้าให้ชัดเจนว่าเป็นส่วนที่ in scope หรือไม่ และอนุญาตให้ทำหรือไม่ แต่อย่างน้อยถ้าเจอว่ามีช่องโหว่ควรจะ report ให้ owner ทราบเพื่อ discuss กันต่อไป

ยกตัวอย่างเช่น primary website เป็น

http://www.example.com

และมีหน้า authentication ซึ่งวิ่งผ่าน TLS เป็น

https://www.example.com/myaccount/

แต่ในกรณีที่ URL ของ mobile app เป็น http แบบด้านล่าง

http://m.example.com/myaccount/

ถือว่ามีช่องโหว่

How to Test

ค้นหา channel อื่นๆ โดย

- advance search engine

- ค้นหาจาก content ต่างๆใน หน้า web หลัก เช่น contact us, home page, help page, robots.txt

- Searching HTTP proxy logs, recorded during previous information gathering and testing, for strings such as "mobile", "android", blackberry", "ipad", "iphone", "mobile app", "e-reader", "wireless", "auth", "sso", "single sign on" in URL paths and body content.
