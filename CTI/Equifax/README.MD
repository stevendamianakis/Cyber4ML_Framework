# Cyber4ML_Framework application in "Equifax" CTI report

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|Yes|No|No|No|


## Documentation

Documentation of the attack: [CTI Report](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script | CVE/CWE |
| - | - | - | - | - |
| Initial Access | Exploit Public-Facing Application | - | (1) | CVE-2017-5638/CWE-20 |
| Execution | Exploitation for Client Execution | - | (1) | CVE-2017-5638/CWE-20 |
| Credential Access | Credentials from Password Stores | - | (2) | - |
| Exfiltration | - | - | (3) | - |


#### Documentation Parts
- (1)
```
On March 7, 2017, a critical vulnerability in the Apache Struts software was publicly
disclosed. Equifax used Apache Struts to run certain applications on legacy operating systems.

On May 13, 2017, attackers began a cyberattack on Equifax. The attack lasted for 76
days. The attackers dropped “web shells” (a web-based backdoor) to obtain remote control over
Equifax’s network. They found a file containing unencrypted credentials (usernames and
passwords), enabling the attackers to access sensitive data outside of the ACIS environment. The
attackers were able to use these credentials to access 48 unrelated databases
```

- (2)
```
On May 13, 2017, attackers began a cyberattack on Equifax. The attack lasted for 76
days. The attackers dropped “web shells” (a web-based backdoor) to obtain remote control over
Equifax’s network. They found a file containing unencrypted credentials (usernames and
passwords), enabling the attackers to access sensitive data outside of the ACIS environment. The
attackers were able to use these credentials to access 48 unrelated databases. 
```

- (3)
```
Attackers sent 9,000 queries on these 48 databases, successfully locating unencrypted
personally identifiable information (PII) data 265 times. The attackers transferred this data out of
the Equifax environment, unbeknownst to Equifax. Equifax did not see the data exfiltration
because the device used to monitor ACIS network traffic had been inactive for 19 months due to
an expired security certificate. On July 29, 2017, Equifax updated the expired certificate and
immediately noticed suspicious web traffic.
```
