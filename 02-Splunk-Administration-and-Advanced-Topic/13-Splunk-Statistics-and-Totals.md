# Advanced Splunk Search Techniques: Statistics and Totals

Additional advanced Splunk SPL commands used for **statistical calculations and generating totals** in datasets.

Commands demonstrated include:

- `stats`
- `chart`
- `addtotals`

These commands help analysts generate **summaries, pivot tables, and grand totals** from data ingested into Splunk.

---

# 1. Calculating Total Sales using `stats`

The `stats` command is used to calculate statistical values such as:

- sum
- average
- count
- min
- max

## Example Query

```
| stats sum(sales) BY product
```

### Explanation

| Command | Purpose |
|------|--------|
| `stats` | Performs statistical calculations |
| `sum(sales)` | Calculates total sales |
| `BY product` | Groups results by product |

### Example Output

| product | total_sales |
|-------|-------------|
| Product A | 1200 |
| Product B | 950 |
| Product C | 780 |

---

# 2. Calculating Quarterly Totals

You can generate totals grouped by quarter.

## Example Query

```
| stats sum(sales) BY quarter
| addtotals row=f col=t labelfield=quarter
```

### Explanation

| Parameter | Meaning |
|----------|--------|
| `row=f` | Disable row totals |
| `col=t` | Enable column totals |
| `labelfield=quarter` | Label totals under the quarter field |

### Output

| quarter | sales |
|--------|------|
| Q1 | 320 |
| Q2 | 400 |
| Q3 | 350 |
| Q4 | 450 |
| **Total** | 1520 |

---

# 3. Creating Pivot Tables using `chart`

The `chart` command is used to create **pivot-style tables**.

## Example Query

```
| chart sum(sales) BY product quarter
```

### Explanation

| Component | Description |
|----------|-------------|
| `chart` | Generates a pivot table |
| `sum(sales)` | Calculates sales totals |
| `BY product quarter` | Groups by product and quarter |

### Example Output

| product | Q1 | Q2 | Q3 | Q4 |
|-------|----|----|----|----|
| Product A | 200 | 250 | 300 | 350 |
| Product B | 150 | 220 | 260 | 320 |

---

# 4. Adding Totals to Pivot Tables

To calculate totals for rows or columns, the `addtotals` command is used.

## Example Query

```
| chart sum(sales) BY product quarter
| addtotals col=t labelfield=product
```

### Explanation

| Parameter | Description |
|----------|-------------|
| `col=t` | Adds column totals |
| `labelfield=product` | Displays totals under product column |

### Example Output

| product | Q1 | Q2 | Q3 | Q4 | Total |
|-------|----|----|----|----|------|
| Product A | 200 | 250 | 300 | 350 | 1100 |
| Product B | 150 | 220 | 260 | 320 | 950 |

---

# 5. Custom Totals Example

You can create multiple totals such as:

- Quarterly totals
- Product totals
- Grand totals

## Example Query

```
| chart sum(sales) BY product quarter
| addtotals col=t
```

This generates:

- Total sales for each product
- Total sales for each quarter

---

# 6. Benefits of These Commands

These commands allow analysts to:

- Generate quick summaries
- Create pivot tables
- Calculate cumulative totals
- Build dashboards and reports

---

# 7. Common Use Cases

These statistical commands are commonly used for:

- Sales analysis
- Financial reporting
- Web traffic monitoring
- Security log analysis
- Business intelligence dashboards

---

# Key Takeaway

Advanced search commands in Splunk enable analysts to perform **powerful statistical analysis on ingested data**.

By combining commands like:

```
stats
chart
addtotals
```

you can generate meaningful insights and customizable reports directly within Splunk.

---

**✍️ Notes By Abhishek (Ez Abyss)**
