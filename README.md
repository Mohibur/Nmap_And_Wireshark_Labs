# Nmap_And_Wireshark_Labs


## Lab Track – Network Recon & Packet Forensics

Hands-on lab using **Nmap** for host/service discovery and **Wireshark** for packet capture & analysis.  
Focus: Correlating scan results with actual packet evidence for each finding.

## About Tools 
### Nmap  
**Nmap (Network Mapper)** is an open-source network scanning tool used for discovering hosts, identifying open ports, detecting services, and mapping networks.  
It supports multiple scanning techniques (SYN scan, TCP connect, UDP scan, etc.), OS fingerprinting, and the **Nmap Scripting Engine (NSE)** for automation, vulnerability scanning, and advanced reconnaissance.  
Widely used in penetration testing, system administration, and network troubleshooting.  

### Wireshark  
**Wireshark** is a free and open-source packet analyzer that captures and inspects network traffic in real time.  
It allows detailed analysis of protocols, packet contents, and communication patterns, making it useful for troubleshooting, security investigations, and learning network behavior.  
Wireshark supports powerful filtering (Display & Capture filters) to isolate specific traffic such as HTTP requests, TCP handshakes, DNS queries, or malicious packets.  


## >>> Ping Scan
- Performed a **ping scan** to detect live hosts on the target network without port scanning.
  
  <img width="541" height="241" alt="ss1" src="https://github.com/user-attachments/assets/8f35c735-77bd-4dd1-b446-94630bdb77d1" />
## >>> Nmap -sn  
- Used **Nmap -sn** for host discovery (ping scan) to identify live targets without scanning ports.
- Captured packets in **Wireshark** during the Nmap `-sn` host discovery. Observed **ARP requests/replies** showing how Nmap detects live hosts.
  
  <img width="704" height="274" alt="ss123" src="https://github.com/user-attachments/assets/b9477eec-9c7b-4d03-9525-9873b2a1d0da" />
  <img width="800" height="635" alt="ss12" src="https://github.com/user-attachments/assets/40349c81-4c0d-4960-9d94-0445c5af1138" />

## >>> Nmap -sS , -Pn , -p- 
- Used **Nmap -sS** (SYN scan) for half-open TCP scanning to identify open ports without completing the 3-way handshake.  
- Used **Nmap -Pn** to skip host discovery and treat all targets as online.  
- Used **Nmap -p-** to scan all 65,535 TCP ports on the target.
- In Wireshark, observed TCP SYN packets with SYN-ACK/RST replies (SYN scan), no ICMP/ARP before TCP traffic (host discovery disabled), and a continuous stream SYN packets to ports 1–65535 (full port range scan).

  <img width="691" height="219" alt="ss2" src="https://github.com/user-attachments/assets/4dadbac7-341a-402d-a6d6-bdb895ed3c0b" />
  <img width="700" height="640" alt="ss21" src="https://github.com/user-attachments/assets/e831340c-394e-4a2f-9d9b-3dc2501ad491" />
  <img width="700" height="195" alt="ss22" src="https://github.com/user-attachments/assets/a7993747-c6db-445f-b732-6f15cd7ee3e5" />

## >>> Nmap -sV, -O , --script vuln(NSE script)  
- **-sV**: Probes open ports to determine service versions and gather banner information.  
- **-O**: Analyzes responses to fingerprint the target’s operating system.  
- **--script vuln**: Runs vulnerability detection scripts against the target using Nmap’s NSE.

  <img width="900" height="892" alt="ss3" src="https://github.com/user-attachments/assets/3754b6c2-00e0-4ad7-93d9-a5903d882d20" />

## >>> Nmap -oN,-oX
- `-oN`: To save the report in text file(`.txt`).
- `-oX`: To save the report in XML file.
## >>> Some Other Popular Nmap Commads
- **-sT**: Performs a full TCP connect scan by completing the 3-way handshake.  
- **-sU**: Scans UDP ports to detect open/closed/filtered services.
- **-p <range>**: Scans a specific range of ports instead of defaults.  
- **-A**: Enables OS detection, version detection, script scanning, and traceroute in one scan.  
- **--traceroute**: Displays the network path to the target host.
## >>> Some Other NSE Scripts
The **Nmap Scripting Engine (NSE)** allows Nmap to run powerful scripts written in Lua for tasks like service detection, vulnerability scanning, and network automation.  
It provides a flexible way to extend Nmap’s capabilities beyond basic port scanning.  

- **--script vuln**: Runs vulnerability detection scripts against the target.  
- **--script safe**: Executes safe scripts that won’t affect the target’s stability.  
- **--script default**: Runs the default set of scripts for basic information gathering.  
- **--script discovery**: Performs host and service discovery tasks.  
- **--script intrusive**: Launches scripts that may disrupt target services.  
- **--script auth**: Attempts to bypass or brute-force authentication on services.  
- **--script brute**: Runs brute-force login attempts against supported services.  
- **--script malware**: Checks for malware-infected hosts or suspicious files.  
- **--script exploit**: Tries known exploits against vulnerable services.  
- **--script banner**: Retrieves and displays service banners from open ports.  


  


  















 
