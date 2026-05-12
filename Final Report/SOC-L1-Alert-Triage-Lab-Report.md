# SOC L1 Alert Triage Lab Report

## Project Overview

This project simulates a Jr SOC Analyst L1 workflow using Splunk, Windows Event Logs, Sysmon and PowerShell. The lab focuses on collecting endpoint logs, creating detection searches, investigating security alerts, documenting findings and making escalation decisions.


The goal of this project was to demonstrate hands-on SOC skills by building a SIEM lab and investigating common endpoint security events.

## Lab Environment


 Host Machine - Windows 10 virtual machine

SIEM Tool - Splunk Enterprise



## Log Sources

 Windows Security Logs

 Windows System Logs

 Windows Application Logs

 Sysmon Operational Logs


## Endpoint Monitoring Tool

Sysmon



## Main Host Investigated

DESKTOP-96A3R4F


## Tools Used

 Splunk Enterprise

 Sysmon

 Windows Event Viewer

 Windows PowerShell

 Windows Security Logs

 Markdown documentation



## Skills Demonstrated

 SIEM monitoring

 Windows log analysis

 Sysmon analysis

 SPL searching

 Endpoint investigation

 Alert triage

 Incident documentation

 Privilege escalation investigation

 PowerShell investigation

 SID resolution using PowerShell

 Escalation decision-making


## Splunk Indexes Created


windows - Used to store Windows Event Logs, including Security, System and Application logs.

sysmon - Used to store Sysmon endpoint telemetry, including process creation events.



## Screenshots Collected

The following screenshots were collected as evidence during the lab:



 `windows-logs-in-splunk.png`

 `sysmon-event-viewer.png`

 `sysmon-logs-in-splunk.png`

 `windows-sourcetype-validation.png`

 `sysmon-sourcetype-validation.png`

 `splunk-log-validation.png`

 `ticket-001-failed-logins.png`

 `ticket-001-successful-login-review.png`

 `ticket-002-new-user-created.png`

 `ticket-003-powershell-activity.png`

 `ticket-004-user-added-to-admin-group.png`

 `ticket-004-sid-resolution.png`

 `ticket-004-local-admin-group-members.png`


## Alerts Investigated


Ticket 001 - Multiple Failed Login Attempts

Investigated multiple failed login attempts using Windows Security Event ID 4625. Reviewed the affected account, host, failure reason, and successful login activity afterward using Event ID 4624.


Ticket 002 - New Local User Account Created

Investigated new local user account creation using Windows Security Event ID 4720. Reviewed the created account, host, and account that performed the action.



Ticket 003 - PowerShell Activity Detected

Investigated PowerShell process execution using Sysmon EventCode 1. Reviewed the process image, command line, parent process, user context, and host.



Ticket 004 - User Added to Local Administrators Group

Investigated a user being added to the local Administrators group using Windows Security Event ID 4732. Reviewed the modified group, initiating account, Member SID, and resolved the SID using PowerShell to identify the account added.



## Key Event IDs Used

| Event ID | Description | Use Case |

| 4624 | Successful logon | Login validation |

| 4625 | Failed logon | Failed login investigation |

| 4720 | User account created | Account creation monitoring |

| 4732 | Member added to local group | Privilege escalation monitoring |

| Sysmon EventCode 1 | Process creation | PowerShell/process investigation |



## Detection Searches Created


The following SPL searches were created to support the SOC L1 alert triage lab:



```spl

## Failed Login Attempts

index=windows EventCode=4625

| table \_time host Account\_Name Logon\_Type Failure\_Reason



## Successful Login Review

index=windows EventCode=4624

| table \_time host Account\_Name Logon\_Type



## New Local User Account Created

index=windows EventCode=4720

| table \_time host Account\_Name SubjectUserName



## User Added to Local Administrators Group

index=windows EventCode=4732 Group\_Name="Administrators"

| table \_time host Account\_Name Group\_Name



## PowerShell Activity

index=sysmon EventCode=1 Image="\*\\\\powershell.exe"

| table \_time host User Image CommandLine ParentImage

```

