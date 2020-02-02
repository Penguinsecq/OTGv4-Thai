Try to map the application architecture, protection devices such as WAF, Firewall, Proxy, Database or other.

How to Test

1. use NMAP scan targets web server and focus on port status (open, filtered, closed)






2. try to generate error page to determine something is placed between web server for example

- request unvailable page on web server if return a different error from 404 message. It may be block by some protection

- some error page will be thrown when attack occur such as imperva WAF


