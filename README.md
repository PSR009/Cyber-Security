# Cyber Security

A beginner's guide to various cybersecurity concepts and tools

***Note*** - Only for education purpose

## Contents

### [Threat Intelligence and Ethical Hacking](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/README.md)
### [Malware Analysis and Reverse Engineering](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/malware-analysis-and-reverse-engineering.md)
### [Digital Forensics and Incident Response](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/dfir.md)

## Network-based

- Public networks like hotels, libraries, airports are the most vulnerable
- Anyone can list every device on the network and see the URLs visited
- One can even redirect the traffic to the attacker's page and steal credentials

### Common Attack Services and Protocols

|Name|
|:-:|
|RDP|
|VNC|
|SSH|
|SMNP|
|SMB|
|Telnet|
|RPC|
|SIP Server|
|NFS|
|Nginx|
|Building Control|

### Tools

- Vulnerability Scanners / Penetration Testing

|Name|Description|
|:-:|:-:|
|[Nmap](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#nmap)|Scan networks to find live hosts / targets / services|
|[Nikto](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#nikto)|Simple and general vulnerability scanner|
|[Skipfish](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#skipfish)|Build a website map and find hidden URLs and files|
|[Wapiti](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#wapiti)|Find all vulnerabilities and exploit them from the terminal|
|[OWASP-ZAP](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#owasp-zap)|All exploitations using a GUI|
|[Xsser](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#xsser)|Super specialised XSS|
|[Nuclei](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#nuclei)|Scan website, network, DNS|
|[Trivy](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#trivy)|Scan your machine and any server|
|[Vuls](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#vuls)|Scan anything for the most recent vulnerabilities|

|Name|
|:-:|
|Kali Linux|
|Metasploit|
|[Wireshark](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#wireshark)|
|John the Ripper|
|Hashcat|
|Hydra|
|Burp Suite|
|Zed Attack Proxy|
|sqlmap|
|aircrack-ng|
|[BeEF](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#beef)|

- MITM Attacks
  - [Bettercap](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#bettercap)
  - [ARP Poisoning & Sniffing](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#mitm-attack--sniffing-network-traffic)

- OSINT

|Name|Description|
|:-:|:-:|
|[Twint](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#twint-for-twitter)|Twitter|
|[Osintgram](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#osintgram-for-instagram)|Instagram|
|[PhoneInfoga](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#phoneinfoga-for-phone-numbers)|Phone Numbers|
|[Sherlock](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#sherlock)|Social Media Hunts|
|[Google Search Dork Requests](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#google-for-passive-recon-fingerprinting)|Passive Recon|

- Search Engines

|Name|Description|
|:-:|:-:|
|Shodan|Search for devices connected to the internet|
|Wigle|Database of wireless networks with statistics|
|Grep App|Search across a half million git repos|
|Binary Edge|Scans the internet for Threat Intelligence|
|ONYPHE|Collects CTI data|
|GreyNoise|Search for devices connected to the internet|
|Censys|Assessing attack surface for internet connected devices|
|Hunter|Search for email addresses belonging to a website|
|Fofa|Search for various Threat Intelligence|
|ZoomEye|GAther information about targets|
|LeakIX|Search publicly indexed information|
|IntelligenceX|Search Tor, I2P, data leaks, domains and emails|
|Netlas|Search and monitor internet connected assets|
|URL Scan|Free service to scan and analyse websites|
|PublicWWW|Marketing and affiliate marketing research|
|FullHunt|Search and discovery attack surfaces|
|CRT sh|Search for certs that have been logged by CT|
|Vulners|Search vulnerabilities in a large database|
|Pulsedive|Search for Threat Intelligence|
|Packet Storm Security|Browse latest vulnerabilities and exploits|
|GrayHatWarefare|Search public S3 buckets|

- [Hacking WiFi Passwords](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#hacking-wifi-passwords)

- Network Engineering

|Name|
|:-:|
|[SolarPUTTY](http://bit.ly/usesolarputty)|
|[WAN Killer](http://bit.ly/WANkiller)|
|[IP Address Scanner](http://bit.ly/ipscansw)|
|[Network Device Scanner](http://bit.ly/netdevicescanner)|
|[Wifi Heat Map](http://bit.ly/wifiheatmapsw)|
|[Wifi Analyzer](http://bit.ly/wifianalyzersw)|
|[SolarWinds NPM](http://bit.ly/netperfmon)|

## Setup

- Access the DarkWeb via VPN &#8594; Tor `.onion`;
  - Use `proxychains4` to setup multiple `SOCKS5` proxies as Threat Actors could control exit and entry nodes
    - Add proxies here : `/etc/proxychain4.conf`
    - Get free proxies from [SPYS.ONE](https://spys.one/en/socks-proxy-list/) that have the least latency but these have to be tested
    - Usage : `proxychains4 <application/cmd-line>`
    - Make sure the service of Tor is running : `sudo service tor start`
    - Tyres of Chaining available - Dynamic, Strict, Round Robin, Random (Hard for HTTPS)
    - Always leave the `proxy_dns` enabled
  - More Tor nodes or longer chains provide more security but speed degrades
  - Search : `ahmia.fi`
  - Use firewall like `Pfsense` and make sure only the required ports are open
- Testing
  - [VPN Leaks Detection](https://ipleak.net/)
  - [DNS Leaks Detection](https://dnsleaktest.com/)
- OS
  - The safest is to run `Tails OS` only on a USB
    - This erases any downloaded files removing your footprint
    - Make sure internet connection is turned off when accessing these downloaded files
  - `Whonix` has a gateway and workstation for access via Tor
  - `Kali Linux` and `Ubuntu` require manual setting up of Tor

## Others

### Domain Controller
- Command to fetch the domainrole
  ```
  > wmic computersystem get domainrole
  ```
  
  |Value|DomainRole|
  |:-:|:-:|
  |0x0|Standalone Workstation|
  |0x1|Member Workstation|
  |0x2|Standalone Server|
  |0x3|Member Server|
  |0x4|Backup Domain Controller|
  |0x5|Primary Domain Controller|
  
### References

|YouTube Channels|
|:-:|
|[David Bombal](https://www.youtube.com/c/DavidBombal)|
|[HackerSploit](https://www.youtube.com/c/HackerSploit)|
|[John Hammond](https://www.youtube.com/c/JohnHammond010)|
|[Network Chuck](https://www.youtube.com/c/NetworkChuck)|
|[Nour's tech talk](https://www.youtube.com/channel/UCVEJtttyiIG-LeTwwn_ML4w)|
|[LiveOverflow](https://www.youtube.com/c/LiveOverflow)|
|[stacksmashing](https://www.youtube.com/c/stacksmashing)|
|[The Cyber Mentor](https://www.youtube.com/c/TheCyberMentor)|

|Reverse Engineering / Malware Analysis|
|:-:|
|[Dr Josh Stroschein](https://www.youtube.com/c/DrJoshStroschein)|
|[DuMp-GuY TrIcKsTeR](https://www.youtube.com/c/DuMpGuYTrIcKsTeR)|
|[HEXORCIST](https://www.youtube.com/c/HEXORCIST)|
|[OALabs](https://www.youtube.com/c/OALabs)|
|[Malfind Labs](https://www.youtube.com/c/MalfindLabs)|
|[MalwareAnalysisForHedgehogs](https://www.youtube.com/c/MalwareAnalysisForHedgehogs)|
|[Neil Fox](https://www.youtube.com/c/0xf0x)|
|[The PC Security Channel](https://www.youtube.com/c/thepcsecuritychannel)|
