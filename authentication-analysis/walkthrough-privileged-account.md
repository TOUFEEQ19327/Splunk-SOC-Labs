# Triage Walkthrough: Privileged Account Creation (AUTH-02)

## 1. Executive Summary
- **Alert:** Suspicious Addition of Account to Privileged Groups
- **Severity:** Medium/High
- **Triage Result:** Investigation of potential persistence or privilege escalation via newly created accounts.
- **MITRE Mapping:** T1136.001 -> T1098

---

## 2. Technical Context & Telemetry
- **Index:** `security`
- **Data Source:** `WinEventLog:Security`
- **Events Tracked:** 4720 (Account Created), 4728/4732 (Group Membership Modification)

---

## 3. Investigation Steps
1. Filter security logs for event codes related to user creation and group additions.
2. Cross-reference the added user against known authorized administrative personnel.
3. Verify the parent process and account responsible for the modification.

---

## 4. Remediation Actions
1. Disable unauthorized accounts immediately.
2. Audit recent actions performed by the compromised or rogue account.
3.
