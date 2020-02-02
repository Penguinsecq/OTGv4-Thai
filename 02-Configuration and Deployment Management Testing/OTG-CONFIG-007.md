Test HTTP Strict Transport Security

How to test

ในระหว่างการ test สามารถดูได้จาก scanner ของ burp pro จะแสดงให้เห็นอัตโนมัติ

  

หรือถ้าเราดูใน burp free ก็ให้ดูใน response header จะต้องมี ดังภาพ





หรือเราสามารถใช้ curl ดังนี้

$ curl -s -D- https://paypal.com/ | grep Strict
Strict-Transport-Security: max-age=14400  

หรือตามรูป

  

