Testing for Bypassing Authentication Schema (OTG-AUTHN-004)

คือการหาวิธีในการ bypass การ authenticate เข้าสู่ระบบ โดยไม่จำเป้นต้องใส่ credential ที่ถูกต้อง ซึ่งจะมีหลากหลายวิธีการในการ bypass ต้องขึ้นอยู่กับแต่ละระบบโดย ในนี้จะยกตัวอย่างจากใน owasp ซึ่งในการ test จริง ต้องอาศัยประสบการณ์และ skill ของ tester ร่วมด้วย

How to Test

Black box

1. Direct page requrest

คือถ้า tester รู้ URL ที่เข้าถึงหน้า page ที่ควรจะต้อง authenticate ก่อน แล้วนำ URL นั้นมาเข้าตรงๆ โดยไม่ authenticate

ให้ลองใช้ tools เช่น nikto และ dir-buster ในการค้นหา directory ที่ต้องผ่านการ authenticate หรือ เป็นของ admin ยกตัวอย่าง

/system/
/password/
/logs/
/admin/
/test/

แล้วลองเข้าถึงโดยไม่ authen หรือกรณีที่มีการ test ในรูปแบบ grey box ร่วมด้วย เราจะรู้ directory หรือ URL ที่ต้องมีการ authentication อยู่แล้ว ก็นำมาลองเข้าถึงดู

2. Parameter Modification

คือการที่เราแก้ไขเพียง parameter แล้วทำให้สามารถได้รับสิทธิ์เหมือนคนที่ผ่านการ authentication แล้ว เช่น



เพียงแค่แก้ไข parameter "authenticated" เป็น yes ก็ทำให้สามารถเข้าถึงเช่นคน authenticate ได้




3. Session ID Prediction

คือกรณีที่ web application ใช้ session id ในการยืนยันคนที่ผ่านการ authenticate แล้ว ถ้า session id สามารถที่จะคาดเดารูปแบบได้ ก็ทำให้ attacker สามารถเดาและผ่านการ authentication ได้ เช่น



มีรูปแบบการ bypass authentication อีกมากมายเช่น การใช้เทคนิค SQL Injection และอื่นๆ ให้ดูรายละเอียดเพิ่มเติม
