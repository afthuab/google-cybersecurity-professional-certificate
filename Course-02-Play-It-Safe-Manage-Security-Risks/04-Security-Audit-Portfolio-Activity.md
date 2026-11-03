# Portfolio Activity: Basic Security Audit

## 1. Purpose

A security audit reviews an organization's systems, policies, and security practices to see whether important safeguards are in place. It can identify gaps and recommend improvements.

This document is an original example based on a fictional small business. It is not an audit of a real organization and does not claim access to actual company systems.

## 2. Audit scenario

**Organization:** Northstar Office Supplies (fictional)  
**Scope:** Employee accounts, company laptops, file storage, backups, and basic security procedures.  
**Objective:** Identify basic security gaps that could affect business data and daily operations.

## 3. Audit checklist and example results

| Area | Audit question | Example result | Priority |
|---|---|---|---|
| User access | Are user accounts unique and assigned appropriate access? | Access review records were not available | Medium |
| MFA | Is MFA enabled for email and remote access? | MFA was not confirmed for all accounts | High |
| Patching | Are operating systems and applications updated? | No regular patch review record was available | High |
| Endpoint protection | Are company devices protected and monitored? | Protection was reported, but coverage records were incomplete | Medium |
| Backups | Are important files backed up and restore tests performed? | Backups were reported, but no recent restore test was documented | High |
| Logging | Are important account and system events recorded and reviewed? | Logs existed, but review responsibilities were unclear | Medium |
| Security awareness | Do employees receive phishing and security training? | No recent training record was available | Medium |
| Incident response | Is there a documented way to report and handle incidents? | No written response procedure was available | High |

## 4. Main findings

### Finding 1: MFA coverage is not confirmed

**Risk:** Stolen passwords could be used to access company accounts.  
**Recommendation:** Require MFA for email, remote access, and privileged accounts. Review enrollment regularly.

### Finding 2: Patch management is not documented

**Risk:** Known software weaknesses may remain unaddressed.  
**Recommendation:** Maintain an asset and software inventory, define a patch schedule, and record outstanding updates.

### Finding 3: Backup restoration has not been tested

**Risk:** Backups may not work when needed, increasing recovery time after data loss or ransomware.  
**Recommendation:** Schedule restore tests, record the results, and protect backup copies from unauthorized changes.

### Finding 4: Incident response responsibilities are unclear

**Risk:** Staff may not know who to contact or what to do during a security incident.  
**Recommendation:** Create a simple incident reporting and escalation procedure and make it available to employees.

## 5. Suggested action plan

| Priority | Action | Suggested owner |
|---|---|---|
| High | Confirm and enforce MFA coverage | IT administrator |
| High | Create a patch management process | IT administrator |
| High | Test backup restoration | IT and business owner |
| High | Document incident reporting steps | IT/security lead |
| Medium | Review user access | System owners |
| Medium | Confirm endpoint protection coverage | IT administrator |
| Medium | Set a log review schedule | IT/security lead |
| Medium | Arrange security awareness training | Management / HR |

## 6. Conclusion

The example audit identified gaps in account protection, patch management, backup testing, and incident response preparation. Addressing the high-priority findings would improve the organization's basic security position.

An actual audit would require authorized access, evidence collection, interviews, and validation of each finding. The example results here are fictional and should not be presented as real audit evidence.

## References

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [CISA Cybersecurity Resources](https://www.cisa.gov/cybersecurity)
- [OWASP](https://owasp.org/)
