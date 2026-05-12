# Ticket 004 - User Added to Local Administrators Group

## Alert Title
User added to local Administrators group

## Severity
High

## Alert Source
Splunk / Windows Security Logs

## Host
DESKTOP-96A3R4F

## User Added
John Neves

## Group Modified
Administrators

## Modified By
Victoria

## Event ID
- 4732 - A member was added to a security-enabled local group

## Member SID
S-1-5-21-999226604-995734374-1361329636-1002

## SID Resolved To
DESKTOP-96A3R4F\John Neves

## Summary
A user account named John Neves was added to the local Administrators group on host DESKTOP-96A3R4F by the Victoria account. Local administrator group changes are high-risk events because they may indicate privilege escalation if the action was not approved.

## Evidence
- Splunk search: `index=windows EventCode=4732`
- Screenshot: `ticket-004-user-added-to-admin-group.png`
- Screenshot: `ticket-004-sid-resolution.png`
- Screenshot: `ticket-004-local-admin-group-members.png`
- Event time: `2026-05-11 20:16:07`
- Group modified: `Administrators`
- Action performed by: `Victoria`
- Member Security ID resolved in PowerShell to `DESKTOP-96A3R4F\John Neves`
- `Get-LocalGroupMember Administrators` confirmed the account was present in the local Administrators group.

## Investigation Steps
1. Searched Splunk for Windows Event ID 4732.
2. Reviewed security-enabled local group membership changes.
3. Identified the affected host as DESKTOP-96A3R4F.
4. Identified the modified group as Administrators.
5. Reviewed the account that performed the action.
6. Opened the raw Event ID 4732 log to review the group membership change details.
7. Observed that the member account name was displayed as `-` in the event log.
8. Copied the Member Security ID from the event.
9. Resolved the Member Security ID using PowerShell.
10. Confirmed the SID resolved to `DESKTOP-96A3R4F\John Neves`.
11. Ran `Get-LocalGroupMember Administrators` to confirm the account was currently listed in the local Administrators group.
12. Confirmed the activity was expected lab activity.
13. Assessed the event as high-risk due to local administrator privilege assignment.

## PowerShell Commands Used
```powershell
$objSID = New-Object System.Security.Principal.SecurityIdentifier("S-1-5-21-999226604-995734374-1361329636-1002")
$objSID.Translate([System.Security.Principal.NTAccount]).Value
Get-LocalGroupMember Administrators