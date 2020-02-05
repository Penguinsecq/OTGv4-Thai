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

![A84610F8-6087-40B5-A853-62FAB075E52A](https://user-images.githubusercontent.com/60565002/73825623-e53e9200-482e-11ea-90ad-19118528528c.png)

![25BA4184-B17C-4664-873D-8F0EE76F760E](https://user-images.githubusercontent.com/60565002/73825628-e7085580-482e-11ea-9f15-83f73f1da09b.png)

2. dnsdumster

![5943F9CF-E7BB-44C9-B8F3-485D3A410779](https://user-images.githubusercontent.com/60565002/73825688-07d0ab00-482f-11ea-9ca5-99a561d847e2.png)

![957D5C67-FB32-4B2E-84D6-0D8A040489BE](https://user-images.githubusercontent.com/60565002/73825699-0b643200-482f-11ea-97b6-5982ba6a2fee.png)

![AF830758-DC03-4FFE-BB0A-57A0AE588262](https://user-images.githubusercontent.com/60565002/73825708-0f904f80-482f-11ea-9745-58c4f767c408.png)

![B55D4896-2E7B-4A03-8E3E-9F87646ABE17](https://user-images.githubusercontent.com/60565002/73825715-1323d680-482f-11ea-889f-68e7d432c624.png)

![5A9F06C4-0B44-4982-B111-7BC37C9B4AEF](https://user-images.githubusercontent.com/60565002/73825721-17e88a80-482f-11ea-8b5e-10d58f3fb553.png)

![E917D613-3794-42C9-BE57-B61D503AE522](https://user-images.githubusercontent.com/60565002/73825725-1a4ae480-482f-11ea-9921-4dfedf419880.png)













3. netcraft.com

http://toolbar.netcraft.com/site_report?url=http://www.mindterra.com







ref : https://github.com/OWASP/wstg/blob/master/document/4_Web_Application_Security_Testing/4.2_Information_Gathering/4.2.4_Enumerate_Applications_on_Webserver_OTG-INFO-004.md

ลองใช้ tools อื่นๆดูต่อครับ
