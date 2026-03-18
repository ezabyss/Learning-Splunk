# 🚨 Splunk Alerts 
### SOC Detection & Real-Time Monitoring

Splunk alerts enable analysts to **automatically detect and respond to important events** in real time.

---

# 🎯 Objective

Detect critical events and trigger actions:

```
Data → Condition → Alert → Action
```

---

# 🧠 Concept

Think of alerts as:

🛡️ **Security Guards for Your Data**

Instead of watching logs manually:

- Splunk monitors continuously  
- detects unusual activity  
- notifies you instantly  

---

# ⚙️ What is a Splunk Alert?

A **Splunk Alert** is a saved search that:

- runs automatically  
- checks conditions  
- triggers actions when conditions are met  

---

## Key Formula

```
Scheduled Search + Condition = Alert
```

---

# 📊 Alert Types

---

## ⏱️ Scheduled Alert

- runs at fixed intervals  
- checks for conditions periodically  

---

## ⚡ Real-Time Alert

- runs continuously  
- triggers immediately when condition is met  

---

# 🔍 Step-by-Step Alert Creation

---

## 1️⃣ Create Search Query

Go to:

```
Search & Reporting
```

---

### Example Query

    index=_internal
    | table component log_level date_wday

---

---

## 2️⃣ Save as Alert

Click:

```
Save As → Alert
```

---

## 3️⃣ Configure Alert

---

### Example Settings

| Setting | Value |
|--------|------|
| Title | Internal Error Log Alert |
| Type | Real-time |
| Expiration | 24 hours |
| Severity | Critical |

---

---

## 4️⃣ Define Trigger Condition

---

### Example Condition

```
log_level="error"
```

---

### Trigger Options

| Option | Meaning |
|-------|--------|
| Per Result | triggers for each event |
| Once | triggers once |
| Threshold | triggers when limit reached |

---

---

## 5️⃣ Save Alert

After saving:

- Splunk monitors continuously  
- triggers alert when condition matches  

---

# 📈 Demo Insight

---

## Example Scenario

Initial condition:

```
log_level="error"
```

---

### Observation

- no alerts triggered ❌  
- because error events are rare  

---

## Testing Condition

Changed to:

```
log_level="info"
```

---

### Result

- alerts triggered continuously ✅  
- because "info" logs occur frequently  

---

# ⚠️ Important Learning

```
Condition sensitivity determines alert frequency
```

---

# 🔄 Alert Behavior

Once enabled:

- alert runs continuously  
- triggers based on condition  
- keeps firing until disabled  

---

# 🛑 Disabling Alerts

Always disable unused alerts.

---

## Why?

- reduces system load  
- avoids alert fatigue  
- prevents unnecessary triggers  

---

# 🛡️ SOC Use Cases

---

## 🚨 Failed Login Detection

```
index=auth_logs status=failed
```

---

## 🧠 Brute Force Attack

```
index=auth_logs
| stats count by user
| where count > 10
```

---

## ⚠️ Error Monitoring

```
index=_internal log_level=error
```

---

## 🌐 Suspicious IP Activity

```
index=network_logs
| stats count by src_ip
| where count > 100
```

---

# 🚀 Alert Actions

Alerts can trigger:

- 📧 email notifications  
- 📊 dashboard updates  
- 📁 log exports  
- 🔗 webhook/API calls  

---

# ⚡ Best Practices

---

## 🎯 Use Correct Conditions

- too strict → no alerts  
- too loose → alert spam  

---

## ⏱️ Choose Right Type

| Scenario | Type |
|--------|------|
| real-time threats | real-time |
| periodic analysis | scheduled |

---

## 🔒 Avoid Alert Fatigue

- limit triggers  
- use thresholds  
- group alerts  

---

## 📊 Add Severity Levels

| Level | Meaning |
|------|--------|
| Low | informational |
| Medium | suspicious |
| High | threat |
| Critical | immediate action |

---

# 🔄 Alerts vs Reports vs Dashboards

| Feature | Alerts | Reports | Dashboards |
|--------|-------|--------|-----------|
| Purpose | detection | summary | monitoring |
| Execution | automatic | scheduled/manual | real-time |
| Output | trigger/action | structured data | visualization |

---

# 🧠 Key Insight

```
Alerts = Action  
Reports = Insight  
Dashboards = Visibility
```

---

# 📌 Final Takeaway

Splunk alerts transform:

```
Passive Monitoring → Active Detection
```

They are essential for:

- SOC operations  
- threat detection  
- real-time response  

---

# 🔥 Pro Insight

A mature SOC system uses:

```
Scheduled Searches → Alerts → Dashboards → Reports
```

This creates a **fully automated security pipeline**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
