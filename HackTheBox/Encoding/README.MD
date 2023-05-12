# Cyber4ML_Framework application in "Encoding" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.54|10.10.11.211|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Encoding Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Encoding/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Reconnaissance | Gather Victim Host Information | Software | - | - |
| Initial Access | Exploit Public-Facing Application | - | [exploit.py](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Encoding/exploit.py) | -/CWE-94 |
| Execution | Exploitation for Client Execution | - | [exploit.py](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/MonitorsTwo/exploit.py), (1) | -/CWE-94  |
| Discovery | System Owner/User Discovery | - | - | - |
| Discovery | File and Directory Discovery | - | - | - |
| Discovery | Permission Groups Discovery | Local Groups | (2) | - |
| Persistence | Valid Accounts | Local Accounts | - | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | (3) | - |

#### Commands/Scripts

- (1)
```
curl localhost:5000/etc/passwd
```

- (2)
```
sudo -l
```

- (3)
```
[Service]
Type=simple
ExecStart=chmod +s /bin/bash
[Install]
WantedBy=multi-user.target
```


## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Encoding/attack_capture.pcapng)

## Malicious Log Data
