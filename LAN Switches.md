- Use multiple links/wires
- Basis of modern (switched) Ethernet

# Switched element
Hosts are wired to Ethernet switches with twisted pair
- Switch serves to connect the hosts
- Wires usually run to a closet
![[Pasted image 20250725115023.png]]

## Inside a hub
All ports are wired together; more convenient and reliable than a single shared wire
![[Pasted image 20250725115538.png]]

## Inside a switch
Uses frame addresses to connect input port to the right output port; multiple frames may be switched in parallel
Port may be used for both input and output (full-duplex)
- Just send, no multiple access protocol
![[Pasted image 20250725115624.png]]

### Multiple inputs sending to one output
![[Pasted image 20250725120300.png]]

# Advantages of switches
Switches and hubs have replaced the shared cable of classic Etherne
- Convenient to run wires to one location
- More reliable; wire cut is not a single point of failure that is hard to find
Switches offer scalable performance
- e.g. 1 Gbps per port instead of 1 Gbps for all nodes of shared cable / hub

[[Switch Forwarding]]