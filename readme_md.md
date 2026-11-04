# 🛡️ SOC Analyst L1 — Splunk Log Analysis Lab

Welcome to the training package dataset directory. All manuals, answer keys, and project directory structures have been removed and flattened to leave only the necessary Splunk data files.

## 👤 About the Author

**Budigi Vamshi**

*Cybersecurity / SOC Analyst (Hands-On Lab & Practical Experience)*  
*Home Security Lab · Self-employed*

## 📌 Project Overview

This project is a practical SOC Analyst L1 Security Monitoring and Incident Response Lab designed to simulate real-world SOC operations. The lab demonstrates an end-to-end security analysis workflow involving:

* **Endpoint & Network Telemetry:** Windows logs, Sysmon, auth, firewall, and web traffic monitoring.
* **Log Ingestion & Enrichment:** Data indexing into Splunk and username enrichment using custom lookups.
* **Threat Detection & SPL:** Crafting Splunk Search Processing Language (SPL) queries for event correlation and threat hunting.
* **Incident Triage & Investigation:** Documenting indicators of compromise (IOCs) and mapping findings to SOC workflows.

## 🧰 Tools & Datasets Used

| Tool / Dataset | Purpose | 
| ----- | ----- | 
| **Splunk Enterprise** | SIEM platform for log ingestion, indexing, SPL searching, and lookup definitions | 
| **Sysmon Events** | Advanced Windows endpoint activity, process creation, and network tracking | 
| **Windows Event Logs** | System authentication, privilege escalation, and file access audits | 
| **Network & Firewall Logs** | Web proxy access, VPN sessions, DNS queries, and firewall flow analysis | 
| **Lookup Tables (`user_accounts.csv`)** | Contextual mapping of user IDs to employee details (name, department, title) | 

## 🏗️ SOC Architecture & Data Flow

```
               Multi-Source Security Logs
  (Windows, Sysmon, Auth, Proxy, Firewall, DNS, VPN)
                        │
                        ▼
                Splunk Enterprise
                        │
                 Index: `main`
                        │
                        ▼
            Lookup Table Enrichment 
                (`user_accounts.csv`)
                        │
                        ▼
              SPL Query & Threat Detection
                        │
                        ▼
               SOC Alert & Triage
```

## 📋 Splunk Dataset Upload Reference

Below is a reference guide for uploading the 14 flattened files in this directory to Splunk:

### 1. Standard Event Logs (Index: `main`)

For each of the following files, navigate to **Settings ➔ Add Data ➔ Upload** in Splunk. Set the **Index** to `main` and choose the corresponding **Source Type**:

| \# | File Name | Recommended Source Type | Description / Use Case | 
| ----- | ----- | ----- | ----- | 
| **1** | `windows_security_logs.csv` | `csv` | Windows Security event logs (logins, privilege escalations, etc.) | 
| **2** | `sysmon_events.csv` | `csv` | Advanced Windows system activity (process creation, network connections) | 
| **3** | `auth.log` | `syslog` | Authentication logs (ssh, login attempts, pam sessions) | 
| **4** | `syslog.log` | `syslog` | General system log messages | 
| **5** | `cron.log` | `syslog` | Scheduled job execution logs | 
| **6** | `firewall_logs.csv` | `csv` | Network firewall traffic logs | 
| **7** | `vpn_logs.csv` | `csv` | Virtual Private Network connection/session details | 
| **8** | `proxy_logs.csv` | `csv` | Web proxy/HTTP access records | 
| **9** | `dns_logs.csv` | `csv` | Domain Name System query resolution logs | 
| **10** | `email_logs.csv` | `csv` | Email transaction/SMTP logs | 
| **11** | `powershell_logs.csv` | `csv` | PowerShell execution and script block logs | 
| **12** | `file_access_logs.csv` | `csv` | Object and file access audits | 
| **13** | `usb_activity_logs.csv` | `csv` | External media / USB insertion and activity | 

### 2. Lookup Tables (File-based Lookup)

The following file is a lookup table to map and enrich usernames with employee details (real name, job title, department, etc.):

* **File Name:** `user_accounts.csv`
* **Splunk Configuration Steps:**

> \[!IMPORTANT\]
> Make sure to configure the lookup table properly to allow mapping fields like `user` or `username` to employee attributes.

1. **Upload Lookup Table:**
   * Go to **Settings ➔ Lookups ➔ Lookup table files ➔ New Lookup Table File**.
   * Set **Destination App** to `search`.
   * Upload the `user_accounts.csv` file.
   * Save the destination filename as `user_accounts.csv`.

2. **Define Lookup:**
   * Go to **Settings ➔ Lookups ➔ Lookup definitions ➔ New Lookup Definition**.
   * Set the name to `user_accounts.csv`.
   * Set **Type** to `File-based`.
   * Set **Lookup file** to `user_accounts.csv`.
   * Save.

## 🛠️ Getting Started in Splunk

1. Ensure your local Splunk instance is running.
2. Create the index `main` if it does not already exist (usually default).
3. Follow the upload reference table above to ingest each dataset file.
4. Verify ingestion by searching `index="main"` in your Splunk Search & Reporting app.