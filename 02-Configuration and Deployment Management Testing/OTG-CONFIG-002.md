

**How to test**

**Black box**

search and finding for

1. sample and known file and directory - try to find default file and directory if we know some web server information , sometime these file is disclosed vulnerability

2. Review comment in page source

3. System Configuraton (if possible) ลองอ่าน hardening guide ของระบบที่ดำเนินการทดสอบ ซึ่งบางครั้งอาจจะทำให้พบช่องโหว่ในการโจมตี

Grey box

This is server configuration review such as
- enable server module that are needed for the applicatoin
- handle server errors (40x and 50x) with custom-made page instead of with the default web server pages.
- run server software with minimized privileges in the operating system.
- logging both legitimate acess and errors.
- server is configured to properly handle overload and DOS





