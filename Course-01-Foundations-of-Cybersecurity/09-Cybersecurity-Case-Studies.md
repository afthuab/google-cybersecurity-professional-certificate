# Cybersecurity Case Studies

These short case studies look at well-known incidents and the security lessons they highlight.

## 1. WannaCry ransomware (2017)

WannaCry was a ransomware outbreak that spread widely in May 2017. It affected vulnerable Windows systems by exploiting the SMBv1 vulnerability addressed by Microsoft's MS17-010 security update.

**What it shows:**

- Known vulnerabilities need to be patched promptly.
- Unsupported or unnecessary services increase risk.
- Network segmentation can limit the spread of an incident.
- Backups and incident response plans are important.

**SOC perspective:** Analysts may look for unusual SMB traffic, unexpected file changes, malware alerts, and similar activity across multiple endpoints.

Reference: [Microsoft Security Bulletin MS17-010](https://learn.microsoft.com/en-us/security-updates/securitybulletins/2017/ms17-010)

## 2. Equifax data breach (2017)

Equifax disclosed a major data breach in 2017. Attackers exploited a vulnerability in Apache Struts, and personal information relating to approximately 147 million people was affected.

**What it shows:**

- Internet-facing applications need timely patching.
- Organisations need accurate software and asset inventories.
- Vulnerability management should be followed through to remediation.
- Monitoring can help identify unusual access and data movement.

**SOC perspective:** Analysts may review web application logs, unusual database access, unexpected outbound traffic, and related alerts.

Reference: [Federal Trade Commission: Equifax Data Breach](https://www.ftc.gov/enforcement/refunds/equifax-data-breach-settlement)

## 3. Colonial Pipeline incident (2021)

Colonial Pipeline experienced a ransomware incident in May 2021. The company temporarily shut down pipeline operations while responding to the incident, disrupting fuel supply in parts of the United States.

**What it shows:**

- Remote access needs strong protection.
- Organisations need to understand dependencies between IT and operational systems.
- Incident response and recovery planning matter.
- Access controls and monitoring should be reviewed regularly.

**SOC perspective:** Analysts may investigate unusual remote logins, account activity, endpoint alerts, and signs of ransomware execution.

Reference: [CISA StopRansomware](https://www.cisa.gov/stopransomware)

## Overall lesson

These incidents had different causes, but they all show why organisations need good asset management, patching, access controls, monitoring, backups, and incident response plans.
