# OS and Network Hardening

## 1. What is security hardening?

Security hardening is the process of reducing a system's attack surface by removing unnecessary software, closing unused ports, enforcing strong authentication, and applying security updates.

## 2. OS hardening practices

Attackers frequently use automated brute-force scripts against exposed login services (such as SSH and RDP) or exploit unpatched operating systems.

- **Patch management:** Apply OS and application security updates regularly to fix known vulnerabilities.
- **Configuration baselines:** Build systems from approved hardened templates (such as CIS Benchmarks) instead of default vendor settings.
- **Disable unnecessary services:** Turn off unused protocols and daemons (`Telnet`, `FTP`, unused file shares) so fewer ports listen on the network.
- **Authentication controls:** Enforce strong passwords, Multi-Factor Authentication (MFA), account lockout limits against brute-force attempts, and SSH key-based authentication.
- **Host firewalls and EDR:** Enable host-based firewalls (`ufw`, `iptables`, Windows Defender Firewall) and endpoint monitoring agents.

### Example Linux hardening commands (illustrative)

These commands show standard configuration examples; they do not represent changes made to a production environment.

```bash
# Deny inbound connections by default and allow outbound connections
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow SSH only from an internal admin subnet and allow HTTPS
sudo ufw allow from 192.0.2.0/24 to any port 22 proto tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

## 3. Network hardening practices

| Control | Purpose | Risk reduced |
|---|---|---|
| VLAN segmentation | Separates user devices, servers, and guest Wi-Fi into distinct networks | Lateral movement across departments |
| Switch port security | Limits which MAC addresses can connect and disables unused physical ports | Unauthorised physical device connections |
| Router and firewall ACLs | Permits only required IP and port traffic and drops everything else | Port scanning and access to internal services |
| Encrypted management | Uses SSH, HTTPS, and SNMPv3 instead of Telnet, HTTP, and SNMPv1/v2c | Credential interception on admin interfaces |
| IDS and IPS | Monitors traffic for known signatures and suspicious patterns | Exploit attempts, brute-force bursts, and malware traffic |

## 4. IDS vs. IPS

- **Intrusion Detection System (IDS):** Monitors a copy of network traffic or host logs and sends alerts when suspicious activity matches a rule or anomaly threshold.
- **Intrusion Prevention System (IPS):** Sits inline with network traffic and can actively drop malicious packets or reset suspicious connections.

## 5. Key point

Hardening reduces the number of weaknesses available to an attacker before an incident happens, while IDS/IPS provides visibility if malicious traffic reaches the network.

## References

- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks)
- [NIST SP 800-123 – Guide to General Server Security](https://csrc.nist.gov/pubs/sp/800/123/final)
