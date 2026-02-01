# Port Scan Detection (Wireshark + Sysmon)

## Overview
This lab simulates network reconnaissance activity from an internal host and documents detection using packet capture analysis.

## Lab Setup
- Victim: Windows 10 VM
- Attacker: Kali Linux VM
- Network: VirtualBox NAT Network
- Tools: Wireshark, Sysmon

## Observed Activity
Wireshark captured multiple TCP SYN packets originating from the Kali VM and targeting multiple destination ports on the Windows VM in rapid succession.

## Evidence
- Source IP: 10.0.2.3
- Destination IP: 10.0.2.15
- TCP Flags: SYN
- Ports Targeted: 135, 445, 3306, 995, 554, etc.

## Analysis
The observed traffic pattern is consistent with TCP SYN port scanning behavior, commonly used during reconnaissance phases of an attack.

## MITRE ATT&CK Mapping
- TA0043 – Reconnaissance
- T1046 – Network Service Discovery

## Conclusion
This activity was classified as a true positive reconnaissance event. Recommended response includes blocking the source IP and monitoring for additional activity.

