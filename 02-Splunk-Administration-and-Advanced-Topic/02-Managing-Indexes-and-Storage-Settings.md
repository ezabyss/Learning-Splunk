# 📘 Managing Indexes & Bucket Storage in Splunk

---

# 1️⃣ Learning Objective

By the end, you will understand:

- Where Splunk indexes are physically stored
- How bucket directories are structured
- What TSIDX files are
- What metadata files exist inside buckets
- How data moves through Hot → Warm → Cold → Frozen → Thawed
- How Splunk manages bucket lifecycle automatically

---

# 2️⃣ Viewing Indexes in Splunk UI

Inside Splunk Enterprise:

Settings → Indexes

Here you can view:

- Index names
- Current size
- Maximum size
- Storage paths
- Status (Enabled/Disabled)

This is the logical view.

---

# 3️⃣ Physical Location of Indexes

To see indexes physically on disk:

Navigate to:

```
$SPLUNK_HOME/var/lib/splunk/
```

Inside this directory you will see:

- _audit
- _internal
- _configtracker
- defaultdb
- index1 (custom index)
- other indexes

Each index has its own folder.

---

# 4️⃣ Inside an Index Folder

Example:

```
$SPLUNK_HOME/var/lib/splunk/index1/
```

Inside you will find:

- db
- colddb
- thaweddb
- datamodel_summary (optional)

These represent bucket stages.

---

# 5️⃣ Inside the DB Folder

Navigate to:

```
index1/db/
```

Here you will find bucket subdirectories.

Each bucket contains:

- Raw data files
- TSIDX files
- Metadata files

---

# 6️⃣ What Files Exist Inside a Bucket?

Every bucket contains:

---

## 🔹 1. Raw Data Files

These contain:

- Compressed event data
- Actual log content

Usually stored inside:

```
rawdata/
```

---

## 🔹 2. TSIDX Files

TSIDX files:

- Are index pointer files
- Enable fast searching
- Map search terms to raw data

Without TSIDX:

Search would be extremely slow.

---

## 🔹 3. Metadata Files

Examples:

- hosts.data
- sources.data
- sourcetypes.data
- strings.data

These help:

- Categorize events
- Optimize search performance
- Store searchable metadata

---

# 7️⃣ Bucket Lifecycle in Splunk

Data flows through stages:

Hot → Warm → Cold → Frozen → Thawed

---

# 8️⃣ Hot Buckets

- New data is written here
- Actively being indexed
- Searchable
- Each index has at least one hot bucket

Location:

```
index_name/db/
```

---

# 9️⃣ Warm Buckets

- Rolled from hot buckets
- No longer actively written to
- Still searchable
- An index may have many warm buckets

Remain inside:

```
index_name/db/
```

---

# 🔟 Cold Buckets

- Rolled from warm buckets
- Moved to colddb directory
- Searchable
- Can reside on cheaper storage

Location:

```
index_name/colddb/
```

Cold buckets can be configured to use a different storage path.

---

# 1️⃣1️⃣ Frozen Buckets

- Rolled from cold buckets
- Deleted by default
- Can optionally be archived
- Not searchable

Frozen = Removed from active index

---

# 1️⃣2️⃣ Thawed Buckets

- Restored from archive
- Placed in thaweddb
- Searchable again

Location:

```
index_name/thaweddb/
```

Thawed data must be manually restored.

---

# 1️⃣3️⃣ Bucket State Summary

| Bucket Type | Writable | Searchable | Storage Location |
|------------|----------|------------|------------------|
| Hot        | Yes      | Yes        | db/              |
| Warm       | No       | Yes        | db/              |
| Cold       | No       | Yes        | colddb/          |
| Frozen     | No       | No         | Deleted/Archive  |
| Thawed     | No       | Yes        | thaweddb/        |

---

# 1️⃣4️⃣ How Bucket Rolling Happens

Bucket rolling occurs when:

- Size threshold is reached
- Time threshold is reached
- Retention policy is triggered

Flow:

Hot → Warm → Cold → Frozen

This is automatic.

---

# 1️⃣5️⃣ Important Concepts

✔ Hot buckets are actively written  
✔ Warm buckets are read-only  
✔ Cold buckets may use cheaper storage  
✔ Frozen buckets are removed  
✔ Thawed buckets are restored archives  

---

# 1️⃣6️⃣ Why This Matters

Understanding physical storage helps:

- Troubleshoot storage issues
- Monitor disk usage
- Plan retention policies
- Optimize performance
- Prepare for compliance audits

---

# 1️⃣7️⃣ Real-World Scenario

Imagine:

- 500 GB daily ingestion
- No lifecycle control

Without bucket management:

- Storage fills rapidly
- Searches slow down
- System crashes

With proper lifecycle:

- Hot = Recent 30 days
- Warm = 60 days
- Cold = 6 months
- Frozen = Archived

Result:

Stable, scalable environment.

---

# 1️⃣8️⃣ Brief Explanation

In Splunk, indexes are physically stored in the `var/lib/splunk` directory. Each index contains bucket directories such as `db`, `colddb`, and `thaweddb`. Data moves through bucket stages: hot, warm, cold, frozen, and thawed. Buckets contain raw data, TSIDX index files, and metadata files. Lifecycle policies automatically control bucket transitions based on size and age thresholds.

---

# 🔥 Final Takeaway

Splunk indexes are not just logical containers.

They are:

- Structured storage systems
- Organized by bucket lifecycle
- Optimized with TSIDX indexing
- Managed automatically via retention rules

Understanding physical bucket storage = Deep Splunk knowledge.

---

**✍️ Notes By Abhishek (Ez Abyss)**
