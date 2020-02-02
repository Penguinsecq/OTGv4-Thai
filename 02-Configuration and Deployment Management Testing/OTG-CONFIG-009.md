Test File Permission  

how to test 

กรณีที่ได้รับอนุญาตให้เข้าถึง file ได้เท่านั้น เช่น grey box หรือ white box

1. review file permission

ถ้าเป็น linux ก็ให้ใช้คำสั่งกลุ่ม "ls"  หรือ ใช้  "namei" ดังนี้

namei -l /absolute/path/to/file  

ผลที่ได้รับควรจะเป็นดังนี้



ถ้ากรณีที่เป็น windows ก็มี tools ชื่อ AccessChk  หรือ  AccessEnum  

