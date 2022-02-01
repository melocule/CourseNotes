2 discrete signals
**non return to zero (NRZ) encoding** transmit bits with voltages high = 1, low = 0 (relative, bc voltage changes unexpectedly as moves across wire)

**synchronous** ⏲ on both sides for proper signal sampling (parsing)

**desynchronization**: mechanically, ⏲s won't be exactly the same, timing can mutate eg:
![[Pasted image 20220125102838.png]]

**non return to zero *inverted* (NRZ*I*) encoding** ensures ⏲ sync for streams of 1s, but not 0s
1 = transition @ ⏲ boundary. 0 = no transition
![[Pasted image 20220125103708.png]]
**Manchester encoding** solves ⏲ skew, takes x2 time
bits are transitions  (1 = high-low, 0 = low-high)

**4-bit/5-bit encoding (100 Mbps Ethernet)** solves ⏲ skew w/o slowness
NZRI + 4-bit mssg -> transmit 5-bit mssg -> receiver translate to 4-bit, prevent super long 0-streams
![[Pasted image 20220125104642.png]]
