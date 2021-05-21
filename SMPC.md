## What is? Secure Multi_party_computation

### Let's Consider 

- A set of parties with private inputs.
- Parties wish to jointly compute a function of their inputs sa that certain security properties are preserved.
- Properties must be ensured even if some of the parties maliciously attack the protocol
- Can model any cryptographic task

For Example: Companies that donot want to share their data to their potential compatitors or security agencies that work on
  the idea of sharing as much less data as possible.
  
## Application
- Election
- Auction
- Private database search
- Privacy-preserving data mining
- Secure set intersection (Tool and Application both)
- Much much more

## Security Requirements
### -- Consider a secure auction (with secret bids):
 - An adversary may wich to learn the bids of all parties
 - To prevent this, we require **PRIVACY**.
 
 - An adversary may wish to win with a lower bid than the highest
 - To prevent this, we require **CORRECTNESS**.
 
 - But, the adversary may also wish to ensure that it always gives the highest bid
 - To prevent this, we require **INDEPENDENCE OF INPUTS**.

 - An adversary may try to abort the execution if its bid is not the highest
 - We require **FAIRNESS**.

## General Security Propeties

Form the above discussion we get the following security properties
- **Pirvacy**: only the output is revealed
- **Correctness**: the function is computed correctly
- **Independence of inputs**: parties cannot choose inputs based on other's input
- **Fairness**: if one party recevies output, all receive output
- **Guranteed output delivery**

## Defining Security
### Option_1: Analyse security concerns for each sepcific problem
- Auctions: as in previous heading
- Elections: privacy, correctness and fairness only (?)
#### Problems:
- How do we know that all concerns are covered?
- Definitions are application dependent and need to be redefined from scratch
  for each task. 
### Option_2: General definition that capture all (most) secure computation tasks
**- Properties of any such definition**
- Well-defined adversary model
- Well-defined execution setting
- Security gurantees are clear and simple to understand


# Modeling Adversaries

## Adversarial behavior

**Semi-honest:** Follows the protocol specification
- Tries to learn more than allowed by inspecting transcript

**Malicious:**  Follows any arbitrary strategy.

**Covert:** Follows any arbitrary strategy, but is averse to being caught...... 

### For Example:
- Two Hospitals want to carry out secure computation over the unoin of their databases but they donot trust each other as the hospitals 
might not want to have a sneak peak over the data and they might not even try. But we cannot say the same for the IT depratment they might 
try to get hands on some of the data form the other hospital. One does not want their's hospitals data to lie around in someone else server.
This type is called **semi-honest** Adversaries.

- Their is a group of companies that is trying to carry out computations over their combined data and there is a rule if one of the company cheats it will be kicked out of the colaboration. So the company may be restrcits itself from attacking or may weight its profits over loss from cheating. This type of adversary comes under **Covert** adversary. 

## Adversial power
- **Polynomial-time:** computational security
- **Computationally unbounded:** Information-theoretic security

## Corruption strategy
- **Static:** The set of corrupted parties is fixed before the execution begins.
###### For Example:
Here the adversary can choose who to corrupt. This can be termed as modern hacking attack, where the attacker can break into a machine which suits it's needs. Supose, there is a portocol where we choose 100 parties and out of them we choose 5 parties for main
computation, so the attacker may attack these 5 parties to get probable chance of successful attack.

- **Adaptive:** The adversary can corrupt parties during the execution, based on what has happened.(Quit harder comapred to static)
- Models modern "hacking"
- cannot use strategies that choose a small set of representatives to compute for all
- In general, **much harder!**

# Exceution Setting

### Stand alone

Consider a single protocol execution only (or that only a single execution is under attack).

### Concurrent general composition

- Arbitrary protocols executed concurrently
- Realistic setting, very important model

### Stand-alone vs compositon

- **Stand-alone:**: A good place to start studying secure computation, techniques and tools are helpful.
- **Compositon:** True goal for construction.

# Feasibility of Secure Computation

**- Assuming an honest majority, any fucntionality can be securely computed**
- Even information theoretically, with adaptive security

**- Without an honest majority, it is impossible to achieve fairness in general**

**- Without an honest majority, any fucntionality can be securely computed without fairness**

# The Yao and BMR Protocols

- Yao presented the first protocol for secure (Two-party) computation.
- Yao's protocol was followed by several protocols for the multi-party setting
  **(Goldreich-Micali-Wigderson(GMW)) - Ben Or-Goldwasser-Wigderson (BGW), Chaum-Crepeau-DAmgard (CCD)**

- Beaver-Micali-Rogaway (BMR) presented a multiparty protocol using a similar approach to yao's, and with only 0(1) commmunication 
rounds.

# Yao's Protocol

#### A protocol for general secure two-party computation

- Consatant number of rounds
- The basics protocol is secure only for semi-honest adversaries
- Many applications of the methodology beyond secure computation.

#### General Secure Computation

- Can securely compute any functionality
- Based on a represntation of the functionality as a Boolean circuit.

This protocol is used against semi-honest adversaries.

# Byzantine Generals Problem

[Link to the paper](https://people.eecs.berkeley.edu/~luca/cs174/byzantine.pdf)


Lets's say, we are in the Byzantine empire (an anicent roman empire 🏰) and it is surrounded by **n** generals. 

#### We consider:

- **n** generals, connected by **pair-wise private, authentic channel**.
- Each General has a secret plan (bit):
    - retreat (0)
    - attack (1)
- Upto **t** generals may be **traitor**.
- Goal: to come up with a **common action plan for the honest generals**.
    - Should be equal plan of the **hosnest generals** if they all had the **same individual action plan**.

#### Computer sciecne based abstraction:

- **n** mutually-distrusting parties.
- Upto to **t** corruption.
- **Goal**: to design a **distributed protocol**, allowing the **honest parties** to agree on a **common output**. 

    - (m1, m2, m3, m4, m5, ......, mn-1, mn ---> m  **[Agreement]**(all the good servers or parties at end should have a common ouput and this is agreement.)
    - (m1, m2, m3, m4, m5, ......, mn-1, mn ---> m  **[Validity]**(if all the good servers have same input.. then that should be the final output.)
    
#### Applications:
   - Secure multi-party computation (MPS) protocols.
   - State-machine replication / distributedd databases.
   
#### Some of the Widely-Studied settings:

- Level of Syncronization
- Type of faults
- Setup available
- Type of channels