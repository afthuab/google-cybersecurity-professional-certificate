# Packet Analysis with tcpdump and Wireshark

## 1. Role of packet analysis in a SOC

Logs show summaries of events, while packet captures show the actual network traffic. Analysts use **Wireshark** (graphical) and **tcpdump** (command-line) to inspect headers, check TCP flags, verify DNS queries, and confirm whether an alert reflects real malicious traffic.

## 2. TCP three-way handshake and flags

Reliable TCP connections start with a three-way handshake: `SYN` -> `SYN-ACK` -> `ACK`.

| tcpdump flag | TCP flag name | Typical purpose |
|---|---|---|
| `[S]` | SYN | Starts a TCP connection |
| `[S.]` | SYN-ACK | Confirms receipt of `SYN` and synchronises sequence numbers |
| `[.]` | ACK | Acknowledges received packets |
| `[P.]` | PSH-ACK | Sends application data immediately to the receiving program |
| `[F.]` | FIN-ACK | Closes a connection normally |
| `[R]` / `[R.]` | RST / RST-ACK | Resets a connection immediately (often seen on closed ports) |

## 3. Useful tcpdump commands

```bash
# Capture packets on interface eth0 without resolving hostnames or port names (-nn)
sudo tcpdump -i eth0 -nn

# Capture only TCP SYN packets
sudo tcpdump -i eth0 -nn 'tcp[tcpflags] & tcp-syn != 0'

# Save DNS traffic to a PCAP file for analysis in Wireshark
sudo tcpdump -i eth0 -nn port 53 -w dns_sample.pcap

# Read packets from an existing PCAP file
tcpdump -nn -r dns_sample.pcap 'tcp port 80'
```

## 4. Simulated exercise: Investigating suspicious tcpdump output

This is a fictional packet-capture excerpt created for learning. The IP addresses below (`203.0.113.45` and `198.51.100.10`) are RFC 5737 documentation-only addresses and do not represent real systems.

```text
10:15:02.110214 IP 203.0.113.45.52110 > 198.51.100.10.80: Flags [S], seq 11001, win 64240, length 0
10:15:02.110502 IP 198.51.100.10.80 > 203.0.113.45.52110: Flags [S.], seq 44102, ack 11002, win 65160, length 0
10:15:02.110790 IP 203.0.113.45.52111 > 198.51.100.10.80: Flags [S], seq 12001, win 64240, length 0
10:15:02.111045 IP 198.51.100.10.80 > 203.0.113.45.52111: Flags [S.], seq 44890, ack 12002, win 65160, length 0
10:15:02.111310 IP 203.0.113.45.52112 > 198.51.100.10.80: Flags [S], seq 13001, win 64240, length 0
10:15:02.111608 IP 198.51.100.10.80 > 203.0.113.45.52112: Flags [S.], seq 45210, ack 13002, win 65160, length 0
```

### Triage observations

1. **Source and destination:** External address `203.0.113.45` repeatedly connects to `198.51.100.10` on port `80` (HTTP) from incrementing ephemeral source ports (`52110`, `52111`, `52112`).
2. **Handshake pattern:** The server responds with `SYN-ACK` (`[S.]`), but `203.0.113.45` never sends the final `ACK` (`[.]`).
3. **Assessment:** Consistent with a simulated **TCP SYN flood** attempting to exhaust the web server's connection table.
4. **Next steps:** Check perimeter firewall logs for volume and additional source IPs, verify whether `SYN cookies` are enabled, and escalate for rate limiting or blocking according to team procedures.

## 5. Key point

Reading timestamps, IP/port pairs, and TCP flags in `tcpdump` lets an analyst quickly confirm whether connections are completing normally or stalling in half-open states.

## References

- [tcpdump Official Manual](https://www.tcpdump.org/manpages/tcpdump.1.html)
- [Wireshark User's Guide](https://www.wireshark.org/docs/wsug_html_chunked/)
