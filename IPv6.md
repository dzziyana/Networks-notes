# Types of IPv6 Unicast Addresses

## Link Local
- _Every_ host has this
- Automatically set up based on MAC address
## GUA (global unique address)
- Globally reachable
- The “normal” IPv6 address
## ULA (unique local address)
- For local deployments
- Similar to RFC 1918 address space
- Can be NATed to GUA

# NDP - Neighbor Discovery Protocol
- provides [[ARP]] and [[DHCP]] functionality for IPv6
![[Pasted image 20250731131006.png]]

# NAT with IPv6
NAT is still possible in IPv6 but no longer needed
- Sufficiently large address space
- End customers typically receive a /64 prefix

Many routers are still configured to block incoming traffic (firewall)
- Manual configuration similar to port forwarding is still necessary in this case

# Happy Eyeballs 
## Problem: Should dual-stack hosts contact servers via IPv4 or IPv6?
### Solution: Try both but prefer IPv6
- Issue A (IPv4) and AAAA (IPv6) DNS queries simultaneously
- If AAAA record is received, start connection setup over IPv6 immediately
- If A record is received, wait 50 milliseconds for AAAA record
- If first connection attempt (e.g., via IPv6) is unsuccessful, try again with different address (e.g., via IPv4)

# Tunneling
![[Pasted image 20250731131609.png]]
![[Pasted image 20250731131628.png]]