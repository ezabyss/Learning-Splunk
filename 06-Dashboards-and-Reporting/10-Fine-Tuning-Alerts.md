# 🎯 Splunk Alert Fine-Tuning & Triggering
### SOC Detection Engineering Guide (Advanced Level)

Fine-tuning alerts is what separates:

```
Beginner Analyst ❌  
SOC Engineer ✅
```

---

# 🎯 Objective

Optimize alerts to:

- reduce false positives  
- avoid alert fatigue  
- detect real threats efficiently  

---

# 🧠 Core Concept

Think of alerts like a **telescope 🔭**:

- Poor tuning → too many signals (noise)  
- Over-strict → miss real threats  

---

## Goal

```
Right Alert = Right Time + Right Condition
```

---

# ⚙️ Why Fine-Tuning Matters

Without tuning:

- 🚨 too many alerts → ignored  
- ❌ missed threats → security risk  

---

## With tuning:

- 🎯 precise detection  
- ⚡ faster response  
- 🧠 meaningful insights  

---

# ⏱️ 1️⃣ Alert Types (Control WHEN it runs)

---

## 📅 Scheduled Alerts

Runs at defined intervals.

---

### Options

| Frequency | Example |
|----------|--------|
| Every hour | system monitoring |
| Daily | reports |
| Weekly | compliance |

---

## ⚡ Real-Time Alerts

Runs continuously.

---

### Use Case

```
Critical threat detection
```

---

### Expiration Setting

Define how long alert stays active:

- seconds
- minutes
- hours
- days

---

# 🎯 2️⃣ Trigger Conditions (Control WHAT triggers)

---

## 🔹 Per Result

```
Triggers for every matching event
```

⚠ Can cause alert flooding

---

## 🔹 Number of Results

Triggers based on count.

---

### Example

```
Trigger if results > 10
```

---

### Use Case

- brute force detection  
- anomaly detection  

---

## 🔹 Number of Hosts

```
Trigger if affected hosts > threshold
```

---

## 🔹 Number of Sources

```
Trigger based on multiple data sources
```

---

## 🔹 Custom Condition

Most powerful option.

---

### Example

```
log_level="error"
```

---

# 🎚️ 3️⃣ Fine-Tuning Strategy

---

## 🎯 Adjust Sensitivity

| Scenario | Setting |
|--------|--------|
| Too many alerts | increase threshold |
| Missed alerts | decrease threshold |

---

## 🧠 Example

### Bad Alert ❌

```
log_level="info"
```

→ triggers constantly

---

### Good Alert ✅

```
log_level="error"
```

→ triggers only on real issues

---

# 🔄 4️⃣ Trigger Modes

---

## 🔹 Trigger Once

- fires only once  
- prevents spam  

---

## 🔹 Trigger Per Result

- fires for each event  
- useful for critical alerts  

---

# ⚡ 5️⃣ Alert Actions (What happens AFTER trigger)

---

## Available Actions

- 📧 Send Email  
- 📊 Add to Triggered Alerts  
- 📁 Output to Lookup  
- 🧠 Run Custom Script  

---

## Example Flow

```
Condition Met → Alert Triggered → Email Sent
```

---

# 🛡️ SOC Use Cases

---

## 🚨 Brute Force Detection

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

## 🌐 Suspicious Traffic

```
index=network_logs
| stats count by src_ip
| where count > 100
```

---

# 🔄 Alert Lifecycle

---

## Flow

```
Create → Enable → Trigger → Monitor → Disable (if not needed)
```

---

## ⚠️ Important

Always disable unused alerts:

- reduces noise  
- saves resources  
- prevents confusion  

---

# 📊 Alert Management

---

## View Alerts

```
Settings → Alerts
```

---

## Actions Available

- edit alert  
- enable/disable  
- change permissions  
- view results  

---

# 🧠 Pro SOC Insights

---

## 🔥 Rule #1 — Avoid Alert Fatigue

Too many alerts = ignored alerts

---

## 🔥 Rule #2 — Use Thresholds

Never rely only on:

```
per result triggers
```

---

## 🔥 Rule #3 — Tune Based on Data

- test conditions  
- adjust continuously  

---

## 🔥 Rule #4 — Prioritize Severity

| Level | Action |
|------|-------|
| Low | monitor |
| Medium | investigate |
| High | respond |
| Critical | immediate action |

---

# ⚖️ Balance is Everything

```
Too Loose → Noise  
Too Strict → Missed Threats  
Perfect → Actionable Intelligence
```

---

# 📌 Final Takeaway

Fine-tuned alerts transform:

```
Raw Logs → Smart Detection → Security Intelligence
```

---

# 🚀 SOC Architecture Insight

```
Scheduled Searches → Alerts → Dashboards → Reports
```

This creates a:

🛡️ **Fully Automated Security Monitoring System**

---

**✍️ Notes By Abhishek (Ez Abyss)**
