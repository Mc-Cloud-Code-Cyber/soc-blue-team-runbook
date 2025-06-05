# Endpoint Monitoring

Effective endpoint monitoring is essential for early detection of threats, rapid investigation, and containment of security incidents. This document outlines what to monitor, recommended data sources, detection strategies, and response considerations for endpoints in a modern enterprise environment.

---

## 1. What to Monitor on Endpoints

### 1.1. User Authentication & Logon Events
- Successful and failed login attempts (local, remote, RDP)
- Logons outside normal hours or from unusual locations
- Use of disabled or expired accounts

### 1.2. Process Creation & Execution
- New or rare process executions (especially from user temp/AppData folders)
- Execution of scripting engines (e.g., PowerShell, wscript, cscript)
- Parent-child process anomalies (e.g., Word spawning cmd.exe)
- Unusual command-line arguments

### 1.3. File and Registry Changes
- Creation or modification of system/critical files
- Suspicious registry key modifications (persistence, autoruns)
- Unexpected file extension changes (e.g., .doc to .exe)

### 1.4. Network Connections
- Outbound connections to untrusted or new IP addresses/domains
- Unusual ports or protocols
- Beaconing behavior (regular intervals to C2 servers)
- Data exfiltration indicators (large uploads)

### 1.5. Device & Peripheral Events
- USB or removable media inserted/removed
- New hardware installed
- Printing or screen capture events

### 1.6. Security Product Activity
- AV/EDR alerts (detections, quarantine, remediation actions)
- Product disablement or tampering events

---

## 2. Data Sources for Endpoint Monitoring

- **Windows Event Logs:**  
  - Security (e.g., 4624/4625 logon, 4688 process, 4719 policy change)
  - Sysmon logs (process, network, registry, driver loads)
  - PowerShell logs (4103/4104, script block logging)
- **Linux Audit Logs:**  
  - /var/log/auth.log, /var/log/secure, auditd
- **Endpoint Detection & Response (EDR):**  
  - Alerts and telemetry from CrowdStrike, Defender ATP, SentinelOne, etc.
- **AV Logs:**  
  - Detections, updates, exclusions
- **Device Control:**  
  - USB activity logs, DLP system events

---

## 3. Detection Strategies

### 3.1. Baseline Normal Behavior
- Document normal user and system behavior (processes, connections, working hours)
- Use baselining to reduce noise and highlight outliers

### 3.2. Use Detection Rules and Signatures
- Leverage vendor-provided and custom YARA/Sigma/Sysmon rules
- Apply MITRE ATT&CK mapping for coverage

### 3.3. Correlate Multiple Events
- Combine logon, process, and network events for richer context
- Detect multi-stage attacks (e.g., phishing -> credential theft -> lateral movement)

### 3.4. Alert Tuning and Noise Reduction
- Regularly review and tune alert thresholds to avoid alert fatigue
- Suppress known-good, repetitive events and whitelist approved tools

---

## 4. Incident Response Considerations

- **Rapid Triage:**  
  - Use EDR console or SIEM for instant endpoint isolation/quarantine
- **Forensics Collection:**  
  - Acquire memory, disk images, and volatile data as needed
- **Containment:**  
  - Disable compromised accounts, block malicious hashes, isolate network segment
- **Remediation:**  
  - Remove malware, reset passwords, patch vulnerabilities
- **Documentation:**  
  - Record incident timeline, evidence, and actions in ticketing/IR platform

---

## 5. Monitoring Tools

| Tool/Platform      | Purpose                                |
|--------------------|----------------------------------------|
| Sysmon            | Detailed Windows endpoint telemetry     |
| Microsoft Defender| AV, EDR, automated investigation        |
| CrowdStrike       | EDR, IOC search, threat hunting         |
| Wazuh             | Open-source SIEM/endpoint monitoring    |
| OSQuery           | Endpoint visibility via SQL-like queries|
| Velociraptor      | Endpoint hunting & forensics            |
| Elastic Agent     | Unified agent for logs, metrics, EDR    |

---

## 6. Example SIEM Detections

- **Suspicious PowerShell:**  
  `EventCode=4104 AND ScriptBlockText IN ("Invoke-WebRequest","DownloadString","IEX")`
- **RDP Logon Outside Business Hours:**  
  `EventCode=4624 AND LogonType=10 AND NOT (TimeGenerated BETWEEN 08:00 AND 18:00)`
- **Unsigned Binary Execution:**  
  `Sysmon EventID=1 AND NOT VerifiedSigner:"Microsoft Windows"`

---

## 7. References

- [MITRE ATT&CK - Endpoint Detection](https://attack.mitre.org/)
- [SwiftOnSecurity: Sysmon Config](https://github.com/SwiftOnSecurity/sysmon-config)
- [Elastic Security: Windows Event IDs](https://www.elastic.co/guide/en/security/current/windows-event-ids.html)
- [CrowdStrike: Endpoint Security Best Practices](https://www.crowdstrike.com/cybersecurity-101/endpoint-security/)

---

*Last Updated: 2025-06-05*
