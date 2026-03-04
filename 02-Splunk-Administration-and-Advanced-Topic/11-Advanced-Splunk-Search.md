# Advanced Splunk Search Commands: accum, addcoltotals, addtotals

This lesson demonstrates several advanced Splunk SPL commands used for calculating totals and cumulative values.

Commands covered:

- `accum`
- `addcoltotals`
- `addtotals`

These commands are useful when performing **data aggregation, running totals, and summarizing results**.

---

# Dataset Used

A sample dataset from Splunk tutorial files is uploaded.

Steps to upload data:

1. Go to **Settings**
2. Click **Add Data**
3. Choose **Upload**
4. Upload the **ZIP file containing tutorial datasets**
5. Select **Automatic source type**
6. Choose index **default**
7. Submit and start searching

This dataset contains:

- Web access logs
- CSV files
- Mock server data

---

# Basic Search Example

Filter records based on:

- `status = 200`
- `category_id = strategy`

Example query:

```
status=200 category_id=strategy
| chart count AS views BY productId
```

### Output

| productId | views |
|----------|------|
| P101 | 898 |
| P205 | 821 |
| P309 | 741 |

---

# 1. Using `accum` Command

The `accum` command calculates a **running total** of a numeric field.

### Example

```
status=200 category_id=strategy
| chart count AS views BY productId
| accum views AS total_views
```

### Explanation

| Field | Meaning |
|------|--------|
| views | Count of product views |
| total_views | Running cumulative total |

### Example Output

| productId | views | total_views |
|----------|------|------------|
| P101 | 898 | 898 |
| P205 | 821 | 1719 |
| P309 | 741 | 2460 |

Each row adds the previous total.

---

# 2. Using `addcoltotals` Command

The `addcoltotals` command **adds a row at the bottom** showing totals for numeric columns.

### Example

```
status=200 category_id=strategy
| chart count AS views BY productId
| addcoltotals
```

### Output

| productId | views |
|----------|------|
| P101 | 898 |
| P205 | 821 |
| P309 | 741 |
| **Total** | 2460 |

---

## Adding a Label

You can specify a label for the total row.

### Example

```
status=200 category_id=strategy
| chart count AS views BY productId
| addcoltotals labelfield="Total Views"
```

This adds a labeled total row.

---

# 3. Using `addtotals` Command

The `addtotals` command computes the **sum of numeric fields for each row**.

It is commonly used with pivot tables or charts.

---

## Example Dataset

Example sales dataset:

| product | quarter | sales |
|-------|--------|------|
| A | Q1 | 200 |
| A | Q2 | 250 |
| B | Q1 | 300 |
| B | Q2 | 400 |

---

## Example Query

```
| chart sum(sales) BY product quarter
| addtotals
```

### Output

| product | Q1 | Q2 | Total |
|-------|----|----|------|
| A | 200 | 250 | 450 |
| B | 300 | 400 | 700 |

---

# Pivot Table using `chart`

Example query:

```
| chart sum(sales) BY product quarter
```

### Output

| product | Q1 | Q2 | Q3 | Q4 |
|-------|----|----|----|----|
| A | 200 | 250 | 300 | 350 |
| B | 300 | 400 | 450 | 500 |

This creates a **pivot-style table**.

---

# Adding Row Totals

```
| chart sum(sales) BY product quarter
| addtotals
```

This generates a **total column** per product.

---

# Summary of Commands

| Command | Purpose |
|------|--------|
| `accum` | Creates running cumulative totals |
| `addcoltotals` | Adds total row at bottom |
| `addtotals` | Adds row totals across columns |
| `chart` | Creates pivot tables |

---

# Practical Uses

These commands are useful for:

- Web traffic analysis
- Sales aggregation
- Product performance tracking
- Trend monitoring
- Business intelligence dashboards

---

# Key Takeaway

Using these commands helps analysts:

- Track cumulative metrics
- Calculate overall totals
- Generate pivot tables
- Summarize large datasets efficiently

These features make Splunk powerful for **data analysis and reporting**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
