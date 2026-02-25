# Multiple Nmap Scan Techniques Detection - Network Traffic Analysis 

## Summary 

Network traffic analysis revealed reconnaissance activity from [Source IP] targeting [Target IP]. Multiple Nmap scanning tehniques were identified during the investigation.

---

## Invetigation 

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


