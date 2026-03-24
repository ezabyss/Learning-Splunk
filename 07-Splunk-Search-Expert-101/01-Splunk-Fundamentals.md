# 🧠 Splunk Fundamentals

---


# 🎯 Splunk in 1 line

```
Splunk = Tool that turns machine data into useful insights
```

---

# 🧠 Core Idea

Think of Splunk like:

🕵️ **A Smart Detective**

- collects clues (logs)
- organizes them
- finds patterns
- alerts you if something is wrong

---

# 🔄 Full Workflow

```
Data → Index → Search → Analyze → Alert → Dashboard
```
---

# 🏗️ 1. Index (Heart of Splunk)

### Simple Meaning

```
Index = Where data is stored
```

---

### Real World Example

👉 Like Google:

- Internet = raw data  
- Google Index = stored/searchable data  

👉 Splunk:

- Logs = raw data  
- Index = searchable storage  

---

# 🏷️ 2. Sourcetype (VERY IMPORTANT)

### Meaning

```
Sourcetype = How Splunk understands data format
```

---

### Real Example

| Data | Sourcetype |
|------|----------|
| Website logs | apache |
| Linux logs | syslog |

---

### Memory Trick

```
Sourcetype = "Language of data"
```

---

# 📦 3. Events

### Meaning

```
Event = Single log entry
```

---

### Example

```
User login failed at 10:05
```

👉 That is ONE event

---

# ⏱️ 4. Timestamp

### Meaning

```
Time when event happened
```

---

### Why Important?

- helps track timeline  
- helps detect attacks  

---

# 🔍 5. Search (SPL)

### Meaning

```
SPL = Language used to search data
```

---

### Example

```
index=web_logs status=404
```

👉 Finds all error pages

---

### Real SOC Example

```
index=auth_logs status=failed
```

👉 Detect failed logins

---

# 📊 6. Analysis

### Example

```
| stats count by user
```

👉 Count activity per user

---

### Real World

👉 Find:

- suspicious users  
- unusual behavior  

---

# 🚨 7. Alerts

### Meaning

```
Alert = Automatic warning when condition is met
```

---

### Real Example

```
If failed logins > 10 → Alert
```

---

### SOC Example

👉 Brute force attack detection

---

# 📑 8. Reports

### Meaning

```
Report = Saved summary of data
```

---

### Example

👉 Weekly login report

---

# 📊 9. Dashboards

### Meaning

```
Dashboard = Visual overview of data
```

---

### Real Example

👉 SOC screen showing:

- attacks  
- logs  
- alerts  

---

# 🧠 Knowledge Objects (Smart Layer)

### Purpose

```
Make data easier to understand
```

---

### Includes

- fields  
- tags  
- lookups  
- reports  

---

# 🔥 Real World Scenario (IMPORTANT)

---

## Scenario: Brute Force Attack

### Step 1 — Data

Logs show login attempts

---

### Step 2 — Search

```
index=auth_logs status=failed
```

---

### Step 3 — Analysis

```
| stats count by user
```

---

### Step 4 — Condition

```
count > 10
```

---

### Step 5 — Alert

🚨 Trigger alert

---

### Step 6 — Action

- block IP  
- notify admin  

---

# ⚡ Why Splunk is Powerful

---

## Without Splunk ❌

- manual log checking  
- slow  
- errors  

---

## With Splunk ✅

- automated monitoring  
- fast detection  
- real-time alerts  

---

# 🧠 Learning Tricks

---

## 🔑 1. Remember Flow

```
Data → Index → Search → Alert
```

---

## 🔑 2. Ask This Always

```
What am I detecting?
Why does it matter?
What action should follow?
```

---

## 🔑 3. Think Like SOC

Not:

❌ "What is this command?"

But:

✅ "What attack can I detect with this?"

---

# 📌 Final Summary (REVISION)

---

## Splunk in One Sentence

```
Splunk collects, searches, analyzes, and alerts on machine data
```

---

## Most Important Concepts

- Index = storage  
- Sourcetype = data format  
- SPL = search language  
- Alerts = detection  
- Dashboard = monitoring  

---

# 🚀 Final Insight

```
Logs → Intelligence → Security Decisions
```

---

**✍️ Notes By Abhishek (Ez Abyss)**
