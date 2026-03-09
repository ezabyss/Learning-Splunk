# Splunk SPL Cheat Sheet for SOC Analysts
### Top SOC Commands for Security Monitoring & Threat Hunting

---

# 1. Basic Search Commands

## Search Everything in an Index

```spl
index=security
```

Search all events stored in the **security index**.

---

## Search by Source Type

```spl
index=security sourcetype=firewall
```

Search only firewall logs.

---

## Search by Host

```spl
index=security host=server01
```

Search logs from a specific host.

---

## Search by Time

```spl
index=security earliest=-24h
```

Search events from the last **24 hours**.

---

# 2. Filtering Events

## AND Condition

```spl
index=security user=admin AND action=login
```

Both conditions must be true.

---

## OR Condition

```spl
index=security user=admin OR user=root
```

Either condition can be true.

---

## NOT Condition

```spl
index=security NOT user=guest
```

Exclude guest user events.

---

# 3. Table Command

Display specific fields.

```spl
index=security
| table _time user src_ip action
```

Output example:

| time | user | ip | action |

---

# 4. Stats Command (Most Important)

Used for **aggregating data**.

Example:

```spl
index=security
| stats count by user
```

Shows number of events per user.

---

## Multiple Statistics

```spl
index=security
| stats count avg(duration) max(duration) by user
```

Calculates:

- count
- average
- maximum

---

# 5. Top Command

Find most frequent values.

```spl
index=security
| top user
```

Shows most active users.

---

# 6. Rare Command

Find unusual events.

```spl
index=security
| rare user
```

Helps detect suspicious or rare users.

---

# 7. Timechart Command

Create time-based graphs.

```spl
index=security
| timechart count by action
```

Useful for detecting spikes.

---

# 8. Eval Command

Create new fields or calculations.

Example:

```spl
index=security
| eval risk_score=if(action="failed_login",10,1)
```

Adds a risk score.

---

# 9. Rex Command (Regex Extraction)

Extract fields from raw logs.

Example:

```spl
index=security
| rex "user=(?<username>\w+)"
```

Extracts username from log.

---

# 10. Regex Filtering

Filter events using regex.

```spl
index=security
| regex user="admin.*"
```

Find usernames starting with "admin".

---

# 11. Sort Command

Sort results.

```spl
index=security
| sort -count
```

Descending order.

---

# 12. Dedup Command

Remove duplicate events.

```spl
index=security
| dedup user
```

Keeps one event per user.

---

# 13. Where Command

Apply advanced filtering.

Example:

```spl
index=security
| where duration > 100
```

Filters events with duration greater than 100.

---

# 14. Transaction Command

Group related events.

Example:

```spl
index=security
| transaction user maxspan=5m
```

Groups events for the same user within 5 minutes.

---

# 15. Lookup Command

Add external data to events.

Example:

```spl
index=security
| lookup malicious_ips ip as src_ip
```

Matches IPs against threat intelligence.

---

# 16. Join Command

Combine two searches.

Example:

```spl
index=auth
| join user
[ search index=web ]
```

Combines authentication and web logs.

---

# 17. Eventstats Command

Adds statistical data to each event.

Example:

```spl
index=security
| eventstats count by user
```

Each event shows total count.

---

# 18. Streamstats Command

Calculates running totals.

Example:

```spl
index=security
| streamstats count by user
```

Useful for sequence detection.

---

# 19. Detect Brute Force Attack

Example SOC query:

```spl
index=auth action=failed
| stats count by user src_ip
| where count > 10
```

Detect users with many failed logins.

---

# 20. Detect Suspicious Login Locations

```spl
index=auth
| stats dc(src_ip) by user
| where dc(src_ip) > 5
```

Detect users logging in from many IPs.

---

# 21. Detect Rare Processes

```spl
index=endpoint
| rare process_name
```

Useful for malware detection.

---

# 22. Detect Large Data Transfers

```spl
index=network
| stats sum(bytes_out) by src_ip
| where sum(bytes_out) > 100000000
```

Possible **data exfiltration**.

---

# 23. Detect New Admin Accounts

```spl
index=windows EventCode=4720
| table _time user account_created
```

Detect account creation events.

---

# 24. Detect Privilege Escalation

```spl
index=windows EventCode=4672
```

Detect privileged logins.

---

# 25. Detect Suspicious PowerShell

```spl
index=windows process="powershell.exe"
| table _time user command
```

Often used in attacks.

---

# Common SPL Commands Summary

| Command | Purpose |
|------|------|
| search | Find events |
| table | Display fields |
| stats | Aggregate data |
| eval | Create fields |
| rex | Extract fields |
| regex | Filter using regex |
| sort | Sort results |
| dedup | Remove duplicates |
| timechart | Time analysis |
| transaction | Group related events |

---

# SOC Investigation Workflow Using SPL

Typical workflow:

```
1. Search logs
2. Filter suspicious activity
3. Aggregate events
4. Detect anomalies
5. Investigate threats
```

Example:

```
Logs → SPL Query → Detection → Investigation
```

---

# Final Tip

SOC analysts should master these **10 core commands first**:

```
search
stats
eval
rex
regex
table
timechart
top
rare
transaction
```

These commands cover **most security investigations in Splunk**.

---

✍️ Notes By Abhishek (Ez Abyss)
