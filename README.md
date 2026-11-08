# Splunk SOC Detection & Threat Hunting Labs

This repository contains practical Search Processing Language (SPL) queries, correlation alerts, and incident triage reports for Security Operations Center (SOC) analysis.

---

## Environment & Data Sources
- **Platform:** Splunk Enterprise
- **Telemetry Sources:**
  - `WinEventLog:Security` (Windows Event IDs 4624, 4625, 4688, 4720)
  - `XmlWinEventLog:Microsoft-Windows-Sysmon/Operational` (Event ID 1, Event ID 3)
  - `linux_secure` (`/var/log/auth.log`)
  - Web Server Access Logs (Apache / Nginx)
- **Framework Alignment:** MITRE ATT&CK Framework

---

## Detection Coverage

| Module | Threat / Activity | MITRE ATT&CK | Focus Area |
| :--- | :--- | :--- | :--- |
| **AUTH-01** | Brute Force to Valid Account Compromise | T1110 / T1078 | Failed authentication spikes & RDP logon triage |
| **AUTH-02** | Privileged Account Creation Outliers | T1136.001 | Off-hours persistence via local admin additions |
| **PERS-01** | Suspicious Scheduled Tasks & Cron Jobs | T1053 | Command-line parameter extraction |
| **WEB-01** | Directory Traversal & Web Shell Upload | T1190 / T1505 | High-frequency POST requests and HTTP status analysis |

---

## Repository Structure
- `authentication-analysis/` — Brute force, credential access, and account modification investigations.
- `persistence-detection/` — Scheduled tasks, services, and startup persistence detection.
- `web-attack-detection/` — Web application scanning, command injection, and shell triage.

---

## Disclaimer
All queries, logs, and scenarios were executed and validated inside an isolated, authorized virtual lab environment.
