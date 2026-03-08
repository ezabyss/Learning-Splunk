# Splunk Security Essentials (SSE) — Advanced Options
### Alerts, Content Mapping & App Configuration

---

# 1. Advanced Options in Splunk Security Essentials

The **Advanced section** in Splunk Security Essentials provides additional tools for monitoring and managing security operations.

These options include:

- Alerts
- Setup
- Content Mapping
- Review App Configuration

These features help security analysts **track threats, review detections, and monitor security posture**.

---

# 2. Alerts in Splunk Security Essentials

Alerts are **automated notifications generated when suspicious activity is detected**.

Location:

```
Advanced → Alerts
```

If alerts are triggered, they will appear in this section.

Example alert triggers:

- Multiple failed login attempts
- Suspicious network traffic
- Privilege escalation
- Malware detection

If no alerts have been triggered yet, the list will appear **empty**.

---

# 3. Setup Section

The **Setup section** allows analysts to configure how SSE interacts with available data.

Location:

```
Advanced → Setup
```

One important component inside Setup is:

```
Data Inventory
```

Data Inventory identifies **what security logs are available in Splunk**.

Examples of detected data sources:

- Windows security logs
- DNS logs
- Domain controller logs
- Application logs

These logs enable **security monitoring and detection rules**.

---

# 4. Content Mapping

Content Mapping shows how **security detections are mapped to available data sources**.

Location:

```
Setup → Content Mapping
```

This section helps analysts understand:

- which detections are active
- which detections require more data
- which security rules are available

Content mapping shows categories such as:

- Authentication monitoring
- Suspicious data movement
- Public cloud storage activity

---

# 5. Example Detection: Authentication Monitoring

One example detection is **Authentication Monitoring**.

Purpose:

Detect unusual login behavior.

Possible indicators include:

- login attempts from new locations
- multiple login failures
- unusual authentication patterns

When executed, the detection displays:

```
Total results
Outliers
Raw events
```

Analysts can review these events to determine if suspicious activity occurred.

---

# 6. Data Availability

Some detections may show:

```
Data unavailable
```

This happens when the required log sources are **not ingested into Splunk**.

Example missing sources:

- cloud logs
- endpoint activity logs
- network traffic logs

Without these logs, certain detections cannot run.

---

# 7. Viewing Detection Results

When detections run successfully, analysts can view results including:

- suspicious events
- raw log entries
- detection statistics

Results can also be exported as:

```
CSV
Excel
Print reports
```

This helps analysts **share investigation results with security teams**.

---

# 8. Review App Configuration

Another important advanced option is:

```
Review App Configuration
```

This section displays **security posture dashboards** for SSE.

It summarizes:

- security detection coverage
- security data sources
- security analytics results

This provides a **high-level overview of the organization's security monitoring capability**.

---

# 9. Demo Data vs Live Data

SSE supports two types of data:

## Demo Data

Demo data is **preloaded example data**.

Purpose:

- learning
- testing detections
- training security analysts

Example demo results:

- simulated malware alerts
- simulated login events
- simulated attack behaviors

---

## Live Data

Live data comes from **actual logs ingested into Splunk**.

Examples:

- Windows security events
- administrator logins
- DNS queries
- system activity logs

Live data allows organizations to monitor **real security events**.

---

# 10. Example: Administrator Account Monitoring

Example detection:

```
Local New Admin Account
```

Purpose:

Detect when new administrator accounts are created.

Example output fields:

| Account Name | Created Time | System |
|---------------|--------------|-------|
| admin_test | 09:21 | Server01 |
| temp_admin | 11:02 | Server02 |

This helps detect **privilege escalation attacks**.

---

# 11. Continuous Data Ingestion

For SSE to function properly, **logs must continuously flow into Splunk**.

Example sources:

- Windows event logs
- authentication logs
- DNS logs
- network traffic logs

Without continuous data ingestion:

```
Live detections will show no results
```

This is why log collection is **critical for SOC monitoring**.

---

# 12. Real SOC Example

Imagine a SOC monitoring system logs.

Events detected:

- administrator login
- new admin account creation
- suspicious login location

SSE detection triggers an alert:

```
Possible unauthorized privilege escalation
```

The SOC team can immediately investigate the affected system.

---

# 13. Why These Advanced Features Matter

The advanced features in SSE help analysts:

- track security alerts
- review detection coverage
- analyze suspicious activity
- monitor security posture
- export investigation results

They provide a **complete monitoring environment for SOC operations**.

---

# Memory Shortcut

Remember advanced SSE features using:

```
A C R
```

```
Alerts
Content Mapping
Review Configuration
```

These help analysts **detect, analyze, and review security activity**.

---

# Final Insight

The **Advanced features in Splunk Security Essentials complete the security monitoring workflow**.

They allow organizations to:

```
collect logs
run detections
generate alerts
review security posture
investigate threats
```

When combined with dashboards, datasets, and reports, SSE becomes a powerful tool for **building a real SOC monitoring environment**.

---

✍️ Notes By Abhishek (Ez Abyss)
