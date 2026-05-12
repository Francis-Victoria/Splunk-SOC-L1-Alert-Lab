\# SOC L1 Alert Triage Lab



\## Overview

This project demonstrates a Jr SOC Analyst L1 workflow using Splunk, Windows Event Logs, Sysmon and PowerShell. The lab focuses on collecting endpoint logs, creating detection searches, investigating security alerts, documenting findings and making escalation decisions.



The purpose of this lab is to simulate common SOC L1 responsibilities, including SIEM monitoring, log analysis, alert triage, evidence collection and incident documentation.



\## Lab Environment

\- Windows 10 virtual machine

\- Splunk Enterprise

\- Sysmon

\- Windows Event Viewer

\- Windows PowerShell



\## Log Sources

\- Windows Security Logs

\- Windows System Logs

\- Windows Application Logs

\- Sysmon Operational Logs



\## Splunk Indexes

\- `windows`

\- `sysmon`



\## Skills Demonstrated

\- SIEM monitoring

\- Windows log analysis

\- Sysmon analysis

\- SPL searching

\- Endpoint investigation

\- Alert triage

\- Incident documentation

\- Privilege escalation investigation

\- PowerShell investigation

\- SID resolution using PowerShell

\- Escalation decision-making



\## Alerts Investigated



\### Ticket 001 - Multiple Failed Login Attempts

Investigated multiple failed login attempts using Windows Security Event ID 4625 and reviewed successful login activity using Event ID 4624.



\### Ticket 002 - New Local User Account Created

Investigated new local user account creation using Windows Security Event ID 4720.



\### Ticket 003 - PowerShell Activity Detected

Investigated PowerShell process execution using Sysmon EventCode 1.



\### Ticket 004 - User Added to Local Administrators Group

Investigated a local administrator group membership change using Windows Security Event ID 4732. The Member SID was resolved using PowerShell to identify the account added to the Administrators group.



\## Key Event IDs



| Event ID | Description | Use Case |

|---|---|---|

| 4624 | Successful logon | Login validation |

| 4625 | Failed logon | Failed login investigation |

| 4720 | User account created | Account creation monitoring |

| 4732 | Member added to local group | Privilege escalation monitoring |

| Sysmon EventCode 1 | Process creation | PowerShell/process investigation |



\## Main Detection Searches



```spl

\# Failed Login Attempts

index=windows EventCode=4625

| table \_time host Account\_Name Logon\_Type Failure\_Reason



\# Successful Login Review

index=windows EventCode=4624

| table \_time host Account\_Name Logon\_Type



\# New Local User Account Created

index=windows EventCode=4720

| table \_time host Account\_Name SubjectUserName



\# User Added to Local Administrators Group

index=windows EventCode=4732 Group\_Name="Administrators"

| table \_time host Account\_Name Group\_Name



\# PowerShell Activity

index=sysmon EventCode=1 Image="\*\\\\powershell.exe"

| table \_time host User Image CommandLine ParentImage

