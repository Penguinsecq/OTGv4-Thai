บทนี้จริงๆ เหมือนแปล อ่านๆได้จาก owasp เลย เป็นข้อๆ อยู่ละ จะกล่าวถึงว่า การใช้ encryption algorithm ที่ไม่แข็งแกร่งเนี่ยจะทำให้เกิดความเสี่ยงของพวก ข้อมูลสำคัญรั่วไหล, การได้มาซึ่งพวก session id ของเหยื่อ, การปลอมแปลงตัวตน อะไรพวกนี้ละ ซึ่งรวมๆ คือไม่ควรใช้ weak encryption เช่น MD5, RC4, หรืออย่าใช้ ECB (Electronic Code Book) ใน asymmetric encryption ทีนี้มาถึงการทดสอบในหัวข้อนี้ ก็มีเป็น checklist ตาม owasp เลย ดังนี้

	* 
ถ้าใช้ AES128 กับ AES256 ตัว IVหรือ Initialization Vector ต้องเป็น random iv หรือ คาดเดาไม่ออก
	* 
ถ้าใช้ RSA ในการทำ encryption, ต้องใช้เป็นโหมด OAEP (Optimal Asymmetric Encryption
	* 
ถ้าใช้ RSA ใน signature, แนะนำให้ใช้ PSS padding 
	* 
กลุ่มของ hash/ encryption algorithms ไม่ควรใช้  MD5, RC4, DES, Blowfish, SHA1. 1024-bit RSA or DSA, 160-bit ECDSA (elliptic curves), 80/112-bit 2TDEA (two key triple DES)



เป็นต้น นอกนั้น อ้างอิงจาก link owasp เลยครับ

https://github.com/OWASP/wstg/blob/master/document/4_Web_Application_Security_Testing/4.10_Testing_for_Weak_Cryptography/4.10.4_Testing_for_Weak_Encryption_OTG-CRYPST-004.md

ซึ่งก็จะมีตัวอย่างของการทำ source code review ด้วย ว่าเราจะใช้ keyword  ในการ check weak encryption algorithms ยังไง

แล้วก็มีแนะนำตัว tools ที่ใช้ช่วยในการทดสอบในบทนี้ครับ
