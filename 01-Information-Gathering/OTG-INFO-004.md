Enumerate the applications within scope that exist on a web server. Find applications hosted in the webserver (Virtual hosts/Subdomain), non-standard ports, DNS zone transfers

How to Test Black-box

For non-standard URLs

1. Use VA Scan such as acunetix and nessus

2. Googling with site operator ( "site: www.example.com)

3. Use dirbuster crawling web server to find non-standard URLs

For non-standard ports

nmap -PN -sT -sV -p0-65535 -A 192.168.xxx.xxx

For Virtual hosts

1. dnsrecon -d www.example.com -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml





2. dnsdumster















3. netcraft.com

http://toolbar.netcraft.com/site_report?url=http://www.mindterra.com







ref : https://github.com/OWASP/wstg/blob/master/document/4_Web_Application_Security_Testing/4.2_Information_Gathering/4.2.4_Enumerate_Applications_on_Webserver_OTG-INFO-004.md

ลองใช้ tools อื่นๆดูต่อครับ
