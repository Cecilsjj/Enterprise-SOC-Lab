# Project 06 - Mock Ticketing and Incident Response Workflow

## Objective

Create a mock SOC ticket using GitHub Issues, document an endpoint alert investigation, add resolution notes, close the ticket, and preserve evidence of the incident response workflow.

## Key Concepts

SOC stands for **Security Operations Center**.

IR stands for **Incident Response**.

Ticketing means documenting an alert, investigation, response action, and final outcome in a tracked case or issue.

Disposition means the final result of an investigation, such as benign, suspicious, or malicious.

In this project, GitHub Issues was used as a mock ticketing system to simulate a basic SOC analyst workflow.

## Alert Scenario

The alert investigated was:

```text
Suspicious Local Account Creation - alerttest
```

This alert was based on Project 05, where a temporary local Windows account named `alerttest` was created and then deleted.

## Tools Used

- GitHub Issues
- Windows Event Viewer
- Splunk Enterprise
- Windows Security Logs
- Screenshots
- SOC-style ticket notes
- Incident response documentation

## Related Event IDs

| Event ID | Meaning |
|---:|---|
| 4720 | A user account was created |
| 4726 | A user account was deleted |

## Ticket Created

A GitHub issue was created with the title:

```text
SOC Ticket - Suspicious Local Account Creation - alerttest
```

The ticket documented:

- Ticket summary
- Alert details
- Related Event IDs
- Severity
- Severity reason
- Evidence reviewed
- Timeline
- Investigation notes
- Response action
- Final disposition
- Recommendation

## Alert Details

| Field | Value |
|---|---|
| Alert Name | Suspicious Local Account Creation |
| Alert Type | Windows user account creation |
| Endpoint | DESKTOP-SU6S662 |
| Detected Account | alerttest |
| Detection Source | Splunk / Windows Security Logs |
| Severity | Medium |
| Final Disposition | Benign authorized lab activity |

## Severity

Severity assigned:

```text
Medium
```

## Severity Reason

Unexpected local account creation can be suspicious because attackers may create accounts to maintain persistence.

In this lab, the activity was authorized and controlled, so no real compromise occurred.

## Evidence Reviewed

The mock SOC ticket referenced the following evidence:

```text
eventviewer-4720-alerttest.png
splunk-4720-alerttest-search.png
splunk-4726-alerttest-deleted.png
endpoint-alert-triage-notes.txt
```

## Timeline

| Stage | Activity |
|---|---|
| Detection | Local account `alerttest` was created |
| Investigation | Event ID 4720 was confirmed in Windows Event Viewer |
| SIEM Review | EventCode 4720 was confirmed in Splunk |
| Response | Temporary account `alerttest` was deleted |
| Validation | EventCode 4726 was confirmed in Splunk |
| Resolution | Ticket was updated with resolution notes and closed |

## Resolution Comment

A resolution comment was added to the GitHub issue.

The comment documented that:

- Investigation was completed
- Account creation was confirmed in Windows Security logs and Splunk
- The activity was authorized lab activity
- The temporary account was deleted
- Deletion was confirmed with Event ID 4726 / EventCode 4726
- Final disposition was benign authorized lab activity
- No further action was required

## Ticket Closure

After adding the resolution comment, the GitHub issue was closed.

This simulated closing a SOC ticket after completing an investigation.

## Evidence Collected

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-06
```

Evidence files collected:

```text
github-soc-ticket-alerttest.png
github-soc-ticket-closed.png
```

## Findings

- A mock SOC ticket was created using GitHub Issues.
- The ticket documented a suspicious local account creation alert.
- The alert was based on Windows Event ID 4720.
- The response action was deletion of the temporary test account.
- The deletion was confirmed with Event ID 4726.
- A resolution comment was added to the ticket.
- The ticket was closed after investigation.
- Screenshots were saved as evidence.

## Security Lessons Learned

- SOC analysts use ticketing systems to document alert investigations.
- Tickets should include alert details, evidence, timeline, severity, response actions, and final disposition.
- Local account creation should be reviewed because it may indicate persistence.
- Evidence should support the analyst’s conclusion.
- Resolution comments help explain what was found and what action was taken.
- Closing a ticket should only happen after the investigation and response are complete.
- Not every alert is malicious; analysts must determine whether activity is benign, suspicious, or confirmed malicious.

## SOC Analyst Summary

I created a mock SOC ticket using GitHub Issues to document a suspicious local account creation alert. The ticket included alert details, severity, evidence reviewed, timeline, investigation notes, response action, final disposition, and recommendations. I added a resolution comment, confirmed the alert was authorized lab activity, documented that the temporary account was deleted, and closed the ticket. This project demonstrated a basic SOC ticketing and incident response workflow.
