# Security Frameworks, the CIA Triad, and Security Controls

## 1. Security frameworks

A security framework gives an organization a structured way to manage cybersecurity. It helps teams set priorities, assign responsibilities, and check whether security practices are working.

A framework gives direction; security controls are the specific safeguards used to reduce risk.

## 2. CIA triad

| Principle | Meaning | Example |
|---|---|---|
| Confidentiality | Only authorized people can access information | Access permissions and encryption |
| Integrity | Information remains accurate and is not changed without authorization | Hash checks and change monitoring |
| Availability | Systems and information are available when needed | Backups and redundant systems |

A single security event can affect more than one part of the CIA triad. For example, ransomware can affect availability and may also affect confidentiality if data is stolen.

## 3. NIST Cybersecurity Framework 2.0

The NIST Cybersecurity Framework (CSF) helps organizations understand, assess, prioritize, and communicate cybersecurity risk. Its six functions are:

1. **Govern:** Set cybersecurity strategy, responsibilities, and oversight.
2. **Identify:** Understand assets, systems, and risks.
3. **Protect:** Put safeguards in place.
4. **Detect:** Find and analyse possible security events.
5. **Respond:** Take action when a cybersecurity incident occurs.
6. **Recover:** Restore services and improve recovery arrangements.

## 4. Types of security controls

| Type | Purpose | Example |
|---|---|---|
| Preventive | Stop or reduce the chance of an incident | MFA, firewall rules, security training |
| Detective | Identify suspicious activity | SIEM alerts, audit logs, IDS |
| Corrective | Help fix a problem or restore normal operation | Remove malware, restore a backup, apply a patch |

Controls can also be described as technical, administrative, or physical, depending on how they are implemented.

## 5. OWASP security principles

OWASP publishes practical guidance for improving application security. Some useful principles include:

- **Least privilege:** Give users and services only the permissions they need.
- **Defence in depth:** Use multiple layers of protection.
- **Secure by default:** Start with safe settings rather than open access.
- **Fail securely:** Errors should not expose sensitive information or grant access.
- **Reduce the attack surface:** Remove unnecessary features, services, and access paths.
- **Validate input:** Treat external input as untrusted and validate it appropriately.

## 6. Applying the ideas

For a company website, confidentiality can be supported by access controls and encryption. Integrity can be supported by change monitoring and secure application design. Availability can be supported by backups and resilient hosting. The NIST CSF can help organize the overall security programme, while individual controls provide the protection.

## References

- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
- [OWASP](https://owasp.org/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
