# Splunk Commands: eventstats, eval, and timechart

## Overview

These three commands are powerful tools in Splunk's SPL (Splunk Processing Language).  
They help analysts **transform, enrich, and visualize data**.

Simple workflow:

    Raw Logs → eval → eventstats → timechart

These commands are extremely important for:

- SOC analysts
- security monitoring
- anomaly detection
- log analysis
- trend analysis

---

# 1️⃣ eval Command (Create or Modify Fields)

## What it does

`eval` is used to **create new fields or modify existing fields using calculations or conditions**.

Think of it as:

    eval = data calculator

You can use it to:

- perform math calculations
- convert units
- create labels
- manipulate strings
- apply conditions

---

## Syntax

    ... | eval new_field = expression

### Example 1 — Convert Seconds to Minutes

    index=index1
    | eval duration_minutes = duration/60

Result:

| duration | duration_minutes |
|---------|------------------|
| 120 | 2 |
| 300 | 5 |

---

### Example 2 — Label Balance Status

    index=index1
    | eval balance_status=if(balance<=0,"Insufficient","Positive")

Result:

| balance | balance_status |
|--------|----------------|
| -50 | Insufficient |
| 300 | Positive |

---

### Real SOC Example

Detect suspicious login attempts.

    index=auth_logs
    | eval suspicious_login=if(login_attempts>5,"Possible Attack","Normal")

---

# 2️⃣ eventstats Command (Add Statistical Context)

## What it does

`eventstats` calculates statistics across events and adds the result to every event.

Important difference:

| Command | Behavior |
|-------|---------|
| stats | summarizes data and removes raw events |
| eventstats | keeps events and adds statistics |

Think of it as:

    eventstats = stats + keep original events

---

## Syntax

    ... | eventstats function(field) AS new_field

---

### Example — Average Duration

    index=index1
    | eventstats avg(duration) AS avg_duration

Result:

| duration | avg_duration |
|---------|-------------|
| 200 | 300 |
| 400 | 300 |

Each event now knows the dataset average.

---

### Example — Detect Anomalies

    index=index1
    | eventstats avg(duration) AS avg_duration stdev(duration) AS sd
    | eval zscore=(duration-avg_duration)/sd
    | where abs(zscore)>3

Explanation:

| Step | Meaning |
|----|-------|
| eventstats | compute dataset statistics |
| avg(duration) | average value |
| stdev(duration) | standard deviation |
| eval | calculate z-score |
| where | filter anomalies |

This detects outliers or abnormal events.

---

### SOC Example

Detect abnormal network traffic.

    index=network_logs
    | eventstats avg(bytes) AS avg_bytes
    | eval anomaly=if(bytes>avg_bytes*5,"Suspicious Traffic","Normal")

---

# 3️⃣ timechart Command (Time-Based Visualization)

## What it does

`timechart` aggregates data over time.

It is used to analyze:

- trends
- spikes
- patterns
- anomalies

Think of it as:

    timechart = stats + time visualization

---

## Syntax

    ... | timechart span=1h count

Meaning:

count events per hour

---

### Example — Website Traffic

    index=web_logs
    | timechart span=1h count

Output example:

| time | count |
|-----|------|
| 10:00 | 500 |
| 11:00 | 750 |

This shows traffic trends over time.

---

### Example — Failed Login Trend

    index=auth_logs status=failed
    | timechart span=5m count

This helps detect:

- brute force attacks
- login spikes
- credential stuffing

---

### Example — CPU Usage Trend

    index=system_logs
    | timechart avg(cpu_usage)

Shows average CPU usage over time.

---

# 4️⃣ Using All Three Together

Example workflow:

    index=web_logs
    | eval response_seconds=response_time/1000
    | eventstats avg(response_seconds) AS avg_response
    | timechart avg(response_seconds)

Steps:

| Step | Command | Purpose |
|----|------|--------|
| 1 | eval | convert milliseconds to seconds |
| 2 | eventstats | calculate dataset statistics |
| 3 | timechart | visualize trend |

---

# 5️⃣ Simple Way to Remember

    eval       → create new data
    eventstats → add statistical context
    timechart  → analyze trends over time

Or remember this flow:

    Transform → Context → Trend
    (eval → eventstats → timechart)

---

# 6️⃣ Real SOC Investigation Example

Detect login spikes.

    index=auth_logs
    | eval failed_login=if(status="failed",1,0)
    | eventstats avg(failed_login) AS avg_fail
    | timechart sum(failed_login)

This helps detect:

- brute force attacks
- credential stuffing
- suspicious login patterns

---

# Final Insight

These three commands are core tools for Splunk analysts.

    eval       → build intelligence
    eventstats → enrich events
    timechart  → reveal patterns

Mastering them allows analysts to move from:

    Raw Logs → Security Insights

---

**✍️ Notes By Abhishek (Ez Abyss)**
