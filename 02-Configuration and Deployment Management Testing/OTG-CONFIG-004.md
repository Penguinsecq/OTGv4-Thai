Testing for unreferenced files, old, backup files.


Black Box Testing

Use manual inspect or dirbuster to enumerate page, function and determine

1. naming scheme for example

viewuser.asp may looking for edituser.asp --> adduser.asp --> deleteuser.asp

or

/app/user --> /app/admin --> /app/manager

2. review comment in page source for example

below shown that there is uploadfile.jsp in this website



below shown that there is /admin/useradmin.jsp in this website.



3. see /robots.txt




4. Find directory listing vuln from by request all enumerated directories .


5. Using google or other search engine to find cache page and try to find old file








Gray Box Testing

perform gray box by examine the files contained in the web directory if possible

in most case copied of files or backup files often using the same naming convention for example

- login.php become login.php.old
