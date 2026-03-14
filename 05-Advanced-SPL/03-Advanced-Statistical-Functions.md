# Advanced Statistical Functions in Splunk
### Correlation • Hypothesis Testing • Anomaly Detection • Chi-Square • Box Plot

---

# 1. Why Advanced Statistical Functions Matter

Advanced statistical functions help analysts:

- uncover hidden relationships in data
- detect anomalies
- test assumptions
- analyze distributions
- generate predictive insights

Simple idea:

```
Raw Data → Statistical Analysis → Hidden Patterns → Better Decisions
```

These functions are extremely useful in:

- cybersecurity monitoring
- fraud detection
- behavioral analytics
- anomaly detection

---

# 2. Correlation Analysis

Correlation measures the **relationship between two variables**.

It tells us whether two values move together.

Example:

| Variable 1 | Variable 2 |
|-------------|-------------|
| account balance | call duration |

If correlation is high:

```
when balance increases → duration increases
```

---

## Splunk Example — Correlation Analysis

```spl
index=index1
| correlate balance duration
```

Explanation:

| Command | Meaning |
|--------|--------|
| correlate | calculates correlation between fields |
| balance | first variable |
| duration | second variable |

This helps identify **relationships between fields**.

---

# 3. Hypothesis Testing

Hypothesis testing checks whether **a difference between groups is meaningful**.

Example question:

```
Do customers with housing loans have different balances?
```

---

## Splunk Example — Average Balance by Housing

```spl
index=index1
| stats avg(balance) AS average_balance BY housing
```

Output example:

| housing | average_balance |
|--------|----------------|
| yes | 1500 |
| no | 1200 |

Meaning:

```
Compare average balances between groups.
```

This helps validate assumptions about data.

---

# 4. Anomaly Detection Using Z-Score

Z-score measures **how far a value is from the average**.

Formula concept:

```
Z = (value - mean) / standard deviation
```

If:

```
|Z| > 3
```

It usually indicates **an anomaly or outlier**.

---

## Splunk Example — Detect Duration Anomalies

```spl
index=index1
| eventstats stdev(duration) AS stdev_duration avg(duration) AS avg_duration
| eval z_score_duration=(duration-avg_duration)/stdev_duration
| where abs(z_score_duration)>3
```

Explanation:

| Step | Meaning |
|------|--------|
| eventstats | calculate statistics across dataset |
| avg(duration) | average duration |
| stdev(duration) | standard deviation |
| eval | compute z-score |
| where | filter anomalies |

Result:

```
Only abnormal duration events remain.
```

---

# 5. Chi-Square Test (Relationship Between Variables)

Chi-square helps determine **whether two variables are related**.

Example question:

```
Is marital status related to subscription success?
```

---

## Splunk Example — Count by Marital Status and Outcome

```spl
index=index1
| stats count BY marital y
```

Example output:

| marital | y | count |
|--------|---|------|
| married | yes | 200 |
| married | no | 600 |
| single | yes | 150 |
| single | no | 400 |

This helps analyze **relationships between categories**.

---

# 6. Box Plot Analysis

Box plots show **distribution of values**.

They help identify:

- median
- quartiles
- outliers

Example analysis:

```
balance distribution by education level
```

---

## Splunk Example — Balance Distribution

```spl
index=index1
| stats values(balance) AS balance BY education
| eval education=if(isnull(education),"unknown",education)
| chart values(balance) BY education
```

Explanation:

| Command | Purpose |
|--------|--------|
| stats values | gather balance values |
| eval | replace null education values |
| chart | visualize data distribution |

This helps compare **balance patterns across education levels**.

---

# 7. Visualization of Statistical Results

Splunk allows multiple visualization types:

- column chart
- bar chart
- line chart
- pie chart
- box plot

Example visualization query:

```spl
index=index1
| stats count BY education
```

Visualization options:

```
Bar Chart
Column Chart
Line Chart
```

---

# 8. Real SOC Example

Detect abnormal login durations.

```spl
index=authentication_logs
| eventstats avg(login_duration) AS avg_login stdev(login_duration) AS stdev_login
| eval zscore=(login_duration-avg_login)/stdev_login
| where abs(zscore)>3
```

This helps detect:

```
unusual login sessions
possible account compromise
automated attacks
```

---

# 9. Key Advanced Statistical Commands

| Command | Purpose |
|--------|--------|
| stats | aggregate statistics |
| eventstats | calculate stats without grouping |
| correlate | measure relationships |
| eval | compute new values |
| where | filter results |
| chart | create visualizations |

---

# 10. Memory Shortcut

Remember advanced statistical analysis using:

```
C H A C B
```

```
Correlation
Hypothesis testing
Anomaly detection
Chi-square analysis
Box plot distribution
```

---

# Final Insight

Advanced statistical functions allow analysts to move from **basic data analysis to deep insights**.

Instead of just counting logs:

```
Statistics → Patterns → Intelligence
```

This is why advanced statistical techniques are **essential for modern data analysis and security monitoring**.

---

✍️ Notes By Abhishek (Ez Abyss)
