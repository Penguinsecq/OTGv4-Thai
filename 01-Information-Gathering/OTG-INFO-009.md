Identify the web application and version to determine known vulnerabilities and the appropriate exploits to use during testing.

**Black Box Testing**

1. Cookies

Find cookie some information give us about web application.

![45ABE023-F00E-4687-A739-C3A93DA73BB4](https://user-images.githubusercontent.com/60565002/73830788-d5777b80-4837-11ea-802a-035e3fd9bd58.png)

Above picture is shown that using wordpress

2. HTML Source Code
finding web framework in page source code

![8E6B1B35-0703-418C-949F-51E80252AB3A](https://user-images.githubusercontent.com/60565002/73830823-ddcfb680-4837-11ea-99e1-8a5acc94ea99.png)

![2D30BD9B-A9E9-456F-8C95-AA66A864F44F](https://user-images.githubusercontent.com/60565002/73830835-e1fbd400-4837-11ea-82f5-e9b0d6c1f57c.png)

3. Specific files and folders

Check robots.tx file and afterthat use dirbuster crawling files and folders , we can finding corresponding file in web server and determine web framework. For example

![90D0FBAB-76F4-45D6-8453-594119DBFC8B](https://user-images.githubusercontent.com/60565002/73830880-fcce4880-4837-11ea-8e27-9a134c2e92d4.png)


more wordlist : https://github.com/fuzzdb-project/fuzzdb

then we can find matching application as list below

Cookies

![9E54FDD4-259A-48D4-8FB6-956F6665D5C2](https://user-images.githubusercontent.com/60565002/73830913-0788dd80-4838-11ea-9265-e9865e46bc35.png)

HTML Source code

![07C32866-EE3F-4474-96EB-67EB67A3A62A](https://user-images.githubusercontent.com/60565002/73830932-0e175500-4838-11ea-9b5b-67a5b6f5895b.png)


Automatic Tools in case of no complex target

Use same application like OTG-INFO-008
