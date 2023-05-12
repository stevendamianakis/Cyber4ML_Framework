# Cyber4ML_Framework application in "Inject" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.54|10.10.11.204|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Inject Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Inject/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Discovery | Network Service Discovery | - | (1) | - |
| Initial Access | Exploit Public-Facing Application | - | - | -/CWE-98 |
| Execution | Exploitation for Client Execution | - | - | -/CWE-98 |
| Discovery | File and Directory Discovery | - | - | - |
| Initial Access | Exploit Public-Facing Application | - | - | CVE-2022-22963/CWE-94 |
| Execution | Exploitation for Client Execution | - | - | CVE-2022-22963/CWE-94 |
| Discovery | System Owner/User Discovery | - | (2) | - |
| Credential Access | Credentials from Password Stores | - | - | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | - |

#### Commands/Scripts
- (1)
```
nmap -sV 10.10.11.204
```

- (2)
```
whoami
```

## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Inject/attack_capture.pcapng)

## Malicious Log Data
