# 🧩 Splunk Data Models — Structure & Concepts

Data Models in Splunk are designed to make **machine data easier to understand and analyze**.

Instead of working directly with complex raw logs, data models provide a structured framework that **abstracts and organizes data** into meaningful datasets.

This allows analysts and business users to explore data without needing deep knowledge of SPL.

```
Raw Machine Data → Data Model → Structured Dataset → Analysis
```

---

# 🧠 What Are Data Models?

A **Data Model** in Splunk is a structured representation of data that groups related events together.

They simplify complex data by:

- organizing datasets
- defining relationships between data fields
- applying constraints to narrow search results

Data models help analysts focus on **meaningful insights instead of raw log complexity**.

---

# 📚 Data Models and Knowledge Objects

Data Models are built on **Splunk Knowledge Objects**.

Knowledge objects include:

| Knowledge Object | Purpose |
|------------------|--------|
| Saved Searches | Predefined searches |
| Field Extractions | Extract structured fields from logs |
| Tags | Categorize events |
| Event Types | Group similar events |
| Lookups | Enrich data with external information |

These objects combine to form **datasets**, which are the building blocks of a data model.

```
Knowledge Objects → Datasets → Data Model
```

---

# 🏗️ Structure of a Splunk Data Model

Data Models are **hierarchical structures**.

They begin with a **root dataset** and expand into multiple child datasets.

```
Root Dataset
   ├── Child Dataset
   ├── Child Dataset
   └── Child Dataset
```

Each dataset contains:

- fields
- constraints
- relationships with other datasets

---

# 1️⃣ Root Datasets

A Data Model begins with a **root dataset**, which defines the base data source.

Root datasets can be of three types:

| Root Type | Description |
|----------|-------------|
| Root Event | Most common dataset type |
| Root Search | Dataset created using a saved search |
| Root Transaction | Combines multiple events into one logical transaction |

---

# Root Event

Root events are the **most commonly used data model datasets**.

They directly reference raw events stored in Splunk indexes.

Example constraint:

```
index=internal
```

This ensures that only relevant events are included in the model.

---

# Root Search

A root search dataset is based on a **saved search query**.

The search defines the data included in the dataset.

Example:

```
index=internal sourcetype=splunkd
```

Root searches must include an **index constraint**.

---

# Root Transaction

Transactions combine multiple events into a **single logical activity**.

Example scenario:

A customer visiting a grocery store:

1. Customer enters store  
2. Customer selects products  
3. Customer checks out  
4. Customer leaves

All events within a time window can be combined into **one transaction**.

This is similar to how Splunk groups related events.

---

# 🔒 Constraints in Data Models

Constraints help **narrow down the dataset**.

They filter the data to ensure analysts only work with relevant events.

Example constraint:

```
index=_internal
```

Constraints improve:

- search performance
- data relevance
- analytical accuracy

---

# 📊 Fields in Data Models

Fields represent **attributes within the dataset**.

Fields can exist at both:

- root datasets
- child datasets

Child datasets automatically **inherit fields from their parent dataset**.

---

# Field Types in Data Models

Splunk supports several types of fields.

| Field Type | Description |
|-----------|-------------|
| Auto-Extracted Fields | Automatically extracted by Splunk |
| Calculated Fields | Generated using `eval` expressions |
| Lookup Fields | Created using lookup tables |
| Regex Fields | Extracted using regular expressions |

---

# Example Field Generation Methods

### Auto-Extracted Fields

Fields automatically discovered by Splunk.

Example:

```
host
source
sourcetype
```

---

### Eval Expressions

Calculated fields generated dynamically.

Example:

```
eval response_time_seconds = response_time / 1000
```

---

### Lookup Fields

Fields created using external lookup tables.

Example:

Mapping IP addresses to geographic locations.

---

### Regex Field Extraction

Fields extracted using regular expressions.

Example:

```
rex field=_raw "user=(?<username>\w+)"
```

---

# 🛡️ Why Data Models Matter for SOC

Data Models are widely used in **Security Operations Centers (SOC)**.

They allow analysts to quickly explore structured security data.

Common SOC uses include:

| Use Case | Example |
|--------|---------|
| Authentication monitoring | failed login analysis |
| Network traffic monitoring | abnormal traffic detection |
| Endpoint monitoring | malware activity |
| Threat hunting | identifying attacker patterns |

Splunk Enterprise Security relies heavily on **data models and the Common Information Model (CIM)**.

---

# ⚙️ Built-In Splunk Data Models

Splunk includes several **prebuilt datasets**.

Examples include:

| Dataset | Description |
|-------|-------------|
| Audit Logs | tracks user activity in Splunk |
| Internal Logs | monitors Splunk system behavior |
| Server Logs | monitors Splunk server operations |

These built-in datasets are useful for **learning and building dashboards**.

---

# 📊 Using Data Models in Dashboards

Once a Data Model is created, it can be used to build:

- dashboards
- reports
- pivot visualizations
- analytical charts

Example workflow:

```
Data Model → Pivot Tool → Dashboard Visualization
```

This approach allows users to create dashboards **without writing SPL queries**.

---

# 🚀 Key Takeaway

Data Models simplify machine data by providing a **structured and hierarchical framework**.

They allow analysts to move from:

```
Raw Logs → Structured Data Model → Faster Analysis
```

By organizing datasets, applying constraints, and defining relationships, Splunk Data Models make **data exploration faster and more intuitive**.

---

# 📌 Final Insight

Understanding Data Models is essential for:

- building Splunk dashboards
- using pivot visualizations
- performing efficient data analysis
- enabling collaboration between analysts

Data Models transform raw machine data into **actionable insights for organizations**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
