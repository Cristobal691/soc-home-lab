# Suspicious PowerShell Execution (Sysmon) 

## Overview 
This lab simulates suspicious PowerShell execution and documents how to detect it using Sysmon process creation events. 

## Lab Setup 
- Victim: Windows 10 VM
- Monitoring Tool: Sysmon
- Log Source: Sysmon Event ID 1

## Observed Activity 
A PowerShell process was run with ExecutionPolicy Bypass and a Base64-encoded command. 

## Evidence 
## Evidence
- Process: powershell.exe
- Parent Process: explorer.exe
- Sysmon Event ID: 1
- Command-Line Flags:
  - -ExecutionPolicy Bypass
  - -EncodedCommand

## Analysis 
Encoded PowerShell execution with policy bypass is a common method attackers use to avoid detection and run harmful scripts. 

## MITRE ATT&CK Mapping 
- TA0002 – Execution
- T1059.001 – PowerShell

## Conclusion 
This activity was identified as a true positive for suspicious PowerShell execution. Recommended actions include isolating the host and reviewing other PowerShell activities.
