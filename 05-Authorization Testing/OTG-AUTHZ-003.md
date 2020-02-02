ในหัวข้อนี้ จะคล้ายๆกับ OTG-AUTHZ-002 ในบทที่แล้ว ซึ่งเกี่ยวกับ authorization เป็นหลัก

จะเป็นการ test ว่า user คนนึงสามารถเข้าถึง resource หรือ function ที่ตัวเองไม่ได้รับอนุญาตหรือไม่ ในทางปฏิบัติจะมีรูปแบบการทดสอบที่หลากหลายขึ้นอยู่กับลักษณะ และการออกแบบ web application นั้นๆ ทีนี้เรามาดูตัวอย่างจาก owasp ซึ่ง โดยภาพรวมก็คือการแก้ไข parameter ต่างๆ เพื่อให้ผู้ทดสอบที่ใช้ user ในระดับนึง สามารถเข้าถึง function หรือ resource ของ user อีกระดับนึงได้ เช่น



ใน post request ด้านบนจะเห็นว่า user คนนี้อยู่ใน groupID = grp001

tester ควรต้องลองว่าถ้าเราแก้ไข value ของ parameter ทั้ง “groupID” และ “orderID” เราจะสามารถเข้าถึง resource ใน groupid อื่นๆ ได้หรือไม่

มาดูตัวอย่างต่อไป จะเป็นการแก้ไข User profile 



ซึ่งถ้า tester แก้ไขเป็นดังภาพด้านบนคือ value=“SysAdmin” เราจะสามารถเป็น administrator ได้ไหม

ยังมีตัวอย่างอื่นๆ อีก ให้ลองดูใน https://www.owasp.org/index.php/Testing_for_Privilege_escalation_(OTG-AUTHZ-003)
