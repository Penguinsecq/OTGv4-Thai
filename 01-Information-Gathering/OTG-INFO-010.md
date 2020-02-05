Try to map the application architecture, protection devices such as WAF, Firewall, Proxy, Database or other.

**How to Test**

1. use NMAP scan targets web server and focus on port status (open, filtered, closed)

![image](https://user-images.githubusercontent.com/60565002/73831058-4880f200-4838-11ea-8002-caec863a398c.png)

![image 2](https://user-images.githubusercontent.com/60565002/73831065-4a4ab580-4838-11ea-807d-4acb3481a148.png)

2. try to generate error page to determine something is placed between web server for example

- request unvailable page on web server if return a different error from 404 message. It may be block by some protection

- some error page will be thrown when attack occur such as imperva WAF

![EDF8A910-95EF-45FF-9660-0AE5EF2079DE](https://user-images.githubusercontent.com/60565002/73831083-50d92d00-4838-11ea-8549-11bbc430900c.png)
