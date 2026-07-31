# Enterprise SOC Analyst Lab

## Overview

This project is a Windows-focused SOC analyst lab designed to build practical skills in Windows Event Viewer, endpoint log investigation, authentication analysis, Windows account activity review, local identity review, Splunk SIEM log ingestion, dashboarding, evidence collection, and incident response documentation.

SOC stands for **Security Operations Center**.

SIEM stands for **Security Information and Event Management**.

The purpose of this project is to expand beyond Linux-based security monitoring and develop hands-on experience with Windows and enterprise-style security operations workflows.

---

## Project Goals

The goals of this lab are to:

- Investigate Windows Security logs
- Understand important Windows Event IDs
- Analyze successful and failed logon events
- Review Windows account and privilege activity
- Practice local user and group security review
- Build foundational Active Directory security concepts
- Ingest Windows Security logs into Splunk
- Search Windows logs using SPL
- Create SIEM-style dashboards
- Practice evidence collection from Windows and Splunk
- Document investigations clearly for a cybersecurity portfolio

---

## Lab Environment

| Component | Description |
|---|---|
| Host Machine | Windows laptop |
| Log Source | Windows Event Viewer |
| Primary Logs | Security, System, Application |
| SIEM Platform | Splunk Enterprise |
| Evidence | Screenshots and copied event details |
| Documentation | GitHub |
| Future Additions | Endpoint alert triage, ticketing workflow, incident response documentation |

---

## Completed Projects

| Project | Title | Focus |
|---:|---|---|
| 01 | Windows Event Log Investigation | Event Viewer, Event ID 4624, Event ID 4625, logon types, evidence collection |
| 02 | Windows Account and Security Events | Logoff events, special privileges, user creation, user deletion, account lockout checks |
| 03 | Windows Local Users, Groups, and AD Security Concepts | Local users, groups, administrator membership, enabled/disabled accounts, identity review |
| 04 | Splunk SIEM Windows Log Ingestion and Dashboarding | Splunk installation, Windows Security log ingestion, SPL searches, EventCode counts, dashboard creation |

---

## Planned Projects

| Project | Title | Focus |
|---:|---|---|
| 05 | Endpoint Alert Triage | Investigating suspicious endpoint activity and documenting alert findings |
| 06 | Mock Ticketing and Incident Response Workflow | Triage, ticket notes, severity, evidence, recommendations |

---

## Skills Demonstrated

This project demonstrates skills in:

- Windows Event Viewer
- Windows Security logs
- Event ID analysis
- Authentication investigation
- Logon type interpretation
- Windows account activity review
- Local user and group review
- Administrator membership review
- PowerShell basics
- Splunk SIEM log ingestion
- SPL search queries
- Dashboard creation
- Evidence collection
- Security documentation
- SOC analyst workflow
- Incident investigation fundamentals

---

## Tools Used

| Tool | Purpose |
|---|---|
| Windows Event Viewer | Review Windows Security, System, and Application logs |
| PowerShell | Run Windows account, group, and security investigation commands |
| Splunk Enterprise | Ingest, search, analyze, and visualize Windows Security logs |
| SPL | Search Processing Language used in Splunk searches |
| Screenshots | Capture investigation evidence |
| GitHub | Document portfolio projects |

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
| 4798 | A user's local group membership was enumerated |

---

## Completed Project Summaries

### Project 01 – Windows Event Log Investigation

In Project 01, I reviewed Windows Security logs using Event Viewer and filtered for Event IDs 4624 and 4625.

I identified:

- Event ID 4624 – Successful logon
- Event ID 4625 – Failed logon
- Logon Type 2 – Interactive logon
- Logon Type 3 – Network logon
- Logon Type 5 – Service logon

I observed a successful service logon by the SYSTEM account and failed logon activity with the reason “unknown username or bad password.”

This project introduced Windows Event Viewer, Windows Security logs, authentication event analysis, logon types, screenshot evidence, and copied event details.

---

### Project 02 – Windows Account and Security Events

In Project 02, I investigated Windows account and security events using Event Viewer.

I reviewed important Windows Security Event IDs, including:

- Event ID 4634 – An account was logged off
- Event ID 4672 – Special privileges assigned to a new logon
- Event ID 4720 – A user account was created
- Event ID 4726 – A user account was deleted
- Event ID 4740 – A user account was locked out

I safely generated account creation and deletion events by creating and deleting a temporary local test user named:

```text
soclabtest
```

This project helped me understand how Windows records account activity, privilege events, account creation, account deletion, and lockout checks that SOC analysts may investigate.

---

### Project 03 – Windows Local Users, Groups, and Active Directory Security Concepts

In Project 03, I reviewed local Windows users, groups, administrator membership, and identity security concepts.

I used PowerShell commands such as:

```powershell
whoami
whoami /groups
net user
Get-LocalUser
net localgroup
net localgroup Administrators
```

I identified the current Windows user:

```text
DESKTOP-SU6S662\cecil
```

I also confirmed that the local user `cecil` was a member of the local Administrators group.

This project introduced identity review concepts that apply to Active Directory environments, including user accounts, group membership, administrator privileges, enabled and disabled accounts, and access review.

---

### Project 04 – Splunk SIEM Windows Log Ingestion and Dashboarding

In Project 04, I installed Splunk Enterprise on Windows and configured it to ingest local Windows Security logs.

I confirmed that Windows Security events were searchable in Splunk using:

```spl
index=main sourcetype="WinEventLog:Security"
```

I summarized Windows Security events by EventCode using SPL and observed events such as:

- Event ID 4672 – Special privileges assigned to a new logon
- Event ID 4624 – Successful logon
- Event ID 4798 – A user's local group membership was enumerated

I created a Splunk dashboard called:

```text
Windows Security Event Dashboard
```

The dashboard included:

- Windows Security Events by EventCode
- Recent Key Windows Security Events

This project demonstrated a full SIEM-style workflow: ingest logs, search data, summarize events, create dashboards, collect evidence, and document findings.

---

## Why This Project Matters

Many entry-level SOC analyst and security operations roles require the ability to investigate Windows endpoint activity, review authentication events, understand common Windows Event IDs, work with SIEM tools, collect evidence, and explain findings clearly.

This project builds those skills through hands-on Windows investigations using Event Viewer, PowerShell, Splunk, screenshots, copied event evidence, and GitHub documentation.

The project also connects Windows endpoint logging with SIEM-style analysis by ingesting Windows Security logs into Splunk, running SPL searches, summarizing EventCodes, and creating a dashboard for analyst review.

---

## Security Lessons Learned

- Windows Security logs are important for investigating authentication and account activity.
- Event ID 4624 helps identify successful logons.
- Event ID 4625 helps identify failed logons.
- Logon Type helps explain how an authentication event occurred.
- Event ID 4672 helps identify privileged logon activity.
- User creation and deletion events can indicate legitimate administration or suspicious account activity.
- Local administrator membership should be reviewed because it represents elevated access.
- Splunk can ingest Windows Security logs and make them searchable.
- SPL can summarize event activity and help identify patterns.
- Dashboards help turn raw logs into readable analyst views.
- Evidence should be preserved using screenshots and copied event details.
- Clear documentation is important for SOC investigations and portfolio presentation.

---

## Future Additions

Future additions will include:

- Endpoint alert triage
- Mock ticketing workflow
- Security incident prioritization
- Severity classification
- Analyst investigation notes
- Evidence-based recommendations
- Final incident response documentation
- Optional Active Directory domain lab when hardware allows
- Optional Microsoft 365 / Defender security investigation labs

---

## Interview Summary

I created a Windows-focused Enterprise SOC Analyst Lab to build practical experience with Windows Event Viewer, Windows Security logs, Event ID analysis, PowerShell identity review, Splunk SIEM log ingestion, SPL searches, dashboarding, evidence collection, and SOC-style documentation.

So far, I have investigated successful and failed logons, reviewed account and privilege events, created and deleted a temporary local test account to generate Windows Security events, reviewed local users and administrator group membership, ingested Windows Security logs into Splunk, summarized events by EventCode, and built a Windows Security Event Dashboard.

This project demonstrates practical entry-level SOC analyst skills in Windows log analysis, SIEM workflow, identity review, evidence collection, and technical documentation.
