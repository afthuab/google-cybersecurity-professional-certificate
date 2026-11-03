# SIEM Alert Investigation – Suspicious Login Activity

## 1. Scenario

A SIEM dashboard generates an alert after several failed login attempts are followed by a successful login for the same account.

This is a fictional investigation example. The IP address and log entries below are reserved for documentation and are not real indicators.

## 2. Sample events

```text
2026-10-10 09:14:02 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:14:18 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:14:35 user=alex event=login_failed src_ip=203.0.113.25
2026-10-10 09:15:01 user=alex event=login_success src_ip=203.0.113.25
```

## 3. Initial triage

| Check | Result from the sample |
|---|---|
| Affected account | `alex` |
| Event pattern | Three failed attempts followed by success |
| Source address | `203.0.113.25` (documentation-only address) |
| Time window | About one minute |
| Initial concern | Possible password guessing or unusual authentication |

## 4. Investigation steps

1. Check whether the user recognizes the login.
2. Confirm whether the source address is expected for the user.
3. Review authentication events from other systems.
4. Check for MFA activity and account changes.
5. Look for access to sensitive resources after the successful login.
6. Search for similar activity against other accounts.
7. Record evidence and escalate if the activity cannot be explained.

## 5. Assessment

The sequence is suspicious enough to investigate. The sample alone is not enough to confirm a compromise because it does not show the user's normal login pattern, MFA result, device details, or later activity.

**Example disposition:** Needs further investigation.

## 6. Recommended response

If additional evidence indicates unauthorized access, follow the organization's account-compromise playbook. This may include escalating the incident, securing the account, revoking sessions, resetting credentials, preserving logs, and checking for further access. These actions should be performed by authorized staff under the organization's procedures.

## 7. Investigation record

| Field | Example entry |
|---|---|
| Alert name | Repeated failed logins followed by success |
| Account | alex |
| Initial assessment | Suspicious; not confirmed |
| Evidence | Four example authentication events |
| Next action | Verify with account owner and review related logs |
| Status | Open – further investigation required |

## 8. Key learning

A SIEM alert is a starting point, not a final conclusion. Analysts should verify context, correlate evidence, choose a careful disposition, and document why they reached it.
