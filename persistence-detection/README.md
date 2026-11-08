Persistence Detection & Web Reconnaissance Lab
Overview
This repository module documents detection engineering and security operation center (SOC) triage procedures for common threat techniques targeting Linux environments and web infrastructure.
Documented Scenarios
1. Cron Job Reverse Shell Persistence
 * MITRE ATT&CK: T1053.003 (Scheduled Task/Job: Cron)
 * Detection File: cron-reverse-shell-detection.spl
 * Triage Guide: walkthrough-cron-reverse-shell.md
 * Focus: Monitoring abnormal additions and edits within crontab files (/etc/cron*, /var/spool/cron/crontabs) executing reverse shells via bash, netcat, or python.
2. WordPress Reconnaissance & Vulnerability Scanning
 * MITRE ATT&CK: T1595.002 (Active Scanning: Vulnerability Scanning), T1190 (Exploit Public-Facing Application)
 * Detection File: WPScan-reconnaissance.spl
 * Triage Guide: walkthrough-wpscan-triage.md
 * Focus: Detecting automated enumeration tools (WPScan) probing WordPress sensitive paths (/wp-login.php, /wp-admin) and malicious user-agents within web access logs.
Log Sources
 * Linux OS: Syslog / Auditd (/var/log/syslog, /var/log/audit/audit.log)
 * Web Servers: Apache / Nginx access logs (access_common)
   
