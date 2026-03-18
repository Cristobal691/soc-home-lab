# Wireshark Investigation: FTP Brute Force and File Upload
--- 
### Overview 

This investigation analyzes network traffic captured in a packet capture (PCAP) file using Wireshark. The objective was to identify suspicous activity
involving FTP authentication attempts and file transfers.

The analysis revealed a brute-force login attack against an FTP account, followed by a successful login and file upload. 
 ---

### Environment 

## Environment

| Tool | Purpose |
|-----|--------|
| Wireshark | Network traffic analysis |
| TryHackMe Lab | Packet capture source |


### Investigation Process

The packet capture was analyzed using Wireshark filters to identify FTP activity.

Example filters used:

```
ftp
```
```
ftp.request.command
```
These filters helped isolate FTP authentication attempts and commands executed by the attacker.

## Findings

| Indicator | Value |
|-----------|-------|
| Failed Login Attempts | 737 |
| File Uploaded | resume.doc |
| File Size | 39,424 bytes |
| Permission Change Command | CHMOD 777 |




