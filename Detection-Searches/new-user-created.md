\# Detection: New User Account Created



\## Purpose

Detect new local or domain account creation.



\## Splunk Search

```spl

index=windows EventCode=4720

| table \_time host Account\_Name SubjectUserName

