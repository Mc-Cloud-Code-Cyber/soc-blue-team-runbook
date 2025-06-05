# SIEM Use Cases

A collection of detection use cases, logic, and scenarios for Security Information and Event Management (SIEM) monitoring. Use these as templates or starting points for building detections in Splunk, Sentinel, QRadar, Elastic, or your SIEM of choice.

---

## 1. Suspicious Authentication Activity

### 1.1. Multiple Failed Logins (Brute Force)
- **Description:** Detect multiple failed logins from the same source within a short period.
- **Detection Logic:**  
  - >5 failed logins from the same username or IP within 5 minutes.
- **Event Sources:**  
  - Windows Security Logs (Event ID 4625), Linux auth logs, VPN logs
- **Response:**  
  - Investigate the source, block offending IP, reset credentials if necessary.

### 1.2. Successful Login After Multiple Failures
- **Description:** Successful login immediately following multiple failures.
- **Detection Logic:**  
  - Failed logins followed by a successful login for the same user/IP within 10 minutes.
- **Response:**  
  - Confirm user intent, investigate potential password compromise.

### 1.3. Impossible Travel / Geo-Velocity
- **Description:** User logs in from two distant locations in an impossible timeframe.
- **Detection Logic:**  
  - Logins from different geolocations less than X hours apart.
- **Event Sources:**  
  - VPN, SSO, O365/AzureAD logs
- **Response:**  
  - Verify user travel, check for compromised credentials.

---

## 2. Privilege Escalation & Account Changes

### 2.1. Privilege Group Membership Change
- **Description:** User added to privileged group (e.g., Domain Admins).
- **Detection Logic:**  
  - Account added/removed from admin or sensitive group.
- **Event Sources:**  
  - Windows Event ID 4728, 4729, 4732, 4733, AzureAD logs
- **Response:**  
  - Validate request, review who made the change, escalate if unauthorized.

### 2.2. Creation of New Admin Account
- **Description:** New user account created with elevated privileges.
- **Detection Logic:**  
  - Account creation event + admin group assignment within 1 hour.
- **Event Sources:**  
  - Windows Event ID 4720, 4728, Azure/O365 logs
- **Response:**  
  - Investigate legitimacy, disable account if unauthorized.

---

## 3. Malware & Endpoint Threats

### 3.1. Malware Detected by AV/EDR
- **Description:** Endpoint security product detects malware or potentially unwanted program.
- **Detection Logic:**  
  - Malware/PUA detection event from EDR/AV console.
- **Event Sources:**  
  - Defender ATP, CrowdStrike, SentinelOne, Sysmon
- **Response:**  
  - Isolate host, run full scan, initiate incident response.

### 3.2. Suspicious Process Execution
- **Description:** Known malicious or rare process executed on endpoint.
- **Detection Logic:**  
  - Execution of process matching threat intel or outlier analysis.
- **Event Sources:**  
  - Sysmon, EDR/AV, Windows Security logs
- **Response:**  
  - Review execution context, investigate user activity.

---

## 4. Data Exfiltration & Network Anomalies

### 4.1. Large Outbound Data Transfer
- **Description:** Sudden, large volume of outbound data from endpoint or server.
- **Detection Logic:**  
  - >1GB outbound to external IP in <1 hour.
- **Event Sources:**  
  - Firewall, proxy, cloud service logs
- **Response:**  
  - Investigate file types and destination, block transfer if malicious.

### 4.2. Unusual Protocols or Destinations
- **Description:** Use of uncommon protocols or connections to rare IPs.
- **Detection Logic:**  
  - Outbound RDP/SSH to internet, connections to newly observed domains.
- **Response:**  
  - Review necessity, block if unauthorized, escalate if suspicious.

---

## 5. Suspicious Email Activity

### 5.1. Phishing Email Detected
- **Description:** Inbound email matches known phishing indicators.
- **Detection Logic:**  
  - Message with malicious attachment/link or from suspicious domain.
- **Event Sources:**  
  - Email gateway, O365, GMail logs
- **Response:**  
  - Quarantine message, alert user, block sender.

### 5.2. Bulk Email Sending from Internal Account
- **Description:** Internal account sends abnormal volume of outbound emails.
- **Detection Logic:**  
  - Account sends >100 messages in 5 minutes.
- **Event Sources:**  
  - Email gateway, mail server logs
- **Response:**  
  - Investigate for compromise, reset credentials, notify recipients.

---

## 6. Infrastructure and Service Monitoring

### 6.1. Service Stoppage or Crash
- **Description:** Critical service (e.g., domain controller, DNS, SIEM) stops unexpectedly.
- **Detection Logic:**  
  - Service stop/exit event without planned maintenance.
- **Event Sources:**  
  - Windows/Linux service logs, application logs
- **Response:**  
  - Check cause (malware, misconfig, resource exhaustion), escalate if suspicious.

### 6.2. Configuration Change Detection
- **Description:** Unauthorized change to firewall, router, or security appliance.
- **Detection Logic:**  
  - Config change log entry not linked to approved change ticket.
- **Event Sources:**  
  - Firewall/router logs, change management system
- **Response:**  
  - Revert if unauthorized, investigate source.

---

## 7. Insider Threat & Policy Violations

### 7.1. Unauthorized File Access
- **Description:** Access to sensitive folders or files by non-privileged user.
- **Detection Logic:**  
  - Access event on sensitive share/resource by user outside whitelist.
- **Event Sources:**  
  - Windows file share logs, DLP, cloud storage logs
- **Response:**  
  - Investigate user intent, lock access, escalate if necessary.

### 7.2. USB Device Connection
- **Description:** Removable storage device connected to sensitive endpoint.
- **Detection Logic:**  
  - USB insert event on restricted workstation/server.
- **Event Sources:**  
  - Endpoint logs, GPO events, DLP logs
- **Response:**  
  - Investigate device and user, enforce policy.

---

## References

- [MITRE ATT&CK Use Case Examples](https://attack.mitre.org/)
- [Splunk Security Content](https://research.splunk.com/)
- [Elastic Security Detection Rules](https://github.com/elastic/detection-rules)

---

*Last Updated: 2025-06-05*
