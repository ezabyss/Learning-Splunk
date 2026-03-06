# Supervised Machine Learning in Splunk

---

# Big Idea

Supervised Machine Learning means:

> We train a system using **data where the correct answer is already known**, so it can learn patterns and **predict future outcomes**.

Simple formula:

```
Past Data + Known Results → Learn Pattern → Predict Future Results
```

Splunk uses this concept through the **Machine Learning Toolkit (MLTK)**.

Instead of manually analyzing logs, we can **teach Splunk to recognize patterns automatically.**

---

# Simple Real-World Analogy

Imagine a **doctor diagnosing diseases**.

The doctor studies thousands of past patients:

| Symptoms | Diagnosis |
|--------|-----------|
| Fever + cough | Flu |
| Chest pain + breath issues | Heart problem |
| Headache + fatigue | Migraine |

Over time the doctor learns patterns.

Now when a new patient arrives, the doctor can **predict the disease quickly**.

Supervised ML works the same way.

```
Past labeled data → Learn relationships → Predict new outcomes
```

---

# Splunk Example (Security)

Suppose a company collects firewall logs.

Each event contains fields like:

- bytes sent
- packets sent
- packets received
- source IP
- destination IP

Past events are labeled as:

| Traffic Pattern | Label |
|---------------|------|
| Normal browsing | Normal |
| Port scanning | Attack |
| Malware traffic | Malicious |

The ML model learns patterns.

Now when **new traffic appears**, Splunk can automatically predict:

```
Normal traffic
OR
Potential attack
```

This helps security teams detect threats faster.

---

# Why This Matters in Splunk

Normally Splunk does:

```
Search logs → Investigate → Respond
```

With Machine Learning:

```
Analyze logs → Learn patterns → Predict problems
```

This moves organizations from **reactive → proactive security**.

---

# How Supervised Learning Works (Step by Step)

## 1. Data Collection

First collect historical data.

Example in Splunk:

```
Firewall logs
Login events
System metrics
Network traffic
```

Important requirement:

The data must contain **correct answers (labels).**

Example:

```
login_success = normal
login_failure = suspicious
```

---

# 2. Data Preprocessing

Before training the model, we clean the data.

Typical tasks:

- remove corrupted events
- normalize fields
- remove missing values
- convert formats

Example:

Bad log:

```
bytes="unknown"
```

Clean log:

```
bytes=1200
```

Clean data → better predictions.

---

# 3. Feature Selection

Features are **important fields used to make predictions**.

Example firewall dataset:

| Field | Meaning |
|------|------|
| bytes_received | data downloaded |
| bytes_sent | data uploaded |
| packets_received | incoming packets |
| packets_sent | outgoing packets |

Not all fields are useful.

Choosing the **right features improves model accuracy.**

---

# 4. Model Selection

Now choose a machine learning algorithm.

Common models in Splunk MLTK:

### Linear Regression
Used when predicting **numbers**.

Example:

```
Predict disk usage
Predict server load
Predict bandwidth usage
```

---

### Logistic Regression

Used when predicting **categories**.

Example:

```
Attack vs Normal
Malware vs Clean
Login Success vs Failure
```

---

# 5. Training the Model

The model studies historical data.

Example training set:

| Packets | Bytes | Label |
|-------|------|------|
| 300 | 1200 | Normal |
| 5000 | 90000 | Attack |
| 200 | 800 | Normal |

The model learns:

```
Large packets + large bytes → suspicious traffic
```

---

# 6. Model Evaluation

After training we test the model.

Common evaluation metrics:

| Metric | Meaning |
|------|------|
| Accuracy | Correct predictions |
| Precision | Correct positive predictions |
| Recall | Ability to detect real threats |

Example:

```
Model accuracy = 92%
```

Good enough for deployment.

---

# 7. Deployment

Now the trained model runs on **live incoming data**.

Example:

```
New firewall traffic detected
```

Splunk predicts:

```
80% probability → Malware activity
```

SOC team receives alert.

---

# Machine Learning Toolkit (MLTK)

Splunk provides **Machine Learning Toolkit (MLTK)** to simplify this process.

It includes:

- built-in algorithms
- training tools
- visualization dashboards
- example datasets

This allows beginners to experiment with ML quickly.

---

# Example Built-in ML Use Cases

MLTK provides ready-to-run examples.

### Predict Disk Utilization

Dataset:

```
server_power.csv
```

Prediction:

```
Future disk usage based on past disk activity
```

Real use case:

Predict when a server will run out of storage.

---

# Predict Future Logins

Prediction:

```
Future login patterns
```

Real use case:

Detect unusual login spikes.

Example:

```
Normal login per hour = 20
Sudden login attempts = 300
```

Possible **brute-force attack**.

---

# Predict VPN Usage

Prediction:

```
Future VPN usage patterns
```

Real use case:

Detect abnormal remote access behavior.

---

# Predict Malware Presence

Dataset:

```
firewall_traffic.csv
```

Algorithm used:

```
Logistic Regression
```

Splunk predicts whether traffic contains malware patterns.

---

# Dataset Splitting

Typical ML workflow:

```
70% → Training data
30% → Testing data
```

Example:

```
50,000 events dataset
```

```
35,000 events → train model
15,000 events → test model
```

Testing ensures the model works correctly.

---

# Why Top Analysts Use Machine Learning

Machine learning helps with:

### Security Monitoring

Detect:

- malware
- intrusions
- suspicious behavior

---

### IT Operations

Predict:

- server failure
- CPU spikes
- storage exhaustion

---

### Business Intelligence

Predict:

- customer behavior
- product demand
- churn risk

---

# Memory Trick

Remember the ML workflow:

```
Collect Data
Clean Data
Choose Features
Pick Model
Train Model
Evaluate Model
Deploy Model
```

Shortcut memory trick:

```
C C F M T E D
```

```
Collect → Clean → Features → Model → Train → Evaluate → Deploy
```

---

# Key Insight

Machine Learning transforms Splunk from:

```
Log Analyzer → Intelligent Prediction Engine
```

Instead of asking:

```
What happened?
```

We start asking:

```
What will happen next?
```

That is the real power of **Splunk + Machine Learning**.

---

# Final Thought

If you understand **Supervised Learning**, you unlock the ability to:

- predict system failures
- detect cyber attacks
- automate monitoring
- uncover hidden patterns in data

And that is why **machine learning is becoming essential for modern SOC and IT operations**.

---

✍️ Notes By Abhishek (Ez Abyss)
