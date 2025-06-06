## 🔐 Lab: SQL Injection Vulnerability Allowing Login Bypass

**Objective**: Perform a SQL injection attack to bypass the login mechanism and gain unauthorized access.

---

### 📝 Description

This lab demonstrates a **SQL injection vulnerability** in a login form. When a user submits a username and password, the application builds a SQL query like:

```sql
SELECT * FROM users WHERE username = 'user' AND password = 'pass'
```

A malicious attacker can inject SQL code into the input fields to manipulate the query and bypass authentication altogether.

---

### 💥 Injection Payload Used

```sql
' OR 1=1--
```

This payload bypasses the password check by transforming the query into:

```sql
SELECT * FROM users WHERE username = '' OR 1=1--' AND password = ''
```

Since `1=1` is always true, the application logs the attacker in **without needing valid credentials**.

---

### 📸 Screenshots

#### 🔹 SQL Injection Entered into Login Form

![SQL injection attack to bypass login](images/SQL%20injection%20vulnerbility%20to%20bypass%20login.png)

#### 🔹 Result After Login Bypass

![Result of SQL login injection](images/Result%20of%20SQL%20login%20injection.png)

---

### ✅ Outcome

- Login was bypassed successfully.
- The lab was marked as **Solved**.
- Unauthorized access was granted using only SQL injection.

---

### 🛡️ Remediation

To prevent SQL injection:

- Use **parameterized queries (prepared statements)**.
- Escape and validate all user inputs.
- Apply **least privilege** access to database accounts.
- Implement logging and monitoring on authentication endpoints.
