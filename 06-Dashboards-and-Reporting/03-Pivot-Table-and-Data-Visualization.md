# 📊 Splunk Data Models & Pivot Visualization Demo
### Building Dashboards Using Data Models

In this demonstration, I learned how to use **Splunk Data Models** to create visualizations and dashboards.

Instead of writing complex SPL queries, we can use the **Pivot Tool** to explore data models and generate charts.

This demo covers:

- exploring an existing data model
- creating visualizations using Pivot
- building a dashboard
- understanding how datasets work inside data models

---

# 🎯 Business Scenario

Business users want analytics based on **Splunk internal logs**.

They requested the following insights for the **last 24 hours**:

- number of searches by type
- number of configuration changes by type
- count of users performing searches
- whether searches were successful
- sorting results by user

We will build a **dashboard** that answers these questions.

---

# 🧩 Step 1 — Exploring Existing Data Models

Navigate to:

```
Settings → Data Models
```

This displays all data models available in the Splunk environment.

Many data models are automatically installed when **Splunk apps** are installed.

Example:

Installing the **AWS Splunk App** automatically creates AWS data models.

---

# 📦 Built-in Splunk Data Models

Splunk includes two built-in internal data models:

| Data Model | Description |
|------------|-------------|
| Splunk Internal Audit Logs | tracks user activity |
| Splunk Internal Server Logs | tracks server operations |

These models help analyze **Splunk system behavior**.

---

# 🔐 Step 2 — Updating Permissions

Before using the built-in data models, permissions must be updated.

Steps:

1. Click **Edit**
2. Select **Edit Permissions**
3. Grant **Read + Write permissions**
4. Apply to **All Apps**

Repeat this for both:

- Internal Audit Logs
- Internal Server Logs

---

# 🧱 Step 3 — Understanding Data Model Structure

Example Data Model:

**Splunk Internal Audit Logs**

Structure:

```
Root Event
   ├── Searches
   └── Modify Splunk Config
```

---

# Root Event

The root event contains the base dataset.

Default fields include:

| Field | Description |
|------|-------------|
| _time | event timestamp |
| host | system generating event |
| source | data source |
| sourcetype | log format |

---

# Constraints in Root Dataset

Each dataset has **constraints**.

Example constraint:

```
index=_audit
```

Constraints filter the events included in the dataset.

This ensures analysts only work with relevant data.

---

# Child Dataset Example — Searches

The **Searches dataset** inherits fields from the root dataset.

Constraint example:

```
index=_audit action=search
```

This means:

- data must come from `_audit` index
- event action must equal `search`

Child datasets inherit **all parent constraints and fields**.

---

# Child Dataset Example — Modify Splunk Config

Another child dataset tracks configuration changes.

Constraint example:

```
index=_audit action=edit_user
OR action=edit_roles
OR action=update
```

This dataset monitors **configuration modifications in Splunk**.

---

# 🧪 Step 4 — Using the Pivot Tool

To analyze data without writing SPL:

Click **Pivot**.

Then select the dataset.

Example:

```
Dataset → Searches
```

Pivot provides an interface to create **tables and charts dynamically**.

---

# 📉 Filtering Data

To focus analysis:

Apply time filters.

Example:

```
Last 24 hours
Last 7 days
All time
```

Filtering reduces noise and improves analysis accuracy.

---

# 📊 Creating a Table Visualization

Example configuration:

| Setting | Value |
|-------|------|
| Column Values | Count |
| Row Values | Search |
| Split Columns | Search Type |

Search types include:

- ad hoc
- scheduled
- real-time
- summary

This produces a **pivot table summarizing search activity**.

---

# 📈 Adding Time Dimension

We can also group results by time.

Example:

```
Row → Time
Column → Search Type
Value → Count
```

This helps analyze **search activity trends over time**.

---

# 📊 Creating Chart Visualizations

Pivot allows multiple visualization types.

Example charts:

| Chart Type | Use Case |
|-----------|----------|
| Column Chart | compare search types |
| Line Chart | analyze search trends |
| Bar Chart | compare categories |
| Pie Chart | show proportional distribution |

Example stacked column chart:

```
Search Count by Search Type
```

---

# 📊 Example Dashboard Panels

The dashboard may contain:

1️⃣ Column Chart — Search Type Distribution  
2️⃣ Line Chart — Search Trends Over Time  
3️⃣ Table — Detailed Search Activity  

---

# 💾 Saving Visualizations to a Dashboard

To save a visualization:

```
Save As → Dashboard Panel
```

Example:

Dashboard Name:

```
Demo Dashboard
```

Panel Names:

- Column Chart
- Line Chart
- Search Table

---

# 🧱 Step 5 — Editing Dashboard Layout

After saving panels:

Navigate to:

```
Dashboards → Edit
```

You can:

- rearrange charts
- change theme
- resize panels
- adjust displayed fields

Example layout:

```
Column Chart | Line Chart
-------------------------
        Table
```

---

# 📊 Example Dashboard Output

The dashboard provides insights such as:

| Metric | Example Insight |
|------|----------------|
| Search Count | total searches executed |
| Search Type | ad hoc vs scheduled searches |
| User Activity | who ran the searches |
| System Changes | configuration modifications |

This helps teams monitor **Splunk system usage**.

---

# 🛡️ SOC Use Cases

In a Security Operations Center, similar dashboards monitor:

| Use Case | Visualization |
|--------|--------------|
| failed login attempts | time-series chart |
| user activity | bar chart |
| alert distribution | pie chart |
| system performance | line graph |

---

# 🚀 Key Takeaway

Data Models and Pivot allow analysts to create dashboards **without writing SPL queries**.

```
Raw Logs → Data Model → Pivot → Visualization → Dashboard
```

This makes Splunk accessible for **both technical and business users**.

---

# 📌 Final Insight

Using Data Models with Pivot enables faster analysis by providing:

- structured datasets
- simplified visualization tools
- interactive dashboards

This approach helps organizations turn **machine data into actionable insights**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
