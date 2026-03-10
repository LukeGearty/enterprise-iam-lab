# enterprise-iam-lab
A simulated 200-user enterprise identity architecture built in Microsoft Entra ID


## Company Profile
TriadTech is a simulated mid-sized technology consulting firm with approximately 200 employees across 7 departments, although only around 30 were created for the purpose of this project.

## What was Built

### Phase 1 - Company Setup
Created simulated users across 7 departments via bulk CSV upload in Entra ID, along with department security groups and a break-glass emergency admin account.


### Phase 2 - Role-Based Access Control
Designed and implemented 7 RBAC security groups based on the principle of least privilege.

### Phase 3 - Privileged Access Model
Configured a tiered admin model with Global Administrator, Helpdesk Administrator, and Security Reader roles. Implemented Privileged Identity Management (PIM) with just-in-time (JIT) elevation, approval workflows, and an 8-hour maximum activation window to eliminate standing privilege.

### Phase 4 - Conditional Access Policies
Built 6 Conditional Access policies covering MFA enforcement, legacy authentication blocking, admin device compliance, geo-blocking, phishing-resistant MFA for admins, and risk-based access blocking.

### Phase 5 - Identity Threat Scenarios
Simulated and documented 5 realistic attack scenarios with detection methods, remediation steps.

- Password Spray Attack
- Impossible Travel
- Dormant Account Risk
- Privilege Escalation Attempt
- Stale Contractor Access

## Tools & Technologies

- Microsoft Entra ID
- Microsoft Entra ID P2
- draw.io

## environment notes

This project was built on a Microsoft Entra ID tenant provisioned through free trials and student accounts. All objects created for this project are prefixed with TT_ to ensure clear notice of data. The Entra ID P2 trial was activated on 3-2-2026, enabling Privileged Identity Management (PIM), Identity Protection, and risk-based Conditional Access policies. The tenant is hosted in the US region and configured with default security baseline settings. My assigned role for this project is Global Administrator, which provides sufficient access to complete all planned phases. No existing companies or users were modified over the course of this project.

## Key Concepts Demonstrated

- Zero-Trust identity architecture
- Principle of least privilege
- Risk-based conditional access
- Identity threat detection and remediation