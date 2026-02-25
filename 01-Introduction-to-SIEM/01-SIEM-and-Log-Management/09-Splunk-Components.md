# 📘 Splunk Components & Sample Dashboard Creation 

---

# 1️⃣ Introduction

In this session, we explore:

- Core Splunk components  
- Data ingestion flow  
- Indexing and storage  
- Search layer  
- Creating a sample dashboard using dummy CSV data  

By the end, you should understand how Splunk components work together and how to build a simple dashboard.

---

# 2️⃣ Core Components of Splunk

Splunk architecture mainly revolves around two major functional areas:

1. Indexing & Storage Layer  
2. Search & User Interface Layer  

---

# 3️⃣ Indexing & Storage Components

When data is ingested into Splunk, it goes through indexing.

During indexing:

- Logs are parsed  
- Metadata is assigned  
- Events are structured  
- Data is stored efficiently  

---

## 🔹 Forwarders

Forwarders are lightweight agents that:

- Collect data from remote systems  
- Forward logs to a central Splunk instance  

Types:

- Universal Forwarder  
- Heavy Forwarder  

They support:

- Syslog  
- HTTP Event Collector  
- Splunk native forwarding  

---

## 🔹 Indexers

Indexers:

- Receive data from forwarders  
- Parse and structure logs  
- Store data in proprietary index format  
- Enable fast searching  

---

## 🔹 Buckets (Data Storage Tiers)

Splunk organizes indexed data into time-based buckets:

- Hot (actively written data)  
- Warm (recent searchable data)  
- Cold (older, less frequently accessed data)  

Splunk automatically manages bucket lifecycle to optimize performance.

---

# 4️⃣ Search & User Interface Components

This is where users interact with data.

Components include:

- Search Head  
- SPL (Search Processing Language)  
- Dashboards  
- Visualizations  
- Splunk Apps  

---

## 🔹 Search Head

The Search Head:

- Provides web interface  
- Executes SPL queries  
- Displays results  
- Manages dashboards and reports  

---

## 🔹 SPL (Search Processing Language)

SPL is used to:

- Search  
- Transform  
- Analyze  
- Visualize data  

Example basic query:

`source=dummydata.csv | table app_name email IP_address message status`

---

## 🔹 Dashboards & Visualizations

Users can create:

- Tables  
- Bar charts  
- Single value panels  
- Line charts  
- Pie charts  

Dashboards provide consolidated analytics.

---

# 5️⃣ Hands-On: Uploading Dummy CSV Data

Steps to upload data:

1. Go to `Settings`
2. Click `Add Data`
3. Choose `Upload`
4. Select CSV file
5. Keep source type as `csv`
6. Set host name (e.g., test)
7. Use default index
8. Review and submit

Once uploaded, Splunk automatically indexes the data.

---

# 6️⃣ Basic SPL Queries

---

## 🔹 Display Specific Fields

`source=dummydata.csv host=test | table app_name email IP_address message status`

Displays selected columns in table format.

---

## 🔹 Display All Fields

`source=dummydata.csv | table *`

The asterisk displays all indexed fields.

Note: Splunk automatically adds metadata fields such as:

- _time  
- host  
- source  
- sourcetype  

---

## 🔹 Count by Status

`source=dummydata.csv | stats count by status`

Example output:

- error = 982  
- success = 1018  

---

## 🔹 Count Only Errors

`source=dummydata.csv | where status="error" | stats count by status`

This returns total error count.

---

## 🔹 Count Only Success

`source=dummydata.csv | where status="success" | stats count by status`

This returns total success count.

---

# 7️⃣ Creating a Dashboard

After running a query:

1. Click `Save As`
2. Choose `New Dashboard`
3. Provide dashboard title (e.g., First Dummy Data Dashboard)
4. Choose visibility (Shared in App or Private)
5. Add panel title
6. Save to dashboard

To add more panels:

- Run new query  
- Click `Save As`
- Select existing dashboard  
- Save  

---

# 8️⃣ Creating Visualizations

From search results:

1. Go to `Visualization`
2. Choose chart type:
   - Column chart
   - Single value
   - Table
3. Customize:
   - Background color
   - Text color
   - Theme (dark/light)

Example:

- Error count → Red background  
- Success count → Green background  

---

# 9️⃣ Editing Dashboard Layout

Steps:

1. Open Dashboard  
2. Click `Edit`  
3. Drag panels  
4. Resize panels  
5. Rename titles  
6. Save layout  

Example panel titles:

- Status = ERROR  
- Status = SUCCESS  
- Table Values in Dummy Data  

---

# 🔟 Final Dashboard Outcome

Dashboard includes:

- Tabular data view  
- Error count panel  
- Success count panel  
- Custom formatting  
- Dark theme (optional)  

All created using simple SPL queries.

---

# 1️⃣1️⃣ Why This Matters

This demonstration shows:

- How data flows through Splunk  
- How indexing works  
- How SPL transforms data  
- How dashboards are built  
- How quickly analytics can be generated  

Even with dummy data, powerful dashboards can be created in minutes.

---

# 1️⃣2️⃣ Brief Explanation

Splunk architecture consists of forwarders, indexers, and search heads. Forwarders collect data, indexers parse and store it into time-based buckets, and search heads allow users to analyze data using SPL and create dashboards. Using simple queries like `stats count by status`, users can quickly build analytical dashboards.

---

# 🔥 Final Takeaway

Splunk is not just about ingesting logs.

It allows you to:

- Structure data  
- Analyze patterns  
- Create visual dashboards  
- Generate insights instantly  

With real production data, this becomes a powerful enterprise monitoring solution.

---

**✍️ Notes By Abhishek (Ez Abyss)**
