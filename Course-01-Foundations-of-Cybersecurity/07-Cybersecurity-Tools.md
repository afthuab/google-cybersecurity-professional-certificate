# Cybersecurity Tools and Technologies

This course introduced several tools and technologies used in security work. This file explains what they are; it does not claim that I have completed hands-on labs with all of them.

## SIEM

A Security Information and Event Management (SIEM) platform collects and analyses logs from sources such as servers, endpoints, firewalls, and applications. It helps security teams search events, connect related activity, and investigate alerts.

Examples include Splunk, Microsoft Sentinel, and Google Security Operations.

## Network protocol analysers

A network protocol analyser captures and inspects network traffic.

- **Wireshark** provides a graphical interface for examining packets and protocols.
- **tcpdump** captures and displays packets from the command line.

These tools can help investigate DNS requests, TCP connections, and unexpected network communication.

## Intrusion Detection Systems

An Intrusion Detection System (IDS) monitors activity for signs of suspicious behaviour. A network IDS examines traffic, while a host-based IDS monitors activity on an individual system.

Suricata is an example of a network threat detection tool. It can also be configured for intrusion prevention.

## Linux

Linux is widely used on servers and in security environments. Analysts may use it to inspect files, manage permissions, review logs, and run security tools.

## SQL

SQL is used to query relational databases. For example:

```sql
SELECT *
FROM login_attempts
WHERE status = 'FAILED';
```

This query returns rows where the login status is recorded as `FAILED`, assuming the table and column names match the database.

## Python

Python can help automate repetitive tasks and process data. This small example counts failed events in a sample list:

```python
login_events = ["SUCCESS", "FAILED", "FAILED", "SUCCESS"]
failed_count = login_events.count("FAILED")

print(f"Failed logins: {failed_count}")
```

Output:

```text
Failed logins: 2
```

## How the tools can work together

A SIEM may raise an alert based on log data. An analyst can review the related records, use a packet capture tool to inspect network traffic, and use scripts to organise large amounts of data. The analyst then records the findings and follows the incident process.

## Further reading

- [Splunk Documentation](https://docs.splunk.com/)
- [Google Security Operations](https://cloud.google.com/chronicle)
- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [Suricata Documentation](https://docs.suricata.io/)
- [Python Documentation](https://docs.python.org/3/)
