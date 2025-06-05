# Network Monitoring

Network monitoring is a core job of any blue team. This means keeping an eye on what’s happening on your network, spotting trouble early, and knowing what “normal” looks like so you can find what isn’t. This guide explains what to watch for, where to get your data, how to spot issues, and some real-world tips for staying ahead.

---

## 1. What to Monitor

### 1.1. Traffic Patterns
- Look for big spikes or drops in network traffic.
- Watch for connections to new or strange external IP addresses.
- Track which internal systems talk to each other, and how often.

### 1.2. Protocols and Ports
- Monitor common ports (80, 443, 3389, 22, etc.) and flag odd ones (e.g., 6667, 31337).
- Notice if standard services (web, email, RDP) are being accessed at weird hours.

### 1.3. Failed Connections and Errors
- Keep an eye on blocked or failed connection attempts (could mean scanning or brute force).
- Monitor for repeated DNS query failures or strange domain lookups.

### 1.4. External Exposure
- Track open ports on your public IPs.
- Monitor for signs of scanning or attempted exploitation from the internet.

### 1.5. Internal Movement
- Be aware of lateral movement (one device probing or connecting to many others).
- Notice if sensitive servers are being accessed by unusual hosts or users.

---

## 2. Data Sources

- **Firewall Logs:** See what’s being allowed, denied, and where it’s coming from/going to.
- **IDS/IPS Alerts:** Tools like Snort, Suricata, Zeek (Bro) flag suspicious traffic.
- **NetFlow/sFlow:** High-level network summaries (who talked to whom, how much, when).
- **Packet Captures:** Detailed look at traffic (use Wireshark, tcpdump for investigations).
- **DNS Logs:** See which sites or services are being requested.
- **Proxy Logs:** Track web access and downloads.
- **VPN Logs:** Who is connecting remotely and from where.

---

## 3. Detection Strategies

### 3.1. Baseline Your Network
- Know your normal traffic levels, peak times, and usual destinations.
- Use baselines to help spot sudden changes or outliers.

### 3.2. Use Rules and Alerts
- Set up IDS/IPS signatures for known threats (malware, exploit attempts, data exfil).
- Make custom rules for your environment (e.g., alert if database server talks to internet).

### 3.3. Correlate Across Sources
- Tie together logs from firewalls, IDS, DNS, etc. to get the full picture.
- Example: Multiple failed logins on a server plus weird outbound traffic = possible compromise.

### 3.4. Track Long-Term Trends
- Review trends weekly/monthly to spot slow-moving attacks or policy drift.
- Use graphs and dashboards (from your SIEM or monitoring tools) to visualize.

---

## 4. Incident Response Tips

- **Rapid Triage:** When you see an alert, check which systems are involved, what data is at risk, and whether the activity is still ongoing.
- **Block Quickly:** Don’t hesitate to block malicious IPs or kill suspicious connections.
- **Capture Evidence:** Save relevant logs, netflow, or packet captures for investigation.
- **Communicate:** Let affected users or teams know about major network incidents.

---

## 5. Example Alerts to Build

- Large file uploads to unknown external servers.
- Internal host scans many other internal devices (port scanning).
- Repeated failed VPN or RDP logins from foreign countries.
- Outbound traffic to known bad IPs/domains (check threat intel feeds).
- DNS queries for weird or random-looking domains (DGA activity).

---

## 6. Monitoring Tools

| Tool/Platform      | Purpose                        |
|--------------------|-------------------------------|
| Wireshark          | Packet capture and analysis   |
| Zeek (Bro)         | Network analysis framework    |
| Suricata/Snort     | Intrusion detection           |
| ntopng             | Real-time traffic monitoring  |
| NetFlow/sFlow      | Traffic summaries             |
| Security Onion     | All-in-one network monitoring |
| pfSense            | Open-source firewall/logging  |

---

## 7. References

- [SANS Network Monitoring Cheat Sheet](https://www.sans.org/white-papers/37861/)
- [Wireshark User Guide](https://www.wireshark.org/docs/wsug_html_chunked/)
- [Zeek (Bro) Documentation](https://docs.zeek.org/en/current/)
- [MITRE ATT&CK: Network-based Techniques](https://attack.mitre.org/tactics/TA0011/)

---

*Last Updated: 2025-06-05*
