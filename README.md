# SOC Report – Splunk SIEM Lab   

------------------------------------------------------------------------------------------------

## 📌 Overview  
This lab demonstrates how a SOC Analyst uses a **SIEM (Security Information and Event Management)** platform to ingest logs, generate custom events, and detect suspicious activity.

The activity was carried out on **Splunk**, using **Kali Linux** as the log source.  
The exercise involved creating custom log entries, ingesting `/var/log/syslog`, running SPL queries, and validating detection of legitimate and simulated malicious events.

------------------------------------------------------------------------------------------------

## 🛡 What is SIEM?  
A **SIEM (Security Information and Event Management)** platform:

- Collects logs and events from multiple systems  
- Analyzes them for threats and suspicious activity  
- Generates alerts for security monitoring  
- Helps with compliance and incident investigation  

**Examples:**  
- Splunk  
- IBM QRadar  
- ArcSight  
- Microsoft Sentinel  

------------------------------------------------------------------------------------------------

## 🎯 Lab Task  
### **S.No 1 – Create a log in Kali using `logger` and detect it in Splunk**

------------------------------------------------------------------------------------------------

## 🎯 Objective  
To create a custom log entry using the `logger` command in Kali Linux, ingest it into Splunk, and confirm detection using Splunk’s **Search & Reporting app**.

------------------------------------------------------------------------------------------------

## 🧪 Step-by-Step Procedure
------------------------------------------------------------------------------------------------
### **1. Open Splunk Web**
http://localhost:8000

markdown
Copy code
------------------------------------------------------------------------------------------------
### **2. Add Data → Files & Directories**
Navigate to:

Settings → Add Data → Files & Directories

powershell
Copy code

Select and upload:

/var/log/syslog

shell
Copy code
------------------------------------------------------------------------------------------------
### **3. Generate a custom log entry in Kali**
Open terminal and run:
logger "This is a test log from Splunk lab"

shell
Copy code
------------------------------------------------------------------------------------------------
### **4. Verify the log was written**
tail -n 5 /var/log/syslog

markdown
Copy code
------------------------------------------------------------------------------------------------
### **5. Submit data to Splunk**
Click **Review → Submit**.
------------------------------------------------------------------------------------------------
### **6. Go to Search**
Open Splunk Search App.
------------------------------------------------------------------------------------------------
### **7. Run SPL query**
source="syslog" host="kali" sourcetype="syslog"

yaml
Copy code
------------------------------------------------------------------------------------------------
### **8. Result**
Splunk successfully displayed the custom log event containing:

- Timestamp  
- Host (kali)  
- Source (syslog)  
- Message: *This is a test log from Splunk lab*  

------------------------------------------------------------------------------------------------

## 🔥 Additional Activity – Failed Login Detection  
I simulated **failed SSH login attempts** in Kali Linux and verified that Splunk ingested them from `auth.log`, allowing detection through SPL queries.

This demonstrates Splunk’s ability to monitor real security events in addition to custom logs.

------------------------------------------------------------------------------------------------

## ✔ Findings  
- Successfully created a custom log using `logger`.  
- Verified ingestion into Splunk through `/var/log/syslog`.  
- Able to detect and visualize the event via SPL query.  
- Simulated failed login attempts were also detected, proving Splunk’s usefulness for SOC monitoring.  

------------------------------------------------------------------------------------------------

## 🛡 Conclusion  
This exercise demonstrates the practical workflow of a SOC Analyst using Splunk SIEM:

- Log creation and ingestion  
- Event detection  
- Querying and analyzing logs  
- Understanding how Splunk handles both normal and suspicious events  

This lab strengthens skills in **log analysis**, **SPL queries**, **event ingestion**, and **security monitoring**.

------------------------------------------------------------------------------------------------
