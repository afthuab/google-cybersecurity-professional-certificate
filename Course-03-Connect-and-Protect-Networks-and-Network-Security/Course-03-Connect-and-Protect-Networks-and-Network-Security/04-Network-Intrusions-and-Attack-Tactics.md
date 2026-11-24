# Network Intrusions and Attack Tactics

## 1. Why networks are targeted

Networks carry authentication traffic, business data, and administrative connections. Attackers target networks to disrupt availability, intercept sensitive information, or impersonate trusted hosts.

## 2. Denial-of-Service (DoS and DDoS)

A **DoS attack** tries to exhaust a system's bandwidth, CPU, or connection memory so legitimate users cannot access a service. A **DDoS attack** uses many compromised systems (a botnet) to send traffic at the same time.

| Attack variant | How it works | Primary impact |
|---|---|---|
| SYN flood | Sends many TCP `SYN` requests without completing the three-way handshake | Fills the server's half-open connection queue |
| ICMP flood | Sends high volumes of ICMP Echo Request packets | Consumes network bandwidth and processing capacity |
| HTTP flood | Sends large numbers of legitimate-looking `GET` or `POST` requests | Exhausts web server threads or backend databases |

## 3. Malicious packet sniffing

Packet capture tools are legitimate utilities for troubleshooting, but attackers can misuse them on unsegmented or unencrypted networks to collect plaintext usernames, passwords, and session tokens from protocols such as HTTP, FTP, or Telnet.

## 4. IP spoofing

**IP spoofing** involves forging the source IP address in packet headers. Attackers use it to hide where traffic originates, impersonate trusted internal systems, or carry out reflection and amplification attacks (for example, using open DNS or NTP servers).

## 5. Interception tactics

- **On-path attack (Man-in-the-Middle):** An attacker secretly positions themselves between two communicating endpoints—such as through ARP spoofing on a local LAN or a rogue Wi-Fi access point—to read or alter traffic.
- **Replay attack:** Valid authentication data or signed packets are captured and resent later to gain unauthorised access without decrypting the message.

## 6. What SOC analysts look for

- Sudden spikes in inbound traffic or incomplete TCP connections (`SYN` without `ACK`)
- Unusual port scans hitting many ports on a perimeter host in a short time
- Plaintext credentials or legacy protocols (`Telnet`, `FTP`, `HTTP`) on internal segments
- Duplicate IP/MAC conflicts or unexpected ARP changes on a local subnet
- Outbound connections to unfamiliar external IP addresses or unusual ports

## 7. Key point

Most network attacks leave recognisable patterns in firewall logs, flow records, or packet captures. Correlating those clues helps distinguish an active intrusion from routine traffic spikes.

## References

- [CISA – Understanding Denial-of-Service Attacks](https://www.cisa.gov/news-events/news/understanding-denial-service-attacks)
- [MITRE ATT&CK – Network Denial of Service (T1498)](https://attack.mitre.org/techniques/T1498/)
