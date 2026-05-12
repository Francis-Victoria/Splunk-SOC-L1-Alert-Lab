# Detection: PowerShell Activity

## Purpose

Detect PowerShell execution on endpoints.


## Splunk Search

```spl

index=sysmon powershell.exe

| table \_time host User Image CommandLine ParentImage

