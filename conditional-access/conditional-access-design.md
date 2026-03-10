# TriadTech - RBAC Design Document
Project: Enterprise IAM Architecture Lab
Company: TriadTech (Simulated Company)
Environment: Microsoft Entra ID

## Overview

Conditional Access is the enforcement engine of TriadTech's zero-trust identity model. The policy stack consists of 6 policies, each targeting a specific threat vector. All policies explicitly exclude the break glass admin account to ensure emergency access is never blocked by policy.

## Named Locations
Before policies were configured, Named Locations were defined to establish what constitutes a trusted sign-in location for TriadTech.

## Policy Stack

### CA_MFA_AllUsers
Require multi-factor authentication for all users across all cloud applications.

### CA_Block_LegacyAuth
Block all legacy authentication protocols that do not support modern MFA.

### AdminCompliantDevice
Require admin role users to sign in from a compliant or Microsoft Entra hybrid joined device.

### GeoBlock
Block all sign-ins originating from outside TriadTech's three operating countries.

### PhishResistant_Admins
Require phishing-resistant MFA specifically for all admin role users, beyond standard MFA.

### BlockHighRisk
Automatically block sign-ins that Entra ID Identity Protection has flagged as high risk in real time.
