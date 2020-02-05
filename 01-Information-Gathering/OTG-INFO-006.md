เพื่อทำความเข้าใจรูปแบบของ HTTP request และ response ของตัว application ให้ถูกต้อง

take note all activities below in excel or other note

**Black Box Testing**

Request
- parameter in get request (usually after a "?" mark).
- parameter (include hidden parameter) in post request
- customer type header (such as debug=False)

![image](https://user-images.githubusercontent.com/60565002/73826876-1e780180-4831-11ea-85c0-3c5d8bd89b0a.png)

![image 2](https://user-images.githubusercontent.com/60565002/73826890-246de280-4831-11ea-8603-c9bf29be0ae5.png)

![image 3](https://user-images.githubusercontent.com/60565002/73826917-32bbfe80-4831-11ea-8aa2-66e5287e84d7.png)


Response
- identify where new cookies are set, modified, or added
- identify any redirects (3xx HTTP status code), 403 forbidden, 500 internal server error.
- other interested in header


Grey box Testing

ในกรณีของ grey box เราอาจจะสามารถขอให้ทาง developer อธิบายให้เราฟังเกี่ยวกับการทำงานของ application ที่จะทดสอบ
