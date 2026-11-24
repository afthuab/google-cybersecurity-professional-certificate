# Portfolio Activity: Using the NIST Cybersecurity Framework to Respond to a Security Incident

## 1. Purpose

This portfolio activity applies the **NIST Cybersecurity Framework (CSF)** to structure an incident response and remediation plan for a network security event.

This document is an original learning example based on a fictional scenario. All IP addresses, systems, and events are simulated and do not represent a real organization or investigation.

## 2. Incident scenario

**Organization:** Harborline Retail (fictional)  
**Affected system:** Public customer web portal (`198.51.100.10`, documentation-only address)  
**Summary of events:** During peak hours, customers reported timeouts on the web portal. Monitoring tools showed high volumes of incomplete TCP `SYN` requests and repetitive HTTP `GET` traffic from multiple external IP addresses, preceded by port scans probing ports `22`, `80`, `443`, and `8080` on the perimeter firewall.

## 3. Incident response mapped to NIST CSF

| NIST CSF function | Goal in this scenario | Recommended actions |
|---|---|---|
| **1. Identify** | Understand affected assets, exposed services, and business impact | Inventory public web servers (`198.51.100.10`), load balancers, and ISP links; review open perimeter ports; assess customer impact of portal downtime. |
| **2. Protect** | Strengthen preventative safeguards to reduce exposure and absorb traffic spikes | Enable TCP `SYN cookies`; apply firewall rate limits; place the portal behind a reverse proxy/CDN with DDoS protection; close unused ports and restrict SSH (`22/TCP`) to VPN access. |
| **3. Detect** | Monitor network telemetry to spot abnormal traffic early | Configure SIEM and IDS/IPS alerts for spikes in half-open TCP connections, high per-IP HTTP request rates, and perimeter port sweeps; capture targeted `tcpdump` samples. |
| **4. Respond** | Contain the attack, mitigate malicious traffic, and document the timeline | Block confirmed abusive source ranges via firewall ACLs and WAF rules; coordinate upstream traffic filtering with the ISP; preserve logs and packet captures for investigation. |
| **5. Recover** | Restore normal availability safely and improve readiness | Gradually lift temporary strict blocks once traffic returns to normal; verify server CPU, memory, and connection tables; update incident playbooks after a post-incident review. |

## 4. Detailed findings and recommendations

### Finding 1: Unfiltered SYN and HTTP flood traffic
- **Risk:** Attackers exhausted web server connection queues, causing legitimate customer requests to time out.
- **Recommendation:** Enable `SYN cookies` on edge hosts, enforce connection-rate thresholds on the firewall and Web Application Firewall (WAF), and use upstream DDoS scrubbing.

### Finding 2: Exposed non-essential ports during reconnaissance
- **Risk:** Perimeter port scans identified open administrative and alternate web ports (`22` and `8080`).
- **Recommendation:** Enforce a default-deny inbound firewall policy, allow only `80/TCP` and `443/TCP` publicly, and require VPN access for administrative interfaces.

### Finding 3: Delayed alert escalation during traffic spikes
- **Risk:** Latency built up before the team correlated firewall drops with web server `503` errors.
- **Recommendation:** Create a SIEM correlation alert combining firewall connection spikes with web server error rates, and document clear escalation steps in the SOC playbook.

## 5. Conclusion

Using the NIST CSF core functions (**Identify, Protect, Detect, Respond, and Recover**) organizes both immediate containment during a DDoS incident and long-term hardening improvements afterward.

## References

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [CISA – Understanding Denial-of-Service Attacks](https://www.cisa.gov/news-events/news/understanding-denial-service-attacks)
- [NIST SP 800-61 Rev. 2 – Computer Security Incident Handling Guide](https://csrc.nist.gov/pubs/sp/800/61/r2/final)
