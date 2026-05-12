\# Ticket 003 - PowerShell Activity Detected



## Alert Title - PowerShell activity detected on endpoint



## Severity

Medium



## Alert Source - Splunk / Sysmon



\## Host

DESKTOP-96A3R4F



\## User

DESKTOP-96A3R4F\\Victoria



\## Event ID

\- Sysmon EventCode 1 - Process Create



\## Process Image

C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe



\## Parent Process

C:\\Windows\\System32\\RuntimeBroker.exe



\## Summary

PowerShell activity was detected on host DESKTOP-96A3R4F through Sysmon process creation logs. PowerShell is a legitimate administrative tool, but it is also commonly reviewed in SOC environments because attackers may use it for discovery, script execution, downloads, and persistence.



\## Evidence

\- Splunk search: `index=sysmon EventCode=1 Image="\*\\\\powershell.exe"`

\- Screenshot: `ticket-003-powershell-activity.png`



\## Investigation Steps

1\. Searched Splunk Sysmon logs for PowerShell process creation events.

2\. Filtered for Sysmon EventCode 1 to identify process execution.

3\. Confirmed the process image was Windows PowerShell.

4\. Reviewed the affected host.

5\. Reviewed the user context.

6\. Reviewed the command line.

7\. Reviewed the parent process.

8\. Determined whether the activity matched expected lab activity.



\## Analysis

The PowerShell activity was expected because it was generated intentionally as part of the lab. The event shows PowerShell launched under the Victoria user account on DESKTOP-96A3R4F. No suspicious indicators such as encoded commands, external downloads, hidden execution, or unusual command-line activity were observed.



\## Assessment

Authorized lab activity.



\## Action Taken

Documented the PowerShell process creation event, reviewed the command line and parent process, and confirmed the activity was expected.



\## Recommendation

Continue monitoring PowerShell usage and review command-line details for suspicious behavior.



\## Escalation Criteria

Escalate to Tier 2 if:

\- PowerShell uses encoded or obfuscated commands

\- PowerShell downloads files from external URLs

\- PowerShell launches from Office applications or browsers

\- PowerShell executes under an unexpected user account

\- PowerShell activity occurs outside normal business hours

\- PowerShell attempts to create persistence or modify security controls

