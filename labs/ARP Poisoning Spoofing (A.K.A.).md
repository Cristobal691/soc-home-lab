# ARP Poisoning/Spoofing (A.K.A.)

## Summary 



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



---
## Conclusion 
