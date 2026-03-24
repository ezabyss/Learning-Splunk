# 🖥️ Splunk Web Interface

---

# 🎯 What is Splunk Web?

```
Splunk Web = Interface to search, analyze, and manage data
```

👉 This is where YOU interact with Splunk

---

# 🧠 Core Idea

Think of Splunk Web like:

🧑‍💻 **Your Control Center**

- search data 🔍  
- create alerts 🚨  
- build dashboards 📊  
- manage system ⚙️  

---

# 📦 1. Apps (VERY IMPORTANT)

---

## 🔹 What is an App?

```
App = Pre-built workspace for a specific use case
```

---

## 🧠 Memory Trick

```
App = "Mini Splunk inside Splunk"
```

---

## 🌍 Real Example

| App | Purpose |
|-----|--------|
| Search & Reporting | analyze logs |
| Security App | detect threats |
| AWS App | monitor cloud |

---

## 💡 Real World

👉 SOC team uses **Security App**  
👉 Dev team uses **Monitoring App**

---

# 👥 2. Roles (ACCESS CONTROL)

---

## 🔐 Why Important?

```
Controls what user can SEE + DO
```

---

## 🎯 3 Main Roles

---

### 👑 Admin (Most Powerful)

- install apps  
- ingest data  
- manage everything  

---

### ⚡ Power User

- create searches  
- share knowledge objects  
- run real-time queries  

---

### 👤 User

- limited access  
- only sees shared content  

---

## 🧠 Memory Trick

```
Admin → Full control  
Power → Advanced user  
User → Basic access
```

---

# 🏠 3. Default Apps

---

## 🏡 Home App

👉 Main dashboard

---

### What You Can Do

- open apps  
- add data  
- read docs  
- manage settings  

---

## 🔍 Search & Reporting App (MOST USED)

👉 Where real work happens

---

### Purpose

```
Search + Analyze + Visualize data
```

---

# 🧱 4. Splunk Interface Components (IMPORTANT)

---

## 🧭 1. Splunk Bar (Top Menu)

---

### Use

- switch apps  
- settings  
- messages  
- search jobs  

---

## 📌 Memory

```
Splunk Bar = Navigation + System Control
```

---

## 📊 2. App Bar

👉 Navigate inside app

---

## 🔍 3. Search Bar (MOST IMPORTANT)

---

### Use

```
Write SPL queries here
```

---

### Example

```
index=web_logs status=404
```

---

## ⏱️ 4. Time Range Picker

---

### Use

```
Select time period of data
```

---

### Example

- Last 24 hours  
- Last 7 days  

---

## 📘 5. How to Search Panel

👉 Learning help + documentation

---

## 📂 6. Data Summary

---

### Shows data breakdown by:

- host  
- source  
- sourcetype  

---

### 🧠 Key Concepts

| Term | Meaning |
|------|--------|
| Host | machine name/IP |
| Source | file/path |
| Sourcetype | data format |

---

## 🧪 7. Table View

---

### Use

```
Explore data WITHOUT writing SPL
```

👉 beginner-friendly tool

---

## 🕘 8. Search History

---

### Use

- view past searches  
- reuse queries  

---

### Filter Options

- today  
- last 7 days  
- last 30 days  

---

# 🔥 Real World Scenario

---

## Scenario: SOC Analyst

---

### Step 1

Open **Search & Reporting**

---

### Step 2

Search:

```
index=auth_logs status=failed
```

---

### Step 3

Set time:

```
Last 24 hours
```

---

### Step 4

Check:

- source → which system  
- host → which machine  
- sourcetype → type of logs  

---

### Step 5

Take action 🚨

---

# ⚡ Why This Matters

---

## Without Interface ❌

- confusing  
- hard to navigate  

---

## With Interface ✅

- easy search  
- fast analysis  
- better decisions  

---

# 🧠 Learning Tricks

---

## 🔑 1. Remember Structure

```
Apps → Roles → Search → Data
```

---

## 🔑 2. Focus on THESE 3

- Search Bar  
- Time Picker  
- Data Summary  

---

## 🔑 3. Always Think

```
Where is my data coming from?
```

---

# 📌 Final Summary

---

## Splunk Web in One Line

```
Interface to interact with data using apps, searches, and dashboards
```

---

## Most Important Things

- Apps = workspaces  
- Roles = permissions  
- Search bar = core tool  
- Time = context  
- Data summary = understanding  

---

# 🚀 Final Insight

```
Good Analyst = Knows WHERE + HOW to search
```

---

**✍️ Notes By Abhishek (Ez Abyss)**
