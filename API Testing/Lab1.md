# Lab: Exploiting an API Endpoint Using Documentation

**Level:** Apprentice  
**Status:** ✅ Solved  
**Objective:** Find the exposed API documentation and delete user `carlos`.  
**Credentials:**

- **Username:** `wiener`
- **Password:** `peter`

---

## 🧠 Required Knowledge

To complete this lab, you should understand:

- What API documentation is
- How API documentation can be exposed and leveraged
- How to discover API documentation endpoints

These concepts are covered in the [PortSwigger API Testing Academy](https://portswigger.net/web-security/api).

---

## 🛠️ Steps to Reproduce the Exploit

1. **Log in** to the application using the credentials `wiener:peter`.

2. **Update your email address** from the account settings page.

3. In **Burp Suite**, go to `Proxy > HTTP history`:

   - Locate the request: `PATCH /api/user/wiener`
   - Right-click and **Send to Repeater**

4. In the **Repeater tab**:

   - Send the request as-is to confirm it returns user data
   - Remove `/wiener` from the path (so it becomes `/api/user`) and resend – expect an error
   - Now remove `/user` from the path (just `/api`) and send again

5. The `/api` endpoint returns **API documentation**.

6. **Right-click** the response → **Show response in browser**

   - Copy the temporary URL and **open it in Burp’s browser**

7. You’ll see an **interactive API documentation page**.

8. Scroll to the `DELETE` row, **enter `carlos`** as the user to delete.

9. Click **Send request** – Carlos is deleted and the lab is solved.

---

## 🧾 Screenshot

![Picture of deleting a user through API endpoint](images/lab1%20screenshot.png)

```md
Let me know if you want me to generate this into a downloadable `.md` file too!
```
