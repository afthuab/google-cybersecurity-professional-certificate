# Network Protocols, Subnetting, and Wireless Security

## 1. Common network protocols and ports

Protocols define the rules devices follow when exchanging data. Ports identify specific services running on a host.

| Protocol | Port(s) | Transport | Purpose | Security note |
|---|---|---|---|---|
| FTP | 20, 21 | TCP | File transfer | Sends credentials in plaintext; prefer SFTP |
| SSH / SFTP | 22 | TCP | Encrypted remote login and file transfer | Common brute-force target; use key authentication |
| Telnet | 23 | TCP | Unencrypted remote terminal | Legacy protocol; plaintext traffic is a security risk |
| SMTP | 25, 587 | TCP | Sending email | Unexpected outbound port 25 traffic may indicate spam or malware |
| DNS | 53 | UDP / TCP | Resolves domain names to IP addresses | Useful for spotting suspicious domains or DNS tunnelling |
| DHCP | 67, 68 | UDP | Assigns IP settings automatically | Rogue DHCP servers can redirect local traffic |
| HTTP | 80 | TCP | Unencrypted web traffic | Data can be read or altered on untrusted networks |
| HTTPS | 443 | TCP | Encrypted web traffic using TLS | Protects confidentiality and integrity in transit |
| SMB | 445 | TCP | Windows file and printer sharing | Should not be exposed directly to the internet |
| RDP | 3389 | TCP / UDP | Remote Windows desktop access | Frequent target for credential attacks and ransomware |

## 2. Subnetting and CIDR notation

Subnetting divides a larger IP network into smaller segments to reduce unnecessary broadcast traffic and limit lateral movement during an incident.

**Classless Inter-Domain Routing (CIDR)** writes the network prefix length after a slash, such as `198.51.100.0/24`.

| CIDR prefix | Subnet mask | Total addresses | Usable host addresses | Common use |
|---|---|---|---|---|
| `/24` | `255.255.255.0` | 256 | 254 | Standard office or workstation subnet |
| `/26` | `255.255.255.192` | 64 | 62 | Small server or department segment |
| `/28` | `255.255.255.240` | 16 | 14 | Small DMZ or perimeter subnet |
| `/30` | `255.255.255.252` | 4 | 2 | Point-to-point link between two routers |

In standard IPv4 subnets, two addresses are reserved: the network address and the broadcast address.

## 3. Evolution of wireless security protocols

- **WEP:** Older standard with serious cryptographic weaknesses; easily broken and no longer safe to use.
- **WPA:** Transitional update that introduced TKIP, but still vulnerable to modern attacks.
- **WPA2:** Uses AES-CCMP encryption. Still widely used, especially in enterprise networks with 802.1X authentication.
- **WPA3:** Current standard. Uses Simultaneous Authentication of Equals (SAE) to protect against offline password guessing and enforces management frame protection.

## 4. Example commands

```bash
# Check the A record for a domain using dig
dig example.com A +short

# Show listening TCP and UDP sockets on Linux
ss -tulnp
```

## 5. Key point

Recognising standard ports, subnet boundaries, and secure protocol versions helps an analyst spot misconfigurations and unexpected network services quickly.

## References

- [IANA Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
- [Wi-Fi Alliance – Security](https://www.wi-fi.org/discover-wi-fi/security)
