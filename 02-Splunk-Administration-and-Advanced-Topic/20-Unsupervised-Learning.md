# Unsupervised Machine Learning in Splunk

---

# Big Idea

Unsupervised Machine Learning means:

> The algorithm learns from data **without any labeled answers**.

Unlike supervised learning, we **do not tell the model what the correct output is**.

Instead, the algorithm explores the dataset and **discovers patterns on its own**.

Simple mental model:

```
Data without labels → Find hidden patterns → Discover structure
```

Splunk can do this using the **Machine Learning Toolkit (MLTK)**.

---

# Simple Real-World Analogy

Imagine a teacher giving students a box of mixed fruits:

```
🍎 Apples
🍊 Oranges
🍌 Bananas
🍇 Grapes
```

But the fruits are **not labeled**.

The students group them by similarity:

- round red fruits → apples
- orange colored fruits → oranges
- long yellow fruits → bananas

This grouping process is exactly what **clustering algorithms** do.

---

# Why Unsupervised Learning Matters

Many real-world datasets **do not have labels**.

Examples:

- network traffic logs
- user behavior logs
- application logs
- system performance metrics

In these cases we cannot say:

```
This is an attack
This is normal
```

Instead we allow the algorithm to **discover patterns automatically**.

---

# Two Main Types of Unsupervised Learning

## 1. Clustering

Clustering groups **similar data points together**.

Example:

```
User Activity Logs
```

The algorithm may automatically group users like:

| Cluster | Behavior |
|------|------|
| Cluster 1 | Heavy users |
| Cluster 2 | Casual users |
| Cluster 3 | Suspicious behavior |

This helps analysts quickly identify unusual patterns.

---

## 2. Dimensionality Reduction

Some datasets contain **too many features**.

Example:

```
Firewall logs with 100+ fields
```

Dimensionality reduction simplifies the dataset while keeping the important information.

Popular technique:

```
PCA (Principal Component Analysis)
```

Benefits:

- reduces complexity
- improves visualization
- speeds up analysis

---

# Real-World Splunk Example (Security)

Imagine a company analyzing **network traffic logs**.

Fields may include:

- source IP
- destination IP
- bytes transferred
- connection duration
- packet count

We do not know which events are malicious.

Using clustering, Splunk may group events like:

```
Cluster A → normal browsing traffic
Cluster B → heavy download activity
Cluster C → unusual network behavior
```

Cluster C might indicate **possible attacks or malware communication**.

---

# Steps to Apply Unsupervised Learning

## 1. Data Collection

First gather the dataset.

Example sources:

- firewall logs
- system logs
- user activity data
- application events

---

# 2. Data Processing

Before analysis, the data must be cleaned.

Typical tasks:

- remove invalid entries
- normalize values
- filter irrelevant fields

Clean data produces **better clustering results**.

---

# 3. Choose the Algorithm

Depending on the goal, select the algorithm.

Common unsupervised algorithms used in Splunk:

### K-Means Clustering

Groups events into clusters based on similarity.

Example:

```
Network traffic clusters
```

---

### PCA (Dimensionality Reduction)

Reduces the number of variables while keeping important information.

Example:

```
Reducing 50 metrics → 5 meaningful components
```

---

# Example: Clustering in Splunk

Splunk Machine Learning Toolkit provides built-in examples.

Example:

```
Cluster Mortgage Loans
```

Dataset used:

```
mortgage_loan_ny.csv
```

Goal:

Cluster mortgage loans based on their features.

---

# Another Example

```
Cluster Houses by Property Description
```

Dataset:

```
housing.csv
```

The model groups houses based on characteristics like:

- size
- location
- price
- property type

Result:

Different clusters representing **similar house types**.

---

# Algorithm Used

These examples typically use:

```
K-Means Clustering
```

How K-Means works:

1. Choose number of clusters (K)
2. Assign data points to closest cluster
3. Recalculate cluster centers
4. Repeat until clusters stabilize

Result:

```
Groups of similar data points
```

---

# Visualizing Clusters in Splunk

After clustering, Splunk can display results using visualizations.

Example chart:

```
Cluster 1 → normal user behavior
Cluster 2 → heavy system usage
Cluster 3 → unusual activity
```

Visualization helps analysts **quickly spot abnormal clusters**.

---

# Real SOC Example

Suppose we analyze **VPN login patterns**.

Features:

- login time
- login location
- login frequency
- device type

Clustering might reveal:

| Cluster | Behavior |
|------|------|
| Cluster 1 | normal employees |
| Cluster 2 | remote workers |
| Cluster 3 | suspicious login activity |

Cluster 3 might indicate:

```
Account compromise
```

---

# Why Unsupervised Learning is Powerful

It allows us to discover insights that we did not know existed.

Examples:

- hidden user groups
- abnormal network patterns
- unusual system activity
- unexpected correlations in data

---

# Memory Trick

Remember unsupervised ML like this:

```
No Labels → Discover Patterns
```

Two main techniques:

```
Clustering → Group similar data
Dimensionality Reduction → Simplify complex data
```

Quick memory shortcut:

```
C + D
```

```
Clustering
Dimensionality Reduction
```

---

# Key Insight

Supervised ML answers:

```
What will happen?
```

Unsupervised ML answers:

```
What patterns exist in this data?
```

This is extremely powerful for **exploratory data analysis**.

---

# Final Thought

In Splunk, unsupervised learning helps analysts move from:

```
Manual investigation → Automated pattern discovery
```

Instead of searching for problems manually, Splunk can **automatically highlight unusual behavior and hidden patterns**.

This is why unsupervised learning is very valuable for:

- cybersecurity
- IT operations
- fraud detection
- behavioral analytics

---

✍️ Notes By Abhishek (Ez Abyss)
