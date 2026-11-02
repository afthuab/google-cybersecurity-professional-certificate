# Phishing Email Analysis

**Exercise type:** Simulated example for learning  
**Objective:** Identify common signs of a phishing email and describe how it should be handled.

## Example email

**From:** `it-support@example-attacker.invalid`  
**Subject:** Urgent: Verify your work account

> Your account will be suspended today unless you complete a security check. Open the link below and sign in to keep your access.
>
> `hxxps://company-login.example/verify`

This is a fictional email. The `.invalid` and `.example` domains are reserved for examples and are not real company login services.

## What looks suspicious?

| Indicator | Why it matters |
|---|---|
| Unfamiliar sender domain | The sender may not belong to the real IT team. |
| Urgent wording | Pressure can make people act without checking. |
| Threat of account suspension | This is a common tactic used to prompt quick action. |
| Login link in an unexpected email | The destination should be verified before anyone uses it. |

## Possible impact

If a user enters their password on a fake site, an attacker may try to use the stolen credentials to access company services. This could lead to unauthorised access or further compromise.

## What should the user do?

1. Do not open the link or enter credentials.
2. Report the email using the organisation's approved process.
3. Check with IT through a known contact method if the message might be genuine.
4. Keep the email available for investigation.

## What could a SOC analyst check?

- Sender details and email headers
- The actual link destination, using safe analysis methods
- Whether other employees received the same message
- Whether anyone clicked the link or submitted credentials
- Related sign-in activity and security alerts

If an account may be compromised, the analyst should follow the organisation's incident response process and escalate as required.

## Conclusion

A single warning sign does not prove an email is malicious. Checking the sender, message, link, and surrounding activity helps an analyst make a better decision.

## Further reading

- [CISA: Recognise and Report Phishing](https://www.cisa.gov/secure-our-world/recognize-and-report-phishing)
