# TriadTech - RBAC Design Document
Project: Enterprise IAM Architecture Lab
Company: TriadTech (Simulated Company)
Environment: Microsoft Entra ID

## Overview
Privileged accounts represent the highest-value targets in any enterprise environment. A compromised Global Administrator account gives an attacker complete control over the tenant. 

## Admin Tier Model

TriadTech follows a tiered admin model, where each role is granted only the permissions necessary to perform its function. No user holds more privilege than their job requires.

## Why Permanent Global Admin is Dangerous

Permanently assigning Global Administrator to a user account creates a persistent, high-value attack surface. If that account's credentials are ever compromised, an attacker immediately inherits full tenant control with no additional steps required.