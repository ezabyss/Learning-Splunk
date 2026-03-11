# Using Tags in Splunk
### Data Categorization and Search Simplification

---

# 1. What Are Tags in Splunk?

Tags are **labels attached to fields or field values** to help organize and categorize data.

They make searching easier by grouping similar events together.

Simple idea:

```
Raw Logs → Add Tags → Categorize Data → Faster Searches
```

Example:

| Field | Value | Tag |
|------|------|------|
| education | secondary | secondary_education |

---

# 2. Why Tags Are Useful

Tags help analysts:

- group similar events
- simplify searches
- classify logs
- build better dashboards
- speed up investigations

Think of tags like **labels on folders in a computer**.

---

# 3. Where to Manage Tags in Splunk

Navigate to:

```
Settings → Tags
```

Here you can:

- view existing tags
- create new tags
- enable or disable tags
- delete tags
- modify permissions

---

# 4. Creating a Tag

Steps:

1. Run a search query.

```
index=index1
```

2. Expand an event.

3. Click **Actions → Edit Tags**.

4. Choose the field and value.

Example:

```
education = secondary
```

5. Create tag name.

Example:

```
secondary_education
```

6. Click **Save**.

Now the tag is attached to that field-value pair.

---

# 5. Searching Using Tags

Tags can be used in search queries.

Syntax:

```
tag:<field>="<tag_name>"
```

Example:

```spl
index=index1 tag:education="secondary_education"
```

Result:

Only events where:

```
education = secondary
```

will appear.

---

# 6. Example — Tagging Contact Type

Field value:

```
contact = cellular
```

Tag name:

```
CellularContact
```

Search query:

```spl
index=index1 tag:contact="CellularContact"
```

This retrieves events with **cellular contact type**.

---

# 7. Viewing Tags

To see all tags:

```
Settings → Tags
```

Information displayed:

| Field | Description |
|---|---|
| Tag Name | label assigned |
| Field-Value Pair | field associated with tag |
| Owner | creator of tag |
| Status | enabled or disabled |

---

# 8. Enabling and Disabling Tags

Tags can be **enabled or disabled**.

If a tag is disabled:

```
Splunk will not use it in searches
```

Example:

Disabled tag query:

```spl
index=index1 tag:contact="CellularContact"
```

Result:

```
No results found
```

Enable the tag again to restore functionality.

---

# 9. Deleting Tags

If a tag is deleted:

```
It is permanently removed
```

Important:

You must **recreate it manually** if needed.

Best practice:

```
Disable tags instead of deleting them.
```

---

# 10. Real SOC Example

SOC analysts often tag events for:

- malware activity
- suspicious login attempts
- known attacker IPs
- phishing domains

Example:

Tag suspicious IP logs.

```
tag:suspicious_ip
```

Search:

```spl
index=firewall_logs tag:suspicious_ip
```

This instantly retrieves **known malicious activity**.

---

# 11. Memory Shortcut

Remember tags with:

```
C S M
```

```
Categorize data
Simplify searches
Manage log labels
```

---

# 12. Key Insight

Tags **do not change the data**.

They simply add **labels for easier searching and grouping**.

Think of tags as:

```
metadata for your log events
```

---

# Final Insight

In Splunk investigations:

```
tags = faster threat hunting
```

By tagging important log patterns, analysts can quickly retrieve **security-relevant events** without complex queries.

---

✍️ Notes By Abhishek (Ez Abyss)
