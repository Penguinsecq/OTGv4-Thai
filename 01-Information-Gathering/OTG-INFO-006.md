เพื่อทำความเข้าใจรูปแบบของ HTTP request และ response ของตัว application ให้ถูกต้อง

take note all activities below in excel or other note

Black Box Testing

Request
- parameter in get request (usually after a "?" mark).
- parameter (include hidden parameter) in post request
- customer type header (such as debug=False)



Response
- identify where new cookies are set, modified, or added
- identify any redirects (3xx HTTP status code), 403 forbidden, 500 internal server error.
- other interested in header


Grey box Testing

ในกรณีของ grey box เราอาจจะสามารถขอให้ทาง developer อธิบายให้เราฟังเกี่ยวกับการทำงานของ application ที่จะทดสอบ
