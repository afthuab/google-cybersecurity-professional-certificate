# Network Architecture and Models

## 1. What is a network?

A computer network connects two or more devices so they can share data, applications, and resources. Understanding how traffic moves across a network helps a SOC analyst tell normal communication apart from suspicious activity.

## 2. Common network devices

| Device | Main role | Security relevance |
|---|---|---|
| Hub | Sends incoming signals to all connected ports | Any connected device can observe local traffic; largely replaced by switches |
| Switch | Forwards frames to the right port using MAC addresses | Supports VLANs and port security controls |
| Router | Directs IP packets between different networks | Enforces Access Control Lists (ACLs) at network boundaries |
| Modem | Connects a local network to an Internet Service Provider (ISP) | Marks the boundary between internal and external networks |
| Access point (AP) | Connects wireless devices to a wired network | Needs strong encryption (WPA2/WPA3) and monitoring for rogue APs |

## 3. Cloud networks and SDN

Traditional networks rely on dedicated hardware appliances where routing decisions and packet forwarding happen on the same device. Cloud environments use **Software-Defined Networking (SDN)** to separate the **control plane** (policy and routing decisions) from the **data plane** (packet forwarding).

This allows security teams to update firewall rules, segment virtual networks, and isolate affected cloud instances centrally through software rather than manually configuring individual switches.

## 4. TCP/IP and OSI models

Network communication is organised into layers. Each layer handles a specific part of sending or receiving data.

| OSI layer | OSI name | TCP/IP layer | Common protocols |
|---|---|---|---|
| 7 | Application | Application | HTTP, HTTPS, DNS, SSH, SMTP |
| 6 | Presentation | Application | TLS/SSL |
| 5 | Session | Application | Session management protocols |
| 4 | Transport | Transport | TCP, UDP |
| 3 | Network | Internet | IPv4, IPv6, ICMP, IPsec |
| 2 | Data Link | Network Access | Ethernet, ARP, Wi-Fi (802.11) |
| 1 | Physical | Network Access | Cables, fibre, radio signals |

When data is sent, each layer adds its own header in a process called **encapsulation**. The receiving device removes those headers in reverse order.

## 5. Addressing on a network

- **MAC address:** A 48-bit hardware identifier used for communication on a local network segment (for example, `00:1A:2B:3C:4D:5E`).
- **IPv4 address:** A 32-bit logical address written as four decimal numbers (for example, `192.0.2.15`).
- **IPv6 address:** A 128-bit hexadecimal address designed to provide a much larger address space than IPv4.

## 6. Useful Linux commands for checking network state

```bash
# View network interfaces, IP addresses, and MAC addresses
ip addr show

# Check the local routing table
ip route show

# View the local ARP table (IP-to-MAC mappings)
ip neigh show
```

## 7. Key point

Knowing which layer a protocol or device operates on makes it easier to narrow down where a network issue or security alert is occurring.

## References

- [NIST SP 800-41 Rev. 1 – Guidelines on Firewalls and Firewall Policy](https://csrc.nist.gov/pubs/sp/800/41/r1/final)
- [Cloudflare Learning Center – What is the OSI Model?](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)
