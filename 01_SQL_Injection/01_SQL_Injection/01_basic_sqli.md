# SQL Injection — Retrieve Hidden Data  
**Lab Level:** Apprentice  
**Category:** SQL Injection  
**Status:** Solved ✔  

---

## 🎯 Objective  
Exploit a SQL injection vulnerability in the product category filter to reveal hidden products.

---

## 🧠 Thought Process  
I started by checking if the parameter was vulnerable to SQL injection by adding a single quote (`'`).  
The application returned an SQL error — meaning the input is directly used in a query.

This confirmed: **vulnerable parameter**.

Next, I tested how the query was being built by injecting different payloads into the "Gifts" category.

---

## 🔍 Steps Taken  

### **1. Identify SQL Injection**
I injected:

'

The page displayed an SQL error → Confirmed vulnerability.

---

### **2. Check reflection in other categories**

I tested:

''

This reflected in the output, confirming the input is being processed raw.

---

### **3. Retrieve hidden, unreleased products**

Payload:

Gifts' ---

This commented out the rest of the query and returned only the unreleased items.

---

### **4. Retrieve *all* categories (released + hidden)**

Payload:

Gifts' +OR+1=1 --

This forced the query to return **all records**, bypassing category restrictions.

---

## 🔥 Final Result  
The application displayed all data → **Lab Solved**.

---

## 📝 Key Takeaways  

- A single quote (`'`) is enough to detect SQL injection.
- Using `--` comments out the remaining query.
- `OR 1=1` forces the database to return all rows.
- Good practice: always test how many columns exist before UNION attacks.

---

## ✔ Status  
Lab Completed successfully.
