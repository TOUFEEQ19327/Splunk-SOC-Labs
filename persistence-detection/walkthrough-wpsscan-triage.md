Triage Walkthrough: WordPress Vulnerability Scan (WEB-01)
1. Executive Summary
 * Alert: WordPress Vulnerability Scan Detected (WPScan)
 * Severity: Medium
 * Triage Result: Identification of active reconnaissance and vulnerability enumeration against WordPress endpoints.
 * MITRE Mapping: T1595.002 (Active Scanning), T1190 (Exploit Public-Facing Application)
2. Technical Context & Telemetry
 * Index: web
 * Sourcetype: access_common
 * Indicators: High request volume to wp-login.php, wp-admin, or User-Agent containing "WPScan".
3. SOC Investigation Steps
 * Analyze Request Patterns: Check if the scanner successfully enumerated valid usernames or sensitive plugins.
 * Review HTTP Status Codes: Differentiate between 403 (Blocked/Forbidden) and 200/404 (Successful discovery).
 * Source IP Reputation: Pivot on the client IP to check for known malicious nodes or Tor exit relays.
4. Remediation Actions
 * Block Attacker IP: Implement temporary drop rules on the perimeter firewall.
 * Harden WordPress: Ensure XML-RPC is disabled and limit login attempts.
