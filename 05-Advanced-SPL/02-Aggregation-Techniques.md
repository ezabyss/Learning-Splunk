# Advanced Aggregation Techniques in Splunk
### Rolling Averages • Percentiles • Combined Aggregations

---

# 1. What is Aggregation in Splunk?

Aggregation means **summarizing data to extract meaningful insights**.

Instead of analyzing every single log event, we summarize them using statistics.

Simple idea:

```
Raw Logs → Aggregation → Insights
```

Example:

```
Millions of logs → Average login attempts per user
```

Aggregation helps analysts:

- understand trends
- detect anomalies
- simplify large datasets
- support decision making

---

# 2. Why Advanced Aggregation Matters

Basic aggregations show simple metrics like:

```
count
average
sum
```

Advanced aggregation helps reveal deeper insights like:

- moving trends
- distribution patterns
- maximum thresholds
- behavior comparison

These techniques are **essential for advanced data analysis and threat detection**.

---

# 3. Rolling Average (Moving Average)

Rolling average smooths **data fluctuations over time**.

It calculates an average across a **moving window of events**.

This helps detect:

- trends
- spikes
- gradual changes

---

## Example — Rolling Average Balance

SPL Query:

```spl
index=index1 source="train.csv"
| timechart span=1s avg(balance) AS avg_balance
| streamstats window=3 avg(avg_balance) AS rolling_avg_balance
```

Explanation:

| Command | Meaning |
|---|---|
| timechart | creates time-based aggregation |
| span=1s | 1-second interval |
| avg(balance) | average balance |
| streamstats | calculates rolling statistics |
| window=3 | rolling window of 3 events |

Result:

```
Smoothed average balance trend
```

---

# 4. Percentile Aggregation

Percentiles help understand **data distribution**.

Example:

```
90th percentile = value below which 90% of data falls
```

Useful for:

- performance analysis
- anomaly detection
- outlier identification

---

## Example — 90th Percentile of Duration

SPL Query:

```spl
index=index1
| stats perc90(duration) AS percentile_90_duration BY marital
```

Explanation:

| Command | Meaning |
|---|---|
| perc90 | 90th percentile |
| duration | analyzed column |
| BY marital | grouped by marital status |

Example output:

| marital | percentile_90_duration |
|---|---|
| married | 550 |
| single | 470 |
| divorced | 520 |

Meaning:

```
90% of duration values fall below this threshold.
```

---

# 5. Combined Aggregation

Combined aggregation means **using multiple statistical functions together**.

This provides richer insights.

Example metrics:

- average value
- maximum value
- minimum value
- event count

---

## Example — Average and Max Balance by Job

SPL Query:

```spl
index=index1 source="train.csv"
| stats avg(balance) AS avg_balance max(balance) AS max_balance BY job
```

Explanation:

| Command | Meaning |
|---|---|
| avg(balance) | average balance |
| max(balance) | maximum balance |
| BY job | grouped by job category |

Example output:

| job | avg_balance | max_balance |
|---|---|---|
| admin | 1500 | 12000 |
| blue-collar | 900 | 7000 |
| technician | 1800 | 15000 |

This helps compare **financial behavior by job role**.

---

# 6. Real SOC Example (Security Analysis)

Example:

Detect abnormal login duration.

```spl
index=authentication_logs
| stats avg(session_duration) max(session_duration) perc90(session_duration)
```

Use cases:

- detect abnormal sessions
- identify potential session hijacking
- analyze login patterns

---

# 7. Key Advanced Aggregation Commands

| Command | Purpose |
|---|---|
| stats | calculate statistics |
| timechart | time-based aggregation |
| streamstats | rolling calculations |
| perc90 | percentile calculation |
| avg | average value |
| max | maximum value |

---

# 8. Aggregation Workflow

Typical analysis process:

```
Collect Logs
Group Data
Apply Aggregation
Analyze Trends
Identify Patterns
```

Example pipeline:

```spl
index=network_logs
| stats count BY src_ip
| sort -count
```

This identifies **most active IP addresses**.

---

# 9. Memory Shortcut

Remember advanced aggregation using:

```
R P C
```

```
Rolling averages
Percentiles
Combined aggregations
```

These reveal **deeper patterns in data**.

---

# Final Insight

Advanced aggregation transforms **large datasets into powerful insights**.

Instead of analyzing millions of logs manually:

```
Aggregation → Patterns → Intelligence
```

This is why aggregation is one of the **most important skills in Splunk data analysis**.

---

✍️ Notes By Abhishek (Ez Abyss)
