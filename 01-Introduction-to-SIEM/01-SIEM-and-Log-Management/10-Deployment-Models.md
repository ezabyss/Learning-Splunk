# 📘 Splunk Deployment Models & Architecture 

---

# 1️⃣ Learning Objectives

By the end, you should understand:

- Splunk deployment models
- How Splunk stores data on disk
- Splunk configuration files (.conf)
- Splunk data pipeline
- Splunk licensing basics
- Splunk apps and add-ons

---

# 2️⃣ Splunk Configuration Files (.conf Files)

Everything Splunk does is governed by configuration files.

These files:

- Are located in the `etc` directory
- Have the extension `.conf`
- Control inputs, indexing, search behavior, apps, authentication, etc.

Example path (Windows):

`C:\Program Files\Splunk\etc`

---

## 🔹 Layered Configuration System

Splunk uses a layered configuration model.

You may have:

- Global-level configuration
- App-specific configuration
- User-specific configuration

⚠️ Important Rule:
Never edit files inside the `default` directory.

Instead, make changes in:

`local` directory of the app

---

## 🔹 Structure of a .conf File

Each `.conf` file contains:

- Stanzas
- Attribute = Value pairs

Example format:

```
[monitor:///var/log/syslog]
disabled = false
index = main
sourcetype = syslog
```

This structure controls how Splunk behaves.

---

# 3️⃣ Splunk Deployment Models

Splunk offers two major deployment environments:

1. On-Premises (Splunk Enterprise)
2. Splunk Cloud

You installed:

Splunk Enterprise (On-Prem)

Splunk Cloud:

- Hosted by Splunk
- Requires provisioning
- Offers 14-day trial
- Managed infrastructure

---

# 4️⃣ Splunk Data Pipeline

Splunk data pipeline consists of four major stages:

Input → Parsing → Indexing → Searching

---

## 🔹 Input Phase

- Data is consumed from sources
- Splunk does not inspect content deeply here

Sources may include:

- Log files
- APIs
- Syslog
- Databases
- Cloud services

---

## 🔹 Parsing Phase

Occurs on:

- Indexer
- Heavy Forwarder

Tasks performed:

- Timestamp recognition
- Metadata assignment
- Event breaking
- Data transformation

---

## 🔹 Indexing Phase

Parsed data is:

- Written to disk
- Stored in flat files
- Organized into buckets

Indexes enable fast searching.

---

## 🔹 Search Phase

Search Head:

- Handles user interaction
- Executes SPL queries
- Retrieves indexed data
- Displays dashboards

---

# 5️⃣ Physical Components of Splunk

There are only two software packages:

1. Universal Forwarder
2. Splunk Enterprise

---

## 🔹 Universal Forwarder

- Lightweight
- Minimal configuration
- Forwards data only
- Does NOT index data

---

## 🔹 Splunk Enterprise

Full version that can act as:

- Search Head
- Indexer
- Heavy Forwarder
- Deployer
- Cluster Manager

---

# 6️⃣ Deployment Model Types

---

## 🔹 1. Small / Departmental Deployment

- Single Splunk Enterprise instance
- Acts as Search Head + Indexer
- Up to 10 forwarders
- Limited users

Best for:
- Labs
- Small teams
- Testing environments

---

## 🔹 2. Small Enterprise Deployment

- Independent Search Head
- 2–3 Load-Balanced Indexers
- 100–200 forwarders
- Around 100 users

Improved:

- Performance
- Data handling
- Scalability

---

## 🔹 3. Distributed Search Head Cluster

Components:

- Multiple Search Heads
- Governed by a Deployer
- Configuration Bundle Distribution
- Search Head Cluster Captain

---

### Search Head Cluster

- Group of search heads
- Users can run searches from any member
- Shares dashboards and results

Cluster Captain:

- Schedules jobs
- Manages replication
- Coordinates cluster activities

---

## 🔹 4. Fully Distributed (Enterprise-Scale)

Includes:

- Search Head Cluster
- Indexer Cluster
- Possibly both

Provides:

- High availability
- Horizontal scalability
- Fault tolerance
- Massive data ingestion capability

This model supports near infinite scalability.

---

# 7️⃣ How Splunk Stores Data on Disk

Splunk stores indexed data as:

- Flat files
- Organized in buckets
- Time-based structure

Bucket types:

- Hot
- Warm
- Cold
- Frozen

Each bucket contains:

- Raw data
- Index files
- Metadata

This structure enables fast search and retrieval.

---

# 8️⃣ Splunk Licensing

Splunk licensing is primarily based on:

Daily Ingestion Volume

For example:

- 500MB/day
- 1GB/day
- Enterprise-level licensing

If exceeded:

- Search functionality may be restricted
- Indexing may pause temporarily

Splunk Cloud licensing follows similar ingestion-based model.

---

# 9️⃣ Splunk Apps & Add-ons

Splunk is highly extensible.

---

## 🔹 Splunk Apps

Apps provide:

- Dashboards
- Pre-built searches
- Reports
- Visualizations
- Domain-specific features

Examples:

- Splunk Enterprise Security (ES)
- IT Service Intelligence (ITSI)

---

## 🔹 Splunk Add-ons

Add-ons provide:

- Field extractions
- Input configurations
- Sourcetype definitions
- CIM normalization

Add-ons support data onboarding.

Apps use add-ons for data normalization.

---

# 🔟 Deployment Model Summary

| Deployment Type | Use Case | Scale |
|----------------|----------|-------|
| Single Instance | Small Teams | Low |
| Search Head + Multiple Indexers | Medium Org | Moderate |
| Search Head Cluster | Large Org | High |
| Fully Distributed | Enterprise | Massive |

---

# 1️⃣1️⃣ Interview-Ready Explanation

Splunk deployment models scale from single-instance environments to fully distributed clusters. The system uses forwarders for data collection, indexers for parsing and storage, and search heads for querying and visualization. Data is stored in time-based buckets on disk, and licensing is based on daily ingestion volume. Apps extend functionality, while add-ons normalize incoming data.

---

# 🔥 Final Mental Model

Splunk Architecture =

Forwarders → Indexers → Search Heads  
Buckets → Indexed Flat Files  
Clusters → Scalability  
Apps + Add-ons → Extensibility  

---

# 🚀 Final Takeaway

Splunk is not just a log tool.

It is:

- A distributed architecture
- A scalable analytics engine
- A compliance platform
- A security operations backbone

Understanding deployment models separates beginners from real Splunk engineers.

---

**✍️ Notes By Abhishek (Ez Abyss)**
