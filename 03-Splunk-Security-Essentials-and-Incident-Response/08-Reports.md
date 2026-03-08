# Splunk Security Essentials (SSE) — Reports

---

# 1. What are Reports in Splunk Security Essentials?

Reports in Splunk are **saved searches that generate structured outputs and visualizations**.

They help analysts:

- summarize security data
- analyze patterns
- visualize trends
- support investigations

Simple idea:

```
Search Query → Process Data → Generate Report
```

Reports allow security teams to **regularly monitor security information without running manual searches every time**.

---

# 2. Where to Find Reports in SSE

To access reports:

```
Advanced → Reports
```

Inside the Reports section you can:

- view existing reports
- edit reports
- run reports
- modify report queries
- add reports to dashboards

Most reports inside SSE are **system-generated reports** provided by the application.

---

# 3. Types of Reports in SSE

Reports inside Splunk Security Essentials usually include:

- **Data availability reports**
- **Security detection reports**
- **Content mapping reports**
- **Security analytics reports**

These reports help security teams understand:

- which data sources exist
- which detections are active
- how security content is mapped

---

# 4. Example Report: Data Availability ML Model

One example report is:

```
Generate Data Availability ML Model
```

Purpose:

- analyze available security data
- check which datasets are present
- visualize data availability

Reports often display:

- charts
- graphs
- tables
- raw event data

---

# 5. Report Visualization

When a report runs, it displays:

```
Visualization (chart/graph)
+
Data table
```

Example outputs:

| Time | Event Count |
|-----|-----|
| 10:00 | 52 |
| 10:05 | 73 |

This helps analysts quickly understand **patterns and trends in security data**.

---

# 6. Editing Reports

Reports can be customized.

You can modify:

- search queries
- report descriptions
- report permissions
- time range
- visualization format

Example time change:

```
Last 24 hours → All Time
```

This changes the dataset used to generate the report.

---

# 7. Viewing the Report Query

Each report is powered by a **Splunk search query**.

Example actions:

```
Open in Search
```

This allows analysts to:

- see the full SPL query
- understand how the report works
- modify the query

Example query components include:

```
eval
where
rename
table
```

These commands help process and structure the report data.

---

# 8. Example Query Logic

Example operations used in reports:

### Eval

Creates new fields.

Example:

```
eval datasource=name . ":" . data_component
```

This combines two fields into one.

Example result:

```
pod:pod_enumeration
```

---

### Rename

Renames fields for better readability.

Example:

```
rename name as data_component
```

---

### Table

Selects which columns appear in the report.

Example:

```
table id name description
```

---

# 9. Understanding the Filldown Command

Another command mentioned in the report query is:

```
filldown
```

Purpose:

```
Replace null values with the last non-null value
```

Example:

| Time | User |
|-----|-----|
| 10:00 | Admin |
| 10:01 | NULL |

After `filldown`:

| Time | User |
|-----|-----|
| 10:00 | Admin |
| 10:01 | Admin |

This keeps reports **clean and consistent**.

---

# 10. Modifying Reports

When editing a report, analysts can:

- remove columns
- add fields
- adjust filters
- change visualization

After modifications you can:

```
Save as new report
Add to dashboard
Update existing report
```

If you do not save changes, the original report remains unchanged.

---

# 11. System Reports vs User Reports

In Splunk reports are divided into two categories.

### System Reports

These come **prebuilt with the SSE application**.

Examples:

- security detection reports
- dataset reports
- content mapping reports

---

### User Reports

These are **custom reports created by analysts**.

They appear under:

```
Reports → Yours
```

If no custom reports exist, this section will be empty.

---

# 12. Why Reports are Important in SOC Operations

Reports help SOC teams:

- monitor security trends
- summarize investigation results
- analyze security events
- generate operational insights

Instead of manually searching logs, analysts can use reports to **quickly review important security metrics**.

---

# 13. Real SOC Example

Imagine a SOC team monitoring authentication logs.

A report might show:

| User | Failed Logins |
|------|------|
| user1 | 35 |
| user2 | 2 |

This report immediately highlights:

```
Possible brute-force attack against user1
```

The analyst can then investigate further.

---

# Memory Shortcut

To remember report capabilities:

```
R E V I E W
```

```
Run saved searches
Edit queries
Visualize data
Investigate patterns
Export insights
Watch security trends
```

---

# Final Insight

Reports in Splunk Security Essentials transform raw search queries into **structured security intelligence**.

They allow security teams to:

```
monitor threats
analyze data
visualize patterns
support SOC investigations
```

Reports are a key part of building **effective security monitoring workflows** in Splunk.

---

✍️ Notes By Abhishek (Ez Abyss)
