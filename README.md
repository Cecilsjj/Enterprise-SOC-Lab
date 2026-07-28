# Enterprise SOC Analyst Lab

## Overview

This project is a Windows-focused SOC analyst lab designed to build practical skills in Windows Event Viewer, endpoint log investigation, authentication analysis, Active Directory basics, SIEM dashboards, alert triage, ticketing workflow, evidence collection, and incident response documentation.

SOC stands for **Security Operations Center**.

The purpose of this project is to expand beyond Linux-based security monitoring and develop hands-on experience with Windows and enterprise-style security operations workflows.

---

## Project Goals

The goals of this lab are to:

- Investigate Windows Security logs
- Understand important Windows Event IDs
- Analyze successful and failed logon events
- Practice evidence collection from Windows Event Viewer
- Build Active Directory and enterprise identity knowledge
- Gain SIEM dashboard and alert triage experience
- Practice mock ticketing and incident response workflows
- Document investigations clearly for a cybersecurity portfolio

---

## Lab Environment

| Component | Description |
|---|---|
| Host Machine | Windows laptop |
| Log Source | Windows Event Viewer |
| Primary Logs | Security, System, Application |
| Evidence | Screenshots and copied event details |
| Documentation | GitHub |
| Future Additions | Active Directory, SIEM, endpoint alerts, ticketing workflow |

---

## Completed Projects

| Project | Title | Focus |
|---:|---|---|
| 01 | Windows Event Log Investigation | Event Viewer, Event ID 4624, Event ID 4625, logon types, evidence collection |

---

## Planned Projects

| Project | Title | Focus |
|---:|---|---|
| 02 | Windows Account and Security Events | User activity, account changes, lockouts, privilege events |
| 03 | Active Directory Security Basics | Users, groups, organizational units, permissions |
| 04 | SIEM Log Forwarding and Dashboarding | Centralized log review and alert visibility |
| 05 | Endpoint Alert Triage | Investigating suspicious endpoint activity |
| 06 | Mock Ticketing and Incident Response Workflow | Triage, ticket notes, severity, evidence, recommendations |

---

## Skills Demonstrated

This project demonstrates skills in:

- Windows Event Viewer
- Windows Security logs
- Event ID analysis
- Authentication investigation
- Logon type interpretation
- Evidence collection
- Security documentation
- SOC analyst workflow
- Incident investigation fundamentals

---

## Key Windows Event IDs

| Event ID | Meaning |
|---:|---|
| 4624 | An account was successfully logged on |
| 4625 | An account failed to log on |
| 4634 | An account was logged off |
| 4672 | Special privileges assigned to a new logon |
| 4720 | A user account was created |
| 4726 | A user account was deleted |
| 4740 | A user account was locked out |

---

## Project 01 Summary

In Project 01, I reviewed Windows Security logs using Event Viewer and filtered for Event IDs 4624 and 4625.

I identified:

- Successful logon activity
- Failed logon activity
- Logon Type 5 service logons
- Logon Type 2 interactive logons
- Logon Type 3 network logons
- Failed logon reason: unknown username or bad password

I collected evidence using screenshots and copied Event Viewer details as text.

---

## Why This Project Matters

Many entry-level SOC analyst roles require the ability to review Windows endpoint logs, identify authentication activity, understand common Event IDs, collect evidence, and explain findings clearly.

This project builds those skills through hands-on Windows investigations and documentation.

---

## Next Steps

Future additions will include:

- More Windows Security Event ID investigations
- Active Directory basics
- User and group security review
- SIEM dashboard practice
- Endpoint alert triage
- Mock ticketing workflow
- Incident response documentation
