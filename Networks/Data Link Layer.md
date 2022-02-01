# Framing Protocols
Send **frames** between physical layers, groups bits into packets & indicates host. No security.

### Byte-Oriented
#### Byte Counting 
![[Pasted image 20220125110111.png]]
😬 Desync risk if bit missing
Overhead: O(1)

#### Sentinel Approach 
Add START and END 
![[Pasted image 20220125110254.png]]
😬 END may appear in the data, cut message off short
![[Pasted image 20220125110513.png]]
✔ (**DLE**) Data Link Escape
![[Pasted image 20220125110543.png]]
😬 DLE may also be in data
✔ DLE the DLE
![[Pasted image 20220125111136.png]]
Overhead: O(n)

### Bit-Oriented
Sentinels, looks for row of 1 (x6)
![[Pasted image 20220125111551.png]]
😬 May be in data
**Bit stuffing** Every 1 (x5), append 0. Receiver removes 0 for every 1 (x4)
Sender 111111... (in data) -> Sender 1111101... -> Receiver, 111111... 
-> 1111110 (end) OR 1111111 (error, discard frame)

Overhead: 1/6 = 17% of length, O(n)

# Reliability
## Physical Noise
### Detection
**Naive error detection**: Send frames twice, x2 time, risk error in both

**Simple Parity check**: Add extra "parity bits" to each block to keep # of 1's even, if row has odd then it transmitted wrong. But, if 2 1's accidentally added then can't catch.
**2 Dimentional Parity**: Simple parity check + column parity bits
![[Pasted image 20220128095932.png]]
**Checksum**: Sum data as 16-bit ints
Overhead O(1)
Risk: If bit flipped in data *and* in checksum

**Cyclic Redundancy Check (CRC)**
- *CRC bits* append to data unit so unit becomes exactly divisible by a second, predetermined binary number
- At the destination, the incoming data unit is divided by the same number. If at this step there is no remainder, the data unit assumed to be correct.
Overhead O(1)

### Reaction
Acknowledge reception
Con: Inefficient for stop-and-wait protocol
Solution: **Sliding window protocol**, accept multiple messages then responses for all

# MAC
**Multiple-access** medium: Broadcast medium shared by many hosts
Risk of **collision** upon simultaneous reception of multiple messages, data is destroyed.

**MAC Protocols**: rulesets on sharing the medium, handles collisions

## Channel partition
Split resources between hosts (e.g. Time Division Multi-Access TDMA cellular, FDMA cellular)
**Taking turns**: Prevent collisions (e.g. token ring network)

## Contention 
Collide and recover (e.g. wifi, ethernet)
Evolution over history:
- ALOHA: Transmit, Acknlowedge, wait and resend. Con: Even a tiny bit of overlap ruins 2 packets, so low-utilization
- Slotted ALOHA: Hosts can only transmit starting and ending off a slot. Either completely collide or not at all. Con: Need synced clocks
- [[Ethernet]] (Carrier-sense multiple access with collision detection): Everyone on the network receives all signals, sense collision then wait to send. Also sense for collision. Abort and retry with randomized wait times and **exponential backoff**.

# Questions
Bit-Oriented Protocol, if receiver gets "11111011[...]" -> "1111111" (1 x 7) why should the frame be discarded? What if the message included "11111111"?
A: should be impossible to transmit 7 1's in a row, thus discard