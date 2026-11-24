# Cloud Network Security

## 1. Cloud service models

Cloud computing delivers compute, storage, and networking resources over the internet on demand.

| Model | What the provider manages | What the customer manages | Example |
|---|---|---|---|
| IaaS (Infrastructure as a Service) | Physical hardware, networking, hypervisor | Guest OS, patching, firewall rules, applications, data | Virtual machines and virtual networks |
| PaaS (Platform as a Service) | Hardware, OS, runtime environment | Applications, configuration, user access, data | Managed web app hosting |
| SaaS (Software as a Service) | Full application and underlying infrastructure | User accounts, permissions, data governance | Cloud email and collaboration suites |

## 2. Shared responsibility model

In cloud environments, security responsibilities are split between the cloud service provider and the customer:

- **Provider responsibility (security *of* the cloud):** Physical data centre security, underlying physical servers, storage hardware, and physical network infrastructure.
- **Customer responsibility (security *in* the cloud):** Virtual network design, security group rules, identity and access management (IAM), OS updates on virtual machines, encryption settings, and log monitoring.

## 3. Securing cloud networks

- **Virtual Private Cloud (VPC):** Isolate cloud workloads inside private virtual networks with controlled IP ranges and route tables.
- **Security groups and Network ACLs:** Restrict inbound and outbound traffic to required ports and trusted source ranges. Avoid leaving administrative ports (`22` or `3389`) open to `0.0.0.0/0`.
- **Private subnets:** Keep databases and internal application servers in private subnets without direct public IP addresses.
- **VPC flow logs:** Enable network flow logging and forward records to a SIEM so analysts can investigate accepted and rejected connections.

## 4. Key point

Moving systems to the cloud changes how network controls are configured, not the need for segmentation, least privilege, and continuous log monitoring.

## References

- [NIST SP 800-145 – The NIST Definition of Cloud Computing](https://csrc.nist.gov/pubs/sp/800/145/final)
- [CISA – Cloud Security Technical Reference Architecture](https://www.cisa.gov/)
