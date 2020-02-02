กรณีที่มี robots.txt ไฟล์ ให้ลองเปิดดูเนื้อหาด้านในว่ามี directory ใดที่ถูก list ไว้บ้าง ซึ่งอาจจะถูกปิดไม่ให้ทำการ search ได้จากการใช้ search engine หรือ tools จำพวก spiders, robots, crawlers ซึ่ง tools เหล่านี้จะกล่าวถึงใน  OTG-INFO-007 ต่อไป

additional : robots.txt should not be considered as a mechanism to enforce restriction คือ robots.txt ไม่ควรจะใช้ในการป้องกันการเข้าถึง web content

ใช้ rockspider ด้วยคำสั่ง โดยให้วิ่งผ่าน burp ด้วยการเปิดทิ้งไว้



สังเกตผลลัพธ์ที่ได้
<meta name=”robots” content=”index, follow” /> อันนี้หมายถึงให้ robot ของ search engine เก็บข้อมูลในหน้า index และวิ่งไป follow ใน link ที่มีอยู่ใน index ด้วย
