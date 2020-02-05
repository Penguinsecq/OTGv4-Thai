รีวิวพวก comments และ metadata ที่อยู่ใน source code เพื่อทำความเข้าใจตัว application ให้มากขึ้น และในบางครั้งก็จะเจอข้อมูลที่สำคัญหรือพวก username, password, path เข้าไปยัง directory และอื่นๆ 

**Black Box Testing**

1. Check HTML source code for comment, metadata, to find sensitive information โดยการคลิ๊กขวาบนหน้าเวป แล้วกด View Page source บน firefox เป็นต้น (browser อื่นๆ ก็ใกล้เคียงกัน)
	* - credential
	* - sql query syntax
	* - meta tag
	* - other etc.

ยกตัวอย่างอันนี้จาก owasp ก็จะเห็น sql syntax ดังรูป

![EF1CCDE7-276E-4F62-A305-F6ED44DD09A1](https://user-images.githubusercontent.com/60565002/73826526-7e21dd00-4830-11ea-8929-037d37170137.png)

![7B8112BE-82E3-4E00-B4C3-31DE4B999FCD](https://user-images.githubusercontent.com/60565002/73826540-8417be00-4830-11ea-9bf2-f0625c998bbf.png)

อันนี้ไม่แปลต่อ ไม่มีอะไร


![FE180231-8617-4510-8046-71A9D2C18377](https://user-images.githubusercontent.com/60565002/73826580-9db90580-4830-11ea-8527-c31fbf81c32c.png)
