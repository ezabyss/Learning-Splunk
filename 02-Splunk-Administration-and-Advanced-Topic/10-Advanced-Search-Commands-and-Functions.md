# Advanced Splunk Search Commands

Several **advanced search commands in Splunk SPL (Search Processing Language)**.  
These commands help perform deeper analysis and extract meaningful insights from datasets.

The dataset used in the examples:

```
index=index1 source="train.csv"
```

---

# 1. Regex Extraction using `rex`

The `rex` command is used to **extract fields from raw event data using regular expressions (Regex)**.

### Example Search

```
index=index1 source="train.csv"
| rex field=_raw "age=(?<age>\d+);job=(?<job>[^;]+)"
| table age job
| head 5
```

### Explanation

| Command | Description |
|------|-------------|
| `rex` | Extracts fields using regex |
| `field=_raw` | Uses the raw event data |
| `(?<age>\d+)` | Extracts numeric value for age |
| `(?<job>[^;]+)` | Extracts job value |
| `table` | Displays selected fields |
| `head 5` | Limits output to first 5 results |

### Output Example

| age | job |
|----|----|
| 31 | technician |
| 45 | admin |
| 28 | management |

---

# 2. Creating Fields using `eval`

The `eval` command is used to **create new fields or modify existing fields**.

### Example: Age Group Classification

```
index=index1 source="train.csv"
| eval age_group=case(
age<35,"young",
age<50,"middle_age",
age>=50,"senior"
)
| table age age_group
| head 5
```

### Explanation

| Condition | Result |
|---------|--------|
| Age < 35 | Young |
| Age < 50 | Middle Age |
| Age ≥ 50 | Senior |

### Example Output

| age | age_group |
|----|-----------|
| 31 | young |
| 45 | middle_age |
| 57 | senior |

---

# 3. Using `stats` Command

The `stats` command is used to **calculate statistics on selected fields**.

Common statistical functions:

- `avg()`
- `sum()`
- `count()`
- `max()`
- `min()`

### Example Search

```
index=index1 source="train.csv"
| stats avg(balance) AS average_balance max(duration) AS max_duration BY education
| table education average_balance max_duration
```

### Output Example

| education | average_balance | max_duration |
|----------|----------------|--------------|
| tertiary | 2100 | 400 |
| secondary | 1600 | 350 |

---

# 4. Time-Based Analysis using `timechart`

The `timechart` command creates **time-based visualizations**.

### Example

```
index=index1 source="train.csv"
| timechart span=1month count
```

### Explanation

| Component | Meaning |
|----------|--------|
| `timechart` | Creates time-based chart |
| `span=1month` | Groups results by month |
| `count` | Counts number of events |

### Visualization Options

Splunk allows different visualization formats:

- Line chart
- Bar chart
- Pie chart
- Trend chart

These can be changed in the **Visualization tab**.

---

# 5. Expanding Multi-value Fields using `mvexpand`

The `mvexpand` command **expands multi-value fields into separate events**.

Example multi-value field:

```
job="admin,technician,manager"
```

### Example Search

```
index=index1 source="train.csv"
| mvexpand job
| table age job
| head 5
```

### Result

| age | job |
|----|----|
| 35 | admin |
| 35 | technician |
| 35 | manager |

Each value becomes a **separate event**.

---

# Summary

The advanced commands covered in this session include:

| Command | Purpose |
|------|---------|
| `rex` | Extract fields using regular expressions |
| `eval` | Create or modify fields |
| `stats` | Perform statistical calculations |
| `timechart` | Generate time-based visualizations |
| `mvexpand` | Expand multi-value fields |

These commands help perform **advanced log analysis and data investigation in Splunk**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
