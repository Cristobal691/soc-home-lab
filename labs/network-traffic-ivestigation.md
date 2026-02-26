# Multiple Nmap Scan Techniques Detection - Network Traffic Analysis 

## Summary 

Network traffic analysis revealed reconnaissance activity from 10.10.60.7 targeting 10.10.47.123. Multiple Nmap scanning tehniques were identified during the investigation.

---

## Investigation

**Tool Used:**
-Wireshark 

---

## TCP Connect Scan 

**Filter Used:** 
```
tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024
```

**Observed Behavior**

- Full TCP three-way handshake completed
- Sequential destination ports
- High frequency connections

**Assessment:**

Behavior consistent with TCP connect scan (-st)


---

### TCP SYN Scan 

**Filter Used** 
```
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

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

Confirmed multiple reconnaissance techniques from 10.10.60.7 targeting 10.10.47.123. 
Activity indicats automated port enumeration using Nmap.

Recommend monitoring or blocking the source if activity persists.





















