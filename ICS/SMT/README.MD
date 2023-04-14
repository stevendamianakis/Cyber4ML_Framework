# Cyber4ML_Framework application in "SMT" research paper

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|No|Yes|No|No|


## Documentation

Documentation of the attack: [SMT Paper](https://tches.iacr.org/index.php/TCHES/article/view/7335)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK Enterprise framework.

| Tactic | Technique | Subtechnique | Description |
| - | - | - | - |
| Initial Access | Supply Chain Compromise | - | (1) |
| Execution | Change Operating Mode | - | (2) |
| Persistence | Hardcoded Credentials | - | (3) |
| Evasion | Masquerading | - | (4) |
| Evasion | Change Operating Mode | - | (2) |
| Lateral Movement | Default Credentials | - | (3) |
| Collection | Automated Collection | - | (5) |
| Impact | Loss of Productivity and Revenue | - | (4) |
| Impact | Loss of Protection | - | (4) |
| Impact | Theft of Operational Information | - | (4) |


#### Commands/Scripts
- (1)
```
To reduce the fabrication cost, most of the manufacturing and
fabrication is pushed offshore [Yeh12]. However, many of the offshore fabrication facilities
are considered to be untrusted. Manufacturing in untrusted foundries has raised concern
over potential attacks in the manufacturing supply chain, with an intimate knowledge of
the fabrication process, the ability to modify and expand the design prior to production,
and an unavoidable access to the fabricated chips during testing. Accordingly, fabrication
in untrusted foundries has introduced multiple forms of security threats from supply chain
including that of overproduction, Trojan insertion, Reverse Engineering (RE), Intellectual
Property (IP) theft, and counterfeiting [GFT13].
```
- (2)
```
In this paper, we introduce the Satisfiability Modulo Theory (SMT) attack on
obfuscated circuits. The proposed attack is the superset of Satisfiability (SAT) attack,
with many additional features. It uses one or more theory solvers in addition to its
internal SAT solver. For this reason, it is capable of modeling far more complex
behaviors and could formulate much stronger attacks. In this paper, we illustrate
that the use of theory solvers enables the SMT to carry attacks that are not possible
by SAT formulated attacks. As an example of its capabilities, we use the SMT attack
to break a recent obfuscation scheme that uses key values to alter delay properties
(setup and hold time) of a circuit to remain SAT hard.
``` 

- (3)
```
The SAT solver iteratively eliminates sets of incorrect keys and finds
the correct key within a small time, and unlike Brute force attack that requires attack
time exponential with respect to the number of inputs, its execution time grows almost
polynomially. Existing SAT attack, which can be modeled with query-by-disagreement
(QBD) or uncertainty-sampling, minimizes the number of queries (inputs) required to learn
(deobfuscate) the target function (obfuscated logic). Also, SAT attack terminates when
no more disagreeing inputs can be found, at which time the attack guarantees to find
the correct key.
```

- (4)
```
Accordingly, fabrication in untrusted foundries has introduced multiple forms of security threats from supply chain including that of overproduction, Trojan insertion, Reverse Engineering (RE), Intellectual Property (IP) theft, and counterfeiting [GFT13].
```

- (5)
```
The SMT attack is an oracle-guided attack. We assume that the attacker has the
reverse engineered but obfuscated netlist and a functional IC (oracle) that is unlocked. The
attacker can query the oracle with any stimuli i, and observe its output o. The purpose of
the attack is to find the key inputs, that make the obfuscated netlist logically equivalent
to that of the unlocked netlist.
```

