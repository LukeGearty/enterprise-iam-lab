# TriadTech - RBAC Design Document
Project: Enterprise IAM Architecture Lab
Company: TriadTech (Simulated Company)
Environment: Microsoft Entra ID

## Overview

The groups created in Phase 1 were designed to simulate a strict organizational hierarchy representing departments. The purpose of the RBAC phase is to demonstrate the principle of least privilege in a controlled setting. Department groups represent what a user is within the organization, while these RBAC groups represent what they are allowed to do.

## RBAC Groups

### Consulting_ReadOnly
"Grants read-only access to client delivery resources for consulting staff. No write or delete permissions permitted."

Assigned to: Consulting & Client Delivery
Access: Read Only

### Engineering_Dev
"Grants access to development environments and internal engineering tooling. Scoped to Engineering & Technology department."

Assigned to: Engineering & Technology
Access: Read and write within dev environments

### BD_CRM
 "Grants access to CRM platform and sales pipeline data. Scoped to Sales & Business Development department only."

Assigned to: Sales & Business Development
Access: CRM platform and sales pipeline data only

### HR_Sensitive Access
"Grants access to sensitive employee records and PII. Restricted to HR & People Operations staff. High sensitivity group."

Assigned To: HR & People Operations
Access Level: Employee records and personally identifiable information (PII)

### IT_Helpdesk
"Grants helpdesk-level permissions including password reset and basic user management. No access to security or admin configurations."
Assigned To: IT & Infrastructure

Assigned to: IT & Infrastructure
Access Level: Password resets and basic user management only

### Finance_ReadOnly
"Grants read-only access to financial reports and billing data. No edit permissions. Scoped to Finance & Operations department."

Assigned to: Finance & Operations
Access Level: Read-only access to financial reports and billing data

### Executive_Restricted
"Grants broad organizational access for executive leadership. Subject to strictest Conditional Access controls including MFA and compliant device requirement."

Assigned to: Executive Leadership
Access Level: Broad organizational access

