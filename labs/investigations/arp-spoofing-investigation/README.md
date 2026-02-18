# ARP Spoofing Detection Investigation

## Alert Summary
Unusual ARP traffic observed indicating potential ARP poisoning / man-in-the-middle activity.

## Data Source
- Wireshark PCAP
- Network segment: Internal LAN

## Investigation Steps
1. Filtered ARP traffic to identify request/reply patterns
2. Identified multiple IP addresses mapping to the same MAC address
3. Observed unsolicited ARP replies
4. Correlated traffic suggesting ARP cache poisoning

## Evidence
- Attacker IP: 192.168.1.25
- Victim IP: 192.168.1.12
- Gateway IP: 192.168.1.1
- Same MAC address claiming multiple IPs

## Analysis
The observed behavior is consistent with ARP spoofing where the attacker impersonates the default gateway and victim to intercept traffic.

## MITRE ATT&CK
- T1557.002 – Adversary-in-the-Middle: ARP Cache Poisoning

## Conclusion
Confirmed ARP spoofing activity. Traffic interception was possible.

## Recommendations
- Enable Dynamic ARP Inspection
- Use static ARP entries for critical systems
- Monitor for duplicate IP/MAC mappings

