# Splunk REX Command — Regex Extraction 

---

# 1. What is the REX Command?

`rex` stands for **Regular Expression Extraction**.

It is used to **extract patterns from raw log data**.

Many logs store information inside **unstructured text**, so `rex` helps convert that text into **structured fields**.

Simple idea:

```
Raw Log Text → Regex Pattern → Extract Field → Analyze Data
```

---

# 2. Why SOC Analysts Use REX

SOC analysts often deal with logs like:

```
User login failed from IP=192.168.1.10 user=admin port=22
```

But Splunk may not automatically extract:

- IP address
- username
- port

Using `rex`, we can extract them as fields.

---

# 3. Basic REX Syntax

```
| rex field=_raw "regex_pattern"
```

Important parts:

| Component | Meaning |
|---|---|
| rex | extraction command |
| field=_raw | search inside raw log text |
| regex_pattern | pattern used to extract data |

---

# 4. Named Field Extraction

In Splunk regex, we extract fields using:

```
(?<fieldname>pattern)
```

Example:

```
(?<ip>\d+\.\d+\.\d+\.\d+)
```

This extracts an **IP address**.

---

# 5. Example 1 — Extract Name from Logs

Search Query:

```spl
index=_internal sourcetype=splunkd
| rex field=_raw "name=(?<name>\w+)"
| table name
```

Explanation:

| Part | Meaning |
|---|---|
| name= | pattern start |
| (?<name>) | extracted field name |
| \w+ | any word characters |

Output Example:

| name |
|---|
| admin |
| system |
| scheduler |

---

# 6. Example 2 — Extract Multiple Fields

Suppose `_raw` log contains:

```
feature=login color=red
```

Query:

```spl
index=_internal sourcetype=splunkd
| rex field=_raw "feature=(?<feature>\w+)"
| rex field=_raw "color=(?<color>\w+)"
| table feature color
```

Output:

| feature | color |
|---|---|
| login | red |
| access | blue |

---

# 7. Extracting Multiple Fields in One Command

You can also extract multiple values in a **single rex command**.

Example:

```spl
index=_internal sourcetype=splunkd
| rex field=_raw "feature=(?<feature>\w+)\s+color=(?<color>\w+)"
| table feature color
```

---

# 8. Common Regex Patterns

| Pattern | Meaning |
|---|---|
| `\w+` | word characters |
| `\d+` | digits |
| `.` | any character |
| `.*` | anything |
| `\s` | space |

Example IP regex:

```
(?<ip>\d+\.\d+\.\d+\.\d+)
```

---

# 9. Real SOC Example — Extract IP Address

Log Example:

```
Failed login from 192.168.10.5 user=root
```

SPL Query:

```spl
index=authentication_logs
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| table ip
```

Output:

| ip |
|---|
| 192.168.10.5 |

This helps analysts detect:

- brute-force attacks
- suspicious IPs
- attacker infrastructure

---

# 10. Real SOC Example — Extract Username

Log:

```
user=ezabyss action=login status=failed
```

Query:

```spl
index=authentication_logs
| rex field=_raw "user=(?<username>\w+)"
| table username
```

Output:

| username |
|---|
| ezabyss |
| admin |

---

# 11. Combining REX with Other Commands

Example pipeline:

```spl
index=authentication_logs
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| stats count by ip
```

This helps identify:

```
Top attacking IP addresses
```

---

# 12. SOC Threat Hunting Example

Detect brute-force login attempts.

```spl
index=auth_logs
| rex field=_raw "user=(?<username>\w+)"
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| stats count by username ip
| sort -count
```

This shows:

| username | ip | attempts |
|---|---|---|
| admin | 185.x.x.x | 200 |

Possible **password brute-force attack**.

---

# 13. Memory Shortcut

Remember REX workflow:

```
R E X
```

```
Read raw log
Extract pattern
Create field
```

---

# 14. When to Use REX

Use `rex` when:

- fields are not automatically extracted
- logs are unstructured
- performing threat hunting
- extracting IPs, usernames, URLs

---

# Final Insight

In Splunk investigations:

```
rex = extract intelligence from raw logs
```

Without regex extraction, many important security indicators stay **hidden inside text logs**.

---

✍️ Notes By Abhishek (Ez Abyss)
