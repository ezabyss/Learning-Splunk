# Customizing Splunk Security Essentials (SSE)

---

# 1. Why Customizing Splunk Security Essentials Matters

After installing **Splunk Security Essentials (SSE)**, the next step is to **configure and customize it properly**.

Why?

Because SSE relies on additional apps and configurations to:

- visualize security data
- improve analytics
- run detection searches
- support investigation workflows

Think of it like this:

```
Install SSE → Configure environment → Enable detection features
```

Without customization, the app **will not operate at its full potential**.

---

# 2. Accessing SSE Configuration

To customize the application:

```
Splunk Security Essentials → Configuration
```

Inside the configuration section you will see:

- required apps
- recommended apps
- visualization apps
- search configurations

This section helps ensure SSE works correctly.

---

# 3. Installing Required Visualization Apps

Some **visualization apps** improve how security data is displayed.

Examples include:

### Sankey Diagram App

Purpose:

```
Visualize data flows between systems
```

Example SOC use case:

```
User → Server → Database access
```

Sankey diagrams show how events move between systems.

---

### Radar Chart Visualization

Purpose:

```
Compare multiple security metrics
```

Example:

Comparing:

- failed logins
- malware alerts
- suspicious network traffic
- privilege escalation attempts

Radar charts help visualize **security posture across multiple dimensions**.

---

### Timeline Visualization App

Purpose:

```
Display events along a timeline
```

Example SOC scenario:

```
09:00 – Login attempt
09:01 – Privilege escalation
09:03 – File download
```

Timeline view helps analysts understand **attack progression**.

---

# 4. Installing Apps from Splunk

Important tip from the lesson:

Do NOT install directly using the SSE link.

Instead follow this process:

```
Copy the app name
```

Then:

```
Apps → Find More Apps
```

Search the app name and install it.

Steps:

1. Copy application name
2. Go to:

```
Apps → Find More Apps
```

3. Search for the app
4. Click **Install**
5. Enter Splunk.com credentials
6. Click:

```
Agree and Install
```

The app will automatically install.

---

# 5. Important Apps to Install

Recommended apps include:

### Visualization Apps

```
Sankey Diagram
Radar Chart
Timeline Visualization
```

These help analysts understand data better.

---

### Analytics Apps

```
Machine Learning Toolkit (MLTK)
URL Toolbox
```

These provide advanced analysis capabilities.

---

# 6. URL Toolbox

The **URL Toolbox app** is useful for security investigations.

It can analyze:

```
URLs
Domains
IP reputation
Threat intelligence
```

SOC analysts use it to investigate:

```
malicious links
phishing domains
command-and-control servers
```

Example investigation:

```
Suspicious URL detected in logs
```

URL Toolbox can help identify if the domain is malicious.

---

# 7. Optional Apps

SSE also lists **optional apps**.

However:

```
You do NOT need to install all of them.
```

Installing too many apps may:

- increase system load
- add unnecessary complexity

Recommended approach:

```
Install only visualization + analytics apps
```

---

# 8. Scheduled Searches

Another important configuration step:

```
Scheduled Searches
```

These searches run automatically.

Example detection searches:

```
Detect brute-force login attempts
Detect suspicious IP connections
Detect new administrator accounts
```

Ensure scheduled searches are:

```
Enabled
```

Status should display:

```
Enabled
```

This ensures automated security monitoring.

---

# 9. Why This Configuration Matters (Real SOC View)

Imagine a SOC team monitoring a network.

Without visualization:

```
Analysts read raw logs manually
```

With SSE visualizations:

```
Attack paths become visible
Threat patterns become easier to detect
```

Example:

```
Sankey diagram shows attacker movement across systems
```

This makes investigations faster.

---

# 10. Real SOC Investigation Example

Suppose the logs show:

```
User login from unknown country
Privilege escalation
Large file transfer
```

Using SSE tools:

- timeline view shows attack sequence
- radar chart highlights abnormal activity
- Sankey diagram shows data movement

The analyst can quickly identify:

```
Possible account compromise
```

---

# 11. Memory Shortcut

To remember the **customization process**:

```
C I V S
```

```
Configure SSE
Install required apps
Visualize data
Schedule detection searches
```

---

# Final Insight

Customizing Splunk Security Essentials is a critical step in building a **functional SOC monitoring environment**.

Proper configuration enables:

```
better visualizations
automated detections
improved threat investigations
```

Once customization is complete, analysts can start **searching security data and detecting threats more effectively**.

---

✍️ Notes By Abhishek (Ez Abyss)
