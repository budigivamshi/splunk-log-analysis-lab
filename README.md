Here is a customized version of your `README.md` template featuring your name, **Budigi Vamshi**, tailored for your Splunk Log Analysis Lab:

```markdown
# 🔍 Splunk Log Analysis Lab

Welcome to the practical log dataset and security telemetry repository. This repository provides multi-source sample logs designed for hands-on SIEM monitoring, threat hunting, and log correlation exercises in Splunk.

---

## 👤 About the Author

**Budigi Vamshi**  
*Cybersecurity Analyst & SOC Practitioner*

<p align="left">
  <a href="https://github.com/vamshibudigi"><img src="https://img.shields.io/badge/GitHub-vamshibudigi-181717?style=flat-for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
  <a href="https://linkedin.com/in/vamshibudigi"><img src="https://img.shields.io/badge/LinkedIn-Budigi%20Vamshi-0A66C2?style=flat-for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
</p>

---

## 📋 Splunk Dataset Upload Reference

Below is a reference guide for uploading the dataset files included in this repository to Splunk:

### 1. Standard Event Logs (Index: `main`)

For each of the log files, navigate to **Settings ➔ Add Data ➔ Upload** in Splunk. Set the **Index** to `main` and choose the corresponding **Source Type**:

| # | File Name | Recommended Source Type | Description / Use Case |
| :---: | :--- | :---: | :--- |
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

---

### 2. Lookup Tables (File-based Lookup)

The following file is a lookup table used to map and enrich usernames with employee or entity details:

*   **File Name:** `user_accounts.csv`
*   **Splunk Configuration Steps:**

> [!IMPORTANT]
> Make sure to configure the lookup table properly to allow mapping fields like `user` or `username` to contextual attributes.

1. **Upload Lookup Table:**
   - Go to **Settings ➔ Lookups ➔ Lookup table files ➔ New Lookup Table File**.
   - Set **Destination App** to `search`.
   - Upload the `user_accounts.csv` file.
   - Save the destination filename as `user_accounts.csv`.

2. **Define Lookup:**
   - Go to **Settings ➔ Lookups ➔ Lookup definitions ➔ New Lookup Definition**.
   - Set the name to `user_accounts.csv`.
   - Set **Type** to `File-based`.
   - Set **Lookup file** to `user_accounts.csv`.
   - Save.

---

### 🛠️ Getting Started in Splunk

1. Ensure your local Splunk instance is running.
2. Verify or create the index `main`.
3. Follow the upload reference table above to ingest each dataset file.
4. Verify ingestion by running `index="main"` in your Splunk Search & Reporting app.

```
