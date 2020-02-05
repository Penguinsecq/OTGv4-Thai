Testing for unreferenced files, old, backup files.


**Black Box Testing**

Use manual inspect or dirbuster to enumerate page, function and determine

1. naming scheme for example

viewuser.asp may looking for edituser.asp --> adduser.asp --> deleteuser.asp

or

/app/user --> /app/admin --> /app/manager

2. review comment in page source for example

below shown that there is uploadfile.jsp in this website


![66287DE9-DC29-4EA3-A51E-E613BCB6B668](https://user-images.githubusercontent.com/60565002/73835287-b846ab00-483f-11ea-954b-f62d4deaef88.png)

below shown that there is /admin/useradmin.jsp in this website.

![B3058943-C4F4-4781-8A1D-2473DBA643C3](https://user-images.githubusercontent.com/60565002/73835326-c8f72100-483f-11ea-9951-eb2e7d6d9837.png)

3. see /robots.txt

![E5683EDF-67B2-475D-8269-26D1D4B31D24](https://user-images.githubusercontent.com/60565002/73835348-d44a4c80-483f-11ea-8e1b-b5ae5cb33ecd.png)

4. Find directory listing vuln from by request all enumerated directories .


5. Using google or other search engine to find cache page and try to find old file

![6EB31BA3-5F08-45F8-9111-4F92E352A4C8](https://user-images.githubusercontent.com/60565002/73835486-0bb8f900-4840-11ea-9397-a12a755c9644.png)

![C815569C-E7CC-4270-9531-6FB8DF3BE74F](https://user-images.githubusercontent.com/60565002/73835399-ea580d00-483f-11ea-9d82-34d14f2a356d.png)


**Gray Box Testing**

perform gray box by examine the files contained in the web directory if possible

in most case copied of files or backup files often using the same naming convention for example

- login.php become login.php.old
