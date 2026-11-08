Triage Walkthrough: Cron Job Reverse Shell Persistence (PERSIST-01)
1. Executive Summary
 * Alert Title: Suspicious Cron Job Execution Leading to Reverse Shell
 * Severity: High
 * Triage Result: Identification of malicious scheduled jobs executing interactive shells for persistence and C2 communication.
 * MITRE ATT&CK Mapping: T1053.003 (Scheduled Task/Job: Cron), T1059.004 (Unix Shell)
2. Technical Context & Telemetry
 * Index: linux
 * Sourcetype: linux_secure (/var/log/auth.log / syslog)
 * Key Indicators: Execution of /bin/bash -i, nc -e, python -c under cron daemon events.
3. SOC Triage & Investigation Steps
 * Inspect Crontab Schedules: Check user-level crontabs (/var/spool/cron/crontabs/) and system directories (/etc/cron*).
 * Network Connection Correlation: Match execution timestamps against firewall/proxy logs or netstat output to identify the remote C2 IP and port.
 * User Context Validation: Determine if the execution user (exec_user) had authorized rights to modify scheduled tasks.
 * Parent Process Analysis: Check audit logs (auditd) to identify how the malicious cron entry was originally written.
4. Containment & Remediation Actions
 * Terminate Active Sessions: Kill the interactive shell process and terminate active network sockets.
 * Remove Malicious Cron Entry: Delete the rogue line from crontab and verify system file integrity.
 * Credential Invalidation: Reset passwords and rotate SSH authorized keys for affected accounts.
