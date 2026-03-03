# 📘 Splunk Monitoring & Universal Forwarder Setup

---

# 1️⃣ Learning Objective

By the end, you will understand:

- What Universal Forwarder is
- How to download it
- How to install it on Windows
- How to configure receiving on Splunk Enterprise
- How to connect Forwarder to Indexer
- How to monitor files using Splunk

---

# 2️⃣ What is Universal Forwarder?

Universal Forwarder (UF) is a lightweight Splunk agent that:

- Collects data from source machines
- Forwards data to Splunk indexer
- Uses minimal system resources
- Does NOT index data locally

Used in:

- Enterprise deployments
- Distributed environments
- Centralized logging systems

---

# 3️⃣ Download Universal Forwarder

Go to:

splunk.com → Downloads → Universal Forwarder

Login using your existing Splunk account.

Download:

Windows 10/11 (64-bit) MSI installer

Version should match your Splunk Enterprise version.


---

# 4️⃣ Installing Universal Forwarder (Windows)

---

## Step 1: Launch Installer

- Accept license agreement
- Select “On-premise Splunk Enterprise instance”
- Click Customize Options

---

## Step 2: Installation Settings

Keep default installation path.

Do NOT configure SSL certificates (leave default).

Click Next.

---

## Step 3: Service Account

Select:

`Local System`

Reason:

Allows forwarder to access system logs and files.

Click Next.

---

## Step 4: Select Data Sources

Enable:

✔ Windows Event Log  
✔ Performance Monitor  

Leave directory monitoring blank (can configure later).

Click Next.

---

## Step 5: Set Admin Credentials

- Username: `admin`
- Set password (minimum 8 characters)
- Do NOT select random password

Remember this password.

Click Next.

---

## Step 6: Configure Receiving Indexer

Before entering details:

Go to Splunk Enterprise.

Navigate:

Settings → Forwarding and Receiving → Configure Receiving → New Receiving Port

Set port:

`9997`

Save.

---

Now return to UF installation screen.

Enter:

Indexer IP: `YourMachineIP`
Port: `9997`

Example:
open cmd and type:
`ipconfig` to find your ip

`192.168.X.X`

Click Next → Install.

---

Installation completes.

Click Finish.

---

# 5️⃣ Verify Forwarder Connection

Go to:

Splunk → Settings → Forwarding and Receiving

You should see:

Receiving port 9997 enabled.

---

# 6️⃣ Monitoring Files in Splunk

Now configure file monitoring.

---

## Step 1: Add Data

Go to:

Settings → Add Data → Monitor

Select:

Files and Directories

---

## Step 2: Choose From List of Option.

for example:

`Local Event Logs`

Click Next.

---


Data Summary

You should see:

- Host name
- Source
- Event count increasing

If events are generating → Monitoring successful.

---

# 8️⃣ Data Flow Architecture

Source Machine  
↓  
Universal Forwarder  
↓ (Port 9997)  
Splunk Indexer  
↓  
Search Head  

---

# 9️⃣ Why Use Universal Forwarder Instead of Upload?

Upload:

- Manual
- One-time ingestion

Universal Forwarder:

- Continuous monitoring
- Real-time log forwarding
- Enterprise-ready
- Scalable

---

# 🔟 Common Troubleshooting

If data not appearing:

✔ Check receiving port 9997 enabled  
✔ Check Windows firewall  
✔ Verify correct IP address  
✔ Restart Splunk services  
✔ Check splunkd.log  

---

# 1️⃣1️⃣ Brief Explanation

The Universal Forwarder is a lightweight Splunk agent used to collect and forward machine data to a Splunk indexer. It does not perform indexing locally. It connects to the indexer over a receiving port (default 9997). This architecture allows centralized logging, scalability, and efficient enterprise monitoring.

---

# 🚀 Final Takeaway

Universal Forwarder = Data Collection Engine

Without forwarders → Manual ingestion  
With forwarders → Continuous enterprise monitoring  

This is how real-world SOC environments ingest logs.

---

**✍️ Notes By Abhishek (Ez Abyss)**
