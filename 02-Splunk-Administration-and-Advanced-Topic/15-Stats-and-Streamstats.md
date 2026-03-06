# Splunk Stats and Streamstats Commands

## Introduction

In Splunk, the **`stats` command** is widely used to calculate statistical summaries of data.  
It allows analysts to compute metrics like:

- Maximum values
- Minimum values
- Average values
- Percentiles
- Counts
- Aggregated statistics

These calculations help analyze large datasets and extract meaningful insights.

---

# Using the Stats Command

Example search:

```
| stats max(bytes) as largest min(bytes) as smallest avg(bytes) as average perc95(bytes) as 95th_percentile
```

### Explanation

| Function | Purpose |
|--------|--------|
| `max(bytes)` | Finds the largest value of bytes |
| `min(bytes)` | Finds the smallest value |
| `avg(bytes)` | Calculates the average value |
| `perc95(bytes)` | Calculates the 95th percentile |

---

# Understanding the 95th Percentile

The **95th percentile** means:

> 95% of values fall below this number.

This metric is useful because **average values can be distorted by extreme outliers**.

Example:

If a dataset has values:

```
10, 15, 20, 25, 1000
```

The **average** becomes misleading due to the outlier `1000`.

Using **percentiles** gives a better representation of normal behavior.

---

# Calculating Event Counts with Stats

We can also count events grouped by a field.

Example:

```
| stats count as total_purchases by itemId
```

### Explanation

| Field | Meaning |
|------|--------|
| `count` | Counts number of events |
| `total_purchases` | Alias for count |
| `itemId` | Field used for grouping |

This shows how many purchases occurred for each item.

---

# Sorting Results

To display the **top results**, use the `sort` command.

Example:

```
| sort - total_purchases
```

### Explanation

| Symbol | Meaning |
|------|--------|
| `-` | Descending order |
| `total_purchases` | Field used for sorting |

---

# Using Streamstats for Ranking

The **`streamstats` command** calculates statistics sequentially across events.

Example:

```
| streamstats count as rank
```

### Purpose

This creates a **ranking column** where:

| Rank | Event |
|------|------|
| 1 | First event |
| 2 | Second event |
| 3 | Third event |

Each event receives an incremental number.

---

# Complete Query Example

Example search combining all commands:

```
| stats count as total_purchases by itemId
| sort - total_purchases
| streamstats count as rank
```

### Query Workflow

1. **stats**

   Calculates the total purchases per item.

2. **sort**

   Sorts items by highest purchase count.

3. **streamstats**

   Assigns a rank to each item.

---

# Example Output

| Rank | Item ID | Total Purchases |
|----|--------|----------------|
| 1 | Item_102 | 450 |
| 2 | Item_055 | 420 |
| 3 | Item_201 | 390 |
| 4 | Item_067 | 360 |
| 5 | Item_011 | 300 |

---

# Importance of Selecting the Right Dataset

The dataset used in Splunk analysis significantly affects the output.

Factors to consider:

- Data completeness
- Event structure
- Field availability
- Relevance to query

Choosing the correct dataset ensures:

- Accurate results
- Meaningful analysis
- Efficient searches

---

# Key Takeaways

- `stats` is used to compute statistical summaries.
- `perc95()` helps avoid skew caused by outliers.
- `count` helps measure event frequency.
- `sort` organizes results.
- `streamstats` creates rankings or running calculations.

These commands are commonly used in **data analysis, reporting, and monitoring workflows in Splunk**.

---

# Summary

By combining **transaction commands**, **stats calculations**, and **streamstats ranking**, analysts can:

- Track user activity
- Identify top events
- Rank results
- Analyze behavioral patterns

These techniques are essential for **efficient Splunk data analysis and investigation**.

---

**✍️ Notes By Abhishek (Ez Abyss)**
