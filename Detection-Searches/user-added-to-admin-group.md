# Detection: User Added to Local Administrators Group

## SOC Case Name

Unauthorized Privilege Escalation - User Added to Local Administrators Group

## Objective

Detect when a user account is added to the local Administrators group on a Windows endpoint. This activity may indicate unauthorized privilege escalation, persistence, or improper administrative access.


## Why This Matters

Adding a user to the local Administrators group gives that account elevated permissions on the endpoint. With local administrator rights, a user may be able to install software, modify system settings, disable security controls, access sensitive files, create additional accounts, or perform other high-risk actions.



In a SOC environment, this activity should be reviewed immediately unless it is tied to an approved IT request or change ticket.



## Log Source

Windows Security Logs



## Relevant Event ID

 4732 - A member was added to a security-enabled local group



## Splunk Detection Search

```spl

index=windows EventCode=4732

| table \_time host Account\_Name Group\_Name

