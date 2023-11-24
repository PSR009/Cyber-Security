# Threat Hunting with VirusTotal

## Episode 2 (by Alexey Firsch, Security Engineer - VirusTotal)

Need
- Focus on undetected threats in your infrastructure
- Finding additional pieces of attack
- Understading whole attack chain
- Learning TTPs and attributing to a threat actor

Yara
- Exact detection
    - AV-like detection for specific IOCs with very few FPs
- Hunting detection
    - Generic approach "any of them" for related IOCs but has more FPs
    - Uncover additional actor's activites
VT
- Retrohunt
    - Search in the past to uncover additional actor activity for attribution
    - Check for FPs
- Livehunt
    - Search in the future for daily scans to track ongoing campaigns
    - Track leaked data, brand protection, etc
- Module for conditions
    - `metadata`
        - vt.metadata.new_file
        - vt.metadata.submitter.country == "CN"
        - vt.metadata.unique_sources == 1
        - vt.metadata.times_submitted == 1
    - `behaviour`
        - Ex: Colibri Loader by MalwareBytes
        - behavior_network:""
        - vt.behaviour.http_conversation
        - vt.behaviour.files_dropped
        - vt.behaviour.dns_lookups
        - vt.behaviour.ip_traffic
        - vt.behaviour.text_decoded
    - `pe`
        - pe.timestamp >= 1424563200
        - pe.pdb_path contains ""
        - pe.machine == pe.MACHINE_AMD64 or pe.machine == pe.MACHINE_IA64
            ```
            for any i in (0 .. pe.number_of_signatures) : (
                pe.singatures[i].issuer contains "" and (pe.signatures[i].serial == "" or pe.signatures[i].serial == "")
                )
            ```
    - `dotnet` : dotnet.assembly.name == "Keylogger"
    - `elf` : elf.number_of_sections == 1
    - `cuckoo` : cuckoo.network.host(/192\.168\.1\.1/)
    - `magic` : magic.type() contains "PDF"
    - `hash` : hash.md5(0, filesize) == ""
    - `math` : math.entropy(0, filesize) >= 7
    - `time` : pe.timestamp > time.now()
- VT Diff
    - Yara Generator
    - Need to maintain clean collection

## Episode 3 

By Alexey Firsch, Security Engineer VT | May 17, 2023 | 57 mins

Need
- Implement own interface for fetching custom data set from internal system
- Integratnio with Splunk, Crowdstrike, etc.
- Script and automate daily routine tasks
- Build own analysis conveyor leveraging VT's data
- Create monitoring dashboards to track TAs, specific malware, network cluster, etc.

Development Environment
- Colaboratory aka Colab - cloud version of Jupyter Notebook
- `Python` and `Go`
- 3rd party scripts and clients maintained (Maltego Transforms)
- Extensive API documentation

VT Search
- `engines:Lazarus OR engines:Bluenoroff`

Dependencies
```
pip install vt-py
pip install nest_asyncio # for vt-py compatibility with Colab
```

Code
```py
import nest_asyncio
import pandas as pd
import vt
import os

from datetime import datetime
from dateutil.relativedelta import relativedelta
from IPython.core.display import display, HTML

nest_asyncio.apply()
API_KEY = os.getenv('API_KEY')
client = vt.Client(API_KEY)

vti_query = 'engines:Lazarus OR engines:Bluenoroff'

files_av = client.iterator
```
