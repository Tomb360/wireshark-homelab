# <p align="center">Wireshark Homelab Project</p>

<h2 align="center">Description</h2>
Analysed sample pcaps to create a series of 6 practical Wireshark labs covering:

- Packet capture
- Network reconnaissance detection
- Malware traffic analysis
- Credential harvesting
- Lateral movement 
- ARP scanning

---
## <p align="center"> Sample Captures Used</p>
- <b>Nmap scan, telnet-cooked and arp-storm from Wireshark wiki</b>
  - [Wireshark Wiki](https://wiki.wireshark.org/SampleCaptures)
- <b>Malware Sample from Malware traffic analysis</b>
  - [Malware Traffic](https://malware-traffic-analysis.net/2026/02/28/index.html)
- <b>Lateral Movement Sample from Github</b>
  - [Lateral Movement](https://github.com/sbousseaden/PCAP-ATTACK/blob/master/Lateral%20Movement/LM_smbexec_smb_dcerpc_svcctl_epm.pcapng)


## <p align="center">Lab 1 - Wireshark Setup and Creating a Capture</p>

### <p align="center">Installed Wireshark</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3af78999-eb7d-43ea-a4d3-87aeec27689d" alt="Wireshark installed" width="800"/>
</p>

<p align="center">Wireshark installed and launched ready for packet capture.</p>

### <p align="center">Selected Main Adapter and Generated Traffic</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ebb4e24e-220a-4c2c-9d08-0e99153271f7" alt="Adapter selected and traffic generated" width="800"/>
</p>

<p align="center">Selected the main Ethernet adapter and visited 3 websites to generate traffic for a live capture.</p>

### <p align="center">Saving the Capture</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5ccacddc-724c-4992-815c-675961c84442" alt="Saving capture" width="800"/>
</p>

<p align="center">Capture saved for further analysis.</p>

### <p align="center">3 Websites Resolved Using DNS Filter</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d6ddcf23-b082-4f21-bec5-a9c6a2d6d938" alt="DNS filter" width="800"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/0ef2f298-ee05-478a-9480-81ce96ad87cb" width="800"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/070c5dba-af87-421c-bac4-9445e98b6e4c" width="800"/>
</p>

<p align="center">Applied a DNS filter to identify the three websites resolved during the capture.</p>

### <p align="center">Protocol Hierarchy</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3f516705-0757-4d54-b886-ff5176e1182b" alt="Protocol hierarchy" width="800"/>
</p>

<p align="center">Used Statistics > Protocol Hierarchy to view the percentage breakdown of traffic by protocol.</p>

### <p align="center">Conversations - Identifying the Most Active IP</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6cb43cf4-7337-4b6c-bbd3-c87d5edc1d4f" alt="Conversations" width="800"/>
</p>

<p align="center">Statistics > Conversations used to identify which IP address generated the most traffic.</p>

### <p align="center">Following UDP Stream to Reveal URL</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a0fc3727-03a4-4f6e-a99c-8fc292f719d3" alt="UDP stream" width="800"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/c012b7b1-e314-4423-91e0-a54fc679c0a5" alt="Nmap scan traffic" width="800"/>
</p>

<p align="center">Followed a UDP stream to reveal the URL embedded in the traffic.</p>

---

## <p align="center">Lab 2 - Network Reconnaissance</p>

### <p align="center">Downloaded Nmap Sample Capture</p>



<p align="center">Downloaded an Nmap scan sample from the Wireshark Wiki sample captures page.</p>

### <p align="center">Standard Nmap Scan - Multiple Connection Attempts</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/93c5e08a-bf1e-4d9a-b300-97c2bd798c8b" alt="Nmap scan traffic" width="800"/>
</p>

<p align="center">Standard Nmap scan visible with many connection attempts originating from 192.168.100.103. Filtered for SYN packets to visualise the attacker probing each port in sequence.</p>

### <p align="center">No SYN-ACK Responses - No Open Ports</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/44ef5330-e6a2-4236-930c-1b6c0d40fcc2" alt="No SYN-ACK results" width="800"/>
</p>

<p align="center">Filter tcp.flags.syn == 1 && tcp.flags.ack == 1 returned no results, confirming no open ports were found by the scanner.</p>

### <p align="center">Capture File Properties — Packet Scan Rate</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1cdbe37b-55c5-4b21-a49d-afe0ab9dba5b" alt="Capture file properties" width="800"/>
</p>

<p align="center">Capture file properties used to calculate the packet scan rate across the duration of the scan.</p>

### <p align="center">Report</p>

<p align="center">

| Finding | Value |
|---------|-------|
| Scanner IP | 192.168.100.103 |
| Target IP | 192.168.100.102 |
| Scan Start | 13.006s |
| Scan End | 34.111s |
| Duration | ~21 seconds |
| Ports Probed | 2000 |
| Scan Rate | ~95 packets per second |
| Open Ports Found | None |
| Evidence | Zero SYN-ACK responses, RST confirms closed ports |

</p>

---

## <p align="center">Lab 3 - Malware Analysis</p>

### <p align="center">Pcap Loaded and Protocol Hierarchy Checked</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ae40cb89-74ac-4ed3-8704-2dab9330f1d0" width="800"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0af6ee55-de1c-4be9-beba-45a09dc0c388" alt="Protocol hierarchy malware" width="800"/>
</p>

<p align="center">Loaded a malware pcap from malware-traffic-analysis.net and checked Statistics > Protocol Hierarchy to identify suspicious traffic patterns including a large volume of HTTP form-encoded data.</p>

### <p align="center">HTTP Filter - POST Requests to Suspicious URL</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ae40cb89-74ac-4ed3-8704-2dab9330f1d0" alt="HTTP filter POST requests" width="800"/>
</p>

<p align="center">HTTP filter applied - almost every packet was a POST request to 45.131.214.85/fakeurl.htm, a clear indicator of malware beaconing to a C2 server.</p>

### <p align="center">Following the HTTP Stream</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d5856089-5f7d-4451-83ca-c8775f4c166f" alt="HTTP stream" width="800"/>
</p>

<p align="center">Followed the HTTP stream to reveal NetSupport Manager traffic — a legitimate remote access tool frequently abused as a Remote Access Trojan (RAT).</p>

### <p align="center">Breaking Down the Communication Pattern</p>

<p align="center">Communication pattern identified: CMD=POLL (infected machine checking in), CMD=ENCD (encoded data exchanged), ES=1 (encryption enabled), and Server: NetSupport Gateway/1.92 confirming attacker-controlled C2 infrastructure.</p>

### <p align="center">VirusTotal Confirms Malicious IP</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/33fa5a74-4540-4c9a-b3a1-bd44700e6693" alt="VirusTotal result" width="800"/>
</p>

<p align="center">Destination IP 45.131.214.85 confirmed as malicious via VirusTotal.</p>

### <p align="center">MAC Address from Packet Info</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3909a3b9-a777-4ede-9cf8-64eacab679b2" alt="MAC address" width="800"/>
</p>

<p align="center">Expanded packet details to retrieve the infected host MAC address: 00:19:d1:b2:4d:ad.</p>

### <p align="center">Kerberos Filter to Find Client Name</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e16b7580-220b-46c9-9b64-d2131178eecf" alt="Kerberos filter" width="800"/>
</p>

<p align="center">Applied the kerberos.CNameString filter to identify the client username as brolf.</p>

### <p align="center">Full Name Found via Find Packet</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/deae31ce-5bc0-499a-aea2-d1d9c55e34fa" alt="Find packet username" width="800"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/b24b9b12-b13c-447e-b103-a28c1cdc499e" width="800"/>
</p>


<p align="center">Used the Find Packet function to search for the string "Rolf" and identify the full username as Becka Rolf.</p>

### <p align="center">Report</p>

<p align="center">

| Finding | Value |
|---------|-------|
| Infected Host IP | 10.2.28.88 |
| Infected Host MAC | 00:19:d1:b2:4d:ad |
| Hostname | desktop-teyq2nr |
| Domain | easyas123.tech |
| Username | brolf |
| Full Name | Becka Rolf |
| C2 Server | 45.131.214.85 |
| C2 URL | http://45.131.214.85/fakeurl.htm |
| Malware Family | NetSupport RAT |
| Beacon Interval | ~60 seconds |

</p>

---

## <p align="center">Lab 4 - Credential Harvesting Detection</p>

### <p align="center">Telnet Capture Loaded</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/bf65fd04-72fe-4582-9a68-931ae6a56b5c" alt="Telnet capture" width="800"/>
</p>

<p align="center">Loaded telnet-cooked.pcap from the Wireshark Wiki.</p>

### <p align="center">Telnet Filter Applied</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/036da8fc-5a4e-41b1-a2ee-580fc10ccd29" alt="Telnet filter" width="800"/>
</p>

<p align="center">Filtered traffic by Telnet protocol to isolate relevant packets.</p>

### <p align="center">Following TCP Stream - Credentials Exposed</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d6de5337-a5b9-4144-9ef8-a7daf9fbf023" alt="TCP stream credentials" width="800"/>
</p>

<p align="center">Followed the TCP stream to reveal plaintext login credentials transmitted over Telnet.</p>

### <p align="center">Report</p>

<p align="center">

| Finding | Value |
|---------|-------|
| Protocol | Telnet |
| Login | fake |
| Password | user |
| Risk | Credentials transmitted in plaintext, visible to any network observer |
| Recommendation | Replace Telnet with SSH to encrypt credentials in transit |

</p>

---

## <p align="center">Lab 5 - Lateral Movement</p>

### <p align="center">SMB Filter - Session Setup Request with Suspicious Username</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e9455101-5b3a-44a5-b7b8-798a071c0bc8" alt="SMB session setup" width="800"/>
</p>

<p align="center">Filtered by SMB to identify a session setup request on packet 24 using the suspicious username "backdoor".</p>

### <p align="center">SMB2 Session Setup Commands</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f944a968-a661-4912-a340-4829d860b164" alt="SMB2 session setup commands" width="800"/>
</p>

<p align="center">Applied smb2.cmd == 1 filter to show all SMB2 session setup commands - two setup attempts identified.</p>

### <p align="center">Packet 25 - Successful Authentication</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0777855b-00f8-4490-a18d-31a5152b4ed6" alt="Successful SMB authentication" width="800"/>
</p>

<p align="center">Expanded packet 25 to confirm the session setup was successful.</p>

### <p align="center">NTLMSSP Auth Username Filter</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/792e7b23-3480-481a-a409-af3f57817a71" alt="NTLMSSP auth filter" width="800"/>
</p>

<p align="center">Applied ntlmssp.auth.username filter to identify the authenticating account.</p>

### <p align="center">DCERPC Protocols — Remote Execution Indicated</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3a240898-ebff-4fe3-9a48-d21361db2bd3" alt="DCERPC protocols" width="800"/>
</p>

<p align="center">DCERPC (Distributed Computing Environment Remote Procedure Call) protocols identified, suggesting remote execution activity following the lateral movement.</p>

### <p align="center">NTLMv2 Hash Captured</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/9e92ffe4-1af8-4e80-a245-9616f079275e" alt="NTLMv2 hash" width="800"/>
</p>

<p align="center">NTLMv2 hash captured for account 3B\Backdoor using the NTProofStr string filter, indicating a likely Pass-the-Hash attack where the attacker replayed a harvested credential to authenticate laterally without knowing the plaintext password.</p>

### <p align="center">Report</p>

<p align="center">

| Finding | Value |
|---------|-------|
| Source Host | 172.16.66.1 |
| Target Host | 172.16.66.36 |
| Account Used | 3B\Backdoor |
| Protocols Used | SMB2 + DCERPC |
| SMB2 Activity | C$ admin share access, file operations |
| DCERPC Activity | Remote procedure calls indicating possible remote execution |
| Authentication | NTLMSSP_AUTH confirmed on both protocols |
| NT Status | STATUS_SUCCESS (0x00000000) |
| Sessions | 4 authenticated sessions total |
| Hash Type | NTLMv2 |
| NTProofStr | eabacea9e12c184981777ec734233d12 |
| Suspicious File | __LegitFile |
| Risk | Hash could be used for Pass-the-Hash or offline cracking |
| Recommendation | Disable account immediately, investigate hash origin, memory forensics on 172.16.66.1 |

</p>

---

## <p align="center">Lab 6 - ARP Scanning</p>

### <p align="center">ARP Storm Capture Loaded</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b06dbb69-87af-484c-9c49-6fa2fa318229" alt="ARP storm capture" width="800"/>
</p>

<p align="center">Loaded arp-storm.pcap from the Wireshark website — all packets confirmed as ARP.</p>

### <p align="center">File Properties - Packet Rate</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3a3fb606-370e-473a-bcae-1f621f0b384e" alt="ARP file properties" width="800"/>
</p>

<p align="center">Capture file properties showed 622 ARP packets across 28.969 seconds.</p>

### <p align="center">Conversations - Single MAC Generating All Traffic</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/75a82230-487c-4a56-a3a2-c06c4e61a982" alt="ARP conversations" width="800"/>
</p>

<p align="center">Statistics > Conversations > Ethernet identified a single MAC address as the source of all ARP broadcast traffic.</p>

### <p align="center">Report</p>

<p align="center">

| Finding | Value |
|---------|-------|
| Activity | ARP scanning / host discovery |
| Scanner MAC | 00:07:0d:af:f4:54 (Cisco device) |
| Scanner IPs | 24.166.172.1 and 69.76.216.1 |
| Destination | Broadcast (ff:ff:ff:ff:ff:ff) |
| Target Range | Multiple subnets |
| Total Packets | 622 |
| Total Data | 37 kB |
| Duration | ~29 seconds |
| Scan Rate | 21.5 packets per second |
| Responses Received | 0 |
| Conclusion | Automated multi-subnet ARP reconnaissance confirmed, no responses captured |

</p>

---

## <p align="center">Skills Demonstrated</p>

<p align="center">Wireshark &nbsp;·&nbsp; Packet Analysis &nbsp;·&nbsp; Network Reconnaissance Detection &nbsp;·&nbsp; Malware Traffic Analysis &nbsp;·&nbsp; Credential Harvesting Detection &nbsp;·&nbsp; Lateral Movement Analysis &nbsp;·&nbsp; ARP Scanning Detection &nbsp;·&nbsp; NTLM Hash Capture &nbsp;·&nbsp; C2 Identification &nbsp;·&nbsp; TCP/UDP Stream Analysis</p>
