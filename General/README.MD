# Cyber4ML_Framework application in a "Keylogger" malware.

## Framework application details

|Documentation|MITRE ATT&CK|Network Analysis|Log Analysis|
|-|-|-|-|
|Yes|Yes|No|No|

|Attacker Level|Environment|VPN|Attacker IP|Victim IP|
|-|-|-|-|-|
|Average|Linux|No|Same|Same|

## Documentation

Documentation of the attack: [Keylogger Documentation](https://github.com/stevendamianakis/Keylogger/blob/main/Linux_Guide/README.MD)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Command/Script |
|-|-|-|-|
| Resource Development | Develop Capabilities | Malware | [keylogger.py](https://github.com/stevendamianakis/Keylogger/blob/main/keylogger.py) |
| Execution | Command and Scripting Interpreter | Unix Shell | (1) |
| Persistence | Boot or Logon Autostart Execution | Login Items | - |
| Defence Evasion | File and Directory Permissions Modification | Linux and Mac File and Directory Permissions Modification | - |
| Credential Access |  Input Capture | Keylogging | [keylogger.py](https://github.com/stevendamianakis/Keylogger/blob/main/keylogger.py) |
| Collection |  Input Capture | Keylogging | [keylogger.py](https://github.com/stevendamianakis/Keylogger/blob/main/keylogger.py) |

#### Commands
- (1)
```
python3 /home/user/Desktop/keylogger.py
```
