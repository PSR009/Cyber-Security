# Threat Intelligence and Ethical Hacking

A beginner's guide to various tools and concepts

***Note*** - Only for education purpose

## Network-based

- Public networks like hotels, libraries, airports are the most vulnerable
- Anyone can list every device on the network and see the URLs visited
- One can even redirect the traffic to the attacker's page and steal credentials

Tools
- [Bettercap](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#bettercap)
- [BeEF](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#beef)
- Vulnerability Scanners
  - Nikto – simple and general vuln scanner
  - Skipfish – build a website map and find hidden URLs and files
  - Wapiti – find all vulnerabilities and exploit them from the terminal
  - OWASP-ZAP – all exploitations using a GUI
  - Xsser – super good super specialised XSS
- Network Engineering
  - [SolarPUTTY](http://bit.ly/usesolarputty)
  - [WAN Killer](http://bit.ly/WANkiller)
  - [IP Address Scanner](http://bit.ly/ipscansw)
  - [Network Device Scanner](http://bit.ly/netdevicescanner)
  - [Wifi Heat Map](http://bit.ly/wifiheatmapsw)
  - [Wifi Analyzer](http://bit.ly/wifianalyzersw)
  - [SolarWinds NPM](http://bit.ly/netperfmon)
- OSINT
  - [Twint](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#twint-for-twitter) for Twitter
  - [Osintgram](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#osintgram-for-instagram) for Instagram
  - [PhoneInfoga](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#phoneinfoga-for-phone-numbers) for Phone Numbers
  - [Sherlock](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#sherlock) for social media hunts
  - [Google Search Dork Requests](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/osint.md#google-dorks)
- [Hacking WiFi Passwords](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#hacking-wifi-passwords)

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
