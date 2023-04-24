# Cyber4ML_Framework application in "The Key is Left under the Mat: On the Inappropriate Security Assumption of Logic Locking Schemes" research paper

## Framework application details

|Documentation|MITRE ATT&CK|Enterprise|ICS|Network Analysis|Log Analysis|
|-|-|-|-|-|-|
|Yes|Yes|No|Yes|No|No|


## Documentation

Documentation of the attack: [The Key is Left under the Mat: On the Inappropriate Security Assumption of Logic Locking Schemes](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9300258)

## MITRE ATT&CK mapping

Below, we map the attack to the MITRE ATT&CK ICS framework.

| Tactic | Technique | Subtechnique | Description |
| - | - | - | - |
| Initial Access | Supply Chain Compromise | - | (1) |
| Impact | Loss of Productivity and Revenue | - | (1) |
| Impact | Loss of Protection | - | (1) |
| Impact | Theft of Operational Information | - | (1) |
| Persistence | Hardcoded Credentials | - | (2) |
| Lateral Movement | Default Credentials | - | (2) |
| Execution | Change Operating Mode | - | (3) |



#### Documentation Parts
- (1)
```
Logic locking has been proposed as an obfuscation
technique to protect outsourced IC designs from IP piracy by
untrusted entities in the design and fabrication process.

In
the horizontal model, different steps of chip manufacturing,
such as design, integration, fabrication, and packaging may no
longer be completed under the same roof. In this case, with
many entities involved in the supply chain that are located
across the globe, original IP owners no longer have control
over the entire supply chain [1], [2]. Hence, Intellectual Property (IP) vendors and design houses are facing the threat of IP
theft/piracy, tampering, overproduction, and counterfeiting. In
the past years, IP protection was entirely dependent on passive
protection schemes like patents, copyrights, and watermarks.
Due to the failure of the protections mentioned above schemes,
researchers have focused on developing active approaches like
IC metering [3], IP encryption [4], logic locking/ obfuscation IP Design IP Integrator Foundry Distribution & Packaging End-user Trusted Untrusted [5], [6], state space obfuscation [7], secure split manufacturing [8], and IC camouflaging [9]. 
```
- (2)
```
In this section, we present how an attacker can proceed to
break into a logic locking circuitry using optical probing. For
a successful attack against logic locking involving malicious
foundries or SoC integrators, or end-users with reverse engineering capabilities, we assume the following information
is available. First, the GDSII layout of a logic obfuscated
chip or IP is available. Hence, the attacker can partially or
entirely reverse engineer the chip or an IP, and thus, localize
the registers or key-gates. Second, an attacker has access to
an unlocked IC and has knowledge about the functionality of
the chip. Third, the attacker has access to an optical probing
system; such a system is available in any FA lab and can be
rented for a couple of hundred dollars per hour. In addition to
that, she may need standard lab equipment, which are available
in the market.
Among these three assumptions, the first one is not applicable to an end-user who does not have the full-blown reverse
engineering capability. To find out the key value form a target
IP using optical probing, she would need to complete the three
following steps: a) Preparing the sample for probing; b) Partial
reverse engineering the chip to localize the key-registers; c)
Extracting the key value form key-gates/registers. The steps
for extracting key values are shown in Fig. 3.
```
- (3)
```
In the case of PoC implementation, the circuit is obfuscated
with the XOR/XNOR gates connected with K1 and K2 inputs,
see Fig. 4a. Once the correct input combination (K1 = 1
and K2 = 0) is applied, the circuit produces the correct
output Y. Here, a, b, and c stand for the inputs of the circuit.
We implemented four of the logic locked circuit shown in
Fig. 4a in a circuit block, as shown in Fig. 4b, each logic
locked circuit connected to three input registers implemented
in parallel representing a, b, and c port in Fig. 4a. The key in
our design is 8-bit length as each logic locked circuit in Fig.
4a has two key bits. We also used 8-bit of parallel registers
to feed the key to key-gates. In the design, a reset signal is
implemented to imitate the reset process in the chip. In the
real scenario, the attacker can connect a signal generator to
the power pins of the chip and reboot the chip to induce the
desired frequency for performing EOFM.
```

