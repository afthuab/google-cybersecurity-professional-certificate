# SIEM, Security Logs, and Dashboards

## 1. What is a SIEM?

Security Information and Event Management (SIEM) software collects and analyses log data from different systems. It helps security teams search events, spot unusual activity, connect related events, and investigate alerts.

Examples include Splunk, Microsoft Sentinel, and Google Security Operations.

## 2. What is a log?

A log is a record of an event that happened on a system, application, or network device. Logs can help explain what happened, when it happened, and which account or device was involved.

Common log sources include:

- Windows and Linux systems.
- Authentication services.
- Firewalls and network devices.
- Servers and applications.
- Endpoint security tools.
- Cloud services.

## 3. What does a SIEM dashboard show?

A dashboard presents security information in a form that analysts can review. It may show alert counts, event timelines, affected users, source IP addresses, event categories, and alert severity.

A dashboard helps an analyst decide where to look, but each alert still needs investigation.

## 4. Common SIEM activities

1. Search for events using a time range or specific field.
2. Filter events by user, host, source IP, or event type.
3. Compare related events from different systems.
4. Review alert details and supporting log records.
5. Record findings and escalate when required.

## 5. Example log records

The following entries are fictional examples for learning:

```text
2026-10-10 09:14:02 host=VPN01 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:14:18 host=VPN01 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:14:35 host=VPN01 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:15:01 host=VPN01 user=alex event=login_success src_ip=203.0.113.25
```

These events show repeated failed logins followed by a successful login from the same example address. This pattern deserves review, but it does not by itself prove that the account was compromised.

## 6. Why context matters

Before deciding that an alert is malicious, an analyst should check whether the activity is expected, whether the user was working remotely, whether the source address is known, and whether other events support the alert.

## 7. Key point

SIEM tools make large amounts of log data easier to search and correlate. Good analysis still depends on checking evidence, understanding normal activity, and documenting the reason for a decision.

## References

- [Splunk Documentation](https://docs.splunk.com/)
- [Microsoft Sentinel Documentation](https://learn.microsoft.com/en-us/azure/sentinel/)
- [Google Security Operations](https://cloud.google.com/security/products/security-operations)
