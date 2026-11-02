# Cybersecurity Analyst Roles and Skills

## What does a cybersecurity analyst do?

A cybersecurity analyst helps an organisation monitor its systems, investigate suspicious activity, and respond to security incidents. Entry-level analysts often work in a Security Operations Centre (SOC).

## Common SOC Analyst tasks

| Task | Example |
|---|---|
| Monitor alerts | Review alerts from a SIEM platform |
| Investigate activity | Check repeated failed login attempts |
| Review logs | Compare authentication events and timestamps |
| Triage alerts | Decide whether an alert needs further investigation |
| Escalate incidents | Pass serious or unclear cases to a senior analyst |
| Document findings | Record evidence, actions, and conclusions |

The exact work varies by organisation and SOC team.

## Skills to build

- **Networking:** Understand IP addresses, ports, DNS, TCP, and common protocols.
- **Windows and Linux:** Know how operating systems, users, permissions, and logs work.
- **SIEM:** Search and investigate events collected from different systems.
- **Log analysis:** Read events and look for unusual patterns.
- **Incident response:** Follow a process to investigate and handle incidents.
- **Scripting:** Use Python or PowerShell to automate simple tasks.
- **Communication:** Explain findings clearly and keep useful records.

## Example: unusual login activity

A user account has many failed logins followed by a successful login from an unfamiliar location.

An analyst may:

1. Check the time and source IP address of each login.
2. Compare the activity with the user's normal pattern.
3. Look for other alerts involving the same account or device.
4. Check whether the successful login was expected.
5. Record the evidence and escalate according to the team's process.

This pattern could have a legitimate explanation, so the analyst should investigate before deciding that the account is compromised.

## Key point

A Tier 1 SOC Analyst usually starts with alert monitoring, basic investigation, documentation, and escalation. Good investigation habits are just as important as knowing the tools.

## Further reading

- [NIST NICE Workforce Framework](https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center)
