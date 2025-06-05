# DDoS Attack Incident Response

## Overview
This playbook outlines the procedures for identifying, responding to, and recovering from Distributed Denial of Service (DDoS) attacks targeting your organization’s services or infrastructure.

---

## 1. Identification

- **Alerts:** Monitor SIEM, IDS/IPS, and network monitoring tools for unusual spikes in inbound/outbound traffic, service unavailability, or multiple failed connection attempts.
- **User Reports:** Users or customers report slow services, downtime, or inability to access applications.
- **Indicators:**  
  - Significant increase in traffic from unusual IP ranges  
  - Services unreachable or slow  
  - Multiple SYN or UDP requests to same service  
  - Network hardware overloaded

### Checklist
- [ ] Confirm alert is not a false positive (e.g., marketing event, software update)
- [ ] Identify impacted services and business functions
- [ ] Collect evidence (logs, netflow, packet captures)

---

## 2. Containment

- **Upstream Filtering:** Contact ISP/cloud provider for traffic filtering or scrubbing services.
- **Rate Limiting:** Enable rate limits or geo-blocking at firewall/load balancer level.
- **Blacklist Malicious IPs:** Block identified attacker IPs, if feasible.
- **Service Offloading:** Redirect or offload traffic to DDoS protection services (e.g., Cloudflare, Akamai).
- **Internal Communications:** Notify internal stakeholders and management.

---

## 3. Eradication

- **Review Block Rules:** Ensure blocks/filters do not affect legitimate users.
- **Adjust Mitigations:** Tune DDoS defense rules based on attacker behavior changes.
- **Coordinate with Providers:** Maintain contact with ISPs and DDoS mitigation vendors.

---

## 4. Recovery

- **Monitor:** Track for reduction or cessation of malicious traffic.
- **Restore Services:** Gradually re-enable access and monitor for lingering issues.
- **User Notification:** Communicate service restoration status to affected users or customers.
- **Post-Incident Monitoring:** Continue monitoring for recurrence.

---

## 5. Lessons Learned & Documentation

- **Document Incident:** Capture timeline, scope, affected services, attack vectors, and actions taken.
- **Update Defenses:** Work with IT/network teams to improve future DDoS detection and mitigation.
- **Review Contracts:** Evaluate DDoS protection services and incident response procedures for improvement.
- **Conduct Debrief:** Hold a post-incident review with stakeholders.

---

## Example Tools

- **Monitoring:** SolarWinds, Nagios, Zabbix, SIEMs
- **DDoS Protection:** Cloudflare, Akamai, AWS Shield
- **Traffic Analysis:** Wireshark, tcpdump, NetFlow analyzers
- **Firewall/IDS:** pfSense, Cisco ASA, Snort, Suricata

---

## References

- [Cloudflare: Understanding DDoS Attacks](https://www.cloudflare.com/learning/ddos/)
- [US-CERT: Security Tip (ST04-015) – Understanding Denial-of-Service Attacks](https://us-cert.cisa.gov/ncas/tips/ST04-015)
- [OWASP: DDoS Countermeasures](https://owasp.org/www-community/attacks/DDoS_Attack)

---

*Last Updated: 2025-06-05*
