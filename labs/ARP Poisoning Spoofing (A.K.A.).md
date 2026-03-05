
# SOC Investigation Report
 
 Case: APR Spoofing Detection

 Tool: Wireshark

## Summary 

Analyzed network activity in Wireshark to identify abnormal APR activity. The investigation focused on identifying potential APR spoofing or Man-in-the-Middle behaviour within the network.

---

## Investigation

Tool Used: Wireshark

Protocols Analyzed: APR (Address Resolution Protocol) 

Filters Applied:
```
arp.opcode== 1 and eth.src == 00:0c:29:e2:18:b4
```
```
http and eth.dst== 00:0c:29:e2:18:b4
```
```
http and frame contains "pass"
```

---

## Observed Behavior

- Multiple ARP requests were conducted from the same MAC address.
- The same MAC address claimed ownership of multiple IP addresses.
- Wireshark generated duplicate IP address detection warnings.
- A high number of ARP replies were observed in a short time frame.

---
## Assessment 

The behaviour indicates a likely ARP spoofing attempt. A malicious host appears to be sending forged ARP replies to associate its MAC address with multiple IP addresses on the network. The attacker attempts to impersonate legitimate devices on the network. This technique is commonly used in Man-in-the-Middle attacks to intercept or manipulate network traffic. 

## Conclusion 

Based on the abnormal ARP activity and duplicate IP detections, the traffic is consistent with an ARP poisoning attack. The attacker attempts to impersonate legitimate devices on the network to intercept communications.

## Evidence

Evidence 1 – Duplicate IP Address Detection  
Wireshark flagged a duplicate IP address warning indicating multiple MAC addresses claiming the same IP.

Evidence 2 – ARP Reply Packet  
Packet shows a device responding with an ARP reply claiming ownership of an IP address.

Evidence 3 – MAC Address Claiming Multiple IPs  
Traffic shows the same MAC address associated with multiple IP addresses, which is abnormal behavior.

Evidence 4 – High Volume of ARP Replies  
Multiple ARP replies observed in a short timeframe suggesting ARP spoofing activity.


