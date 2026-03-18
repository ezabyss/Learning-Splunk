# 📑 Splunk Report Creation — Hands-On Demo
### SOC Analyst Guide (Search + Data Model + Pivot)

This guide demonstrates how to **create, schedule, and manage reports in Splunk** using:

- uploaded dataset (CSV)
- SPL search queries
- Data Models + Pivot
- visualization reports

---

# 🎯 Objective

Build reports to analyze:

- backup activity data
- domain-based filtering
- time-based insights
- system search activity

---

# 📥 Step 1 — Upload Dataset

Upload CSV data into Splunk.

### Steps

1. Go to **Add Data**
2. Choose **Upload**
3. Select CSV file
4. Configure:

```
Source Type → CSV
Index → default / index1
Sourcetype → Data1
```

5. Click **Submit**

---

# 🔍 Step 2 — Search & Filter Data

Navigate to:

```
Search & Reporting
```

---

## Example Query

    index=index1
    | search domain="East US"
    | table backupduration backupvolume c0 date_hour date_mday date_minute destinationip

---

## Purpose

This query:

- filters data by domain
- selects relevant fields
- creates structured output for reporting

---

# 📊 Step 3 — Create Report from Search

After running the search:

```
Save As → Report
```

---

## Example Report Name

```
Backup Report for East US
```

---

## Output

- tabular data
- structured insights
- ready for scheduling or sharing

---

# ⏱️ Step 4 — Schedule the Report

Reports can be automated.

---

## Example Schedule

| Setting | Value |
|--------|------|
| Frequency | Weekly |
| Day | Monday |
| Time | 09:00 AM |

---

## Advanced Scheduling Options

- change execution day/time
- define time range (e.g., last 7 days)
- set priority
- configure execution window

---

## Key Benefit

```
Manual Analysis → Automated Reporting
```

---

# 📧 Step 5 — Add Actions (Automation)

Reports can trigger actions when executed.

---

## Available Actions

- send email (PDF/CSV)
- trigger alerts
- share reports

⚠ Requires Splunk Enterprise license for email automation.

---

# 📊 Step 6 — Export & Share Reports

Reports can be exported in multiple formats:

- CSV
- JSON
- XML

---

## Example Use

- share with team
- offline analysis
- audit reporting

---

# 🧩 Step 7 — Create Report Using Data Model (Pivot)

Instead of SPL, use **Pivot Tool**.

---

## Steps

1. Go to:

```
Settings → Data Models
```

2. Select:

```
Internal Server Logs
```

3. Click:

```
Pivot
```

---

## Example Configuration

- Dataset: Scheduler
- Rows: Time
- Columns: Search Name
- Values: Count

---

## Save as Report

```
Save As → Report
Name: Data Model Report Generated
```

---

# 📊 Step 8 — Enhance Report Visualization

Modify Pivot results:

- split by status (success/failure)
- add filters
- adjust grouping

---

## Visualization Options

- column chart
- line chart
- pie chart
- scatter plot

---

# Example

```
Search Activity by Time + Status
```

---

# 📈 Step 9 — Save Chart as Report

Each visualization can be saved separately.

---

## Example

```
Save As → Report
Name: Weekly Search Trends Chart
```

---

# ⏱️ Step 10 — Schedule Visualization Reports

Charts can also be scheduled.

---

## Example Schedule

| Frequency | Weekly |
|----------|--------|
| Time | 06:00 AM |
| Range | Last 7 Days |

---

## Result

- chart auto-generated
- updated insights
- ready for decision-making

---

# 🧱 Step 11 — Add Report to Dashboard

Reports can be reused.

```
Add to Dashboard Panel
```

---

## Benefit

```
Report → Dashboard → Unified Monitoring
```

---

# 📊 Reports vs Dashboards (Real Difference)

| Feature | Report | Dashboard |
|--------|--------|-----------|
| Execution | scheduled | real-time |
| Purpose | specific analysis | overall monitoring |
| Automation | yes | no |
| Output | snapshot | live data |

---

## Key Concept

```
Report → Scheduled Insight  
Dashboard → Continuous Monitoring
```

---

# 🛡️ SOC Use Cases

Reports are critical in SOC environments.

---

## Examples

| Use Case | Report Type |
|--------|-------------|
| Backup Monitoring | scheduled report |
| User Activity | audit report |
| Threat Detection | alert-based report |
| System Logs | weekly summary |

---

# 🚀 Key Takeaway

Splunk reports allow analysts to:

- automate analysis
- schedule insights
- share findings
- monitor trends over time

---

# 🧠 Final Insight

Splunk Reports transform:

```
Raw Data → Structured Analysis → Scheduled Insights
```

They are essential for:

- operational monitoring
- compliance reporting
- security analysis

---

# 📌 Pro Tip

Use:

- **Reports** → for automation  
- **Dashboards** → for monitoring  

Combining both creates a **powerful analytics system**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
