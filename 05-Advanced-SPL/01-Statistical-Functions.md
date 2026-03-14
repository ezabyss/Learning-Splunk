# Statistical Functions in Splunk
### Understanding Data Analysis Using SPL Statistics

---

# 1. What Are Statistical Functions?

Statistical functions help analyze and summarize large datasets.

They transform **raw data into meaningful insights**.

Simple idea:

```
Raw Logs → Statistical Functions → Trends & Insights
```

Example uses:

- identify patterns
- detect anomalies
- summarize large datasets
- support decision making

---

# 2. Why Statistical Functions Matter

Statistical functions allow analysts to:

- understand data distribution
- detect outliers
- identify relationships
- analyze trends
- support predictions

Example:

SOC analysts can detect:

```
abnormal login frequency
unusual network traffic
suspicious activity spikes
```

---

# 3. Types of Statistical Functions

## 3.1 Descriptive Statistical Functions

These summarize data characteristics.

Common descriptive functions:

| Function | Purpose |
|---|---|
| mean / avg | average value |
| median | middle value |
| standard deviation | variability in data |

---

### Mean (Average)

Mean calculates the **average value of a dataset**.

Formula idea:

```
sum of values / number of values
```

Example:

If durations are:

```
100, 200, 300
```

Mean:

```
(100 + 200 + 300) / 3 = 200
```

---

### Median

Median is the **middle value when data is sorted**.

Example dataset:

```
10, 15, 20, 25, 30
```

Median:

```
20
```

Benefit:

```
Less affected by outliers than mean.
```

---

### Standard Deviation

Standard deviation measures **data variability**.

It tells how far data points are from the average.

Small standard deviation:

```
data is close to mean
```

Large standard deviation:

```
data varies widely
```

SOC example:

Large deviation in login attempts may indicate:

```
brute force attack
```

---

# 4. Inferential Statistical Functions

These functions help **draw conclusions beyond the dataset**.

Examples:

| Function | Purpose |
|---|---|
| correlation | relationship between variables |
| regression | prediction based on data trends |

---

### Correlation

Measures relationship between two variables.

Example:

```
network traffic ↑ → CPU usage ↑
```

Strong correlation may indicate:

```
possible attack or heavy system usage
```

---

### Regression Analysis

Regression predicts one variable based on another.

Example:

```
previous traffic data → predict future traffic
```

Used for:

- capacity planning
- anomaly detection
- predictive analytics

---

# 5. Using Statistical Functions in Splunk

In Splunk, statistical analysis is usually done using:

```
stats command
```

Basic syntax:

```spl
| stats function(field)
```

---

# 6. Example — Mean and Standard Deviation

Dataset index:

```
index=index1
```

SPL query:

```spl
index=index1
| stats avg(duration) AS mean stdev(duration) AS standard_deviation
```

Explanation:

| Command | Meaning |
|---|---|
| avg(duration) | calculate mean |
| stdev(duration) | calculate standard deviation |
| AS | rename output column |

Output example:

| mean | standard_deviation |
|---|---|
| 258.4 | 145.7 |

---

# 7. Real SOC Example

Detect abnormal login behavior.

Query:

```spl
index=authentication_logs
| stats avg(login_duration) stdev(login_duration)
```

Use case:

If login duration suddenly spikes:

```
possible automated attack
```

---

# 8. Other Common Splunk Statistical Functions

| Function | Description |
|---|---|
| count | total events |
| sum | total value |
| avg | average value |
| max | maximum value |
| min | minimum value |
| stdev | standard deviation |
| values | list unique values |

Example:

```spl
index=network_logs
| stats count by src_ip
```

This shows **number of events per IP address**.

---

# 9. Memory Shortcut

Remember statistical analysis using:

```
S A T
```

```
Summarize data
Analyze patterns
Track anomalies
```

---

# Final Insight

Statistical functions help analysts convert **large volumes of raw data into actionable intelligence**.

Instead of reading thousands of logs manually:

```
Statistics → Patterns → Insights
```

This is why statistical functions form the **foundation of data analysis in Splunk**.

---

✍️ Notes By Abhishek (Ez Abyss)
