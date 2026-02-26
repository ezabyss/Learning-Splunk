# 📘 How Splunk Stores Data – Indexes, Events & Buckets

---

# 1️⃣ Learning Objective

By the end, you will understand:

- How Splunk stores data
- What indexes are
- What events and fields are
- Default fields in Splunk
- What buckets are
- Bucket lifecycle (Hot → Warm → Cold → Frozen → Thawed)
- Where data lives on disk

---

# 2️⃣ What Happens When Data Enters Splunk?

When Splunk processes raw data:

1. It parses the data  
2. It creates events  
3. It extracts fields  
4. It writes data to an index  
5. That index maps to disk storage locations called buckets  

---

# 3️⃣ What is an Index?

An index:

- Is a logical container of data
- Maps to physical storage on disk
- Stores compressed raw data + index files
- Enables fast search

---

## 🔹 Default Indexes in Splunk

Splunk comes with built-in indexes:

- `main` → Default index for user data
- `_internal` → Stores Splunk internal logs
- `_audit` → Audit events
- `_introspection` → Performance data

You can also create custom indexes.

---

# 4️⃣ What is an Event?

An event:

- Is a single row of data
- Represents one log entry
- Contains fields

Example event:

`status=error user=admin ip=192.168.1.10`

---

# 5️⃣ What are Fields?

Fields are:

- Key-value pairs
- Extracted automatically by Splunk
- Used for searching and filtering

Example:

`status=error`

Here:
- status = field name
- error = field value

---

## 🔹 Automatic Field Extraction

Splunk automatically detects:

- key=value patterns
- Common structured formats
- Some patterns even without "="

---

# 6️⃣ Default Fields Added to Every Event

Splunk automatically adds metadata fields:

| Field | Meaning |
|-------|---------|
| `_time` | Timestamp of event |
| `host` | Hostname or IP of source |
| `source` | File or input source |
| `sourcetype` | Format of data |

Example:

- Apache logs → sourcetype=apache
- Syslog → sourcetype=syslog

---

# 7️⃣ How Splunk Stores Data on Disk

Splunk stores data inside indexes.

Each index contains:

- Compressed raw data
- Index files
- Organized subdirectories called buckets

Buckets are time-based storage directories.

---

# 8️⃣ Bucket Lifecycle in Splunk

There are six bucket states, but five are most important:

1️⃣ Hot  
2️⃣ Warm  
3️⃣ Cold  
4️⃣ Frozen  
5️⃣ Thawed  

---

## 🔥 Hot Bucket

- Newly indexed data
- Actively being written
- Each index has at least one hot bucket

---

## 🌤 Warm Bucket

- Data rolled from hot
- No longer actively written
- Still searchable
- An index can have multiple warm buckets

---

## ❄️ Cold Bucket

- Rolled from warm
- Stored in separate location
- Still searchable
- Can have many cold buckets

---

## 🧊 Frozen Bucket

- Rolled from cold
- Deleted by default
- Can be archived before deletion

Not searchable in Splunk unless restored.

---

## 🔄 Thawed Bucket

- Restored from archive
- Searchable again
- Used for forensic investigations

---

# 9️⃣ Bucket Naming Convention

Buckets follow specific naming patterns.

Example structure:

```
$SPLUNK_HOME/var/lib/splunk/<index_name>/db/
```

Inside index folder you will see:

- `db` → Hot/Warm buckets
- `colddb` → Cold buckets
- `thaweddb` → Restored data

---

# 🔟 Default Storage Path (Windows Example)

Example installation path:

```
C:\Program Files\Splunk\var\lib\splunk\
```

Inside:

```
var
 └── lib
     └── splunk
         └── <index_name>
             ├── db
             ├── colddb
             └── thaweddb
```

You do not manually create these.
Splunk manages them automatically.

---

# 1️⃣1️⃣ What is Inside a Bucket?

Each bucket contains:

- Raw data files
- tsidx index files
- Metadata files

This structure allows:

- Fast searching
- Time-based filtering
- Efficient storage

---

# 1️⃣2️⃣ Data Retention & Archiving

You can configure:

- Retention policies
- Archiving policies
- Index size limits
- Data lifecycle rules

Options include:

- Manual archiving
- Automatic freezing
- Backup strategies
- Partitioning index data

---

# 1️⃣3️⃣ Important Concept: Compression

Splunk compresses raw data before storing.

Benefits:

- Reduced disk usage
- Faster read performance
- Optimized indexing

---

# 1️⃣4️⃣ Mental Model

Think of Splunk storage like:

Index → Cabinet  
Bucket → Drawer  
Event → File  
Field → Label  

Hot → Active drawer  
Warm → Recently used drawer  
Cold → Storage room  
Frozen → Archived box  
Thawed → Restored archive  

---

# 1️⃣5️⃣ Brief Explanation

Splunk stores data in indexes, which map to disk locations called buckets. Each bucket contains compressed raw data and index files. Data flows from hot to warm to cold to frozen states. Default fields such as _time, host, source, and sourcetype are automatically added to every event. Frozen data is deleted by default but can be archived and later restored as thawed buckets.

---

# 🔥 Final Takeaway

Splunk does not just store logs.

It:

- Structures them
- Compresses them
- Organizes them by time
- Manages lifecycle automatically
- Enables high-speed search across terabytes of data

Understanding buckets is key to mastering Splunk architecture.

---

**✍️ Notes By Abhishek (Ez Abyss)**
