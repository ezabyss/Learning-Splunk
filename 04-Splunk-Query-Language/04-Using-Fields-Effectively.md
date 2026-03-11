# Using Fields in Splunk 
### Understanding Field Extraction, Transformation, and Analysis

---

# 1. What Are Fields in Splunk?

Fields are **key pieces of information extracted from raw log data**.

They help Splunk turn **unstructured logs** into **structured data** that can be searched, filtered, and analyzed.

Example raw log:

```
Failed login from IP=192.168.1.10 user=admin port=22
```

Extracted fields:

| Field | Value |
|------|------|
| ip | 192.168.1.10 |
| user | admin |
| port | 22 |

Simple idea:

```
Raw Log → Extract Fields → Analyze Data
```

---

# 2. Why Fields Are Important

Fields allow analysts to:

- search specific information
- filter logs quickly
- group data
- detect patterns
- investigate security incidents

Without fields, logs would be **just large text blocks**.

Fields make data **searchable and meaningful**.

---

# 3. Basic Field Extraction

Field extraction converts **raw log text into structured fields**.

One common method uses the **rex command** with regex.

Example:

```spl
index=authentication_logs
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| table ip
```

This extracts an **IP address field**.

---

# 4. Automatic Field Extraction

Splunk can automatically detect fields when logs follow common formats.

Examples automatically extracted:

- IP addresses
- URLs
- file paths
- timestamps
- usernames

This is called **Field Discovery**.

Benefits:

- saves time
- reduces manual regex work
- speeds up investigations

---

# 5. Transforming Fields with `eval`

After extracting fields, we can modify them using the **eval command**.

`eval` allows:

- calculations
- conditions
- string manipulation
- new field creation

Example:

Convert seconds to minutes.

```spl
index=call_logs
| eval duration_minutes = duration/60
| table duration duration_minutes
```

---

# 6. Enriching Fields Using Lookups

Lookups add **external context** to field values.

Example:

Add **country information** to an IP address.

Lookup table example:

| ip | country |
|---|---|
| 192.168.1.1 | USA |
| 185.x.x.x | Russia |

Splunk query:

```spl
| lookup ip_lookup ip OUTPUT country
```

This enriches the log data.

SOC use cases:

- IP reputation
- geolocation
- threat intelligence

---

# 7. Time-Based Fields

Many logs include **timestamp fields**.

Splunk can analyze:

- time trends
- event spikes
- attack timelines

Example time analysis query:

```spl
index=authentication_logs
| timechart count by user
```

This shows **login activity over time**.

---

# 8. Real SOC Example

Example log:

```
User login failed from 203.0.113.25 user=root
```

Extract fields:

```spl
index=auth_logs
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| rex field=_raw "user=(?<username>\w+)"
| stats count by ip username
```

This helps detect:

- brute force attempts
- suspicious IPs
- targeted user attacks

---

# 9. Field Management Best Practices

### 1. Use Automatic Extraction When Possible

Let Splunk extract common fields automatically.

Good for:

```
large log datasets
```

---

### 2. Focus on Important Fields

Extract fields relevant to investigations.

Examples:

- IP address
- username
- process name
- command execution
- file path

---

### 3. Optimize Regex

Bad regex slows down Splunk searches.

Tips:

- avoid overly complex patterns
- test regex before production use

---

### 4. Use Clear Field Names

Use readable names like:

```
source_ip
destination_ip
username
login_status
```

Instead of:

```
field1
field2
```

---

### 5. Consider Performance

Heavy transformations may slow searches.

Examples that impact performance:

- large regex extractions
- complex eval calculations
- large lookups

---

# 10. SOC Workflow Using Fields

Typical investigation flow:

```
Collect Logs
Extract Fields
Filter Events
Analyze Patterns
Detect Threat
```

Example query pipeline:

```spl
index=firewall_logs
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| stats count by ip
| sort -count
```

This identifies **top communicating IP addresses**.

---

# 11. Memory Shortcut

Remember:

```
E T E A
```

```
Extract fields
Transform data
Enrich context
Analyze patterns
```

---

# Final Insight

Fields are the **foundation of Splunk analysis**.

Without fields:

```
logs = unreadable text
```

With fields:

```
logs → structured intelligence
```

This allows analysts to **detect attacks, investigate incidents, and understand system behavior quickly**.

---

✍️ Notes By Abhishek (Ez Abyss)
