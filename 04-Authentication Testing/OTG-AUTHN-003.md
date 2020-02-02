Testing for Weak lock out mechanism (OTG-AUTHN-003)กรณีที่มีเพียง account เดียวในการ test ให้ test หัวข้อนี้เป็นหัวข้อสุดท้ายHow to test (beware impact of account lockout)ก่อนทำการ test บนระบบจริงให้สอบถามและวางแผนร่วมกับเจ้าของระบบก่อน เพื่อหลีกเลี่ยงผลกระทบที่จะเกิดขึ้นจากการที่ account ถูก lockout
	* Attempt to log in with an incorrect password 3 times.
	* Successfully log in with the correct password, thereby showing that the lockout mechanism doesn't trigger after 3 incorrect authentication attempts.
	* Attempt to log in with an incorrect password 4 times.
	* Successfully log in with the correct password, thereby showing that the lockout mechanism doesn't trigger after 4 incorrect authentication attempts.
	* Attempt to log in with an incorrect password 5 times.
	* Attempt to log in with the correct password. The application returns "Your account is locked out.", thereby confirming that the account is locked out after 5 incorrect authentication attempts.
	* Attempt to log in with the correct password 5 minutes later. The application returns "Your account is locked out.", thereby showing that the lockout mechanism does not automatically unlock after 5 minutes.
	* Attempt to log in with the correct password 10 minutes later. The application returns "Your account is locked out.", thereby showing that the lockout mechanism does not automatically unlock after 10 minutes.
	* Successfully log in with the correct password 15 minutes later, thereby showing that the lockout mechanism automatically unlocks after a 10 to 15 minute period.


