# Digital Forensics and Incident Response (DFIR)

## Windows Event IDs


|Event ID|Description|
|:-:|:-:|
|4624|	Successful Login|
|4625|	Failed Login|
|4672|	Admin Account Login|
|4634, 4647|	Successful Logoff|
|4771|	Pre-authentication failed across Domain|
|4768|	Domain Controller issued TGT|
|4776|	Successful or failed login across Domain|
|7034|	Service Crashed unexpectedly|
|7035|	Service sent a Start, Stop signal|
|7036|	Service is stopped or started|
|7040|	Service Start Type Changed i.e. changes to Boot, On Request, Boot|
|5140|	Network Share is Mapped|
|4778|	RDP session initiation|
|4779|	RDP session termination|

### Windows Login Type

|Login Type|	Description|
|:-:|:-:|
|2	|Login locally i.e. with keyboard|
|3	|Network Login|
|4	|Batch Login- used for scheduled tasks|
|5	|Windows service login- will be non-interactive|
|7	|Credentials supplied to lock/unlock screen|
|8	|Network Login sending credentials in clear |
|9	|New credentials are used other than current login user like run as command|
|10|	Used for RDP|
|11|	Cached credentials to login when machine is unable to contact DC|
|12|	Cached RDP|
|13|	Cached unlock|

### Scheduled Tasks

|Event ID|Description|
|:-:|:-:|
|106|	Task Scheduled|
|200|	Task Executed|
|201|	Task Completed|
|141|	Task Removed|

### Hunting Lateral Movement

#### Login Type - 3

- 4624 - Login to another system on network with Login Type 3
- 4672 - Elevating to Admin
- 5140 - Copy payload onto target system (network share mapping)
- 200 - Scheduled Task malicious filename under `Action Name` attribute
- 4634 - Logoff

#### Login Type - 10

- 4778 - RDP session initiation that shows the souce IP and hostname
- 4624 - Authentication accepted
- 5140 - Copy payload onto target system (network share mapping)
- 200 - Scheduled Task malicious filename under `Action Name` attribute
- 4779 - RDP session termination

### Note
- Too many 4625 IDs can give us an indication of a brute force/password guess attack.
- Windows stores hash of last ten successful authentications in it. (Pass-the-hash attack)
- The IDs 4778, 4779 alone doesn't indicate an RDP session as Windows also uses that for Fast User Switching feature.

### Filtering

- [A Complete Guide to Using the Get-WinEvent PowerShell Cmdlet](https://adamtheautomator.com/get-winevent/)
- [A Better Way To Search Events](https://powershell.org/2019/08/a-better-way-to-search-events/)
  - FilterHashTable
  - FilterXPath
  - FilterXML

### Tools

|Name|  Description|
|:-:|:-:|
|[DeepBlueCLI](https://github.com/sans-blue-team/DeepBlueCLI)|  PowerShell Module for Threat Hunting via Windows Event Logs|

### References

- [Relevance of Windows EventIDs in investigation](https://resources.infosecinstitute.com/topic/relevance-of-windows-eventids-in-investigation/)
- [Threat Hunting via Event Logs](https://systemweakness.com/threat-hunting-via-event-logs-a98b4a4ea64f)
