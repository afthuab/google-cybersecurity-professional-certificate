# Firewalls, VPNs, Proxies, and Security Zones

## 1. Firewalls

A firewall inspects network traffic and allows or blocks packets based on security rules.

| Firewall type | How it works | Key difference |
|---|---|---|
| Stateless firewall | Checks each packet individually against static rules (IP, port, protocol) | Fast, but does not track active connections |
| Stateful firewall | Tracks active session states in a state table | Automatically recognises valid return traffic for established sessions |
| Next-Generation Firewall (NGFW) | Inspects application-layer traffic and integrates IPS and threat intelligence | Provides deeper visibility beyond ports and IP addresses |

## 2. Virtual Private Networks (VPNs)

A VPN creates an encrypted tunnel across an untrusted network such as the public internet.

- **IPsec VPN:** Encrypts and authenticates IP packets at the network layer; often used for site-to-site links and remote employee access.
- **TLS/SSL VPN:** Uses TLS over standard HTTPS (`443/TCP`), making remote access easier through restrictive client networks.

A VPN protects traffic in transit, though endpoints still need patching, MFA, and access controls.

## 3. Proxy servers

A proxy server acts as an intermediary between clients and destination servers.

- **Forward proxy:** Sits between internal users and the internet. It can filter outbound web requests, cache content, and hide internal client IP addresses.
- **Reverse proxy:** Sits in front of internal web servers. It handles TLS termination, distributes load, and hides backend server addresses from external clients.

## 4. Network segmentation and security zones

Segmentation divides a network into zones with different trust levels so that a compromise in one area does not automatically expose the whole organisation.

1. **Untrusted zone:** The public internet, outside the organisation's direct control.
2. **Demilitarised Zone (DMZ):** A perimeter subnet for public-facing services such as web servers, mail gateways, and external DNS. Firewall rules block direct connections from the DMZ into the internal LAN.
3. **Internal (trusted) zone:** Employee workstations and internal business systems.
4. **Restricted zone:** Highly sensitive assets such as databases, domain controllers, and financial servers with strict access controls.

## 5. Example traffic flow

An external customer connects to a company's online store over HTTPS (`443/TCP`). The request passes through the perimeter firewall and reverse proxy into the web server inside the **DMZ**. When the web server needs product data, it queries a database in the **restricted zone** through an internal firewall rule that only allows database traffic from that specific web server.

## 6. Key point

Combining firewalls, VPNs, proxies, and segmented zones enforces defence in depth and limits how far an attacker can move after initial access.

## References

- [NIST SP 800-41 Rev. 1 – Guidelines on Firewalls and Firewall Policy](https://csrc.nist.gov/pubs/sp/800/41/r1/final)
- [CISA – Layering Network Security Through Segmentation](https://www.cisa.gov/)
