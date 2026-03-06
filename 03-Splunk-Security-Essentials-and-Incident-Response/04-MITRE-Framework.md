# MITRE ATT&CK Framework in Splunk Security Essentials

---

# 1. What is the MITRE ATT&CK Framework?

MITRE ATT&CK stands for:

```
Adversarial Tactics, Techniques, and Common Knowledge
```

It is a **globally recognized cybersecurity framework** that documents how attackers behave in real-world attacks.

Instead of focusing only on vulnerabilities, it focuses on:

```
How attackers actually perform attacks
```

Security teams use it to:

- understand attacker behavior
- improve threat detection
- build stronger security monitoring

---

# 2. Why MITRE ATT&CK is Important

Traditional security focuses on:

```
Blocking threats
```

MITRE ATT&CK focuses on:

```
Understanding attacker behavior
```

This helps organizations answer questions like:

```
How do attackers move inside networks?
How do they steal credentials?
How do they maintain persistence?
```

This knowledge helps security teams build **better detection strategies**.

---

# 3. MITRE ATT&CK Matrix Structure

The framework is organized into a **matrix**.

The matrix contains:

```
Rows → Tactics
Columns → Techniques
```

---

## Tactics

Tactics describe **the attacker’s goal at each stage of the attack**.

Examples:

```
Initial Access
Execution
Persistence
Privilege Escalation
Defense Evasion
Credential Access
Discovery
Lateral Movement
Collection
Exfiltration
Command and Control
Impact
```

Each tactic represents **a stage of an attack lifecycle**.

---

## Techniques

Techniques describe **how attackers perform each tactic**.

Example:

Tactic:

```
Credential Access
```

Possible techniques:

```
Password dumping
Credential harvesting
Brute force attacks
```

---

# 4. Platforms Supported by MITRE ATT&CK

The framework covers multiple operating systems and environments.

Examples include:

```
Windows
Linux
macOS
Cloud environments
Containers
Mobile devices
```

This makes MITRE ATT&CK useful across many security environments.

---

# 5. MITRE ATT&CK in Splunk Security Essentials

Splunk Security Essentials integrates the MITRE ATT&CK framework to help analysts:

- map detections to attacker techniques
- understand attack stages
- prioritize security monitoring

Location in SSE:

```
Analytics Advisor → MITRE ATT&CK Framework
```

Here you can see:

- ATT&CK tactics
- detection coverage
- available detection searches
- missing detections

---

# 6. ATT&CK Visualizations in Splunk

Splunk Security Essentials can visualize the ATT&CK framework using different charts.

Examples include:

---

## Chart View

Displays detection coverage across attack techniques.

Helps analysts see:

```
Which attack techniques are monitored
Which ones are missing
```

---

## Radar View

Displays **security coverage across multiple attack categories**.

Example:

```
Credential access
Privilege escalation
Lateral movement
Exfiltration
```

Radar charts quickly show **security gaps**.

---

## Sankey Diagram

Shows relationships between:

```
Attack techniques
Data sources
Security detections
```

Example flow:

```
Technique → Detection Rule → Data Source
```

This helps understand **how attacks are detected in the system**.

---

# 7. ATT&CK Content Recommendations

Splunk Security Essentials can recommend detection content based on MITRE ATT&CK.

Examples include detection categories such as:

```
Malware
Phishing
Ransomware
Network attacks
Cloud security threats
Web attacks
Threat intelligence
Vulnerability scanning
```

These recommendations help security teams build **better detection coverage**.

---

# 8. Data Source Mapping

ATT&CK detections rely on security data sources.

Examples include:

```
Windows event logs
DNS logs
Firewall logs
Endpoint activity
Network traffic
Authentication logs
```

If a required data source is missing, Splunk may show:

```
No content meeting the criteria
```

This means the detection cannot run without proper data.

---

# 9. Risk-Based Alerting

Splunk Security Essentials also supports **Risk-Based Alerting (RBA)**.

Instead of triggering alerts for every event, RBA assigns **risk scores**.

Example scenario:

```
Multiple failed logins → risk score 20
Privilege escalation → risk score 40
Suspicious file download → risk score 40
```

Total risk score:

```
100
```

When risk exceeds a threshold, Splunk generates a **high-priority alert**.

This reduces false positives and helps analysts focus on **real threats**.

---

# 10. Real SOC Example

Imagine an attacker compromises a system.

Attack sequence:

```
Phishing email
User login from unusual IP
Privilege escalation
Lateral movement
Data exfiltration
```

MITRE ATT&CK mapping may show:

| Stage | ATT&CK Tactic |
|------|---------------|
| Phishing | Initial Access |
| Suspicious login | Credential Access |
| Privilege escalation | Privilege Escalation |
| Lateral movement | Lateral Movement |
| Data theft | Exfiltration |

Splunk Security Essentials helps analysts visualize this entire attack path.

---

# 11. Memory Shortcut

To remember ATT&CK structure:

```
T → T
```

```
Tactics → Attacker Goal
Techniques → How Attack Happens
```

Think of it as:

```
Goal → Method
```

---

# Final Insight

MITRE ATT&CK helps security teams shift from:

```
Reactive security → Behavior-based detection
```

Instead of only detecting malware signatures, organizations can detect **attacker techniques**.

This makes Splunk Security Essentials a powerful tool for:

```
Threat detection
Attack investigation
Security maturity improvement
```

---

✍️ Notes By Abhishek (Ez Abyss)
