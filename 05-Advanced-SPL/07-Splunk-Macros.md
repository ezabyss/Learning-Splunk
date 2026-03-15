# ⚡ Splunk Macros
### Simplifying Complex Queries in SPL

Splunk **macros** are reusable search snippets that allow analysts to simplify complex queries and improve efficiency.

Instead of repeatedly writing long SPL queries, macros allow you to **create shortcuts for commonly used searches**.

Macros help analysts:

- simplify complex searches
- improve query readability
- standardize investigations
- increase efficiency in SOC workflows

---

# 🧠 SOC Investigation Workflow with Macros

Typical analyst workflow:

    Raw Logs → SPL Query → Macro → Reusable Detection

Macros help transform long queries into **short reusable commands**.

Example:

Instead of writing a full SPL query every time, analysts can simply run a macro.

---

# 1️⃣ What Are Splunk Macros?

A **macro** is a reusable search definition.

Think of it like a **function in programming**.

Example concept:

```
Long SPL Query → Macro → Short Command
```

---

# 2️⃣ Why Macros Are Powerful

Macros provide several advantages.

| Benefit | Explanation |
|-------|-------------|
| Simplified queries | Reduces long SPL queries |
| Efficiency | Saves time during investigations |
| Consistency | Standardizes search logic |
| Reusability | Same logic used across dashboards |

---

# 3️⃣ Example Scenario

Imagine you are a **bank analyst** investigating customer behavior.

Goal:

Understand **which job categories have higher account balances**.

Dataset used:

```
train.csv
```

---

# 4️⃣ Creating a Macro in Splunk

Steps to create a macro:

1. Go to **Settings**
2. Select **Advanced Search**
3. Click **Search Macros**
4. Click **Add New**
5. Define the macro

---

# 5️⃣ Example Macro Definition

Macro Name:

```
AvgBalanceByJob
```

Definition (search query):

    index=index1
    source=train.csv
    | stats avg(balance) AS average_balance BY job

---

# Query Explanation

| Component | Purpose |
|----------|---------|
| `index=index1` | Search logs from index1 |
| `source=train.csv` | Dataset used |
| `stats` | Aggregates results |
| `avg(balance)` | Calculates average balance |
| `BY job` | Groups results by job category |

---

# 6️⃣ Saving the Macro

When creating the macro, configure:

| Setting | Value |
|-------|-------|
| Name | AvgBalanceByJob |
| Definition | SPL query |
| Arguments | None |

If arguments were needed, they would appear as:

```
$argument$
```

---

# 7️⃣ Using a Macro in SPL

Macros are executed using **tilde symbols (`)**.

Example:

    `AvgBalanceByJob`

Splunk will automatically execute the query defined in the macro.

---

# Example Output

| job | average_balance |
|----|----------------|
| admin | 2500 |
| technician | 3200 |
| management | 4100 |

---

# 8️⃣ Comparing Macro vs Normal Query

### Without Macro

    index=index1
    source=train.csv
    | stats avg(balance) AS average_balance BY job

### With Macro

    `AvgBalanceByJob`

Both produce **exactly the same result**.

But macros make searches **shorter and easier to reuse**.

---

# ⚠ Important Note

Macros must be wrapped in **tilde symbols**:

```
`macro_name`
```

These are **not single quotes**.

---

# 9️⃣ App Visibility of Macros

Macros are **app-specific**.

If created in one app (for example `Launcher`), they may not appear in another app.

To fix this:

Create the macro inside the **Search & Reporting app**.

---

# 🛡️ SOC Use Cases for Macros

Macros are widely used in **Security Operations Centers (SOC)**.

Example use cases:

| Use Case | Example |
|--------|--------|
| Failed login detection | reusable authentication queries |
| Malware investigation | repeated endpoint searches |
| Threat hunting | reusable IOC searches |
| Security dashboards | simplified panel queries |

Example detection macro:

    index=auth_logs
    | stats count BY user, src_ip

Saved as:

```
SuspiciousLoginSearch
```

---

# 📊 Macro Command Quick Reference

| Feature | Description |
|------|-------------|
| Macro | reusable search logic |
| Arguments | variables inside macros |
| Definition | SPL query executed |
| Execution | `macro_name` |

---

# 🚀 Key Takeaway

Macros help analysts transform:

    Long SPL Queries → Short Reusable Commands

This significantly improves **investigation speed and query management**.

---

# 🧠 Analyst Insight

In real SOC environments, macros are often used to:

- standardize detection queries
- simplify dashboards
- speed up investigations
- maintain consistent analytics

Mastering macros is a key step toward becoming a **power Splunk user**.

---

# 📌 Final Concept

The real power of Splunk comes from **reusability and automation**.

Macros enable analysts to move from:

    Manual Queries → Reusable Security Analytics

---

**✍️ Notes By Abhishek (Ez Abyss)**
