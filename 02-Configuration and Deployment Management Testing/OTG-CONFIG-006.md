How to test

1.  Discover supported http method

Use nmap with http-methods NSE script as following picture. Below picture is shown "Supported Methods"




2. Test XST Potential

use "curl" to test

Example not vulnerable server:

# curl -i -A 'Mozilla/5.0' -X 'TRACE /' -k https://www.not-vulnerable.com
HTTP/1.1 403 Forbidden
Date: Sat, 04 Jun 2011 06:46:21 GMT
Server: Apache
Content-Length: 202
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>403 Forbidden</title>
</head><body>
<h1>Forbidden</h1>
<p>You don't have permission to access /
on this server.</p>
</body></html>

Example of a vulnerable server:

# curl -i -A 'Mozilla/5.0' -X 'TRACE /' -k https://www.vulnerable.com
HTTP/1.1 200 OK
Date: Sat, 04 Jun 2011 06:34:51 GMT
Server: Apache
Connection: close
Content-Type: message/http

TRACE / / HTTP/1.1
User-Agent: Mozilla/5.0
Host: www.vulnerable.com
Accept: */*  


******
-i   --> nclude the HTTP response headers in the output. The HTTP response headers can include things like server name, cookies, date of the document, HTTP version and more...   

-A  -->  (HTTP) Specify the User-Agent string to send to the HTTP server. To encode blanks in the string, surround the string with single quote marks. This header can also be set with the -H, --header or the --proxy-header options.

-X -->  specifies a customer request method to use when communicating with the HTTP server.

-k  --> test TLS or SSL for https

***********

3. Test arbitrary HTTP method

ลองใช้ชื่อ method เช่น JEFF ตามภาพ ซึ่ง web server ควรจะแสดง error page ด้วย 405 หรือ 501 แต่ถ้าเรียกแล้วตอบด้วย 200 ก็ถือว่ามีช่องโหว่



แล้วเราสามารถจะลองใช้ การ issue command ตัวอย่างเช่น

•  FOOBAR /admin/createUser.php?member=myAdmin
•  JEFF /admin/changePw.php?member=myAdmin&passwd=foo123&confirm=foo123
•  CATS /admin/groupEdit.php?group=Admins&member=myAdmin&action=add
อาจจะสามารถ create user ได้

4. Testing HEAD access control bypass

ลองใช้ method HEAD เรียก หน้าของ admin ซึ่งโดยปกติ ต้องถูก redirect 302 ไปหน้า login  แต่ถ้าลองแล้วได้ 200 ดังภาพ แสดงว่ามีช่องโหว่ที่อาจจะ bypass authen ได้




จากภาพจะเห็นว่า web server ตอบกลับมาด้วย header ของ admin โดยไม่มี body ถ้าเราเจอแบบนี้ อาจจะมีช่องโหว่ให้เราลอง

•  HEAD /admin/createUser.php?member=myAdmin
•  HEAD /admin/changePw.php?member=myAdmin&passwd=foo123&confirm=foo123
•  HEAD /admin/groupEdit.php?group=Admins&member=myAdmin&action=add


