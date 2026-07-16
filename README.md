# Identity Detection Engineering

### Building Enterprise Detections for Identity-Based Threats

---

<p align="center">

# Haris Trust

### *Guarding Digital Trust.*

**Enterprise Identity Security Portfolio**

</p>

---

## Repository Information

| Category | Details |
|----------|---------|
| Level | Beginner → Advanced |
| Reading Time | 45–60 Minutes |
| Hands-on Lab | Yes |
| Enterprise Focus | Yes |
| Interview Preparation | Yes |

---

## Introduction

Attackers rarely begin by deploying ransomware or stealing sensitive data. Almost every attack starts with an identity.

Someone logs in.

Someone requests privileged access.

Someone resets a password.

Someone authenticates from an unusual location.

Identity Detection Engineering is the practice of monitoring these activities, identifying suspicious behavior, and creating detection rules that alert defenders before attackers achieve their objectives.

Instead of waiting for malware, defenders monitor identities.

This repository teaches how enterprise security teams detect identity attacks using authentication logs, Active Directory events, Azure AD (Microsoft Entra ID), Identity Providers (IdPs), SIEM platforms, UEBA solutions, and security analytics.

Whether your goal is becoming an IAM Engineer, SOC Analyst, Detection Engineer, Threat Hunter, or Blue Team professional, identity detection engineering is becoming one of the most valuable cybersecurity skills.

---

# Learning Objectives

After completing this repository you should understand:

- What Identity Detection Engineering is
- Why identities are the primary attack surface
- Authentication logging fundamentals
- Windows Security Event IDs
- Active Directory detection concepts
- Microsoft Entra ID detections
- Identity Provider telemetry
- SIEM correlation
- UEBA basics
- Threat detection lifecycle
- Alert tuning
- Detection engineering workflow
- Enterprise best practices

---

# Why This Matters

Traditional security focused on malware.

Modern security focuses on identities.

Microsoft, CrowdStrike, Google, Okta, and Mandiant all report that attackers increasingly target credentials instead of exploiting software vulnerabilities.

If attackers steal legitimate credentials, they appear to be normal users.

Detection Engineering helps defenders discover:

- Password spraying
- Credential stuffing
- Privilege escalation
- Suspicious MFA activity
- Impossible travel
- Service account abuse
- Lateral movement
- Persistence
- Insider threats

The faster these behaviors are detected, the smaller the impact.

---

# What is Identity Detection Engineering?

Identity Detection Engineering is the process of designing, building, testing, and improving security detections that identify suspicious identity-related activities.

Instead of searching for malware files, detection engineers monitor:

- Login attempts
- Failed authentications
- Password resets
- Privilege changes
- MFA events
- Group membership modifications
- Administrative actions
- Account creation
- Account deletion
- Service account usage

The goal is simple:

Detect attacker behavior as early as possible.

---

# Identity Attack Lifecycle

A typical identity attack follows this pattern:

Reconnaissance

↓

Credential Theft

↓

Initial Authentication

↓

Persistence

↓

Privilege Escalation

↓

Lateral Movement

↓

Data Access

↓

Exfiltration

Every stage generates identity logs.

Detection engineers transform those logs into alerts.

---

# Core Concepts

## Authentication

Verifying a user's identity.

Examples:

- Username & Password
- Smart Card
- MFA
- Biometrics
- Certificates

---

## Authorization

Determining what an authenticated user can access.

---

## Identity Signals

Identity signals include:

- Login success
- Login failure
- Password change
- Password reset
- MFA challenge
- Group membership change
- Role assignment
- New device registration
- New application consent

Every signal provides evidence.

---

## Detection Rule

A detection rule identifies suspicious activity.

Example:

IF

More than 20 failed logins

FROM

Same IP

WITHIN

5 minutes

THEN

Generate Alert

---

## Correlation

One event is rarely enough.

Detection engineering combines multiple events into one meaningful alert.

Example:

Failed Logins

+

Successful Login

+

Privilege Escalation

+

New Device

=

High Confidence Alert

---

# Enterprise Identity Log Sources

Detection engineers collect logs from many systems.

| Source | Information |
|----------|------------|
| Active Directory | Authentication, Group Changes |
| Microsoft Entra ID | Cloud Authentication |
| Okta | SSO Events |
| Ping Identity | Federation Events |
| Duo Security | MFA Events |
| CyberArk | Privileged Sessions |
| SailPoint | Identity Lifecycle |
| ServiceNow | Access Requests |
| Defender XDR | Endpoint Identity Signals |
| CrowdStrike | User Activity |
| VPN | Remote Access |
| Firewall | Source IP |

---

# High Value Identity Events

Examples include:

- New administrator created
- Domain Admin added
- Password reset
- Password changed
- Disabled account enabled
- Locked account unlocked
- MFA disabled
- Conditional Access modified
- Service account created
- New trust relationship
- Kerberos anomalies
- NTLM authentication
- Failed logins
- Impossible travel
- Privileged role activation

These events deserve immediate attention.

---

# Windows Event IDs Every Engineer Should Know

| Event ID | Description |
|-----------|------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4634 | Logoff |
| 4648 | Explicit Credential Logon |
| 4672 | Special Privileges Assigned |
| 4688 | Process Creation |
| 4720 | User Created |
| 4722 | User Enabled |
| 4725 | User Disabled |
| 4726 | User Deleted |
| 4728 | Added to Security Group |
| 4732 | Added to Local Group |
| 4740 | Account Locked |
| 4768 | Kerberos TGT Request |
| 4769 | Kerberos Service Ticket |
| 4771 | Kerberos Failure |
| 4776 | NTLM Authentication |

Interview Tip:

Memorizing these Event IDs gives you a significant advantage during SOC and IAM interviews.

---

# Common Identity Detection Use Cases

## Password Spraying

Indicators:

- Many usernames
- Same password
- Same IP
- High failure rate

Detection:

Multiple failed logins across many users.

---

## Impossible Travel

Indicators:

User logs in from:

India

↓

Five minutes later

Germany

Detection:

Impossible geographic movement.

---

## Privilege Escalation

Indicators:

User suddenly becomes:

- Domain Admin
- Global Administrator
- Enterprise Admin

Immediate investigation required.

---

## Dormant Account Usage

Inactive accounts suddenly authenticate.

Possible compromise.

---

## Disabled Account Authentication

A disabled account attempting authentication may indicate malicious activity.

---

## Service Account Abuse

Indicators:

- Interactive login
- Weekend activity
- Midnight authentication
- Internet login

Service accounts should behave predictably.

---

## Excessive MFA Failures

Repeated MFA failures could indicate MFA fatigue attacks.

---

# Detection Engineering Workflow

Collect Logs

↓

Normalize Data

↓

Create Detection Rule

↓

Test Detection

↓

Reduce False Positives

↓

Deploy

↓

Monitor

↓

Improve

↓

Repeat

Detection engineering is a continuous process.

---

# Enterprise Perspective

Large organizations receive millions of identity events daily.

Not every event is malicious.

Detection Engineers balance:

- Sensitivity
- Accuracy
- Performance
- Alert fatigue
- Investigation effort

The best detections are both accurate and actionable.

---

# Detection & Defense

Defenders should:

- Enable auditing
- Collect identity logs centrally
- Protect domain controllers
- Secure identity providers
- Monitor privileged accounts
- Review service accounts
- Enable MFA everywhere
- Use Conditional Access
- Implement Least Privilege
- Perform regular access reviews
- Tune detections continuously

---

# Hands-on Lab

## Scenario 1

Create five failed login attempts.

Observe:

- Windows Event 4625

Question:

Should an alert trigger?

---

## Scenario 2

Reset a user password.

Observe:

Directory audit logs.

Question:

Who performed the reset?

---

## Scenario 3

Add a user to Administrators.

Observe:

Group membership events.

Question:

How quickly can your SIEM detect this?

---

## Scenario 4

Create a disabled account.

Attempt login.

Observe generated logs.

---

# Interview Questions

1. What is Identity Detection Engineering?

2. Why are identity logs important?

3. Explain Password Spraying.

4. What is Impossible Travel?

5. Difference between authentication and authorization?

6. Which Windows Event IDs do you monitor first?

7. How would you detect privilege escalation?

8. What causes false positives?

9. How do SIEM and UEBA work together?

10. Why are service accounts high-value targets?

---

# From the Field

Most real-world identity attacks are discovered because defenders noticed unusual authentication patterns—not malware.

A successful detection often combines multiple weak signals into one high-confidence alert.

Experienced detection engineers spend as much time improving existing detections as creating new ones. Reducing false positives while maintaining visibility is one of the most valuable skills in enterprise security.

Identity logs are often the first and last evidence available during an investigation. Organizations that invest in high-quality identity telemetry and well-designed detections respond faster, investigate more efficiently, and reduce the impact of breaches.

---

# Key Takeaways

- Identity is the modern security perimeter.
- Every authentication creates valuable telemetry.
- Detection Engineering transforms logs into actionable alerts.
- Correlation is more powerful than single-event monitoring.
- Enterprise security depends on continuous detection improvement.
- Identity Detection Engineering combines IAM, SOC, SIEM, UEBA, and Threat Hunting into one discipline.

---

# References

- Microsoft Learn
- MITRE ATT&CK
- NIST Cybersecurity Framework (CSF)
- OWASP Authentication Cheat Sheet
- Microsoft Security Event Documentation
- Sigma Detection Rules
- Elastic Detection Engineering
- Splunk Security Essentials

---

# Next Repository

Identity-Federation-Lab

---

# Haris Trust

### *Guarding Digital Trust.*

**Enterprise Identity Security Portfolio**
