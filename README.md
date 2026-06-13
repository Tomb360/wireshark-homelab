# <p align="center">Wireshark Homelab Project</p>

<p align="center">A series of practical Wireshark labs covering packet capture, network reconnaissance detection, malware traffic analysis, credential harvesting, lateral movement, and ARP scanning using world pcap samples and simulated traffic.</p>

---
## <p align="center"> Sample Captures Used</p>
- <b>Nmap scan, telnet-cooked and arp-storm from Wireshark wiki</b>
  - [Wireshark Wiki](https://wiki.wireshark.org/SampleCaptures)
- <b>Malware Sample from Malware traffic analysis</b>
  - [Malware Traffic](https://malware-traffic-analysis.net/2026/02/28/index.html)
- <b>Lateral Movement Sample from Github</b>
  - [Lateral Movement](https://github.com/sbousseaden/PCAP-ATTACK/blob/master/Lateral%20Movement/LM_smbexec_smb_dcerpc_svcctl_epm.pcapng)


## <p align="center">Lab 1 — Wireshark Setup and Creating a Capture</p>

### <p align="center">Installed Wireshark</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514848359163236362/image.png?ex=6a2e2d79&is=6a2cdbf9&hm=41946d2ddd400529b40ad63c20d8c88e45e0a5964cce4bf2b21b625eb7e8355f&" alt="Wireshark installed" width="800"/>
</p>

<p align="center">Wireshark installed and launched ready for packet capture.</p>

### <p align="center">Selected Main Adapter and Generated Traffic</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514848782502727691/image.png?ex=6a2e2dde&is=6a2cdc5e&hm=9760fb0b258c139f52373646b293113875cc69b7f24894ac4f5641991650840d&" alt="Adapter selected and traffic generated" width="800"/>
</p>

<p align="center">Selected the main Ethernet adapter and visited 3 websites to generate traffic for a live capture.</p>

### <p align="center">Saving the Capture</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514849186984759336/image.png?ex=6a2e2e3e&is=6a2cdcbe&hm=293dbcc2c7fa221457071b7061338ab34d445703e9305d794c516fcde1663029&" alt="Saving capture" width="800"/>
</p>

<p align="center">Capture saved for further analysis.</p>

### <p align="center">3 Websites Resolved Using DNS Filter</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514855023320895509/image.png?ex=6a2e33ae&is=6a2ce22e&hm=fdab8ee9e69e2dc5dcb445222fcae2b954344ab6a9b0a816bd30aee1ae76e40c&" alt="DNS filter" width="800"/>
</p>
<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514855091218415646/image.png?ex=6a2e33be&is=6a2ce23e&hm=063d2e8c80d718fa97c95bf6762e593b2bb7ed2f2bd9cc5c1fc490bb3893cfff&" width="800"/>
</p>
<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514855201042071624/image.png?ex=6a2e33d8&is=6a2ce258&hm=7ea51278c0d566a5f394dee5f4c0614a2d12c200367928f91e70428c142983cd&" width="800"/>
</p>

<p align="center">Applied a DNS filter to identify the three websites resolved during the capture.</p>

### <p align="center">Protocol Hierarchy</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514857187686744216/image.png?ex=6a2e35b2&is=6a2ce432&hm=d4fe8f4d51d763bcca0be8a4ed9782dfde05f38e3eaf24e1ab1db4b07221502e&" alt="Protocol hierarchy" width="800"/>
</p>

<p align="center">Used Statistics > Protocol Hierarchy to view the percentage breakdown of traffic by protocol.</p>

### <p align="center">Conversations — Identifying the Most Active IP</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514857963334930452/image.png?ex=6a2e366b&is=6a2ce4eb&hm=303b3faad36939e8e7c3bd49e8d88bd710ef35c075da81787b2b9b9d797c0716&" alt="Conversations" width="800"/>
</p>

<p align="center">Statistics > Conversations used to identify which IP address generated the most traffic.</p>

### <p align="center">Following UDP Stream to Reveal URL</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514858880209780819/image.png?ex=6a2e3745&is=6a2ce5c5&hm=ff64130cb3c0596e57cf637182dc9233078a7a5ce49ab5b67dec1c96e969a456&" alt="UDP stream" width="800"/>
</p>

<p align="center">Followed a UDP stream to reveal the URL embedded in the traffic.</p>

---

## <p align="center">Lab 2 — Network Reconnaissance</p>

### <p align="center">Downloaded Nmap Sample Capture</p>

<p align="center">
  <img src="" alt="Nmap sample capture" width="800"/>
</p>

<p align="center">Downloaded an Nmap scan sample from the Wireshark Wiki sample captures page.</p>

### <p align="center">Standard Nmap Scan — Multiple Connection Attempts</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514862603346903132/image.png?ex=6a2e3abd&is=6a2ce93d&hm=3822c4b50d9e25226f93490584ddaf3ca318489e84c793e4d4063966cd582c30&" alt="Nmap scan traffic" width="800"/>
</p>

<p align="center">Standard Nmap scan visible with many connection attempts originating from 192.168.100.103.</p>

### <p align="center">Filtering SYN Packets to Show the Attacker Knocking</p>

<p align="center">
  <img src="" alt="SYN filter" width="800"/>
</p>

<p align="center">Filtered for SYN packets to visualise the attacker probing each port in sequence.</p>

### <p align="center">No SYN-ACK Responses — No Open Ports</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514865709174226944/image.png?ex=6a2e3da1&is=6a2cec21&hm=0ac2c846e945e8e4b814691e934c0d10117feeeecf79cf3af0bd66ddeaaa1901&" alt="No SYN-ACK results" width="800"/>
</p>

<p align="center">Filter tcp.flags.syn == 1 && tcp.flags.ack == 1 returned no results, confirming no open ports were found by the scanner.</p>

### <p align="center">Capture File Properties — Packet Scan Rate</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514867460397072434/image.png?ex=6a2e3f43&is=6a2cedc3&hm=fa3b66a2e032ec37089bf22823eb79361d5e5804c5db0860c3173a82e5a8ff49&" alt="Capture file properties" width="800"/>
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

## <p align="center">Lab 3 — Malware Analysis</p>

### <p align="center">Pcap Loaded and Protocol Hierarchy Checked</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514870743261773824/image.png?ex=6a2e4252&is=6a2cf0d2&hm=4bac4fe24df8bda84bb447d29e75e1a9eaad98e60e00d72e5fc9b656625e1252&" alt="Protocol hierarchy malware" width="800"/>
</p>

<p align="center">Loaded a malware pcap from malware-traffic-analysis.net and checked Statistics > Protocol Hierarchy to identify suspicious traffic patterns including a large volume of HTTP form-encoded data.</p>

### <p align="center">HTTP Filter — POST Requests to Suspicious URL</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514871160825712710/image.png?ex=6a2e42b5&is=6a2cf135&hm=db198fb7820daa8da8f1b923beaa85a3d9f3b945210ba70602077f94c57b9377&" alt="HTTP filter POST requests" width="800"/>
</p>

<p align="center">HTTP filter applied — almost every packet was a POST request to 45.131.214.85/fakeurl.htm, a clear indicator of malware beaconing to a C2 server.</p>

### <p align="center">Following the HTTP Stream</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514871868199534672/image.png?ex=6a2e435e&is=6a2cf1de&hm=20b0ebb5e00b8eb30f9d7f7e6c64509661dec1deecf7c49874d6d64cdc4ced67&" alt="HTTP stream" width="800"/>
</p>

<p align="center">Followed the HTTP stream to reveal NetSupport Manager traffic — a legitimate remote access tool frequently abused as a Remote Access Trojan (RAT).</p>

### <p align="center">Breaking Down the Communication Pattern</p>

<p align="center">
  <img src="" alt="C2 communication pattern" width="800"/>
</p>

<p align="center">Communication pattern identified: CMD=POLL (infected machine checking in), CMD=ENCD (encoded data exchanged), ES=1 (encryption enabled), and Server: NetSupport Gateway/1.92 confirming attacker-controlled C2 infrastructure.</p>

### <p align="center">VirusTotal Confirms Malicious IP</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514872417749569677/image.png?ex=6a2e43e1&is=6a2cf261&hm=e73e9a9296556216373827aa8331e1bdffb393f45d865693b3e45751e3d60ee5&" alt="VirusTotal result" width="800"/>
</p>

<p align="center">Destination IP 45.131.214.85 confirmed as malicious via VirusTotal.</p>

### <p align="center">MAC Address from Packet Info</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514873654477983764/image.png?ex=6a2e4508&is=6a2cf388&hm=3cd51959c830b2f9b5f29f019cc6ad31dc610ec23045330cfe02ed77da7af20b&" alt="MAC address" width="800"/>
</p>

<p align="center">Expanded packet details to retrieve the infected host MAC address: 00:19:d1:b2:4d:ad.</p>

### <p align="center">Kerberos Filter to Find Client Name</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514879600717594624/image.png?ex=6a2e4a91&is=6a2cf911&hm=c40daf8354b15e56ce12e2600a987c26e8f3d8574cb97045f920d2f51b1f0004&" alt="Kerberos filter" width="800"/>
</p>

<p align="center">Applied the kerberos.CNameString filter to identify the client username as brolf.</p>

### <p align="center">Full Name Found via Find Packet</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514883566138294433/image.png?ex=6a2da583&is=6a2c5403&hm=1de0c1366b706d77dd8c943ecc1cdb176df17e832c8f2ad6bb0aa4b0d991c919&" alt="Find packet username" width="800"/>
</p>
<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514883357438382160/image.png?ex=6a2da551&is=6a2c53d1&hm=99f562c6ca57b1cec9a411043bf63b4f54b222f76698a58ca6b17f1d2fe5ec26&" width="800"/>
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

## <p align="center">Lab 4 — Credential Harvesting Detection</p>

### <p align="center">Telnet Capture Loaded</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514887806000955523/image.png?ex=6a2da976&is=6a2c57f6&hm=67e20129d026a68497d9c963ba1821ff6ed7957f16607cd9bca115481d52a91d&" alt="Telnet capture" width="800"/>
</p>

<p align="center">Loaded telnet-cooked.pcap from the Wireshark Wiki.</p>

### <p align="center">Telnet Filter Applied</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514888602679640174/image.png?ex=6a2daa34&is=6a2c58b4&hm=bef9a838faaf18cbc41d727bf795da232894dbe654e1b37dbc15c9ec2b8ffd05&" alt="Telnet filter" width="800"/>
</p>

<p align="center">Filtered traffic by Telnet protocol to isolate relevant packets.</p>

### <p align="center">Following TCP Stream — Credentials Exposed</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1514888744254050324/image.png?ex=6a2daa55&is=6a2c58d5&hm=ca685fd4268ebad34fe96b39ea343e15fabdea64ba772296efd06f150fe8fff4&" alt="TCP stream credentials" width="800"/>
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

## <p align="center">Lab 5 — Lateral Movement</p>

### <p align="center">SMB Filter — Session Setup Request with Suspicious Username</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515244700142010438/image.png?ex=6a2e4d18&is=6a2cfb98&hm=3055e29c026791c6dbc00bdd62e1883c7c1822bd2318963497f41c6b00052674&" alt="SMB session setup" width="800"/>
</p>

<p align="center">Filtered by SMB to identify a session setup request on packet 24 using the suspicious username "backdoor".</p>

### <p align="center">SMB2 Session Setup Commands</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515248702166532198/image.png?ex=6a2e50d2&is=6a2cff52&hm=34c55b8475a82577f7705abf8fce56770f0fffdf91810c18cf0fdf581d60d1d2&" alt="SMB2 session setup commands" width="800"/>
</p>

<p align="center">Applied smb2.cmd == 1 filter to show all SMB2 session setup commands — two setup attempts identified.</p>

### <p align="center">Packet 25 — Successful Authentication</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515248878658781295/image.png?ex=6a2e50fc&is=6a2cff7c&hm=0611516c8c17f4b29129f89138b21750d3c89a4da881a05858509ffc80ede761&" alt="Successful SMB authentication" width="800"/>
</p>

<p align="center">Expanded packet 25 to confirm the session setup was successful.</p>

### <p align="center">NTLMSSP Auth Username Filter</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515250190766968962/image.png?ex=6a2e5235&is=6a2d00b5&hm=077b2947b1f17a8d5448dac3fc6fcd18f7cb09f69ace7d31c30c7847813facbf&" alt="NTLMSSP auth filter" width="800"/>
</p>

<p align="center">Applied ntlmssp.auth.username filter to identify the authenticating account.</p>

### <p align="center">DCERPC Protocols — Remote Execution Indicated</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515251281738862672/image.png?ex=6a2e5339&is=6a2d01b9&hm=cde463971365d712a98949e9bc1486ac9570c06945d7e24e5ce10a0382fe6443&" alt="DCERPC protocols" width="800"/>
</p>

<p align="center">DCERPC (Distributed Computing Environment Remote Procedure Call) protocols identified, suggesting remote execution activity following the lateral movement.</p>

### <p align="center">NTLMv2 Hash Captured</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515251347396497528/image.png?ex=6a2e5349&is=6a2d01c9&hm=5d36eef2d1434f943b571e63c3514fcbf220c971cdf4f7009331c6705b89c86e&" alt="NTLMv2 hash" width="800"/>
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

## <p align="center">Lab 6 — ARP Scanning</p>

### <p align="center">ARP Storm Capture Loaded</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515252422497275944/image.png?ex=6a2e5449&is=6a2d02c9&hm=a04627e29d5ea69f68156b1a111f760a5b8c4b372090a747a00d0864fbed7c53&" alt="ARP storm capture" width="800"/>
</p>

<p align="center">Loaded arp-storm.pcap from the Wireshark website — all packets confirmed as ARP.</p>

### <p align="center">File Properties — Packet Rate</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515253131309613076/image.png?ex=6a2e54f2&is=6a2d0372&hm=7f9504517e4c2978f6404baaeb8b4e15328ff3ddfb7347dd737fbaedf11e94a6&" alt="ARP file properties" width="800"/>
</p>

<p align="center">Capture file properties showed 622 ARP packets across 28.969 seconds.</p>

### <p align="center">Conversations — Single MAC Generating All Traffic</p>

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1514476543982702773/1515255446720741448/image.png?ex=6a2e571a&is=6a2d059a&hm=641bf46b7f06611c9f159480b108c10e07ce8c0bf454a074ea6eeb9e746fed44&" alt="ARP conversations" width="800"/>
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
