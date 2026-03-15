# ⚙️ Splunk Advanced Macros & Macro Functions

Splunk macros become even more powerful when they support **parameters and functions**.

Advanced macros allow analysts to:

- dynamically modify queries
- reuse complex search logic
- simplify investigation workflows
- build reusable analytics for dashboards

Macros act like **functions in programming**, allowing analysts to pass arguments and execute logic dynamically.

---

# 🧠 SOC Workflow Using Advanced Macros

Typical workflow in a Security Operations Center:

    Raw Logs → SPL Query → Macro → Parameterized Detection → Investigation

Instead of writing long queries repeatedly, analysts can build **parameterized macros**.

---

# 1️⃣ Review: What Are Macros?

A macro is a reusable **bundle of SPL logic**.

Once created, the macro can be called using a simple command.

Example:

```
Long SPL Query → Macro → Short Command
```

---

# 2️⃣ Parameterized Macros

Parameterized macros allow analysts to **pass arguments dynamically**.

Instead of hardcoding values, analysts can specify values when executing the macro.

Example use case:

Calculate the **average balance for a specific job category**.

---

# 3️⃣ Creating a Parameterized Macro

Navigate to:

```
Settings → Advanced Search → Search Macros → Add New
```

Create the macro with a parameter.

Macro Name:

```
macro_calc_avg_balance_byjob(1)
```

The `(1)` indicates the macro accepts **one argument**.

---

# Macro Definition

    index=index1
    source=train.csv
    job=$job$
    | stats avg(balance) AS Avg_Balance BY job
    | eval Avg_Balance=round(Avg_Balance,2)

---

# Macro Argument

Argument Name:

```
job
```

Allowed characters for arguments:

- letters
- numbers
- underscore
- hyphen

---

# 4️⃣ Executing the Macro

Macros are executed using **backticks (`)**.

Example:

    `macro_calc_avg_balance_byjob("management")`

---

# Example Outputs

### Job = Management

| job | Avg_Balance |
|----|-------------|
| management | 2843.21 |

---

### Job = Blue-Collar

    `macro_calc_avg_balance_byjob("blue-collar")`

| job | Avg_Balance |
|----|-------------|
| blue-collar | 1985.77 |

---

### Job = Retired

    `macro_calc_avg_balance_byjob("retired")`

| job | Avg_Balance |
|----|-------------|
| retired | 3152.54 |

---

# 5️⃣ Macros for Data Manipulation

Macros can also include **data manipulation functions**.

Common commands used inside macros:

| Command | Purpose |
|------|---------|
| eval | create calculated fields |
| stats | perform aggregations |
| chart | generate statistical visualizations |

---

# Example Macro

Macro Name:

```
macro_contact_distribution_byjob
```

Macro Definition:

    index=index1
    source=train.csv
    | stats count BY job contact

---

# Executing the Macro

    `macro_contact_distribution_byjob`

---

# Example Result

| job | contact | count |
|----|--------|------|
| admin | cellular | 120 |
| technician | telephone | 87 |
| management | cellular | 210 |

This helps analyze **communication channels used by different job groups**.

---

# 6️⃣ Real-World Example: Campaign Success Analysis

Goal:

Calculate **campaign success rate based on education level**.

---

# Macro Name

```
macro_campaign_success_byeducation
```

---

# Macro Definition

    index=index1
    source=train.csv
    | eval success_rate=if(poutcome="success",1,0)
    | stats sum(success_rate) AS successful count AS total BY education
    | eval success_rate=round((successful/total)*100,2)

---

# Executing the Macro

    `macro_campaign_success_byeducation`

---

# Example Output

| education | successful | total | success_rate |
|----------|-----------|------|--------------|
| tertiary | 420 | 900 | 46.67 |
| secondary | 380 | 1000 | 38.00 |
| primary | 150 | 500 | 30.00 |

---

# 7️⃣ Why Advanced Macros Matter in SOC

Advanced macros allow analysts to:

- standardize investigations
- automate complex analytics
- reuse detection logic
- simplify dashboards

They are often used in:

| SOC Use Case | Example |
|--------------|---------|
| Threat hunting | reusable IOC searches |
| Authentication analysis | login anomaly detection |
| Endpoint monitoring | malware detection queries |
| Dashboard panels | real-time analytics |

---

# 📊 Macro Quick Reference

| Feature | Description |
|-------|-------------|
| Macro | reusable SPL logic |
| Parameterized Macro | macro with arguments |
| Definition | search logic executed |
| Execution | `macro_name(parameters)` |

---

# 🚀 Key Takeaway

Advanced macros transform long SPL queries into **dynamic reusable analytics**.

They allow analysts to move from:

    Static Searches → Dynamic Investigations

---

# 🧠 Analyst Insight

In large SOC environments, macros are frequently used for:

- reusable threat hunting queries
- detection rule libraries
- dashboard automation
- investigation workflows

Mastering macros makes analysts **significantly faster in Splunk investigations**.

---

# 📌 Final Concept

The true power of Splunk lies in **automation and reusability**.

Macros enable analysts to convert:

    Complex SPL → Reusable Security Intelligence

---

**✍️ Notes By Abhishek (Ez Abyss)**
