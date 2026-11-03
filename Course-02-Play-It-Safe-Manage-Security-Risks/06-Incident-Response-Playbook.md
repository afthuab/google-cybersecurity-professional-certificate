# Incident Response Playbook

## 1. What is an incident response playbook?

An incident response playbook is a set of documented steps that helps a team handle a particular type of security incident. It explains what to check, who to contact, what actions are allowed, and what information needs to be recorded.

A playbook supports a consistent response. It does not replace judgement or the organization's incident response policy.

## 2. Common incident response phases

A common incident response process includes:

1. **Preparation:** Maintain tools, contacts, procedures, and training before an incident occurs.
2. **Detection and analysis:** Review alerts, collect evidence, and decide whether an incident has occurred.
3. **Containment:** Limit the spread or impact of the incident using approved actions.
4. **Eradication:** Remove the cause of the incident, such as malware or unauthorized access.
5. **Recovery:** Restore systems safely and monitor them for further problems.
6. **Post-incident review:** Record lessons learned and improve controls and procedures.

Organizations may organize these activities differently. Follow the incident response process approved by the organization.

## 3. Example playbook: Suspicious account activity

**Trigger:** SIEM alert for repeated failed logins followed by a successful login from an unusual source.

### Step 1 – Triage

- Record the alert ID and time.
- Identify the affected account and system.
- Check the number and timing of login attempts.
- Review whether the source and location are expected.

### Step 2 – Investigate

- Review authentication logs before and after the alert.
- Check for MFA prompts, password changes, or account changes.
- Look for access to sensitive systems after the login.
- Compare the activity with the user's normal pattern where this data is available.

### Step 3 – Contain

- Escalate to the authorized incident responder or account owner.
- Request account disablement, session revocation, or credential reset when justified and approved.
- Preserve relevant logs and evidence.
- Avoid taking disruptive action without the required authorization.

### Step 4 – Eradicate and recover

- Confirm the account is secured.
- Remove unauthorized access or persistence if found.
- Restore affected services if necessary.
- Monitor the account for further suspicious activity.

### Step 5 – Close and review

- Record the timeline, evidence, decisions, and actions.
- Document whether the activity was confirmed malicious, benign, or inconclusive.
- Recommend improvements, such as MFA coverage or alert tuning.

## 4. Information to record

- Alert or incident reference.
- Date and time, including time zone.
- Affected account, host, and service.
- Relevant IP addresses and event IDs.
- Evidence reviewed.
- Actions taken and who approved them.
- Escalation details.
- Final status and lessons learned.

## 5. Key point

A playbook helps an analyst work methodically under pressure. The analyst should preserve evidence, follow authorization rules, communicate clearly, and document each important action.

## References

- [CISA – Incident Response](https://www.cisa.gov/)
- [NIST Computer Security Incident Handling Guide](https://csrc.nist.gov/pubs/sp/800/61/r2/final)
