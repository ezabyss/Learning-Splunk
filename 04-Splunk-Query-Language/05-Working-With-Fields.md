# Working with Fields in Splunk 
### Filtering, Renaming, and Analyzing Fields

---

# 1. What Are Fields in Splunk?

Fields are **pieces of information extracted from log data**.

Example event:

```
age=35 balance=5000 education=tertiary marital=married
```

Fields:

| Field | Value |
|------|------|
| age | 35 |
| balance | 5000 |
| education | tertiary |
| marital | married |

Fields help analysts **filter, analyze, and visualize data**.

---

# 2. Limiting Fields Using `fields`

Sometimes logs contain **many fields**, but analysts only need a few.

Use the `fields` command to display only selected fields.

Example:

```spl
index=index1
| fields age balance campaign day duration education source
```

Meaning:

```
Only show these fields in the search results.
```

Important:

- This **does NOT remove data**
- It only **controls which fields appear in the UI**

---

# 3. Renaming Fields Using `rename`

The `rename` command changes field names to make them easier to understand.

Example:

```spl
index=index1
| rename education AS customer_education
| fields customer_education
```

Result:

| customer_education |
|---|
| tertiary |
| secondary |
| primary |

Benefits:

- easier readability
- better dashboards
- clearer reports

---

# 4. Performing Statistics with `stats`

The `stats` command calculates statistical values.

Common functions:

| Function | Meaning |
|---|---|
| count | number of events |
| avg | average |
| sum | total |
| max | maximum |
| min | minimum |

Example — average balance:

```spl
index=index1
| stats avg(balance)
```

Result:

```
Average balance of all customers
```

---

# 5. Statistics by Category (Group By)

We can calculate statistics **by field values**.

Example:

Average balance for **married users**.

```spl
index=index1 marital="married"
| stats avg(balance) by marital
```

Example output:

| marital | avg(balance) |
|---|---|
| married | 4523 |

---

# 6. Removing Duplicate Values Using `dedup`

The `dedup` command removes duplicate field values.

Example:

```spl
index=index1
| table education
| dedup education
```

Result:

| education |
|---|
| secondary |
| primary |
| tertiary |
| unknown |

This is similar to **SQL DISTINCT**.

---

# 7. Sorting Results Using `sort`

The `sort` command orders results.

Example:

```spl
index=index1 marital="married"
| fields education month
| sort education month
```

Sorting rules:

```
alphabetical order
numeric order
time order
```

---

# 8. Limiting Results Using `head`

`head` shows only the **first N records**.

Example:

```spl
index=index1 marital="married"
| fields education month
| sort education month
| head 5
```

Meaning:

```
Return only the first 5 results
```

Useful when:

- logs contain millions of events
- you want quick previews

---

# 9. Combined Example Query

Example pipeline:

```spl
index=index1 marital="married"
| fields education month balance
| sort education month
| head 5
```

Steps happening:

```
Search logs
Select specific fields
Sort results
Return first 5 records
```

---

# 10. Real SOC Example

SOC analyst investigating login logs.

Goal:

Find top login attempts by user.

Query:

```spl
index=authentication_logs
| fields user src_ip
| stats count by user
| sort -count
| head 10
```

This shows:

```
Top 10 users with the most login attempts
```

Possible indicators:

- brute force attack
- compromised accounts
- automated login scripts

---

# 11. Memory Shortcut

Remember these commands:

```
F R S D S H
```

```
Fields → select columns
Rename → change field names
Stats → perform calculations
Dedup → remove duplicates
Sort → order results
Head → limit results
```

---

# 12. Key Insight

In Splunk:

```
fields command controls what you SEE
stats command controls what you CALCULATE
```

These commands help analysts **simplify complex logs into useful insights**.

---

# Final Insight

Efficient field usage allows analysts to:

- reduce noise in search results
- focus on important data
- build clean dashboards
- detect security threats faster

Fields are the **foundation of Splunk data analysis**.

---

✍️ Notes By Abhishek (Ez Abyss)
