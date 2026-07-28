# Project 03 – Windows Local Users, Groups, and Active Directory Security Concepts

## Objective

Investigate local Windows users, groups, administrator membership, enabled and disabled accounts, and security-relevant group configuration using PowerShell and Windows local account commands.

## Key Concepts

SOC stands for **Security Operations Center**.

Active Directory is Microsoft’s enterprise identity system used to manage users, computers, groups, permissions, and authentication in domain environments.

SAM stands for **Security Account Manager**. It stores local Windows user and group account information.

RDP stands for **Remote Desktop Protocol**. It allows remote graphical access to a Windows system.

Although this project was performed on a local Windows system instead of a full Active Directory domain controller, the same identity review concepts apply: users, groups, administrator membership, disabled accounts, and access control.

## Tools Used

- Windows PowerShell
- Local Windows user and group commands
- Screenshots
- Text evidence copied from PowerShell
- GitHub documentation

## Commands Practiced

```powershell
whoami
whoami /groups
net user
Get-LocalUser
net localgroup
net localgroup Administrators
net localgroup "Remote Desktop Users"
net localgroup "Event Log Readers"
```

## Local User Review

I used:

```powershell
Get-LocalUser
```

This command displayed local Windows accounts and whether each account was enabled or disabled.

The system showed 5 local accounts.

The output included account status values such as:

```text
Enabled: True
Enabled: False
```

This is useful because disabled built-in accounts may be expected, while unexpected enabled accounts may require investigation.

## Current User and Group Membership

I used:

```powershell
whoami
```

Observed current user:

```text
DESKTOP-SU6S662\cecil
```

I also used:

```powershell
whoami /groups
```

This displayed the groups assigned to the current user session.

Group membership is important because it helps determine what access and privileges a user has.

## Local Groups Review

I used:

```powershell
net localgroup
```

This displayed local Windows groups on the system.

Security-relevant groups observed included:

```text
Administrators
Device Owners
Distributed COM Users
Guests
Hyper-V Administrators
IIS_IUSRS
OpenSSH Users
Performance Log Users
Performance Monitor Users
Remote Management Users
System Managed Accounts Group
Users
```

## Administrators Group Review

I used:

```powershell
net localgroup Administrators
```

Observed members:

```text
Administrator
cecil
```

This confirmed that the local user `cecil` is a member of the local Administrators group.

## Why Administrator Membership Matters

The local Administrators group has complete and unrestricted access to the computer.

From a SOC analyst perspective, administrator membership is important because:

- Admin accounts can install software
- Admin accounts can change system settings
- Admin accounts can create or delete users
- Admin accounts can disable security controls
- Unexpected admin membership may indicate privilege escalation or unauthorized access

## Remote Desktop Users Group Check

I checked for the Remote Desktop Users group using:

```powershell
net localgroup "Remote Desktop Users"
```

Result:

```text
The specified local group does not exist.
```

This means the exact local group was not present on this Windows system.

## Event Log Readers Group Check

I checked for the Event Log Readers group using:

```powershell
net localgroup "Event Log Readers"
```

Result:

```text
The specified local group does not exist.
```

This means the exact local group was not present on this Windows system.

## Evidence Collected

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-03
```

Evidence files:

```text
whoami-groups.png
whoami-groups-evidence.txt
local-users.png
local-users-evidence.txt
local-groups.png
local-groups-evidence.txt
administrators-group.png
administrators-group-evidence.txt
missing-security-groups.png
missing-security-groups-evidence.txt
```

## Findings

- The current Windows user was `DESKTOP-SU6S662\cecil`.
- `Get-LocalUser` worked and displayed 5 local accounts.
- Enabled and disabled account status was visible.
- Local Windows groups were reviewed using `net localgroup`.
- The local Administrators group contained `Administrator` and `cecil`.
- The user `cecil` had local administrator rights.
- The Remote Desktop Users group was not found on this system.
- The Event Log Readers group was not found on this system.
- Evidence was collected through screenshots and copied PowerShell output.

## Security Lessons Learned

- Local user accounts should be reviewed for unexpected enabled accounts.
- Disabled built-in accounts may be normal, but enabled accounts should be verified.
- Local group membership determines user permissions and access level.
- Administrator membership is high risk and should be reviewed regularly.
- Unexpected administrators may indicate privilege escalation or unauthorized access.
- Group membership review is a core identity security task.
- Local Windows account review helps build foundational Active Directory security knowledge.
- Evidence should be saved when performing identity and access reviews.

## SOC Analyst Summary

I reviewed local Windows identity and access settings using PowerShell. I identified the current user, reviewed local accounts, checked enabled and disabled account status, listed local groups, and confirmed that the user `cecil` was a member of the local Administrators group. I also checked for Remote Desktop Users and Event Log Readers groups, which were not present on this system. This project helped build foundational Windows identity review skills that apply to Active Directory and enterprise security investigations.
