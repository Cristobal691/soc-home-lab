# Incident Summary 

Multiple Nmap scans were conducted.

# Alert Details 

Multiple handshake processes were conducted.

# Investigation Steps
FIlters used:
tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024
tcp.port == 80
icmp.type==3 and icmp==3
udp.port in {55..70}

# Evidence



# Findings

# Conclusion 

# Recommendations 










