# YARA

## Tools
- Yara
- String Analyzer
- PE file Viewer
    - PE Studio (free, x64)
    - CFF Explorer, Cerbero Suite (commercial)
- Hex Viewer
    - Hiew (paid, Windows)
    - FAR (free, Windows)
    - Total Commander (free, Windows)
    - Radare2 (free, open-source, cross-platform)
- Binary diffing tool (vbindifff, radiff2)
- IDA Pro / Ghidra (Optional)

## Docs
- Yara and VirusTotal
- [File format memos](https://github.com/corkami/pics)

## Strings
- fullword
- wide
- wide ascii
- nocase
- wild characters
- range of characters
- conditional characters
- `$a=/regexp .* blah/ wide ascii`

## Conditions
- Check Headers
    - Good : `uint16(0) == 0x5A4D`
    - Bad : `($mz at 0)`
    - Mach-O or ELF
        - `(uint32(0) == 0x464c457f) or (uint32(0) == 0xfeedfacf)`
        - `(uint32(0) == cffaedfe) or (uint32(0) == feedface) or (uint32(0) == cefaedfe)`
- String count : `(#a == 5) or (#b > 7)`
- Filesize : `(filesize > 512) and (filesize < 5000000) or (filesize < 5MB)`
- `all of them`
- `any of them`
- `($a at 0), ($a at pe.entry_point)`
- `$a at (@b+16)`
- `$a in (0..100) and $b in (100..filesize)`
- `$a in (pe.entry_point .. pe.entry_point + 10)`
- `2 of ($a, $b, $c)`
- `2 of them`
- `2 of ($a*)`

## Uses
- Identify and classify malware
- Find new samples based on specific features
- Find new exploits and zero-days
- Help speeding IR
- Increase defenses by deplouyinh custom rules in-lab
- Idenotyf file formats, archives, packed files, known threats
- Filter network traffic
- Build own private AV

## Rule Naming Convention
- rule apt_CN_Winnti_stolencert {...}
- APT, exploit, crimeware, clean
- country/lang, designator, ZZ if unkown
- Threat Actor name
- malware name or family

## Metadata
- author
- date
- version
- reference
- description
- hash
- Others
    - last_modified
    - copyright/TLP
    - yara_version

## Rules
- The Good, the Bad and the Ugly
- Test rules internally or using a cloud solution (KLARA, VTMIS) to avoid too many FPs
- Use "fullword" when string is short
- Not based only on popular imports/exports
- Other than memory scan
    - Use filesize
    - Always check header
- Bad if catches only one sample
- Don't use runtime generated strings
- Don't put all possible criterias as a necessary condition
- Use 'strings -e l" to extratc ASCII test strings
- Look at results manually
    - Mutex or Event names
    - Rare user-agents
    - Registry key or Unique value names
    - Typos
    - PDB paths
    - GUIDs
    - Internal module names
    - Encoded or encrypted config strings
- Sources
    - Public, Exchange groups, APT reports
    - Test them and organize in different collections
        - [KLARA](https://github.com/KasperskyLab/klara) by Kaspersky (Similar to VT Retrohunt)
- FP Testing
    - Own Set : Windows XP, 7, 8; Linux, OSX, iOS
    - Public Set : Microsoft, Stuba

## Performance
- Use `-p` with SSD:
    - SSD + i7 : `-p 4`
    - SSD + RAIDO : `-p 32`
    - HDD : `-p 2`
- String List >> Loop

## Automatic Rule generators
- [`yarGen`](https://github.com/Neo23x0/yarGen) by Florian Roth
- `yara-generator.net` from JoeSandbox
- `XenOphOn` by Chris Clark
- `autorule` by Joxean Koret

## References
- Upping the APT hunting game: learn the best YARA practices from Kaspersky (Mar 31 2020 | 75 mins)
    - Costin Raiu, Director of Kaspersky's Global Research & Analysis Team (GReAT)
- Yara Rules
    - [Florian Roth](https://github.com/Neo23x0/signature-base/tree/master/yara)
    - [Trellix ATR Team](https://github.com/advanced-threat-research/Yara-Rules)
- VT Hunting
    - [Official Python 3 client library for VirusTotal](https://github.com/VirusTotal/vt-py)
    - [Online hash checker for Virustotal and other services](https://github.com/Neo23x0/munin)
    - [Generate VT hunting report and send it by email, slack or telegram](https://github.com/fr0gger/vthunting)
    - [Automating VirusTotal's API v3 for IP address and URL analysis w/HTML Reporting](https://github.com/b-fullam/Automating-VirusTotal-APIv3-for-IPs-and-URLs)

