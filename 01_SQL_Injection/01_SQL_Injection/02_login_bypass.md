SQL Injection — Login Bypass  
**Lab Level:** Apprentice  
**Category:** Authentication / SQL Injection  
**Status:** Solved ✔  

---

## 🎯 Objective  
Bypass the login page using SQL injection.

---

## 🧠 Thought Process  
The lab hinted that the username was likely **administrator**.  
So I tried injecting SQL directly into the password field to break the query.

If the query uses:

SELECT * FROM users WHERE username='administrator' AND password='xyz'

Then injecting a comment (`--`) can bypass password validation.

---

## 🔍 Steps Taken  

### **1. Username used:**

administrator

### **2. Password payload:**

'--

Any remaining SQL after `--` becomes a comment, so the password check is ignored.

---

## 💣 Final Payload  
Username:

administrator

Password:

'--

---

## 🏁 Result  
Logged in successfully.  
Authentication bypassed → **Lab Solved**.

---

## 📝 Key Takeaways  

- SQL comments (`--`) are extremely powerful in login bypasses.  
- If an app doesn’t sanitize input, authentication becomes useless.  
- Always test username and password fields separately.

---

## ✔ Status  
Completed successfully.
