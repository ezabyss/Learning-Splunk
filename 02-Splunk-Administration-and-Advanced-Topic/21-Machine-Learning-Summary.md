# Splunk Machine Learning Master Notes

---

# 1. Introduction to Machine Learning in Splunk

Splunk is a powerful platform used for:

- collecting machine data
- indexing logs
- analyzing events
- monitoring systems
- detecting security threats

Machine Learning adds another layer:

Instead of only asking:

```
What happened?
```

We can now ask:

```
What will happen next?
```

or

```
Is something unusual happening?
```

Splunk uses the **Machine Learning Toolkit (MLTK)** to integrate machine learning directly into the Splunk environment.

---

# 2. What is Machine Learning?

Machine Learning is a branch of Artificial Intelligence where systems learn patterns from data and improve their predictions over time.

Simple idea:

```
Data → Learn Patterns → Make Predictions
```

Example:

A security team analyzes firewall logs.

Machine learning can learn patterns such as:

- normal traffic
- suspicious activity
- malware communication

After learning, the system can detect threats automatically.

---

# 3. Types of Machine Learning in Splunk

There are mainly **two types** used in Splunk.

```
1. Supervised Learning
2. Unsupervised Learning
```

---

# 4. Supervised Machine Learning

Supervised learning means the algorithm learns from **labeled data**.

Example dataset:

| Packets | Bytes | Label |
|--------|------|------|
| 200 | 800 | Normal |
| 5000 | 90000 | Attack |

The model learns patterns between input data and output labels.

After training, it can predict new events.

Example:

```
New traffic detected → Model predicts → Possible attack
```

---

# Real World Example

Predicting **house prices**

Input features:

- number of bedrooms
- location
- square footage

Output:

```
House price
```

The model learns from historical data and predicts the price of new houses.

---

# Steps in Supervised Learning

### 1 Data Collection

Collect historical labeled data.

Examples:

- login success / failure
- normal traffic / attack traffic
- malware / clean file

---

### 2 Data Preprocessing

Clean and prepare data.

Tasks include:

- removing missing values
- correcting formats
- filtering noise

---

### 3 Feature Selection

Choose important variables.

Example firewall data features:

```
bytes_received
bytes_sent
packets_received
packets_sent
```

---

### 4 Model Selection

Choose the algorithm.

Common algorithms used in Splunk:

```
Linear Regression
Logistic Regression
Decision Trees
Random Forest
```

---

### 5 Training

The model studies historical data and learns patterns.

---

### 6 Evaluation

Test the model using metrics such as:

```
Accuracy
Precision
Recall
```

---

### 7 Deployment

The trained model predicts future events.

Example:

```
Predict disk usage
Predict login attempts
Predict malware traffic
```

---

# 5. Examples of Supervised ML in Splunk

MLTK includes example datasets.

Examples include:

### Predict Disk Utilization

Dataset:

```
server_power.csv
```

Purpose:

Predict future disk usage.

---

### Predict VPN Usage

Predict abnormal VPN usage patterns.

Use case:

Detect suspicious remote access.

---

### Predict Malware Presence

Dataset:

```
firewall_traffic.csv
```

Algorithm used:

```
Logistic Regression
```

Goal:

Predict if traffic contains malware.

---

# Dataset Splitting

Machine learning models usually split data:

```
70% → training
30% → testing
```

Example:

```
50,000 events dataset
```

```
35,000 used for training
15,000 used for testing
```

---

# 6. Unsupervised Machine Learning

Unsupervised learning works with **unlabeled data**.

The algorithm finds patterns without knowing the correct answers.

Idea:

```
No labels → discover hidden patterns
```

---

# Real World Example

Imagine analyzing user behavior logs.

You may not know which users are suspicious.

Clustering may group users like:

```
Cluster 1 → normal users
Cluster 2 → heavy users
Cluster 3 → suspicious activity
```

---

# Two Main Unsupervised Techniques

## Clustering

Groups similar data points together.

Example:

```
Group similar network traffic patterns
```

---

## Dimensionality Reduction

Simplifies large datasets while keeping important information.

Popular method:

```
PCA (Principal Component Analysis)
```

---

# Example in Splunk

### Cluster Mortgage Loans

Dataset:

```
mortgage_loan_ny.csv
```

Goal:

Group loans based on similar characteristics.

---

### Cluster Houses

Dataset:

```
housing.csv
```

Goal:

Group houses based on property features.

---

# Algorithm Used

```
K-Means Clustering
```

K-Means works by grouping data points into clusters based on similarity.

---

# 7. Anomaly Detection in Splunk

An anomaly is a data point that is significantly different from normal behavior.

Examples:

```
sudden login spike
unexpected network traffic
unusual system activity
```

MLTK can detect anomalies automatically.

---

# Real World Example

Normal network traffic:

```
200 MB per hour
```

Sudden spike:

```
5 GB transfer
```

This could indicate:

```
data exfiltration attack
```

---

# Benefits of Anomaly Detection

- early threat detection
- system monitoring
- fraud detection
- proactive security

---

# 8. Event Correlation in Splunk

Event correlation identifies relationships between events.

Example sequence:

```
User login
Privilege escalation
Sensitive file access
```

Individually these events may look normal.

But together they indicate:

```
possible insider attack
```

Splunk correlates events to identify patterns.

---

# Correlation Techniques

### Temporal Correlation

Events related by time.

Example:

```
Multiple login failures within seconds
```

---

### Sequence Analysis

Detect abnormal sequences of events.

Example:

```
view → download → delete logs
```

---

### Cross System Correlation

Combine data from multiple systems.

Example:

```
Firewall + Server logs + Authentication logs
```

---

# 9. Transaction Command

The `transaction` command groups related events.

Example:

```
transaction clientIP maxspan=30s maxpause=5s
```

Fields created automatically:

```
duration
eventcount
```

---

# Example Transaction

User actions:

```
view item
add to cart
purchase item
```

Grouped as a single transaction.

---

# 10. Useful Stats Commands

Example:

```
stats max(bytes) as largest
stats min(bytes) as smallest
stats avg(bytes) as average
```

Percentile calculation:

```
p95(bytes)
```

Meaning:

95% of values fall below this number.

Useful for detecting outliers.

---

# Ranking Example

```
stats count as total_purchases by itemID
| sort - total_purchases
| streamstats count as rank
```

Purpose:

Identify most purchased products.

---

# 11. Why Machine Learning Matters in Splunk

Machine learning enables organizations to:

- predict system failures
- detect cyber attacks
- automate monitoring
- discover hidden patterns

Instead of reacting to problems, organizations become **proactive**.

---

# 12. Key Memory Summary

Supervised Learning:

```
Labeled Data → Predict Outcomes
```

Unsupervised Learning:

```
No Labels → Discover Patterns
```

Anomaly Detection:

```
Find unusual behavior
```

Event Correlation:

```
Connect related events
```

---

# Final Insight

Machine learning transforms Splunk from a simple log analyzer into an intelligent analytics platform.

Traditional approach:

```
Search logs → Investigate
```

Machine learning approach:

```
Learn patterns → Predict problems → Detect threats automatically
```

This is why **machine learning is becoming essential for modern cybersecurity operations**.

---

✍️ Notes By Abhishek (Ez Abyss)
