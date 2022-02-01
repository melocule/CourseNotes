**Ethernet link** / segment = One transmission medium, switches don't count.
**LAN** = One wire
**Repeater** = Layer 1 device, echoes bits. Max 4 between any pair of hosts, or too many collisions. 
**Hub** = Layer 1 device, echoes mssg from one port to all *other* ports

# CSMA-CD 
*Carrier-sense multiple access with collision detection*
- (CS) Carrier sense = Nodes can distinguish between idle/busy link
- (MA) **Multiple access network** = Many hosts on one transmission medium (wire), everyone hears everything
- (CD) Collision detection = Hosts detect if their own messages collided with another's
Limited distance between hosts, because farther -> larger min message size to guarantee collision detection

# CSMA/CA
*Collision avoidance*
TODO

# Bridge
**Bridge** = switch that expands range of network by connecting multiple separate LANs, and redirecting messages, connects to both LANs.
*Layer 2 device* b/c interprets mssg w/ processor, memory for directory, doesn't just take signal and redirect like a *hub* would. More `$$$` though.
**Queue** for messages stored in memory, in case other side is busy. Memory limited, will lose all messages after capacity.
**Source** = Port mssg came from
Process:
1. Source includes destination in mssg
2. Source sends throughout LAN
3. Bridge detects if source is new host in network or moved to a different port, updates **forwarding table** based on input port`*`
4. Bridge gets destination MAC address from mssg 
5. Bridge determines output port w/ **forwarding table**
6. If output port different from source port, send to the other side. Otherwise source and destination were in the same LAN and already got the mssg, bridge discards it.
The bridge, not the sender, handles redirecting. So we don't need to add directory info to every new host.
**Internals:** Input ports, memory buffer to queue packets, output ports

**Forwarding Table** tracks MAC Address, Port, Age (Optional, good for investigating issues)

`*` If there is a loop, source will keep switching

### Example

Bridge1 - Hub - Bridge2
             /         \
        HostA       HostB

HostA mssg to host on Bridge1 -> Hub -> Bridge1, Bridge2, HostB
Bridge1: Sends to destination
Bridge2: Discards mssg b/c dest port = source port 
HostB: Discards

## Spanning  Tree Algorithm
### Loops
![[Pasted image 20220201105957.png]]
J: "Say hi to Z for me!"
B4: "Who? he's not in my forwarding table yet...lemme ask links H & I." -> B6, B1
B6 (in I): "Idk...lemme ask link G?" -> B1
B1 (in H): "Idk B6, lemme ask B4"
B4: 👁👄👁 "I have no message history so I don't know that I asked Guild I before, lemme ask them again"

Realistic reasons for bridge loops: 
- Multiple admins, nobody knows whole configuration so could be added unknowingly. 
- More likely, loops added on purpose for redundancy in case of failure. 

### Spanning Tree Algorithm
Subset of actual network topology *w/o* loops, based on root node.
![[Pasted image 20220201111154.png]]
How is this actually formed?
Each host makes local decisions on their preference...nobody knows the whole graph....

# Ethernet Switch
Evolution of bridge. 

# Questions
Why do bridge forwarding tables track age?
Why max 4 repeaters between any pair of hosts, to avoid collisions?