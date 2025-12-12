Nmap Lab Reproduction

1. Host Discovery

Command
nmap -sn 10.6.6.0/24

Purpose
To identify which hosts are up without scanning ports.
Used for initial network reconnaissance.

2. Basic Port Scan

Command
nmap 10.6.6.250

Purpose
Performs a default SYN scan on top 1,000 ports.

3. Full Port Scan

Command
nmap -p- 10.6.6.250

Purpose
Scans all 65,535 ports to find hidden services.

4. Service & Version Detection

Command
nmap -sV 10.6.6.250

Purpose

Identifies software running on each open port.

5. OS Fingerprinting

Command
nmap -O 10.6.6.250

Purpose
Attempts to guess the operating system based on TCP/IP fingerprint.

6. Aggressive Scan

Command
nmap -A 10.6.6.250

Purpose
Combines: 
OS detection, Version detection, Script scanning,Traceroute

7. Nmap Scripting Engine (NSE)
command
nmap --script vuln 10.6.6.250

Purpose
Runs vulnerability-related NSE scripts to identify weak configurations.



B. Scapy Lab Reproduction

1. Packet Crafting (ICMP Ping)

Command
packet = IP(dst="10.6.6.250")/ICMP()
send(packet)

Purpose
Crafts a manual ICMP packet (ping) at a low level.

2. Sending Custom TCP Packets

Command
packet = IP(dst="10.6.6.250")/TCP(dport=80, flags="S")
send(packet)

Purpose
Sends a SYN packet to port 80 to test response behavior.

3. Sniffing Packets

Command
sniff(count=10)

Purpose
Captures 10 packets from the network.

4. Filtering Packets

Command
sniff(filter="tcp and port 80", count=5)

Purpose
Captures only HTTP-related packets.

5. Packet Analysis

Command
pkt = sniff(count=1)[0]
pkt.show()

Purpose
Prints the structure of any captured packet.
