# Phishing Email Incident Response

## Overview
This playbook provides a step-by-step procedure for handling phishing email incidents within an organization. It is intended for SOC analysts and incident responders.

---

## 1. Identification

- **User Reports:** User forwards or reports a suspicious email.
- **SIEM Alerts:** Automated detection by email security or SIEM tools.
- **Indicators:** Email contains suspicious links, attachments, urgent requests, spoofed sender, or poor grammar.

### Checklist
- [ ] Verify user report authenticity
- [ ] Review reported email in a sandboxed environment
- [ ] Extract email headers, body, and attachments for analysis

---

## 2. Containment

- **Isolate Affected Accounts:** Temporarily lock or monitor user accounts suspected of compromise.
- **Block Sender:** Add sender or domain to blocklist at email gateway.
- **Quarantine Email:** Remove phishing emails from mailboxes using admin tools.
- **Network Actions:** Block any known malicious domains/URLs in web filters and firewalls.

---

## 3. Eradication

- **Remove Artifacts:** Delete malicious emails and attachments from all user mailboxes.
- **Clean Up:** Ensure no malware was executed. Run antivirus/EDR scans on affected hosts.
- **Reset Credentials:** For any user who clicked a link or entered credentials, force password reset and session revocation.

---

## 4. Recovery

- **Restore Services:** Re-enable access for users after confirming safety.
- **Monitor:** Watch for further suspicious activity from affected users/devices for at least 7 days.
- **Educate:** Notify and educate user(s) about phishing risks and how to spot/report suspicious emails.

---

## 5. Lessons Learned & Documentation

- **Document Incident:** Record timeline, indicators, actions taken, and final resolution in your incident management platform.
- **Update Detection:** Tune SIEM rules and email security filters based on new indicators.
- **Awareness Training:** Feed relevant examples back into the organization's security awareness program.

---

## Example Tools

- **Email Analysis:** MxToolbox, VirusTotal, Any.Run, PhishTool
- **Header Analysis:** [Google Admin Toolbox Messageheader](https://toolbox.googleapps.com/apps/messageheader/)
- **IOC Search:** VirusTotal, Hybrid Analysis, AbuseIPDB

---

## References

- [SANS Incident Handler's Handbook](https://www.sans.org/white-papers/33901/)
- [CISA Phishing Guidance](https://www.cisa.gov/news-events/news/protecting-against-phishing-attacks)
- [Microsoft: Responding to a Compromised Email Account](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)

---

*Last Updated: 2025-06-05*
