# Triage Walkthrough: Brute Force with Compromised Credential (AUTH-01)

## 1. Executive Summary
- **Alert:** High-Volume Failed Logons Followed by Successful Interactive Authentication
- **Severity:** High
- **Triage Result:** True Positive — Credential Stuffing / Password Guessing attack via RDP resulting in valid account access.
- **MITRE Mapping:** T1110.001 -> T1078.002

---

## 2. Technical Context & Telemetry
- **Index:** `security`
- **Data Source:** `WinEventLog:Security`
- **Logon Types Evaluated:**
  - `Logon_Type=3`: Network
  - `Logon_Type=10`: RemoteInteractive

---

## 3. Investigation Progression

### Query 1: Identifying the Anomaly
```spl
index=security sourcetype="WinEventLog:Security" EventCode=4625
| stats count by IpAddress, SubStatus, TargetUserName
| sort - count

Query 2: Validating Compromise
index=security sourcetype="WinEventLog:Security" IpAddress="198.51.100.44" EventCode IN (4624, 4625)
| eval Status=if(EventCode=4625, "FAIL", "SUCCESS")
| table _time, Status, TargetUserName, Logon_Type, IpAddress
| sort _time

4. Indicators of Compromise (Defanged)
 * IPv4: 198.51.100[.]44
 * User Account: jdoe
 * Host System: WIN-SRV-CORP01
5. Remediation Actions Taken
 * Host Isolation initiated.
 * User account locked and password reset forced.
 * Perimeter firewall block applied.
