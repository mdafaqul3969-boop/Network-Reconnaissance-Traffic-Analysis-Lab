# Network-Reconnaissance-Traffic-Analysis-Lab
A beginner cybersecurity lab demonstrating network reconnaissance and traffic analysis. Features Nmap port and service enumeration on Metasploitable 2 alongside Wireshark packet capture to analyze host discovery and TCP scanning mechanics.
## 📌 Overview
This project demonstrates basic network reconnaissance and traffic analysis in an isolated virtual lab environment. Using Nmap, active services and open ports were enumerated on a target host (Metasploitable 2). Concurrently, Wireshark was used to capture and analyze the underlying network traffic (TCP handshakes, ICMP probes, and protocol headers) to understand how port scanning and service detection operate at the packet level.
## 🎯 Objectives
Set up a safe, isolated host-only virtual laboratory using VMware Workstation.Identify active hosts, open ports, service versions, and target OS details using Nmap.Inspect network packets during enumeration using Wireshark to analyze scanning techniques (e.g., SYN scans).Document potential vulnerabilities associated with outdated services running on the target.
## ⚙️️ Environment & SetupAttacker Machine:
Kali Linux (192.168.x.x)Target Machine: Metasploitable 2 (192.168.x.x)Network Mode: Host-Only (Isolated from external networks)Tools Used: Nmap, Wireshark, VMware Workstation
## 🔍 Key Findings1.
Discovered Services & Open Ports
| Port | Protocol | Service | Version | Risk Level |
| :--- | :--- | :--- | :--- | :--- |
| 21 | TCP | FTP | vsftpd 2.3.4 | High |
| 22 | TCP | SSH | OpenSSH 4.7p1 | Medium |
| 80 | TCP | HTTP | Apache httpd 2.2.8 | Medium |
| 139 / 445 | TCP | NetBIOS / SMB | Samba 3.0.20 | High |
## 📊 Traffic Analysis (Wireshark)
#### TCP SYN Stealth Scan (-sS):
Captured initial [SYN] requests sent to target ports. Open ports responded with [SYN, ACK] followed by an immediate [RST] from Nmap to teardown the half-open connection.
#### Unencrypted Communications:
Observed plain-text service communications on port 21 (FTP) and port 80 (HTTP) without TLS encryption.
## 🖼️ Screenshots

## 💡 Key TakeawaysEnumeration is Critical:
Port scanning provides immediate insight into an enterprise's attack surface.Packet Visibility: Wireshark filtering (ip.addr == <target-ip>) highlights how stealth scans interact with remote firewalls and sockets.Remediation: Outdated services like vsftpd 2.3.4 and legacy Samba versions must be updated or disabled to prevent remote code execution.
