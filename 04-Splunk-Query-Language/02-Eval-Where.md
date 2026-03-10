# SPL Eval & Where Command
### Splunk Processing Language (SPL) | Filtering & Data Evaluation

---

# 1. Goal

By the end you should understand how to use:

- `eval` → create new fields or perform calculations  
- `where` → filter events using conditions

Simple idea:

```
Raw Logs → Evaluate Data → Filter Data → Analyze Results
```

These commands are **very common in SOC investigations**.

---

# 2. Example Dataset

Index used:

```
index=index1
```

Fields inside dataset:

| Field | Meaning |
|------|------|
| balance | account balance |
| duration | call duration (seconds) |
| contact | communication type |
| job | job type |
| education | education level |

---

# 3. The `eval` Command

The `eval` command is used to:

- create new fields
- perform calculations
- manipulate data
- transform values

Basic syntax:

```
| eval new_field = expression
```

---

# 4. Example 1 — Detect Balance Status

Goal:

Identify whether the account balance is:

- **insufficient**
- **positive**

SPL Query:

```spl
index=index1
| eval balance_value=case(balance<=0,"insufficient balance",true(),"positive balance")
| table balance balance_value
```

Explanation:

| Condition | Output |
|---|---|
| balance ≤ 0 | insufficient balance |
| balance > 0 | positive balance |

---

# 5. Example 2 — Convert Duration from Seconds to Minutes

The dataset stores duration in **seconds**.

We convert it to **minutes**.

SPL Query:

```spl
index=index1
| eval duration_minutes = duration/60
| table duration duration_minutes
```

Example:

| duration (seconds) | duration_minutes |
|---|---|
| 120 | 2 |
| 300 | 5 |

---

# 6. Example 3 — Convert Balance from Euros to Rupees

Assume:

```
1 Euro = 170.97 NPR
```

SPL Query:

```spl
index=index1
| eval balance_rupees = balance * 170.97
| table balance balance_rupees
```

---

# 7. Example 4 — Check Minimum Balance Requirement

Minimum balance required:

```
10,000 rupees
```

SPL Query:

```spl
index=index1
| eval balance_rupees = balance * 170.97
| eval balance_status = case(balance_rupees<=10000,"insufficient balance",true(),"positive balance")
| table balance balance_rupees balance_status
```

Example Output:

| balance | balance_rupees | status |
|---|---|---|
| 953 | 86647 | positive |
| 6 | 545 | insufficient |

---

# 8. Using the `where` Command

The `where` command filters events based on conditions.

Syntax:

```
| where condition
```

Example:

```
| where contact="cellular"
```

Meaning:

Only show events where **contact type is cellular**.

---

# 9. Example — Filter by Contact Type

SPL Query:

```spl
index=index1
| where contact="cellular"
| table contact balance duration
```

This removes:

```
telephone
unknown
```

---

# 10. Example — Multiple Conditions with `where`

You can filter using multiple fields.

Example:

- duration ≥ 250
- job = blue-collar

SPL Query:

```spl
index=index1
| eval balance_rupees = balance * 90.92
| eval difference_min_balance = balance_rupees - 10000
| where duration>=250 AND job="blue-collar"
| table education difference_min_balance balance duration job
```

---

# 11. Real SOC Example

Imagine monitoring login events.

We want to detect:

- suspicious login duration
- specific job roles
- unusual activity

Example SPL:

```spl
index=authentication_logs
| eval session_minutes=session_duration/60
| where session_minutes>60 AND user_role="admin"
```

Meaning:

```
Show admin sessions longer than 1 hour
```

Possible indicators:

- compromised admin account
- persistence activity
- lateral movement

---

# 12. Combining SPL Commands (Pipeline)

Splunk queries follow a pipeline model:

```
search → eval → where → table
```

Example pipeline:

```spl
index=index1
| eval balance_rupees = balance*90.92
| eval duration_minutes = duration/60
| where contact="cellular"
| table balance_rupees duration_minutes contact
```

---

# 13. Memory Shortcut

Remember SPL workflow:

```
E W T
```

```
Eval → create fields
Where → filter data
Table → display results
```

---

# 14. Why SOC Analysts Use These Commands

SOC analysts use `eval` and `where` to:

- detect suspicious behavior
- transform log data
- filter relevant security events
- build dashboards
- perform threat hunting

---

# Final Insight

In Splunk investigations:

```
eval = data transformation
where = data filtering
```

Together they allow analysts to convert raw logs into **actionable security insights**.

---

✍️ Notes By Abhishek (Ez Abyss)
