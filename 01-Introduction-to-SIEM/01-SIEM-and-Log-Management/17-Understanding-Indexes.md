# 📘 Indexes in Splunk

---

# 1️⃣ Learning Objective

By the end, you will understand:

- What an index is in Splunk
- Why indexes are important
- Key index components
- How to create an index
- Index data types (Events vs Metrics)
- Storage paths
- Retention policy configuration

---

# 2️⃣ What is an Index in Splunk?

An index is:

- A structured repository
- Where data is stored
- A fundamental part of Splunk architecture

When data is ingested:

1. It is parsed  
2. It is tokenized  
3. It is indexed  
4. It is stored inside an index  

Indexes enable:

- Fast search
- Efficient retrieval
- Organized storage
- Optimized performance

---

# 3️⃣ Key Index Components

When working with indexes, important concepts include:

- Data ingestion
- Indexing process
- Data segmentation
- Metadata schema
- Search retrieval
- Retention policies
- Archiving
- Search performance optimization

---

# 4️⃣ Viewing Existing Indexes

To view indexes:

Go to:

Settings → Indexes

Here you can see:

- Default indexes
- Internal indexes
- Audit indexes
- Fishbucket
- History DB
- Default DB

You will also see:

- Max size of each index
- Current storage usage
- Storage paths

---

# 5️⃣ Creating a New Index

You do NOT need to ingest data to create an index.

Steps:

1. Go to `Settings`
2. Click `Indexes`
3. Click `New Index`

---

# 6️⃣ Step-by-Step Index Creation

---

## 🔹 Step 1: Index Name

Always use meaningful names.

Example:

`web_logs_index`

Avoid generic names like:

`index1`

Naming should reflect:

- Data source
- Purpose
- Environment

---

## 🔹 Step 2: Index Data Type

You will see two options:

### 1️⃣ Events

Use for:

- Log files
- Text-based logs
- Machine-generated logs
- Human-readable records

Most common choice.

---

### 2️⃣ Metrics

Use for:

- Numeric time-series data
- Monitoring systems
- Sensor data
- Performance metrics

Metrics are optimized for time-series storage.

---

## 🔹 Step 3: Storage Paths

You can define:

- Home Path (Hot/Warm buckets)
- Cold Path
- Thawed Path

If left blank, Splunk uses default paths:

```
$SPLUNK_HOME/var/lib/splunk/<index_name>/db
$SPLUNK_HOME/var/lib/splunk/<index_name>/colddb
$SPLUNK_HOME/var/lib/splunk/<index_name>/thaweddb
```

Best practice:

Use default unless advanced storage planning required.

---

## 🔹 Step 4: Data Integrity Check

Option:

Enable Data Integrity Check

If enabled:

- Splunk computes hashes
- Ensures data tampering detection
- Improves compliance

Recommended for regulated environments.

---

## 🔹 Step 5: Maximum Index Size

Default:

500 GB

You can set:

- MB
- GB
- TB

Consider:

- Data volume
- Retention requirements
- Storage capacity

---

## 🔹 Step 6: Bucket Size Limits

You can configure:

- Max Hot bucket size
- Max Warm bucket size
- Max Cold bucket size

If set to Auto:

Splunk manages automatically.

Recommended for most deployments.

---

## 🔹 Step 7: Frozen Data Path

Defines where data goes when frozen.

If not specified:

- Default archiving behavior applies
- Frozen buckets deleted unless archived

---

## 🔹 Step 8: App Association

Typically:

`Search & Reporting` app

You can associate index with specific app context.

---

## 🔹 Step 9: Retention Policy

Retention policy controls:

How long data remains searchable.

Option:

Enable Reduction

If enabled:

- Removes older tsidx files
- Reduces storage cost
- May impact performance

You can define retention in:

- Days
- Hours
- Minutes
- Seconds

If disabled:

- Data retained as long as index exists

---

# 7️⃣ tsidx Files Explained

`tsidx` files:

- Store index metadata
- Enable fast searching
- Improve search performance

Reducing tsidx:

- Saves storage
- May slow older searches

---

# 8️⃣ After Creating Index

Click:

Save

Your new index is now available.

It can be used for:

- Data ingestion
- Filtering
- Searching
- Retention management

---

# 9️⃣ Index Creation Without Data

You can create indexes:

Before ingesting data

Useful when:

- Planning architecture
- Preparing for production
- Designing storage layout

---

# 🔟 Best Practices

✔ Use meaningful index names  
✔ Separate security logs from application logs  
✔ Plan retention before ingestion  
✔ Enable integrity checks for compliance  
✔ Avoid modifying default internal indexes  
✔ Monitor storage usage regularly  

---

# 1️⃣1️⃣ Brief Explanation

An index in Splunk is a logical repository that stores parsed and tokenized event data for efficient searching and retrieval. During ingestion, data is processed and stored in hot, warm, and cold buckets. Administrators can configure index size, retention policies, storage paths, and data types (event or metric). Proper index planning improves performance, storage optimization, and compliance management.

---

# 🔥 Final Takeaway

Indexes are the backbone of Splunk storage.

They determine:

- Where data lives
- How long it stays
- How fast it searches
- How much it costs

---

**✍️ Notes By Abhishek (Ez Abyss)**
