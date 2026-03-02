
# SOC Investigation Report
 
 Case: APR Spoofing Detection

 Tool: Wireshark

## Summary 

Analyzed network activity in Wireshark to identify abnormal APR activity. The invstigation focused on identifying potential APR spoofing or Man-in-the-Middle behaviour within the network.

---

## Investigation

Tool Used: Wireshark

Protocols Analyzed: APR (Address Resolution Protocol) 

Filters Applied:
```
arp.opcode== 1 and eth.src == 00:0c:29:c2:18:b4
```
```
http and eth.dst== 00:0c:29:e2:18:b4
```
```
http and frame contains "pass"
```

---

## Observed Behavior

- Multiple ARP request were conducted from the same MAC address.
- The same MAC adress claimed ownership of multiple IP adresses.
- Wireshark generated duplicate IP address detection warnings.
- A high numeber of ARP replies were observed in a short time frame.

---
## Assessment 

The bahaviour indicates a likely ARP spoofing attempt. A malicious host appears to be sending forged ARP replies to associate its MAC address with multiple IP addresses on the network.

## Conclusion 
