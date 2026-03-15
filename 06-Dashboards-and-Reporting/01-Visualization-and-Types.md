# 📊 Splunk Visualization Fundamentals & Data Models
### SOC Analyst Guide

Data visualization plays a critical role in **data analysis, security monitoring, and decision-making**. Raw log data is often difficult to interpret directly, especially for non-technical users.

Visualization transforms raw data into **clear insights that humans can easily understand**.

Instead of analyzing thousands of log entries, visualizations allow analysts to quickly detect:

- trends
- patterns
- anomalies
- system behavior changes

---

# 🧠 Why Data Visualization Matters

Raw data alone is not always useful for decision-making.

Example search query:

    index=_internal

Running this query produces **raw tabular data**, which can be difficult for many users to interpret.

### Raw Data Challenges

| Problem | Explanation |
|--------|-------------|
| Too much information | Raw logs contain excessive detail |
| Difficult interpretation | Non-technical users struggle with raw events |
| Hidden patterns | Trends are difficult to see manually |

Visualization solves these problems by converting data into **human-friendly graphical formats**.

---

# 👁️ Human-Centric Data Understanding

Humans naturally recognize **patterns and visual relationships**.

Visualization allows users to:

- detect anomalies faster
- understand relationships between data fields
- interpret large datasets quickly

This is why **visual analytics is essential in modern data platforms like Splunk**.

---

# 📚 Visualization Vocabulary

Before building visualizations, it is important to understand key concepts.

---

# 1️⃣ Dimensions

A **dimension** represents a field used to categorize or group data.

Think of a cube.

A cube has three dimensions:

- height
- width
- depth

In data analysis, dimensions represent **attributes used to measure or organize data**.

Example dimensions:

| Dimension | Description |
|----------|-------------|
| date/time | when an event occurred |
| customer | who performed an action |
| product | item purchased |

---

# 2️⃣ Measures

Measures represent **quantifiable values**.

Examples:

| Measure | Example |
|-------|---------|
| purchase price | $100 |
| duration | 20 seconds |
| event count | 150 events |

Measures are typically used in **aggregations and visualizations**.

---

# 3️⃣ Grain (Level of Detail)

Grain represents the **lowest level of detail required by the business**.

Example grain:

```
One Date + One Customer + One Purchase Price
```

Each unique combination represents **one record in the dataset**.

When aggregated, multiple records combine into higher-level insights.

---

# 📦 What is a Dataset in Splunk?

A **dataset** is a collection of structured data used for analysis.

Datasets are typically managed by **Splunk Knowledge Managers**.

They define datasets for specific business or analytical purposes.

Example dataset fields:

| Field | Description |
|------|-------------|
| customer_id | customer identifier |
| purchase_date | transaction date |
| purchase_price | purchase value |

---

# 🧩 What is a Data Model in Splunk?

A **Data Model** is a structured representation of relationships between different datasets.

It allows analysts to interact with data **without needing complex SPL queries**.

Data models are created and maintained by **Knowledge Managers**.

Benefits:

- simplifies complex data
- organizes relationships between fields
- supports visual analysis

---

# ⚙️ Where to Find Data Models in Splunk

You can access data models by navigating to:

```
Settings → Data Models
```

Splunk will display a list of available data models.

These models can then be used for:

- reporting
- dashboards
- visualizations
- pivot analysis

---

# 🔄 Using Data Models for Visualization

Instead of writing SPL queries manually, analysts can use **Pivot**.

Pivot allows users to:

- explore datasets visually
- build charts without SPL
- generate reports easily

This enables **non-technical users** to create visualizations.

Example workflow:

```
Data Model → Pivot Tool → Visualization → Dashboard
```

---

# 🎯 Designing Effective Visualizations

When building dashboards, analysts should consider:

### Audience

Different users need different types of visualizations.

| Audience | Example Visualization |
|---------|-----------------------|
| Executives | high-level dashboards |
| SOC Analysts | detailed event charts |
| Operations Teams | system performance graphs |

---

### Goal of the Dashboard

Ask:

- What message should the visualization communicate?
- Is it meant to inform, monitor, or analyze?

Clear goals lead to better dashboards.

---

# 📈 Visualization Types in Splunk

Splunk provides multiple visualization options.

---

# 1️⃣ Pie Chart

Shows proportional distribution.

Example:

```
Authentication Events by Source
```

---

# 2️⃣ Line Chart

Shows how values change over time.

Best for:

- time-series analysis
- monitoring trends

---

# 3️⃣ Area Chart

Similar to a line chart but highlights **aggregated data over time**.

Useful for showing **cumulative metrics**.

---

# 4️⃣ Column Chart

Used to compare **discrete values**.

Example:

```
Events per Server
```

---

# 5️⃣ Bar Chart

Similar to column charts but displayed horizontally.

Used for **category comparisons**.

---

# 6️⃣ Statistics Table

Tables allow analysts to:

- compare multiple fields
- aggregate values
- view exact metrics

---

# 7️⃣ Single Value Visualization

Displays a **single key metric**.

Example:

```
Total Failed Logins
```

Colors can be applied to highlight critical values.

---

# 8️⃣ Gauge Visualization

Gauges show how a metric compares to a defined range.

Types include:

- radial gauge
- marker gauge
- filler gauge

Example:

```
CPU Usage vs Threshold
```

---

# 🛡️ SOC Visualization Examples

In Security Operations Centers, visualizations are used to monitor:

| Use Case | Visualization |
|--------|---------------|
| login failures | time-series chart |
| network traffic | line graph |
| threat distribution | pie chart |
| security alerts | single value metrics |

---

# 🚀 Key Takeaway

Visualization transforms **complex datasets into actionable insights**.

Instead of interpreting raw logs:

```
Raw Logs → Structured Data → Visualization → Insight
```

Splunk Data Models and visualizations enable analysts and business users to **understand data quickly and make better decisions**.

---

# 📌 Final Insight

Effective dashboards combine:

- structured data models
- clear visualizations
- meaningful context

This allows organizations to move from:

```
Data → Understanding → Action
```

---

**✍️ Notes By Abhishek (Ez Abyss)**
