# Risk Management and the NIST Risk Management Framework

## 1. What is risk management?

Risk management is the process of identifying possible security problems, understanding how likely they are and how much damage they could cause, and deciding what to do about them.

## 2. A simple risk management process

1. **Identify assets:** Work out what needs protection, such as systems, data, and services.
2. **Identify threats and vulnerabilities:** Find what could cause harm and which weaknesses could be exploited.
3. **Assess likelihood and impact:** Estimate how likely an event is and what the consequences could be.
4. **Prioritize risks:** Deal with the most important risks first.
5. **Choose a response:** Select a suitable way to handle each risk.
6. **Monitor and review:** Check whether controls are working and reassess risks when things change.

## 3. Common ways to handle risk

| Response | Meaning | Example |
|---|---|---|
| Mitigate | Reduce the likelihood or impact | Apply patches and enable MFA |
| Avoid | Stop the activity that creates the risk | Retire an unsafe service |
| Transfer | Shift some financial impact to another party | Obtain suitable cyber insurance |
| Accept | Formally acknowledge and tolerate the risk | Accept a low risk with documented approval |

Accepting a risk should be a considered decision by the appropriate risk owner, not an accidental failure to act.

## 4. NIST Risk Management Framework (RMF)

The NIST RMF provides a structured process for managing security and privacy risk in information systems. Its seven steps are:

1. **Prepare:** Establish the context and roles for managing risk.
2. **Categorize:** Categorize the system and the information it handles.
3. **Select:** Choose suitable security and privacy controls.
4. **Implement:** Put the selected controls in place.
5. **Assess:** Check whether the controls are implemented correctly and work as intended.
6. **Authorize:** Have the responsible official make an informed decision about operating the system.
7. **Monitor:** Keep checking the system, controls, and risks over time.

## 5. Example

A company uses a web application to store customer details. The team identifies the application and its data as important assets. It finds that the application is missing security updates and that administrator accounts do not use MFA.

The team assesses the possible impact of account compromise, prioritizes the weaknesses, applies updates, enables MFA, and monitors the application for unusual activity. The risk is then reviewed to check whether the changes have reduced it.

## 6. Risk register example

| Asset | Risk | Likelihood | Impact | Suggested action |
|---|---|---|---|---|
| Customer database | Unauthorized access | Medium | High | Restrict access, enable MFA, review logs |
| Employee laptops | Malware infection | Medium | Medium | Endpoint protection and patching |
| File server | Data loss | Low | High | Test backups and restrict admin access |

The ratings above are illustrative. An organization should use its own approved risk rating method.

## 7. Key point

Risk management is ongoing. New systems, new threats, software changes, and business changes can all affect an organization's risk.

## References

- [NIST Risk Management Framework](https://csrc.nist.gov/projects/risk-management)
- [NIST SP 800-37 Rev. 2](https://csrc.nist.gov/pubs/sp/800/37/r2/final)
