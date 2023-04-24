# Cyber4ML_Framework application in "Power Side-Channel Attack Analysis" research paper

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|No|Yes|No|No|


## Documentation

Documentation of the attack: [Power Side-Channel Attack Analysis Paper](https://mdpi-res.com/d_attachment/cryptography/cryptography-04-00015/article_deploy/cryptography-04-00015-v3.pdf?version=1592905738)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK ICS framework.

| Tactic | Technique | Subtechnique | Description |
| - | - | - | - |
| Initial Access | - | - | (1) |
| Persistence | Hardcoded Credentials | - | (2) |
| Lateral Movement | Default Credentials | - | (2) |

#### Documentation Parts
- (1)
```
One common setup for a CPA is shown in Figure 13. To mount this attack, we use a computer
that can send random but known messages to the device we are attacking, and trigger a device to
record power measurements of the data bus. After some amount of time, we end up with a data pair
of known input and power measurements.
```
- (2)
```
Throughout this survey, we have seen that side-channel attacks for key recovery have a similar
attack model. A model is designed based on knowledge of the cryptographic algorithm being attacked,
such that when fed with the correct key guess, its output will be as close as possible to the output of the
device being attacked when given the same input. Figure 17 illustrates that model from a high-level
perspective and terminates in an expression for what is called the distinguisher. A distinguisher is any
statistic which is used to compare side-channel measurements with hypothesis-dependent predictions,
in order to uncover the correct hypothesis.
``` 
