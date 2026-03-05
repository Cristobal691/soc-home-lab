# Multiple Nmap Scan Techniques Detection - Network Traffic Analysis 

## Summary 

Network traffic analysis revealed reconnaissance activity from 10.10.60.7 targeting 10.10.47.123. Multiple Nmap scanning techniques were identified during the investigation.

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
tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size <= 1024
```

**Observed Behavior** 

- SYN packets sent to multiple ports
- No handshake completion
- Rapid port enumeration

**Assessment** 

Behavior consistent with TCP SYN (half-open) scan (-sS)

---

### UDP Scan 

**Filter Scan
```
udp 
```
**Observed Behavior**

- UDP packets sent to multiple destinations
- ICMP "Port Unreachable" responses observed
- No handshake behavior (UDP is connectionless)
- Port 68 is likely open or filtered based on the lack of an ICMP error response.

**Assessment:**

---

## Conclusion 

Confirmed multiple reconnaissance techniques from 10.10.60.7 targeting 10.10.47.123. 
Activity indicats automated port enumeration using Nmap.

Recommend monitoring or blocking the source if activity persists.


# Evidence

TCP Scan

<img width="825" height="518" alt="image" src="https://github.com/user-attachments/assets/fe390478-67e1-43fb-9c76-ac379c040f2b" />


SYN Scan

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/70212ca3-2252-4857-bac0-8b4e6dbf2fc1" />

UDP Scan

<img width="600" height="838" alt="image" src="https://github.com/user-attachments/assets/d2b2fc97-3819-474a-a9c4-58199b3a5eb0" />



















