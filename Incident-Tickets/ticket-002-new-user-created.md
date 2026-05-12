# Ticket 002 - New Local User Account Created

## Alert Details

**Alert Title:** New local user account created  
**Severity:** High  
**Alert Source:** Splunk  
**Host:** DESKTOP-96A3R4F  
**Created Account:** John Neves  
**Created By:** Victoria  

## Event ID

 4720 - A user account was created


## Summary

A new local user account named John Neves was created on host DESKTOP-96A3R4F by the Victoria account. New account creation can be legitimate administrative activity, but in a SOC environment, unexpected account creation should be reviewed because it may indicate unauthorized access or persistence activity.



## Evidence

\- Splunk search: `index=windows EventCode=4720`

\- Screenshot: `ticket-002-new-user-created.png`



## Investigation Steps

1\. Searched Splunk for Windows Event ID 4720.

2\. Confirmed that a new user account creation event was logged.

3\. Identified the affected host as DESKTOP-96A3R4F.

4\. Identified the created account as John Neves.

5\. Reviewed the account that initiated the action.

6\. Confirmed the activity was expected lab activity.



## Analysis

The account creation was expected because it was performed intentionally as part of the SOC lab. In a real SOC environment, new local account creation should be validated against an approved service ticket or change request. If the account was not approved, this would be treated as suspicious and escalated.


## Assessment

Authorized lab activity.


## Action Taken

Documented the account creation event, reviewed the host, created account, and initiating user, and confirmed the event was expected.


## Recommendation

Monitor for additional account activity, especially if the account is added to privileged groups or used to log in shortly after creation.


## Escalation Criteria

Escalate to Tier 2 if:

\- The account was not approved

\- The account is added to the local Administrators group

\- The account is created outside normal business hours

\- The account name appears suspicious

\- The account is used shortly after creation for login activity

