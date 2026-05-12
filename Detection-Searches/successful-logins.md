\# Detection: Successful Logins



\## Purpose

Review successful Windows logins.



\## Splunk Search

```spl

index=windows EventCode=4624

| table \_time host Account\_Name Logon\_Type

