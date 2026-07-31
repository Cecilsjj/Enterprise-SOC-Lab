# Project 04 - Splunk SIEM Windows Log Ingestion and Dashboarding

## Objective

Install Splunk Enterprise, ingest Windows Security logs, search important Windows Event IDs, create a SIEM-style dashboard, collect evidence, and document the investigation workflow.

## Key Concepts

SIEM stands for **Security Information and Event Management**.

SOC stands for **Security Operations Center**.

Splunk is a log analysis and SIEM platform used to collect, search, visualize, and investigate machine data.

Windows Security logs contain authentication, privilege, account, and security-related events.

## Tools Used

- Splunk Enterprise
- Windows Security Logs
- Windows Event Viewer
- Splunk Search & Reporting
- Screenshots
- GitHub documentation

## Evidence Folder

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-04
```

## Step 1 - Splunk Installation

Splunk Enterprise was installed successfully on Windows.

Splunk opened locally in the browser at:

```text
http://localhost:8000
```

Evidence collected:

```text
splunk-homepage.png
```

## Step 2 - Windows Security Log Input Created

Windows Security logs were added to Splunk using the local event log collection option.

The selected log source was:

```text
Windows Security Log
```

Splunk was configured to monitor the local Windows Security event log.

Evidence collected:

```text
splunk-data-input-created.png
```

This confirms that Windows Security logs were configured as a Splunk data input.

## Step 3 - Windows Security Events Visible in Splunk

After adding the Windows Security log as a local event log input, I searched Splunk using:

```spl
index=main sourcetype="WinEventLog:Security"
```

Splunk returned many Windows Security events.

The search results showed important Splunk fields, including:

```text
host
source
sourcetype
```

Evidence collected:

```text
splunk-security-events-search.png
```

This confirmed that Windows Security logs were successfully ingested into Splunk and were searchable through the Search & Reporting app.

## Step 4 - EventCode Count Summary

I used Splunk to summarize Windows Security events by EventCode.

Search used:

```spl
index=main sourcetype="WinEventLog:Security"
| stats count by EventCode
| sort - count
```

Important EventCodes observed included:

```text
4672 = Special privileges assigned to a new logon
4624 = Successful logon
4798 = A user's local group membership was enumerated
```

Evidence collected:

```text
splunk-eventcode-counts.png
```

This showed that Splunk could summarize Windows Security events and identify common event types for investigation.

## Step 5 - Splunk Dashboard Created

I created a Splunk dashboard to visualize Windows Security events.

Dashboard created:

```text
Windows Security Event Dashboard
```

Dashboard panels created:

```text
1. Windows Security Events by EventCode
2. Recent Key Windows Security Events
```

Search used for EventCode count panel:

```spl
index=main sourcetype="WinEventLog:Security"
| stats count by EventCode
| sort - count
```

Search used for recent key security events panel:

```spl
index=main sourcetype="WinEventLog:Security" (EventCode=4624 OR EventCode=4625 OR EventCode=4672 OR EventCode=4720 OR EventCode=4726 OR EventCode=4798)
| table _time EventCode host source sourcetype Message
| sort - _time
```

Important EventCodes included:

```text
4624 = Successful logon
4625 = Failed logon
4672 = Special privileges assigned to a new logon
4720 = User account created
4726 = User account deleted
4798 = A user's local group membership was enumerated
```

Evidence collected:

```text
splunk-windows-security-dashboard.png
```

This dashboard showed that Windows Security logs were ingested into Splunk, searchable by EventCode, and visualized in a SIEM-style dashboard.

## Evidence Collected

Evidence was saved locally in:

```text
Documents\Enterprise-SOC-Lab\Evidence\Project-04
```

Evidence files collected:

```text
splunk-homepage.png
splunk-data-input-created.png
splunk-security-events-search.png
splunk-eventcode-counts.png
splunk-windows-security-dashboard.png
```

## Findings

- Splunk Enterprise was installed successfully on Windows.
- Splunk was accessed locally through `http://localhost:8000`.
- Windows Security logs were added as a local event log input.
- Splunk successfully ingested Windows Security events.
- The `host`, `source`, and `sourcetype` fields were visible in Splunk search results.
- Windows Security events were searchable using `sourcetype="WinEventLog:Security"`.
- EventCode counts were summarized using Splunk SPL.
- Important EventCodes observed included `4672`, `4624`, and `4798`.
- A dashboard was created to visualize Windows Security events.
- The dashboard included an EventCode count panel and a recent key security events panel.

## Security Lessons Learned

- Splunk can be used as a SIEM-style platform for collecting and searching Windows Security logs.
- Windows Security logs provide useful authentication, privilege, and account activity data.
- EventCode searches help analysts focus on specific security events.
- Dashboards help turn raw logs into easier-to-review visual summaries.
- Event ID 4624 shows successful logon activity.
- Event ID 4672 shows special privileges assigned to a new logon.
- Event ID 4798 shows local group membership enumeration.
- Field names like `host`, `source`, and `sourcetype` help analysts understand where events came from.
- Evidence screenshots help document the SIEM investigation workflow.

## SOC Analyst Summary

I installed Splunk Enterprise on Windows, configured Splunk to ingest local Windows Security logs, confirmed that events were searchable in the Search & Reporting app, summarized events by EventCode using SPL, and created a Splunk dashboard with panels for EventCode counts and recent key Windows Security events. This project demonstrated a full SIEM-style workflow: ingest logs, search data, identify important events, visualize results, collect evidence, and document findings.
