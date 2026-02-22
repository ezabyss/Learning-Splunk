# 📘 Splunk Log Search & Analysis

---

# 1️⃣ Introduction

Log search and analysis is one of the most critical capabilities of any SIEM platform.

Organizations collect massive amounts of log data daily.  
Without proper search and analysis:

- Logs are just stored data  
- Threats go unnoticed  
- Insights remain hidden  

Splunk provides powerful tools to:

- Search log data  
- Filter relevant events  
- Analyze patterns  
- Detect anomalies  
- Visualize trends  
- Automate responses  

---

# 2️⃣ Why Log Search & Analysis Matters

Log analysis enables organizations to:

- Detect security incidents  
- Investigate suspicious activity  
- Monitor system performance  
- Support forensic investigations  
- Make data-driven decisions  

> Collection gives visibility.  
> Search gives intelligence.

---

# 3️⃣ Splunk Search Processing Language (SPL)

Splunk uses its own query language called:

Splunk Processing Language (SPL)

SPL allows you to search, filter, transform, and analyze log data efficiently.

---

## 🔹 1. Basic Search Syntax

You can search using simple keywords or patterns.

Example:

`index=security failed login`

This searches for events containing the terms “failed” and “login” in the security index.

You can also search:

- Specific phrases  
- Patterns  
- Error codes  
- IP addresses  

---

## 🔹 2. Field Extraction

Splunk automatically extracts fields from structured and semi-structured logs.

Example extracted fields:

- host  
- source  
- sourcetype  
- status  
- user  
- IP  

This makes it easier to search specific attributes.

You can also define custom field extractions based on your log format.

---

## 🔹 3. Search Modifiers & Operators

SPL supports:

- Time range modifiers  
- Logical operators (`AND`, `OR`, `NOT`)  
- Wildcards (`*`)  
- Comparison operators (`=`, `>`, `<`)  

Example:

`index=security status=failed AND user=admin`

This narrows results to failed admin login attempts.

---

# 4️⃣ Log Search & Analysis Techniques

---

## 🔹 1. Filtering & Narrowing Down Data

You can filter based on:

- Time range  
- Host  
- Source  
- Event type  
- User  
- IP address  

Example:

`index=security host=server01`

Filtering reduces noise and focuses on relevant data.

---

## 🔹 2. Aggregation & Statistics

Splunk allows statistical analysis using built-in functions.

Common commands:

- `stats`
- `count`
- `avg`
- `sum`
- `min`
- `max`

Example:

`index=security | stats count by user`

This counts events grouped by user.

This helps identify:

- Suspicious users  
- Top error sources  
- Login frequency patterns  

---

## 🔹 3. Correlation & Time-Series Analysis

By correlating events across different sources, you can:

- Identify attack patterns  
- Detect lateral movement  
- Discover anomalies  
- Monitor performance trends  

Example:

`index=security | timechart count by status`

Time-series analysis helps detect unusual spikes in activity.

---

# 5️⃣ Visualization & Dashboards

Splunk provides powerful visualization capabilities.

---

## 🔹 1. Charts & Graphs

You can visualize data using:

- Bar charts  
- Line charts  
- Pie charts  
- Area charts  
- Tables  

Visualization helps identify:

- Trends  
- Distributions  
- Comparisons  

---

## 🔹 2. Interactive Dashboards

Dashboards allow:

- Consolidated log visibility  
- Custom panel arrangement  
- Real-time monitoring  

You can combine:

- Search results  
- Charts  
- Alerts  
- KPIs  

This creates a “single pane of glass” for SOC teams.

---

# 6️⃣ Alerting & Automation

Splunk enables proactive monitoring through alerts.

---

## 🔹 1. Alert Configuration

You can define:

- Search-based conditions  
- Threshold values  
- Statistical triggers  

Example condition:

If failed logins > 20 in 5 minutes

When condition is met:

- Alert is triggered  
- Security team is notified  

---

## 🔹 2. Automated Response Actions

Splunk supports automated actions such as:

- Sending email notifications  
- Triggering webhooks  
- Executing scripts  
- Creating tickets  
- Integrating with SOAR platforms  

This reduces:

- Manual response time  
- Human error  
- Incident handling delays  

---

# 7️⃣ Real-World SOC Scenario

## 🚨 Scenario: Suspicious Login Spike

Security team notices:

- Sudden spike in failed logins  
- Multiple IP addresses  
- Targeting admin accounts  

Using Splunk:

1. Search failed logins  
2. Aggregate by IP  
3. Visualize trend  
4. Correlate across systems  
5. Trigger alert  

Result:

- Early brute-force detection  
- Rapid containment  
- Reduced risk  

---

# 8️⃣ Key Benefits of Splunk Log Search

- Fast searching across massive datasets  
- Flexible filtering  
- Advanced statistical analysis  
- Correlation across log sources  
- Real-time monitoring  
- Automated alerting  
- Interactive dashboards  

---

# 9️⃣ Explanation

Splunk empowers organizations to search, filter, aggregate, correlate, and visualize log data using SPL. Through real-time monitoring, statistical analysis, dashboards, and automated alerting, it enables rapid threat detection and data-driven decision-making.

---

# 🔟 Memory Formula

Search → Filter → Aggregate → Correlate → Visualize → Alert → Automate

---

# 🔥 Final Takeaway

Log collection gives you data.  
Log search gives you intelligence.  
Log analysis gives you security.

Splunk transforms massive log data into meaningful, actionable insights that support threat detection, incident response, and operational excellence.

---

**✍️ Notes By Abhishek (Ez Abyss)**
