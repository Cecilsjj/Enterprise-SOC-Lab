# Project 01 – Windows Event Log Investigation

## Objective

Investigate Windows Security logs using Event Viewer, identify successful and failed logon events, interpret important Event IDs, and collect evidence for documentation.

## Key Concepts

SOC stands for **Security Operations Center**.

Windows Event Viewer is a built-in Windows tool used to view system, application, and security logs.

Event ID 4624 means:

```text
An account was successfully logged on.
```

Event ID 4625 means:

```text
An account failed to log on.
```

Logon Type helps explain how the logon occurred.

## Tools Used

- Windows Event Viewer
- Windows Security Logs
- Event ID filters
- Screenshots
- Text evidence copied from Event Viewer

## Log Sources Reviewed

```text
Event Viewer → Windows Logs → Security
```

## Events Investigated

| Event ID | Meaning | Result |
|---:|---|---|
| 4624 | Successful logon | Found |
| 4625 | Failed logon | Found |

## Successful Logon Event

I filtered the Windows Security log for:

```text
4624
```

The event message showed:

```text
An account was successfully logged on.
```

One observed event showed:

```text
Event ID: 4624
Account Name: SYSTEM
Logon Type: 5
```

## Logon Type 5 Explanation

Logon Type 5 means:

```text
Service logon
```

This means a Windows service started or ran under an account, usually the built-in SYSTEM account.

This was not a manual keyboard login. It was local service activity.

## Failed Logon Event

I filtered the Windows Security log for:

```text
4625
```

The event message showed:

```text
An account failed to log on.
```

Observed details included:

```text
Account Name: cecil
Failure Reason: Unknown username or bad password
Logon Type: 2 - Interactive
Logon Type: 3 - Network
```

## Logon Type Explanation

| Logon Type | Meaning |
|---:|---|
| 2 | Interactive logon, usually at the keyboard or screen |
| 3 | Network logon, usually access over the network |
| 5 | Service logon, used by Windows services |

## Evidence Collected

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-01
```

Evidence files:

```text
4624-successful-logon.png
4625-failed-logon.png
successful-logon-4624-evidence.txt
failed-logon-4625-evidence.txt
```

## Findings

- Windows Security logs contained successful logon events.
- Event ID 4624 confirmed successful authentication activity.
- One successful logon was a service logon by the SYSTEM account.
- Event ID 4625 confirmed failed authentication activity.
- The failed logon reason was unknown username or bad password.
- Logon Type 2 represented an interactive logon.
- Logon Type 3 represented a network logon.
- Logon Type 5 represented a service logon.

## Security Lessons Learned

- Windows Event Viewer is important for investigating endpoint activity.
- Event ID 4624 helps identify successful logons.
- Event ID 4625 helps identify failed logons.
- Logon Type helps explain how an authentication event occurred.
- Failed logons may indicate user error, password issues, scanning, or brute-force activity.
- Successful logons should be reviewed to understand whether they are normal user, service, or network activity.
- Evidence should be saved as screenshots and copied event details.

## SOC Analyst Summary

I reviewed Windows Security logs using Event Viewer and filtered for Event IDs 4624 and 4625. I identified a successful service logon by the SYSTEM account and a failed logon event with the reason “unknown username or bad password.” I interpreted the logon types and collected screenshot and text evidence for documentation.
