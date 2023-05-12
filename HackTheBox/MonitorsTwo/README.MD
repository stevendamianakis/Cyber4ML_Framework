# Cyber4ML_Framework application in "MonitorsTwo" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.54|10.10.11.211|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [MonitorsTwo Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/MonitorsTwo/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Reconnaissance | Gather Victim Host Information | Software | - | - |
| Initial Access | Exploit Public-Facing Application | - | [exploit.py](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/MonitorsTwo/exploit.py) | CVE-2022-46169/CWE-77/CWE-74  |
| Execution | Exploitation for Client Execution | - | [exploit.py](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/MonitorsTwo/exploit.py) | CVE-2022-23935/CWE-77/CWE-74  |
| Discovery | System Owner/User Discovery | - | (1) | - |
| Discovery | File and Directory Discovery | - | (2) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | (3) |
| Credential Access | Credentials from Password Stores | Password Managers | - | - |
| Credential Access | Brute Force | Password Cracking | (4) | - |
| Persistence | Valid Accounts | Local Accounts | (5) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | - |

#### Commands/Scripts

- (1)
```
whoami
```

- (2)
```
find / -perm -u=s -type f 2>/dev/null
```

- (3)
```
/sbin/capsh --gid=0 --uid=0 -- 
```

- (4)
```
john hashes --wordlist=rockyou.txt
```

- (5)
```
ssh marcus@10.10.11.211
```

## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/MonitorsTwo/attack_capture.pcapng)

## Malicious Log Data
