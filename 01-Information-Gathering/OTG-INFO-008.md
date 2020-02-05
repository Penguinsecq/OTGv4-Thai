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



More about cookie

How to rename "PHPSESSID" to another

2.1


2.2 edit in php.ini


2.3 edit in .htaccess is also working




3. HTML source code

something like



4. File Extension




5. Specific files and folders

Use dirbuster crawling files and folders , we can finding corresponding file in web server and determine web framework

more wordlist : https://github.com/fuzzdb-project/fuzzdb


6.Error Message





Automatic Tools in case of no complex target



Whatweb


