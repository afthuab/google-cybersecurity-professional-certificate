# CIA Triad, Frameworks, and Security Controls

## The CIA triad

The CIA triad is a basic model used in information security.

| Principle | Meaning | Example control |
|---|---|---|
| Confidentiality | Only authorised people can see the information. | Access controls and encryption |
| Integrity | Information stays accurate and is not changed without permission. | Hashes and audit logs |
| Availability | Systems and information are accessible when needed. | Backups and redundant systems |

## Security frameworks

A security framework gives an organisation a structured way to manage cybersecurity.

### NIST Cybersecurity Framework 2.0

The framework has six functions:

1. **Govern** – Set direction, responsibilities, and oversight.
2. **Identify** – Understand assets and risks.
3. **Protect** – Put safeguards in place.
4. **Detect** – Find possible security events.
5. **Respond** – Take action when an incident occurs.
6. **Recover** – Restore services and improve after an incident.

## Security controls

Controls are safeguards used to reduce risk.

- **Preventive:** Try to stop an incident, such as MFA or a firewall rule.
- **Detective:** Help find an incident, such as SIEM alerts or audit logs.
- **Corrective:** Help fix a problem, such as removing malware or restoring a backup.

A control can serve more than one purpose depending on how it is used.

## Secure design principles

- **Least privilege:** Give users only the access they need.
- **Defence in depth:** Use several layers of protection.
- **Separation of duties:** Split sensitive tasks between people where appropriate.
- **Secure defaults:** Start with settings that reduce unnecessary exposure.

## Example

A company protects employee accounts with MFA (preventive), monitors sign-in logs for unusual activity (detective), and has a process to disable a compromised account and restore access (corrective).

## Key point

The CIA triad describes what security aims to protect. Frameworks help organise the work, while controls are the safeguards used in practice.

## Further reading

- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
- [NIST Risk Management Framework](https://csrc.nist.gov/projects/risk-management)
