# Network-Scanning-and-Analysis

## Table of Content
1. [Introduction](#introduction)
2. [Tools Needed](#tools-needed)
3. [Overview Of Tools](#overview-of-tools)
4. [Conclusion](#conclusion)



## Introduction

Network Scanning and Analysis" is a cybersecurity project focused on gaining practical experience with network assessment techniques. 
This project documents the process of using Nmap to map network layouts, identify active hosts and services, and detect open ports. 
Furthermore, it incorporates Wireshark to analyze network traffic, providing a deeper understanding of network communication and potential security loopholes. 
The findings of this project illustrate the importance of proactive network security measures.



## Tools Needed

- Network Mapper **(Nmap)**
  [Download Here!](https://nmap.org/download.html)
- Wireshark
  [Download Here!](https://www.wireshark.org/download.html)



## Overview Of Tools

### Network Mapper (Nmap)
- **Background**
    - Nmap is a powerfull open source network scanner for host discovery, service and opeating system detection, and security auditing. It works by sending
      variouse packets to target hosts and analyzing the responses. Nmap is highly versatile and supports numerous scanning technique, including
      TCP SYN scans, UDP scans, and OS fingerprinting.

- **How it Works**
    - Nmap sends specially crafted packets to target hosts. The responses from the hosts reveal information about their open ports, running services, and operating systems.
      Different scan types use different packet types and techniques to achieve specific goals. For example, a SYN scan sends SYN packets and analyzes the SYN/ACK oe RST
      responses to determine open ports.

#### Step by Step Process**
I prefere using the command line interface **(CLI)** rather than the Graphic User Interface **(GUI)**.
- **Step 1**<br />
   On a Windows systems, typing **ipconfig** will display your IP Address.<br />
   
   ![ipconfig](1.png)

- **Step 2**<br />
Using the command **namp "IP Address here"**. Use your IP address from the ipconfig.<br />
This will show you basic stuff like an open port and its protocols.<br />

   ![nmap](image22.png)

- **Step 3**<br />
If you want to see more details, type the command **nmap - A "IP Address here"**.<br />
This scan will give you the OS, its version, script scan, and traceroute.<br />

   ![nmap](nmap-A.png)<br />
   
**Note**, we could type **nmap -h** to see the help page of how to use nmap and all the options we could use **(-sV, -sC, -A, etc)**. 



### Wireshark
- **Background**
    - To truly understand network behavior, look at the raw data. That's where Wireshark comes in. This project utilizes Wireshark, a widely used network protocol analyzer, to capture and analyze network packets.
      By examining this data, I can identify communication patterns, detect anomalies, and better understand how devices interact on the network.
      This analysis can be crucial for identifying security vulnerabilities and optimizing network performance..

- **How it Works**<br />
    - Wireshark **captures** network **packets** by putting the network interface card (NIC) into promiscuous mode, allowing it to see all traffic.
      It then decodes the packets and displays them in a user-friendly format, showing protocol headers, data payloads, and other
      relevant information. It uses **filters** to view only certain types of traffic and then **analyze** the communication between the different devices.

#### Step by Step Process**

- **Step 1**<br />
   After downloading and configuring Wireshark in your system, launch it and select the network from which you want to capture packets.<br />
   For my case, I selected the Wi-Fi network because that is how my computer was connected.

  ![nmap](Image3.png)

- **Step 2**<br />
   When you select the network you want to capture packets, look for the blue symbol button located top left<br />
   under file. Click it and let it start capturing. We can then see both the source and destination IP Addresses and also their respective protocols.<br />

   ![nmap](capturewifi.png)

- **Step 3**<br />
   Knowing that HTTP is not a secure protocol because it runs on port 80, I filter the network using the **Apply a display filter** <br />
   box to filter for **HTTP traffic** running on my network, and analyze what source and destination IP Addresses they are using.<br />

   ![nmap](HTTPtraffic.png)

- **Step 4**<br />
   Still with the **Apply a display filter** box, I filter for Domain Name System **(DNS)** queries.<br />
   This shows me the domain name being resolved to troubleshoot issues like slow responses, errors, or incorrect server usage.<br />

   ![nmap](DNSfilter.png)


## Conclusion 

This conclusion summarizes my findings on my Wi-Fi network while carrying out this project. Follow these steps to see if your system has any vulnerabilities. 

### For Nmap
   - I found open ports that pose a potential risk for unauthorized access. For example, port 135/tcp (msrpc), 139/tcp (netbios-ssn), 445/tcp (microsoft-ds)
     They are associated with Windows file and printer sharing (SMB/NetBIOS) and are notorious for being targets of malware and exploits, such as WannaCry.
   - Also, with Nmap -A for aggressive scan, I could use this option to detect what OS I was using. 

#### Likes and dislikes 
   - Nmap is a good tool because it is powerful and versatile, with a wide range of scanning options. It is excellent for host discovery and service identification.
     The downside of Nmap is that the command-line interface (CLI) can sometimes be intimidating for beginners. I am speaking from experience.
     Another downside is that IDS can also detect some scans. 

### For Wireshark
   - With the detailed filtering of DNS and HTTP, I was able to reveal websites that I have visited that are not secure, as well as the domain name resolution. 

   - The exciting part is that one can see traffic in real time and identify its source and destination IP addresses. 

#### Likes and dislikes 

   - I like the fact that Wireshark is a highly detailed packet analyzer. It is a user-friendly GUI with powerful filtering capabilities
     and open-source software, and it is well documented. The downside about it is that, when capturing large amounts of traffic, it can generate huge files
     It also requires one to have extensive knowledge of protocols. It can also be resource-intensive. 
