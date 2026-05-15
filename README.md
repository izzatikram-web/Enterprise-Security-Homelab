# Enterprise Security Homelab

This project is a virtualized cybersecurity homelab built using VirtualBox, pfSense, Ubuntu Server, Kali Linux, and Wireshark. The goal was to create a small enterprise-style network where I could practice firewall configuration, network segmentation, attacker simulation, and traffic analysis.

## Lab Overview

The lab includes:

- pfSense firewall/router
- Ubuntu Server as an internal machine
- Kali Linux as an attacker/testing machine
- Segmented virtual networks
- DHCP configured through pfSense
- Firewall rules to control traffic between networks
- Nmap scanning from Kali
- Wireshark packet capture and traffic analysis

## Network Design

```text
Internet
   |
pfSense Firewall
   |
------------------------------------------------
|                                              |
LAN Network                                    Attack Network
10.10.10.0/24                                  10.30.30.0/24
|                                              |
Ubuntu Server                                  Kali Linux
10.10.10.100                                   10.30.30.x
```

##Tools Used
VirtualBox
pfSense
Ubuntu Server
Kali Linux
Nmap
Wireshark
OpenSSH
##What I Configured

pfSense Firewall

I installed and configured pfSense as the main firewall and router for the lab. I configured interfaces for the LAN and attack networks and used pfSense to provide DHCP addressing.

Ubuntu Server

Ubuntu Server was used as the internal system in the LAN network. I enabled SSH so that the server could be discovered during scanning and used for testing firewall rules.

Kali Linux

Kali Linux was used as the attacker/testing machine. I used Kali to scan the Ubuntu server with Nmap and verify what services were exposed.

Firewall Rules

I created firewall rules on pfSense to control traffic from the attack network. After confirming that Kali could scan the Ubuntu server, I added a block rule to prevent the attack network from reaching the Ubuntu server.

Wireshark Traffic Analysis

I used Wireshark to capture and inspect traffic between Kali and Ubuntu. This helped me verify ICMP traffic, scan traffic, and how firewall rules changed communication between the networks.

Testing Performed
1. Connectivity Testing

I tested connectivity between the VMs using ping.

2. Nmap Scan

From Kali, I scanned the Ubuntu server:

nmap -sV 10.10.10.100

The scan identified SSH running on port 22.

3. Firewall Blocking Test

After confirming the scan worked, I created a pfSense firewall rule to block traffic from the attack network to the Ubuntu server. I then tested again using ping and Nmap to confirm the traffic was blocked.
4. Packet Capture

I used Wireshark to capture ICMP and TCP traffic during testing.

##Screenshots
Ubuntu Server IP Address
<img width="840" height="94" alt="image" src="https://github.com/user-attachments/assets/ab73eca2-2cb3-45e8-ae96-b7fd0e778691" />

Kali Linux IP Address
<img width="577" height="227" alt="image" src="https://github.com/user-attachments/assets/1fc99190-c3fb-477b-98ac-da845dc0a73f" />

Successful Nmap Scan
<img width="626" height="507" alt="image" src="https://github.com/user-attachments/assets/464be08d-5e11-483a-be13-b13331abe7be" />

pfSense Firewall Block Rule
<img width="1331" height="447" alt="image" src="https://github.com/user-attachments/assets/1409dea5-4ca1-42ce-be06-5ae1c636dd89" />

Blocked Ping or Scan
<img width="689" height="119" alt="image" src="https://github.com/user-attachments/assets/9405e6d5-245f-4be0-abf0-43c8a0c8fcd2" />

Wireshark Capture
<img width="745" height="509" alt="image" src="https://github.com/user-attachments/assets/e2027ade-271d-4fc0-8f22-99336debd28e" />
<img width="766" height="563" alt="Screenshot 2026-05-15 000549" src="https://github.com/user-attachments/assets/44d592c1-f7e4-44dc-9f88-66efa10f726a" />




##Skills Practiced
Virtualization
Network segmentation
Firewall configuration
DHCP configuration
Linux server administration
Kali Linux testing
Nmap scanning
SSH service discovery
Wireshark packet analysis
Basic threat simulation
Security control validation

##Challenges

One challenge was getting traffic between segmented networks to work properly. pfSense blocks optional interfaces by default, so I had to create the correct firewall rules to allow or block traffic depending on the test.

I also attempted to add OpenVPN as an extension, but I decided to keep it as a future improvement because the main lab goals were already completed.

##Future Improvements
Add OpenVPN remote access
Add Suricata or Snort IDS/IPS
Add Windows Server and Active Directory
Forward logs to Wazuh or Splunk
Create dashboards for security monitoring
Add more attack and detection scenarios

##Project Summary
This homelab gave me hands-on practice with firewall routing, network segmentation, attacker simulation, and packet analysis. It helped me understand how traffic moves between networks and how firewall rules can be used to control access in a security environment.

This homelab gave me hands-on practice with firewall routing, network segmentation, attacker simulation, and packet analysis. It helped me understand how traffic moves between networks and how firewall rules can be used to control access in a security environment.
