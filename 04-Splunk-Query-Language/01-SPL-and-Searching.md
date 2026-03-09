# SPL Basics — Splunk Processing Language

---

# 1. What is SPL?

SPL stands for **Splunk Processing Language**.

It is the **query language used in Splunk** to:

- search data
- filter logs
- analyze events
- generate statistics
- build dashboards

Simple idea:

```
Raw Data → SPL Query → Insights
```

Example SPL query:

```spl
index=index1
```

This searches all events stored in **index1**.

---

# 2. Dataset Used in the Lesson

The dataset used is:

```
train.csv
```

This dataset represents a **bank marketing campaign dataset**.

Goal:

Predict whether a customer will **subscribe to a term deposit**.

Target variable:

```
Y = yes / no
```

---

# 3. Important Columns in the Dataset

| Column | Description |
|------|------|
| age | Customer age |
| job | Job type |
| marital | Marital status |
| education | Education level |
| default | Credit default (yes/no) |
| balance | Average yearly balance |
| housing | Housing loan (yes/no) |
| loan | Personal loan (yes/no) |
| contact | Contact type (phone, cellular) |
| day | Last contact day |
| month | Last contact month |
| duration | Call duration |
| campaign | Number of contacts in campaign |
| pdays | Days since last contact |
| previous | Previous contacts |
| poutcome | Previous campaign outcome |
| y | Target variable (term deposit subscription) |

---

# 4. Importing the Dataset into Splunk

Steps to upload the dataset:

```
Add Data → Upload
```

Then select:

```
train.csv
```

Configuration example:

| Setting | Value |
|------|------|
| Source Type | CSV |
| Host | SPL1 |
| Index | index1 |

Submit and start search.

---

# 5. Viewing All Fields

Basic SPL command:

```spl
table *
```

This displays **all fields in table format**.

---

# 6. Filtering Data Using Conditions

Example:

Find customers who have **both housing loan AND personal loan**.

```spl
housing="yes" AND loan="yes"
```

Result:

```
4367 events
```

---

# 7. Display Specific Fields

Use the **table command**.

Example:

```spl
housing="yes" AND loan="yes"
| table age education housing loan contact
```

Output shows selected columns only.

---

# 8. Using AND vs OR

## AND Operator

Returns events where **both conditions are true**.

Example:

```spl
housing="yes" AND loan="yes"
```

Meaning:

Customer has:

```
Housing loan = yes
Personal loan = yes
```

---

## OR Operator

Returns events where **either condition is true**.

Example:

```spl
housing="yes" OR loan="yes"
```

Meaning:

- housing loan = yes  
OR  
- personal loan = yes  

This returns **more results**.

---

# 9. Finding Customers with No Loans

Query:

```spl
housing="no" AND loan="no"
```

Result:

```
17,204 customers
```

Meaning:

Customers who have **no housing loan and no personal loan**.

---

# 10. Using Stats Command

The **stats command** performs statistical calculations.

Example:

```spl
| stats count(eval(housing="yes")) as housing_loan
```

This counts:

```
Customers with housing loan
```

---

# 11. Multiple Counts Using Stats

Example query:

```spl
| stats 
count(eval(housing="yes")) as housing_loan
count(eval(loan="yes")) as personal_loan
count(eval(housing="yes" AND loan="yes")) as both_loans
```

Output example:

| housing_loan | personal_loan | both_loans |
|------|------|------|
| 25130 | 7244 | 4367 |

This quickly summarizes the dataset.

---

# 12. Transpose Command

The **transpose command** converts rows into columns.

Example:

```spl
| transpose
```

Before transpose:

| housing_loan | personal_loan |
|------|------|

After transpose:

| Field | Value |
|------|------|
| housing_loan | 25130 |
| personal_loan | 7244 |

This improves readability.

---

# 13. Counting Customers with No Loans

Example query:

```spl
| stats 
count(eval(housing="yes")) as housing_loan
count(eval(loan="yes")) as personal_loan
count(eval(housing="yes" AND loan="yes")) as both_loans
count(eval(housing="no" AND loan="no")) as no_loan
| transpose
```

Example output:

| Category | Count |
|------|------|
| housing_loan | 25130 |
| personal_loan | 7244 |
| both_loans | 4367 |
| no_loan | 17204 |

---

# 14. Key SPL Concepts Learned

Commands used in this lesson:

| Command | Purpose |
|------|------|
| table | Display selected fields |
| stats | Perform statistical calculations |
| eval | Create calculated fields |
| count | Count events |
| transpose | Rotate rows into columns |

Logical operators:

```
AND
OR
```

Note:

```
Operators must be in CAPITAL letters
```

---

# 15. Why SPL is Powerful

Even with **45,000+ records**, SPL can quickly:

- filter data
- summarize statistics
- generate insights
- support dashboards

Example workflow:

```
Raw dataset → SPL queries → Insights → Dashboard
```

---

# Memory Shortcut

Remember the main SPL commands:

```
T S E T
```

```
Table
Stats
Eval
Transpose
```

---

# Final Insight

SPL allows analysts to transform raw data into **actionable insights within seconds**.

Using simple queries, you can:

- analyze thousands of events
- detect patterns
- summarize data
- build dashboards

This is why SPL is one of the **most powerful tools in Splunk analytics**.

---

✍️ Notes By Abhishek (Ez Abyss)
