# 📘 Field Extraction in Splunk – Regex & Delimiter Methods

---

# 1️⃣ Learning Objective

By the end of this session, you will understand:

- How to extract new fields in Splunk
- How to use the internal index
- Field extraction using Delimiters
- Field extraction using Regular Expressions (Regex)
- How extracted fields appear in search
- Case sensitivity in SPL

---

# 2️⃣ Using the Internal Index

To demonstrate field extraction, we use:

```
index=_internal
```

The `_internal` index contains:

- Splunk system logs
- Operational metrics
- Performance details
- Troubleshooting information

⚠️ Always limit time range to **Last 24 hours** when searching internal logs.

---

# 3️⃣ What is Field Extraction?

Sometimes Splunk:

- Does not automatically extract certain fields
- Or you want custom-named fields

To create a new field:

➡ Click **Extract New Field**

This opens the Field Extraction Wizard.

---

# 4️⃣ Method 1: Field Extraction Using Regular Expression (Regex)

Regex is used when:

- Log format is complex
- Patterns are dynamic
- You need precise control

---

## 🔹 Example Log Entry

Assume your log looks like this:

```
192.168.1.15 - ezabyss [24/May/2026:14:32:10 +0000] "GET /login HTTP/1.1" 200 512
```

You want to extract:

- IP address
- Username
- HTTP status code

---

## 🔹 Regex Example 1: Extract IP Address

Regex Pattern:

```
(?<client_ip>\d+\.\d+\.\d+\.\d+)
```

Explanation:

- `\d+` → One or more digits
- `\.` → Literal dot
- `(?<client_ip>...)` → Named capturing group

Result:

New field created → `client_ip`

---

## 🔹 Regex Example 2: Extract Username

Regex Pattern:

```
-\s(?<username>\w+)\s
```

Explanation:

- `\s` → Space
- `\w+` → Word characters
- Captures username between spaces

Result:

New field → `username`

---

## 🔹 Regex Example 3: Extract HTTP Status Code

Regex Pattern:

```
"\s(?<status_code>\d{3})\s
```

Explanation:

- `\d{3}` → Exactly 3 digits
- Captures values like 200, 404, 500

Result:

New field → `status_code`

---

## 🔹 Using Regex Directly in SPL

Instead of wizard, you can extract fields directly in search:

```
index=_internal 
| rex "(?<client_ip>\d+\.\d+\.\d+\.\d+)"
```

Example extracting status:

```
index=_internal
| rex "\" (?<status_code>\d{3}) "
```

`rex` command allows inline regex extraction.

---

# 5️⃣ Method 2: Field Extraction Using Delimiters

Use delimiters when:

- Logs are structured
- Fields are separated by spaces, commas, tabs, or pipes

---

## 🔹 Example Using Space Delimiter

Log:

```
192.168.1.15 ezabyss +0000 GET
```

If delimiter = Space

Splunk splits automatically:

- Field 1 → IP
- Field 2 → username
- Field 3 → timezone
- Field 4 → method

You can rename:

- IP
- username
- time_zone

---

# 6️⃣ Case Sensitivity in SPL

Field names are case sensitive.

If field created as:

```
IP
```

This works:

```
index=_internal | table IP username
```

This does NOT:

```
index=_internal | table ip username
```

---

# 7️⃣ Regex vs Delimiter Comparison

| Feature | Regex | Delimiter |
|----------|--------|------------|
| Flexibility | Very High | Medium |
| Complex Patterns | Yes | No |
| Structured Logs | Good | Excellent |
| Dynamic Logs | Best | Limited |
| Beginner Friendly | Moderate | Easy |

---

# 8️⃣ When to Use Regex

Use Regex when:

- Logs contain mixed patterns
- Fields vary in length
- You need precision
- Delimiters are inconsistent

---

# 9️⃣ When to Use Delimiters

Use Delimiters when:

- Logs are clean and structured
- Fields are clearly separated
- You need quick extraction

---

# 🔟 Why Field Extraction Matters

Field extraction enables:

- Faster searches
- Better filtering
- Accurate dashboards
- Alert creation
- Statistical analysis
- SOC investigations

Without proper fields → You cannot analyze efficiently.

---

# 1️⃣1️⃣ Brief Explanation

Field extraction in Splunk can be performed using regular expressions or delimiters. Regex is used for dynamic and complex log patterns using named capturing groups such as `(?<fieldname>pattern)`. Delimiters are used for structured logs separated by consistent characters like commas or spaces. Extracted fields become searchable and can be used in SPL queries, dashboards, and alerts.

---

# 🔥 Final Takeaway

Field extraction transforms:

Raw Logs → Structured Data → Actionable Insights

Regex transforms:

Raw Text → Structured Fields → Actionable Intelligence




---

**✍️ Notes By Abhishek (Ez Abyss)**
