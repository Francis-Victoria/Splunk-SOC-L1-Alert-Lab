# Detection: Failed Logins



## Purpose

Detect failed Windows login attempts.



## Splunk Search

```spl

index=windows EventCode=4625

| table \_time host Account\_Name Logon\_Type Failure\_Reason

