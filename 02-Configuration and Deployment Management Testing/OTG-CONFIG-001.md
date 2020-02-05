Objective : Map the infrastructure supporting the application and understand how it affects the security of the application.  

![E9C49320-3626-437D-8AB1-1D1E86A15BE2](https://user-images.githubusercontent.com/60565002/73834939-2ccd1a00-483f-11ea-9de9-2dcbfe4e342a.png)  

![ic350980](https://user-images.githubusercontent.com/60565002/73834944-2f2f7400-483f-11ea-93d6-ee429b2d6cc9.png)


**How to test**

1. Known Server Vulnerabilities

Request (if grey box selected or possible)
- web server version
- application or software version
- OS version
- database version
- etc.

from customer or vendor's software for find public vulnerability


2. Administrative tools
Try to find administrative page or requesst from customer
- พิจารณาวิธีการเข้าถึงของแต่ละ element เช่น  database หรือ web server เนื่องจากบางครั้ง element อื่นๆนี้ ถ้าเราสามารถเข้าถึงได้ อาจจะพาเรา ให้เข้าถึงหน้า admin ของ web appได้ หรือ compromise web app ได้เลย
- ดูเรื่อง user authentication ของแต่ละ element ด้วย และให้ใช้ default username, password

3. ถ้าเข้าถึงไม่ได้ อาจจะขอดูการ configure จาก ลูกค้าในแต่ละ element ก็จะมีภาพให้เราสามารถพิจารณาถึงช่องโหว่ที่เป็นไปได้
