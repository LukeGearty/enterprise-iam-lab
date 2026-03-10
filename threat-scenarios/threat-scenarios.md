# TriadTech - RBAC Design Document
Project: Enterprise IAM Architecture Lab
Company: TriadTech (Simulated Company)
Environment: Microsoft Entra ID

## Overview
The goal of this phase was to simulate realistic identity-based attack scenarios against the TriadTech environment, document how each was detected using Entra ID tooling, and define remediation steps as would be followed in a real enterprise incident response process.

## Scenarios

### Password Spray Attack
An attacker attempts a single commonly used password against multiple user accounts in sequence, deliberately staying below account lockout thresholds to avoid detection. This technique is effective because it exploits weak or reused passwords without triggering per-account lockout policies.

Multiple failed authentication attempts were manually generated against the following TriadTech accounts using an incorrect password.

Detection: Entra ID Sign-in logs

Remediation
- As a response to these, I would take these steps:
- Identify all accounts targeted 
- Confirm none of the attempts succeeded by filtering logins for successes from the same IP. Since this all came from my own IP, that would be impossible to show here.
- Reset passwords on targeted accounts as a precaution.
- Block source IP if pattern persists

Lessons Learned: Enable MFA enforcement. Even if an attacker successfully guesses a password, they cannot complete authentication without the second factor


### Impossible Travel
A user's account shows two successful sign-ins within a time window that would be physically impossible given the geographic distance between the two locations.

A TriadTech user account was signed into from a normal location in New York. A VPN was then activated to change the apparent sign-in location to Amsterdam, Netherlands, and the same account was signed in again immediately.

Detection: Entra ID Sign-in logs

Remediation:
- Identify the two sign-in locations - in this case one is from New York and one is from Amsterdam. 
- Immediately revoke all active sessions for the affected account and force a password reset.
Require re-registration of MFA
Investigate any potential data exfiltration

Lessons Learned: 
Impossible travel detection requires fast response. Automating the response via a risk-based Conditional Access policy reduces this window significantly.


### Dormant Account
User accounts that have had no sign-in activity for an extended period represent an unmonitored attack surface.

Three accounts were identified as dormant.

Detection: Entra ID Users List and Sign-in Logs

Remediation:
- Export full user list with sign-in activity data
Identify any account with no sign-in in the last 30+ days
- Cross-reference with HR to confirm employment status. If they are employed, notify their manager to investigate why their account is unused.
- If they are not employed, disable the account and schedule it for deletion

Lessons Learned: 
Defined offboarding workflow and regular access reviews are important to prevent this kind of attack surface. Depending on the organization, this attack surface can grow. 


### Privilege Escalation
A standard user account is granted a high-privilege administrative role, either maliciously by an insider or attacker who has compromised an admin account, or accidentally through misconfiguration.

A random user, TT_Liam_Okafor, was chosen and granted admin rights to simulate this threat. 

Detection: Entra ID Audit Logs and Privileged Identity Management, Email

Remediation: 
- Remove TT_Liam_Okafor from the Global Administrators assignments
- Investigate who made the assignment and any potential compromises
- Check the potential actions taken during the elevated access
- Reset credentials
- Configure PIM to ensure that elevated privilege assignment requires approval


Lessons Learned:
A direct active role assignment triggered an email notification. Monitoring emails and the audit log, and perhaps alerting on any kind of elevated access, could help with this threat.


### Stale Contractor Access
An external contractor was brought in for a short-term engagement, granted guest access, and assigned to internal security groups. After the engagement ended the contractor's account was still active.


Detection: Entra ID Users List filtered by Guest accounts

Remediation:
- Remove contractor from all internal groups
- Disable guest account
- Review audit logs to determine what resources the contractor accessed
- Implement offboarding procedure
- Implement regular access reviews

Lessons Learned:
A process failure can have just as much security impact as a technical failure. Offboarding procedures and regular access reviews could remediate this risk.

