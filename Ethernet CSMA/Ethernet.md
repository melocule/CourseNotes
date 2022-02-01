Has minimum packet size (prevent collision), **MTU - Maximum Transmission Unit** (prevent hogging)

# Header
- Preamble: Syncs receiver clocks of everyone on network
- Start Frame
- Source (MAC address)
- Pad (optional, to meet minimum packet length)
- Checksum

# Collisions with a Hub
(Carrier-sense multiple access with collision detection): Everyone on the network receives all signals, sense collision then wait to send. Also sense for collision. Abort and retry with a determined order.

## Detection
Distance ⟹ **Propogation delay**, more likely to collide
![[Pasted image 20220128105137.png]]
Risk: Senders don't detect collision, C can't detect collision because it doesn't read and check the bits there. 
![[Pasted image 20220128105502.png]]
Solution: Minimum packet size & maximum distance

**Cable Length Formula**
`min_frame_size / (2*bondwidth) * light_speed = mox_coble_length`

## Reaction
Sender detects collision -> Send **jam signal** to all hosts O(1)
**Slot time**: 
**Exponential backoff** 
**MACA for wireless**

# Switch
CSMA/CD no longer needed, switch handles it.