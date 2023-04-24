# Cyber4ML_Framework application in "Evaluating the Security of Logic Encryption Algorithms" research paper

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|No|Yes|No|No|


## Documentation

Documentation of the attack: [Evaluating the Security of Logic Encryption Algorithms](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7140252&tag=1)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK ICS framework.

| Tactic | Technique | Subtechnique | Description |
| - | - | - | - |
| Initial Access | Supply Chain Compromise | - | (1) |
| Persistence | Hardcoded Credentials | - | (2) |
| Lateral Movement | Default Credentials | - | (2) |
| Execution | Change Operating Mode | - | (3) |
| Impact | Loss of Productivity and Revenue | - | (4) |
| Impact | Loss of Protection | - | (4) |
| Impact | Theft of Operational Information | - | (4) |



#### Documentation Parts
- (1)
```
1) Attack Model: Considering a malicious foundry, we
assume the attacker has access to layout and mask information.
The gate-level netlist can be reverse-engineered from this [22].
We also assume that the attacker has access to an activated
IC on which to apply input patterns and observe outputs. This
could be obtained by purchasing an activated IC from the open
market. The components of our attack model are therefore: (i)
a gate-level netlist of the encrypted IC and (ii) a means for
applying arbitrary input patterns and observing the resultant
outputs on an activated IC.2
```
- (2)
```
2) Potential Attacks: Given the above attack model, an
attack is possible when an attacker can determine the correct
values of the key inputs. Let us consider potential attacks.
The naive idea of brute-force search does not work. If the
circuit has M inputs and L key inputs, this requires 2M
observations from an activated IC and O(2M+L) computations
on the encrypted design. Clearly, this is not practical.
```
- (3)
```
Rajendran et al. [17] propose using automatic test pattern
generation (ATPG) tools [3] to generate input patterns that
expose the value of a key input.
```
- (4)
```
This has led to increased
concerns of IC counterfeiting, piracy and unauthorized overproduction by the contract foundry [7, 16, 23]. The financial
risk due to counterfeit and unauthorized ICs was estimated to
be over $169 billion a year by IHS Technology [11]. Besides
financial losses, this issue potentially has national security
implications. The Semiconductor Industry Association (SIA)
estimates that 15% of all spare and replacement semiconductors purchased by the Pentagon are counterfeit
```
