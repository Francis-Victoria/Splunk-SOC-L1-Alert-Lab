
## Alert Details
# Ticket 001 - Multiple Failed Login Attempts



**Alert Title:** Multiple failed login attempts detected  
**Severity:** Medium  
**Alert Source:** Splunk  
**Host:** DESKTOP-96A3R4F  
**User Account:** Victoria  
**Logon Type:** 2 - Interactive logon  


## Event IDs

 4625 - Failed logon

 4624 - Successful logon


## Summary

Multiple failed login attempts were detected for the Victoria account on host DESKTOP-96A3R4F. I reviewed the failed logon events in Splunk, checked the failure reason and compared them against successful logon activity to determine whether the activity looked like normal user error or a potential authentication issue. 

## Evidence

 Failed login search: `index=windows EventCode=4625`

 Successful login review: `index=windows EventCode=4624`

 Screenshot: `ticket-001-failed-logins.png`

 Screenshot: `ticket-001-successful-login-review.png`


## Investigation Steps

1\. Searched Splunk for Windows failed logon events using Event ID 4625.

2\. Identified 6 failed login events within the last 24 hours.

3\. Reviewed the affected host and account name.

4\. Confirmed the failed logins were related to host DESKTOP-96A3R4F and account Victoria.

5\. Reviewed successful login events using Event ID 4624.

6\. Confirmed successful interactive logins occurred after the failed attempts.

7\. Checked the failure reason, which showed unknown user name or bad password.


## Analysis

## Analysis

The activity appears to be a series of failed interactive login attempts on the local workstation. Since the attempts were limited and followed by a successful login, the event may have been caused by normal user error, such as entering the wrong password.

However, in a real SOC environment, failed logins followed by a successful login should still be reviewed carefully. This pattern could indicate password guessing or unauthorized access, especially if it involves a privileged account, occurs outside normal business hours, or appears across multiple systems.


## Assessment

Suspicious but not confirmed malicious.


## Action Taken

Documented the activity, reviewed related successful login events, and validated the affected host and account.


## Recommendation

Continue monitoring the account for additional failed logins. If more failed attempts occur, verify with the user and consider a password reset.


## Escalation Criteria

Escalate to Tier 2 if:

 Failed login attempts continue

 Multiple accounts are targeted

 The successful login came from an unusual source

 The account is privileged

 Login activity occurs outside normal business hours

