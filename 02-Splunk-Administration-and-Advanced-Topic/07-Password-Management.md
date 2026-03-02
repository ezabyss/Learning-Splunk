# 📘 Splunk Password Management & Security Policy

---

# 1️⃣ Learning Objective

By the end, you will understand:

- How password policies work in Splunk
- How to configure password complexity rules
- Password expiration settings
- Password history enforcement
- Login lockout settings
- Security best practices for internal authentication

---

# 2️⃣ Where to Configure Password Policy

Navigate to:

Settings → Access Controls → Password Management

⚠ Important:
These settings apply ONLY to **Internal Splunk Authentication**.
They do NOT apply to:

- LDAP authentication
- SAML authentication

---

# 3️⃣ Password Complexity Rules

You can define:

- Minimum password length
- Required numerals
- Required lowercase characters
- Required uppercase characters
- Required special characters

---

## 🔹 Default Setting

Minimum length: `8 characters`

Other requirements: `0`

Meaning:

- Password can contain anything
- No required numbers
- No required uppercase
- No required special characters
- Only minimum length enforced

---

## 🔹 Example Secure Configuration

Minimum characters: `8`  
Minimum numerals: `1`  
Minimum uppercase: `1`  
Minimum special characters: `1`  
Lowercase: optional  

Example valid password:

`Admin@123`

---

## 🔹 Recommended Enterprise Policy

Minimum length: `12+`  
At least:

- 1 uppercase
- 1 lowercase
- 1 number
- 1 special character

Stronger example:

`Splunk$Secure2026`

---

# 4️⃣ Password Expiration Policy

You can enable automatic expiration.

---

## 🔹 Configuration Options

- Days until password expires
- Warning days before expiration

Example:

Password expires in `90 days`  
Warning shown `15 days` before expiration  

After 90 days → user must change password.

---

## 🔹 When to Use Expiration

✔ Enterprise environments  
✔ Compliance requirements  
✔ High-security deployments  

Not always required for small lab setups.

---

# 5️⃣ Password History Policy

Prevents users from reusing old passwords.

---

## 🔹 Example Configuration

Password history count: `10`

Meaning:

User cannot reuse any of their last 10 passwords.

This prevents:

- Password cycling
- Weak password reuse
- Security loopholes

---

## 🔹 Why This Matters

Without history enforcement:

User could change:

Password1 → Password2 → Password1 again

With history enforcement:

System blocks reuse of previous passwords.

---

# 6️⃣ Login Settings & Account Lockout

Critical for brute-force protection.

---

## 🔹 Failed Login Attempts

Default:

- Failed attempts allowed: `5`
- Lockout threshold window: `5 minutes`
- Lockout duration: `30 minutes`

---

## 🔹 What This Means

If a user fails login 5 times within 5 minutes:

→ Account is locked  
→ Must wait 30 minutes before retrying  

Prevents:

- Brute-force attacks
- Credential stuffing
- Automated login abuse

---

## 🔹 Login Delay Setting

Optional delay (0–5 seconds)

Adds slight delay between login attempts.

Useful for slowing automated attacks.

---

# 7️⃣ Security Impact Summary

| Setting | Purpose |
|----------|----------|
| Complexity Rules | Prevent weak passwords |
| Expiration | Force periodic password rotation |
| History | Prevent reuse |
| Lockout | Stop brute-force attacks |
| Delay | Slow automated attempts |

---

# 8️⃣ Internal vs External Authentication

These password rules apply ONLY when:

Authentication Method = Internal

If using:

- LDAP
- SAML (SSO)

Then password policy is controlled externally.

---

# 9️⃣ Real-World Example (Enterprise Setup)

Company Policy:

- 12-character minimum
- 1 uppercase
- 1 lowercase
- 1 number
- 1 special character
- 90-day expiration
- 10-password history
- 5 failed attempts lockout

This creates:

Secure internal authentication environment.

---

# 🔟 Best Practices

✔ Use strong password complexity rules  
✔ Enable account lockout  
✔ Enable password history  
✔ Use expiration in regulated industries  
✔ Avoid over-restrictive rules for small labs  
✔ Document all policy changes  

---

# 🔥 Brief Explanation

Splunk allows administrators to configure password management policies for internal authentication. This includes password complexity enforcement, expiration rules, password history tracking, and login lockout settings. These controls enhance security by preventing weak passwords, password reuse, and brute-force attacks. However, these policies apply only to internal Splunk authentication and not to LDAP or SAML-based external authentication systems.

---

# 🚀 Final Takeaway

Password policy = First line of defense.

Weak passwords → System compromise  
Strong policies → Hardened Splunk environment  

Security starts with authentication.

---

**✍️ Notes By Abhishek (Ez Abyss)**
