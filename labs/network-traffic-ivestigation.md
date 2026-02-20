# Network Traffic Investigation Report

Platform: TryHackMe

Environment: VM + Provided PCAP 

Tool Used: Wireshark

Focus Areas: Reconnaissance, MITM, Credential Exposure, Tunneling Detection


# Executive Summary 

Analysis of the provided packet capture identified multiple stages of attacker behavior, including:

- TCP and UDP reconnaissance scanning

- ARP poisoning consistent with man-in-the-middle activity

- Clear-text credential exposure over FTP and HTTP

- Suspicious DNS behavior

- Normal encrypted HTTPS traffic

No evidence of exploitation or lateral movement was observed; however, the activity reflects early attack lifecycle stages, particularly reconnaissance and credential harvesting.


# Reconnaissance Activity

## Overview

High-volume TCP and UDP scanning activity was detected targeting sequential ports on a single host.

## Detection Methodology

Filter used to identify initial TCP scan activity:

**Wireshark**
tcp.flags.syn == 1 and tcp.flags.ack == 0

**Wireshark**
tcp.port == 80


## Observations

- 1000 TCP Connect scan attempts identified

- Full three-way handshakes completed

- Sequential port targeting observed

UDP scan detection:

**Wireshark**
icmp.type == 3 and icmp.code == 3

- 1083 ICMP “Port Unreachable” responses detected

- UDP port 68 identified as open (no ICMP response)

## Security Impact

The traffic is consistent with automated reconnaissance activity. Port scanning is typically the first stage of an attack lifecycle and indicates active probing of services.

**Risk Level: Medium**












