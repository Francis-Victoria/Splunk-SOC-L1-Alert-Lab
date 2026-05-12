\# Ticket 001 - Multiple Failed Login Attempts

## Alert Details

**Alert Title:** Multiple failed login attempts detected  
**Severity:** Medium  
**Alert Source:** Splunk  
**Host:** DESKTOP-96A3R4F  
**User Account:** Victoria  
**Logon Type:** 2 - Interactive logon  



\## Event IDs

\ 4625 - Failed logon

\ 4624 - Successful logon



\## Summary

Multiple failed login attempts were detected for the Victoria account on host DESKTOP-96A3R4F. The failed attempts were followed by a successful interactive login, so the activity was reviewed to determine whether it was normal user error or suspicious authentication activity.



\## Evidence

\- Failed login search: `index=windows EventCode=4625`

\- Successful login review: `index=windows EventCode=4624`

\- Screenshot: `ticket-001-failed-logins.png`

\- Screenshot: `ticket-001-successful-login-review.png`



\## Investigation Steps

1\. Searched Splunk for Windows failed logon events using Event ID 4625.

2\. Identified 6 failed login events within the last 24 hours.

3\. Reviewed the affected host and account name.

4\. Confirmed the failed logins were related to host DESKTOP-96A3R4F and account Victoria.

5\. Reviewed successful login events using Event ID 4624.

6\. Confirmed successful interactive logins occurred after the failed attempts.

7\. Checked the failure reason, which showed unknown user name or bad password.



\## Analysis

The activity appears to be failed interactive login attempts against the local workstation. Since the failed attempts were limited and followed by a successful login, this could be normal user error. However, in a real SOC environment, repeated failed logins followed by a successful login should be reviewed carefully because it may indicate password guessing or unauthorized access.



\## Assessment

Suspicious but not confirmed malicious.



\## Action Taken

Documented the activity, reviewed related successful login events, and validated the affected host and account.



\## Recommendation

Continue monitoring the account for additional failed logins. If more failed attempts occur, verify with the user and consider a password reset.



\## Escalation Criteria

Escalate to Tier 2 if:

\- Failed login attempts continue

\- Multiple accounts are targeted

\- The successful login came from an unusual source

\- The account is privileged

\- Login activity occurs outside normal business hours

