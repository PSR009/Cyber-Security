# Cyber Security

A beginner's guide to various cybersecurity concepts and tools

***Note*** - Only for education purpose

## Contents

### [Digital Forensics and Incident Response](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/dfir.md)
### [Malware Analysis and Reverse Engineering](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/malware-analysis-and-reverse-engineering.md)
### [Network-based Tools and Techniques](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md)
### [Threat Hunting and Cyber Threat Intelligence](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/Hunting-CTI-OSINT/Hunting-CTI-OSINT.md)
  - Tracking
    - [APTs](https://github.com/PSR009/Cyber-Security/blob/main/Hunting-CTI-OSINT/APTs.md)
    - [Hacktivist Group](https://github.com/PSR009/Cyber-Security/blob/main/Hunting-CTI-OSINT/Hacktivism.md)
  - [OSINT](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md)
    - [Global Conflict Tracker](https://www.cfr.org/global-conflict-tracker) by Council on Foreign Relations (CFR)
  - [VirusTotal](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/Hunting-CTI-OSINT/VirusTotal.md)
  - [Yara](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/Hunting-CTI-OSINT/yara.md)
### [Tools / Plugins](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/Tools-Plugins.md)

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
