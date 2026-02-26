 Multiple Nmap Scan Techniques Detection - Network Traffic Analysis 

## Summary 

Network traffic analysis revealed reconnaissance activity from [Source IP] targeting [Target IP]. Multiple Nmap scanning tehniques were identified during the investigation.

---

## Investigation

**Tool Used:**
-Wireshark 

---

## TCP Connect Scan 

**Filter Used:** 
'''
[tcp filter here]
'''

**Observed Behavior**

- Full TCP three-way handshake completed
- Sequential destination ports
- High frequency connections

**Assessment:**

Behavior consistent with TCP connect scan (-st)


---

### TCP SYN Scan 

**Filter Used** 

'''
tcp.flags.syn == 1 && tcp.flags.ack == 0
'''

**Observed Behavior** 

- SYN packets sent to multiple ports
- No handshake completion
- Rapid port enumeration

**Assessment** 

Behavior consisitent with TCP SYN (half-open) scan (-sS)

---

### UDP Scan 

**Filter Scan
```
udp
```
**Observed Behavior**

- UDP packets sent to multiple destinations
- ICMP "Port Unreachable" responses observed
- No handshake behavior (UDP is connectionless

**Assessment:**

---

## Conclusion 

Confirmed multiple reconnaissance techniques from [source IP] targeting [Target IP]. 
Activity indicats automated port enumeration using Nmap.

Recommend monitoring or blocking the source if activity persists.





















