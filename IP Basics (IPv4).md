# Header
## immediate needs
![[Pasted image 20250327131211.png]]

## addressing
![[Pasted image 20250327131255.png]]

## packet size differences
![[Pasted image 20250327131348.png]]

## other needs
![[Pasted image 20250327131422.png]]

# Prefixes
![[Pasted image 20250327132208.png]]
![[Pasted image 20250327132218.png]]
### In practice, the first and the last address of a prefix are not usable
## Mask Notation
### **Network Prefix Calculation**

A **network prefix** is obtained by applying the subnet mask to the IP address using a **bitwise AND operation**:

  `01010010.10000010.01100110.00110001  (IP Address) -- AND --   11111111.11111111.11111111.00000000  (Subnet Mask)`
  `01010010.10000010.01100110.00000000  (Network Address)`

Converting `01010010.10000010.01100110.00000000` back to decimal gives:
	
- **Network Address**: `82.130.102.0`

## Longest Matching Prefix
### Hierarchical addresses result in a compact table
• Less specific prefixes reduce table size

### Finding longest match more complex than table lookup
• Was a concern for fast routers, but not an issue in practice these
days thanks to TCAM (ternary content-addressable memory)
• However, TCAMs consume a lot of power …

## Aspects of Forwarding
Decrement TTL value
• Protects against loops

Check and recalculate header checksum
• To add reliability

Fragment large packets
• Split to fit it on next link

Send congestion signals
• Warns hosts of congestion

Generate error messages
• To help manage network

# Helper Protocols

### The Problem

> [!Question] The Problem
> A node wakes up for the 1st time...
> How does it get the IP address, network prefix, what is the IP of the default router, DNS resolver?...
> Link layer (MAC - medium access control) address is given on the NIC

## [[DHCP]] - Dynamic Host Configuration Protocol


## [[ARP]] - Adress Resolution Protocol