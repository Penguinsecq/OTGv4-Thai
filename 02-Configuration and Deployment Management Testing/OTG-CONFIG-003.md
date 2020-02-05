**How to Test Black Box**

Use VA Scan, Dirbuster, Nikto or other tools such as wget, curl, google for web mirrorign tools to find important files extension which maybe included sensitive information. The following file extensions should be inspected.

•  .asa
•  .inc
•  .zip, .tar, .gz, .tgz, .rar, ...: (Compressed) archive files
•  .java: No reason to provide access to Java source files
•  .txt: Text files
•  .pdf: PDF documents
•  .doc, .rtf, .xls, .ppt, ...: Office documents
•  .bak, .old and other extensions indicative of backup files (for example: ~ for Emacs backup files)
Try to find more file extension and if you suspect that you encounter with load balance architecture , try to determine whether this may introduce different behavior

GreyBOx

request related web application file and checking configuration of web server and application server, then find sensitive information and vuln. (maybe whitebox testing if possible)




