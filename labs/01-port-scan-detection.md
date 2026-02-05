# Port Scan Detection (Wireshark + Sysmon) 

## Overview 

This lab simulates network reconnaissance from an internal host and shows detection through packet capture analysis. 

## Lab Setup 
- Victim: Windows 10 VM
- Attacker: Kali Linux VM
- Network: VirtualBox NAT Network
- Tools: Wireshark, Sysmon 

## Observed Activity 
Wireshark captured many TCP SYN packets coming from the Kali VM. These packets targeted different destination ports on the Windows VM quickly, one after another. 

## Evidence 
- Source IP: 10.0.2.3
- Destination IP: 10.0.2.15
- TCP Flags: SYN
- Ports Targeted: 135, 445, 3306, 995, 554, etc.
- PCAP File:  
  [`port_scan_kali_to_windows.pcapng`](../pcaps/port_scan_kali_to_windows.pcapng)

  ### How to Reproduce
1. Open the PCAP in Wireshark
2. Apply filter: `tcp.flags.syn == 1 && tcp.flags.ack == 0`
3. Observe multiple SYN packets targeting sequential ports



## Analysis 
The traffic pattern matches typical TCP SYN port scanning behavior often seen during the reconnaissance phase of an attack. 

## MITRE ATT&CK Mapping 
- TA0043 – Reconnaissance
- T1046 – Network Service Discovery

## Conclusion 
This activity was identified as a true positive reconnaissance event. The recommended response is to block the source IP and keep monitoring for more activity.

