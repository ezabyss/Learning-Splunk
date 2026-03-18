# ⏱️ Scheduled Searches in Splunk
### SOC Automation & Continuous Monitoring Guide

Scheduled searches allow Splunk to **automatically run queries at defined intervals** — eliminating manual effort.

---

# 🎯 Objective

Automate data analysis to:

- monitor systems continuously
- generate periodic insights
- detect patterns without manual searching

---

# 🧠 Concept

Think of scheduled searches as:

```
Manual Search → Automated Execution → Continuous Insights
```

Splunk acts like a **smart detective** that:

- scans data regularly
- finds patterns
- updates results automatically

---

# ⚙️ What is a Scheduled Search?

A **scheduled search** is a saved SPL query that runs:

- automatically
- at a defined time interval
- without user interaction

---

## Key Idea

```
Search + Schedule = Automated Intelligence
```

---

# 📊 Real-World Example

### Scenario

You want to track:

```
Number of website visitors every day
```

---

### Without Scheduling

- manually run search every day ❌

---

### With Scheduling

- Splunk runs search automatically ✅
- generates results daily ✅

---

# 🔍 Step-by-Step Demo

---

## 1️⃣ Create Search Query

Go to:

```
Search & Reporting
```

---

### Example Query

    index=_internal
    | table component date_month date_wday log_level

---

### Time Range

```
Last 24 hours
```

---

## 2️⃣ Save Search as Report

Click:

```
Save As → Report
```

---

### Example Name

```
Internal Logs Report
```

---

## 3️⃣ Enable Scheduling

Go to:

```
Edit → Schedule
```

---

### Example Configuration

| Setting | Value |
|--------|------|
| Frequency | Every Hour |
| Time | 30 minutes past the hour |

---

## Example

```
Runs at: 1:30, 2:30, 3:30...
```

---

# 🔄 How It Works

Once scheduled:

1. Splunk executes query automatically  
2. Results are generated  
3. Report is updated  

---

## Behind the Scenes

```
Saved Search → Runs Automatically → Updates Report
```

---

# 📈 Output Behavior

- results refresh at scheduled time
- no manual execution required
- consistent monitoring

---

# ⚡ Key Insight

Scheduled searches power:

- reports
- alerts
- automation workflows

---

# 🛡️ SOC Use Cases

---

## 🔍 Log Monitoring

```
index=_internal | stats count by log_level
```

Track system activity regularly.

---

## 🚨 Suspicious Activity Detection

```
index=auth_logs status=failed
```

Run every 5–15 minutes.

---

## 📊 System Health Monitoring

- CPU usage
- memory logs
- service status

---

## 📑 Compliance Reporting

- daily audit logs
- weekly summaries

---

# ⏱️ Scheduling Types

| Frequency | Use Case |
|----------|--------|
| Every 5 min | real-time monitoring |
| Hourly | system tracking |
| Daily | reports |
| Weekly | compliance |

---

# 🚀 Benefits

---

## Automation

```
No manual effort required
```

---

## Consistency

- same query
- same timing
- reliable output

---

## Time Saving

Analysts focus on:

- investigation
- decision making

---

## Scalability

Handles:

- large datasets
- continuous monitoring

---

# ⚠️ Important Notes

- scheduled searches run in background
- same SPL query is reused
- results depend on time range selected

---

# 🔄 Scheduled vs Manual Search

| Feature | Scheduled | Manual |
|--------|----------|--------|
| Execution | automatic | manual |
| Effort | low | high |
| Use Case | monitoring | investigation |

---

# 🧠 Pro Insight 

Scheduled searches are the **foundation of alerts**.

```
Scheduled Search + Condition = Alert
```

---

# 📌 Final Takeaway

Scheduled searches transform:

```
Reactive Analysis → Proactive Monitoring
```

They are essential for:

- SOC automation
- real-time awareness
- continuous security monitoring

---

# 🔥 Next Step

Combine scheduled searches with:

- alerts 🚨  
- dashboards 📊  
- reports 📑  

to build a **full SOC monitoring system**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
