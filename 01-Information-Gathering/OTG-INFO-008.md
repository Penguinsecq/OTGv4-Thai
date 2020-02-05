To define type of used web framework so as to have a better understanding of the security testing methodology.

**Black Box Testing**

1. HTTP headers

Use Burp intercept response header from target web server (finding in every page if not found in early)

![CFB35F8A-08C7-4DE6-8250-188D32DD261E](https://user-images.githubusercontent.com/60565002/73827375-02289480-4832-11ea-9af7-1bfed12278e2.png)

Remark :

"X-Powered-By" is a common non-standard HTTP response header (most headers prefixed with an 'X-' are non-standard). It's often included by default in responses constructed via a particular scripting technology.

It's important to note that it it can be disabled and/or manipulated by the server. Some servers chose not to include it or even to provide misleading information to throw off hackers that might target a particular technology/version.

If I wanted to send out that response header in a PHP script it's as simple as including the following code:

> header('x-powered-by: ZendServer 8.5.0,ASP.NET');


2. Cookies

Use Burp Suite intercept when submit request and consider cookie information


![FCB0E623-E5B9-4615-95D8-96684E5AD195](https://user-images.githubusercontent.com/60565002/73827630-7cf1af80-4832-11ea-9ab7-37bcea74c221.png)


More about cookie

How to rename "PHPSESSID" to another

2.1

![F3BE64E7-9ED7-48CE-A23D-6FD4592A87A6](https://user-images.githubusercontent.com/60565002/73827699-9a267e00-4832-11ea-8c81-244086f85615.png)

2.2 edit in php.ini

![647866C6-5CCE-4738-8BEC-C0C0BE8A602F](https://user-images.githubusercontent.com/60565002/73827720-a3174f80-4832-11ea-8e67-df618cc3aa57.png)

2.3 edit in .htaccess is also working

![2C84FE42-12ED-4D84-B46E-C31CED5BDF7C](https://user-images.githubusercontent.com/60565002/73827732-a8749a00-4832-11ea-9445-25b612d15ec6.png)

3. HTML source code

something like

![100D96E8-FE84-4EC5-902F-9542D29EF94D](https://user-images.githubusercontent.com/60565002/73827779-bfb38780-4832-11ea-8f67-8f31456e61a8.png)

4. File Extension

![A812F2EF-4BF6-4AFD-A980-1AAF97BD2DD5](https://user-images.githubusercontent.com/60565002/73827788-c2ae7800-4832-11ea-9320-b68578a6e396.png)


5. Specific files and folders

Use dirbuster crawling files and folders , we can finding corresponding file in web server and determine web framework

more wordlist : https://github.com/fuzzdb-project/fuzzdb


6.Error Message

![BA191D0E-DDA7-43E8-9DDA-8672B2420D45](https://user-images.githubusercontent.com/60565002/73827951-0608e680-4833-11ea-8024-581c1723a3aa.png)



Automatic Tools in case of no complex target

![4D42E897-8EBA-4966-8F74-9165AEFA71F5](https://user-images.githubusercontent.com/60565002/73827966-0e612180-4833-11ea-91cc-ba417048a55f.png)

Whatweb

![95A564D8-A562-453A-8127-6901DB2718F0](https://user-images.githubusercontent.com/60565002/73827979-115c1200-4833-11ea-9883-328d2b7149ea.png)
