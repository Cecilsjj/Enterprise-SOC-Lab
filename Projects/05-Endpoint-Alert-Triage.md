# Project 05 - Endpoint Alert Triage

## Objective

Simulate and investigate an endpoint security alert involving local Windows account creation. Confirm the activity in Windows Event Viewer and Splunk, collect evidence, assign severity, and write SOC-style triage notes.

## Key Concepts

SOC stands for **Security Operations Center**.

SIEM stands for **Security Information and Event Management**.

Endpoint means a user device such as a laptop, desktop, or server.

Triage means the first stage of an investigation where an analyst reviews an alert, checks evidence, determines severity, and recommends response actions.

Persistence means a method an attacker may use to maintain access to a system after initial compromise.

## Alert Scenario

Alert name:

```text
Suspicious Local Account Creation
```

Alert type:

```text
Windows user account creation
```

The Windows Event ID investigated was:

```text
4720 = A user account was created
```

A related cleanup event was also investigated:

```text
4726 = A user account was deleted
```

## Tools Used

- Windows PowerShell
- Windows Event Viewer
- Windows Security Logs
- Splunk Enterprise
- Splunk Search & Reporting
- Screenshots
- Triage notes
- GitHub documentation

## Test Account Created

A temporary local test account was created:

```text
alerttest
```

This account was created only for a controlled lab simulation and deleted after evidence was collected.

## Step 1 - Generate Endpoint Alert Event

PowerShell was opened as Administrator.

Command used:

```powershell
net user alerttest TestPassword123! /add
```

Command explanation:

```text
net = Windows command-line tool for managing users, groups, and network resources
user = manages Windows user accounts
alerttest = temporary account name
TestPassword123! = temporary password
/add = creates the account
```

The command completed successfully.

This generated:

```text
Event ID 4720 - A user account was created
```

## Step 2 - Confirm Event in Windows Event Viewer

I opened Windows Event Viewer and went to:

```text
Windows Logs → Security
```

I filtered the Security log for:

```text
4720
```

The event showed:

```text
A user account was created.
```

Observed account:

```text
alerttest
```

Evidence collected:

```text
eventviewer-4720-alerttest.png
```

## Step 3 - Confirm Event in Splunk

I opened Splunk Enterprise and used the Search & Reporting app.

Splunk search used:

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4720 alerttest
```

Search explanation:

```text
index=main = searches the main Splunk index
sourcetype="WinEventLog:Security" = searches Windows Security logs
EventCode=4720 = searches for user account creation events
alerttest = searches for the temporary account name
```

Splunk found the Windows Security event showing that the account `alerttest` was created.

Evidence collected:

```text
splunk-4720-alerttest-search.png
```

## Step 4 - Delete Temporary Test Account

After confirming the account creation event, I deleted the temporary account.

PowerShell command used:

```powershell
net user alerttest /delete
```

Command explanation:

```text
net = Windows command-line tool
user = manages Windows user accounts
alerttest = temporary account name
/delete = deletes the account
```

The command completed successfully.

This generated:

```text
Event ID 4726 - A user account was deleted
```

## Step 5 - Confirm Deletion Event in Splunk

Splunk search used:

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4726 alerttest
```

Splunk found the event showing that the account `alerttest` was deleted.

Evidence collected:

```text
splunk-4726-alerttest-deleted.png
```

## Triage Notes

Alert Name:

```text
Suspicious Local Account Creation
```

Alert Type:

```text
Windows user account creation
```

Endpoint:

```text
DESKTOP-SU6S662
```

Detected Account:

```text
alerttest
```

Related Event IDs:

```text
4720 - A user account was created
4726 - A user account was deleted
```

Detection Source:

```text
Splunk
Windows Security Logs
```

Triage Summary:

A local Windows user account named `alerttest` was created on the endpoint. This generated Windows Security Event ID 4720. The event was confirmed in Splunk using the Windows Security log sourcetype.

The account was created intentionally as part of a controlled SOC lab simulation. The test account was deleted after evidence was collected, generating Event ID 4726.

Severity:

```text
Medium
```

Severity Reason:

Unexpected local account creation can be suspicious because attackers may create accounts to maintain persistence. In this lab, the activity was authorized and controlled, so no real compromise occurred.

Impact:

```text
No real security impact. This was a controlled lab event.
```

Response Action:

```text
The temporary test account alerttest was deleted.
```

Final Disposition:

```text
Benign authorized lab activity.
```

Recommendation:

In a real environment, unexpected local account creation should be investigated by checking the account creator, endpoint name, timestamp, related logon activity, group membership changes, and whether the account was used after creation.

## Evidence Collected

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-05
```

Evidence files collected:

```text
eventviewer-4720-alerttest.png
splunk-4720-alerttest-search.png
splunk-4726-alerttest-deleted.png
endpoint-alert-triage-notes.txt
```

## Findings

- A temporary local Windows account named `alerttest` was created.
- Event Viewer confirmed Event ID 4720 for account creation.
- Splunk confirmed EventCode 4720 for account creation.
- The temporary account was deleted after evidence collection.
- Splunk confirmed EventCode 4726 for account deletion.
- Triage notes were created to document the alert, severity, impact, response action, and final disposition.
- The alert was classified as Medium severity in a real-world context but benign in this controlled lab.

## Security Lessons Learned

- Local account creation can be an important endpoint security alert.
- Event ID 4720 helps identify when a Windows user account is created.
- Event ID 4726 helps identify when a Windows user account is deleted.
- Unexpected account creation may indicate persistence or unauthorized access.
- Splunk can be used to search and confirm Windows Security events.
- Triage notes should include alert name, affected endpoint, evidence, severity, impact, response, and final disposition.
- Not every alert is malicious; analysts must determine whether activity is authorized, suspicious, or confirmed malicious.
- Cleanup actions should be documented after investigation.

## SOC Analyst Summary

I simulated an endpoint alert by creating a temporary local Windows account named `alerttest`. I confirmed the account creation event in Windows Event Viewer and Splunk using Event ID 4720. I then deleted the temporary account and confirmed the deletion event in Splunk using Event ID 4726. I collected screenshot evidence and wrote SOC-style triage notes documenting the alert, severity, impact, response action, final disposition, and recommendations.
