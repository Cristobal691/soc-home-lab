# Wireshark Investigation: FTP Brute Force and File Upload
--- 
## Overview 

This investigation analyzes network traffic captured in a packet capture (PCAP) file using Wireshark. The objective was to identify suspicous activity
involving FTP authentication attempts and file transfers.

The analysis revealed a brute-force login attack against an FTP account, followed by a successful login and file upload. 

 ---

## Environment 

| Tool | Purpose |
|-----|--------|
| Wireshark | Network traffic analysis |
| TryHackMe Lab | Packet capture source |

---

## Investigation Process

The packet capture was analyzed using Wireshark filters to identify FTP activity.

Example filters used:

```
ftp
```
```
ftp.request.command
```
These filters helped isolate FTP authentication attempts and commands executed by the attacker.

---

## Findings


| Indicator | Value |
|-----------|-------|
| Failed Login Attempts | 737 |
| File Uploaded | resume.doc |
| File Size | 39,424 bytes |
| Permission Change Command | CHMOD 777 |


---

## Attack Timeline

1. Multiple failed FTP login attempts observed.
2. Attack successfully authenticated to the FTP account.
3. A file named **resume.doc** was uploaded.
4. The attacker attempted to modify file permissions usiing.

```
CHMOD 777
```
This command gives full read, write, and execute persmissions to all users.

---

## Evidence 

**FTP Brute Force Attempts**

Screenshot showing muiltiple failed authentication responses.

![Screenshot_20260318_124219_Edge](https://github.com/user-attachments/assets/cadb2fae-a9ea-4a23-9005-c6f7361927d6)


---

**File Upload**

Evidence showing file upload command:

```
STOR resume.doc
```
![Screenshot_20260318_124928_Edge](https://github.com/user-attachments/assets/8ba5d469-0b62-4f75-babf-4a080f36eba0)



**Permission Modification**

Evidence showing command:

```
CHMOD 777
```

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/57ef4396-a059-4892-8b47-b3bfe1bb9060" />


---

## Security Assessment 

This activity indicates a successful brute-force attack followed by file upload and permission modification.
Attackers may use this technique to upload malicious scripts or establish persistence.

FTP transmits cridentials and commands in cleartext, making it insecure for production environments.

---

## Mitigation Recommendations 

- Replace FTP with SFTP or FTPS
- Enforce strong password policies
- Implement account lockout after multiple failed attempts
- Monitor authntication logs
- Deploy IDS rules to detect brute-force activity

---

## Conclusion

Analysis of the network traffic identified a brute-force attack against an FTP server, resulting in unauthorized file upload and 
attempted permission modification. This highlights the risks of using cleartext protocols such as FTP.


