# 📘 Data Collection & Management in Splunk

---

# 1️⃣ Module Overview

Welcome to **Data Collection and Management in Splunk**.

By the end, you will understand:

- How to get data into Splunk
- Basic input settings
- What forwarders are
- Field extraction basics
- Data filtering techniques

This module builds your foundation as a Splunk data manager.

---

# 2️⃣ Getting Data into Splunk

Splunk supports ingestion of:

- CSV files
- Excel files
- Text files
- Log files
- JSON
- XML
- Practically any structured or semi-structured format

You can ingest data using:

- `Settings → Add Data`
- Common “Add Data” button from dashboard

---

# 3️⃣ Data Ingestion Methods

### 🔹 Upload

Upload files directly from your system.

### 🔹 Monitor

Continuously monitor directories or files.

### 🔹 Forwarders

Remote data collection from other systems.

---

# 4️⃣ Example: Uploading World Airports CSV

Steps:

1. Go to `Settings`
2. Click `Add Data`
3. Select `Upload`
4. Choose file (e.g., `World_Airports.csv`)
5. Click Next

---

# 5️⃣ Input Configuration Options

When uploading CSV:

- Field delimiter → Comma (default)
- Can change to:
  - Pipe (`|`)
  - Tab
  - Space
- Quote character:
  - Double quotes
  - Single quotes

Splunk automatically:

- Detects headers
- Maps columns
- Assigns timestamps
- Structures preview

---

# 6️⃣ Source & Host Settings

By default:

- Source = filename
- Sourcetype = csv
- Host = system hostname

You can modify:

Example:

`Host = airport_data`

---

# 7️⃣ Index Selection

Options:

- Use default index (`main`)
- Create new index

When creating new index:

- Define max size (e.g., 500GB)
- Define cold bucket path
- Define frozen bucket path
- Set retention policy

For demo purposes → Use default index.

---

# 8️⃣ After Submission

Once data is submitted:

- Splunk indexes the data
- Events are created
- Fields are extracted
- Search environment opens automatically

---

# 9️⃣ Working with Fields

In the Search interface:

You will see:

- Selected Fields
- Interesting Fields
- Default Fields

---

## 🔹 Selecting Fields

Click a field (e.g., `continent`) → Select it.

It appears in the **Selected Fields** list.

Selected fields are highlighted in search results.

To remove → Click again.

---

# 🔟 Field Exploration

When clicking a field (e.g., `name`), Splunk shows:

- Top 10 values
- Frequency count
- Percentage distribution
- Rare values
- Time-based distribution

Example:

If `Name = XYZ Airport` appears 83 times  
Splunk shows:

Count = 83  
Percentage = (83 / Total events)

---

# 1️⃣1️⃣ Searching with Field Filters

Example:

```
name="John F Kennedy International Airport"
```

Returns only matching records.

---

Example:

```
ISO_country="US"
```

Returns all events where country is US.

---

# 1️⃣2️⃣ Field Statistics

Splunk allows:

- Top values
- Rare values
- Count by field
- Time distribution
- Event filtering

Example:

```
stats count by ISO_country
```

---

# 1️⃣3️⃣ Real-Time vs Static Data

Static dataset:

- No real timestamp variation
- Used for demo/testing

Real production logs:

- Time-based
- Continuous generation
- Useful for monitoring & alerting

---

# 1️⃣4️⃣ Why Field Selection Matters

Field selection helps:

- Focus on relevant data
- Remove noise
- Speed up analysis
- Improve query performance
- Enable accurate reporting

---

# 1️⃣5️⃣ Splunk as a Data Analysis Engine

Splunk allows you to:

- Filter records
- Select specific columns
- Analyze frequency
- Detect anomalies
- Generate insights

It is widely used for:

- Server log analysis
- Security monitoring
- Performance monitoring
- Troubleshooting
- Compliance auditing

---

# 1️⃣6️⃣ Practical Mental Model

Data Ingestion → Field Extraction → Field Selection → Filtering → Analysis → Insight

---

# 1️⃣7️⃣ Brief Explanation

Splunk allows ingestion of data through upload, monitoring, or forwarders. During ingestion, fields are automatically extracted. Users can select and filter fields in the search interface to analyze datasets efficiently. Field-based searching enables targeted querying, making Splunk a powerful log analysis and data management platform.

---

# 🔥 Final Takeaway

Splunk is not just about importing data.

It allows you to:

- Control field visibility
- Analyze frequency patterns
- Filter intelligently
- Generate insights from raw logs

Mastering data ingestion and field selection is the first real step toward becoming a Splunk power user.

---

**✍️ Notes By Abhishek (Ez Abyss)**
