# Middleboxes
![[Pasted image 20250731121756.png]]

## Advantages
• A possible rapid deployment path when there is no other option
• Control over many hosts
## Disadvantages
• Breaking layering interferes with connectivity; strange side effects
• Poor vantage point for many tasks
• Cause Internet ossification: makes it more challenging to deploy new protocols

# How NAT works
NAT device keeps an internal/external table
- Typically uses IP address + TCP/UDP port (transport layer)
- This is address and port translation

# NAT Downsides
- Connectivity has been broken!
	- Can only receive incoming packets after an outgoing connection is set up
	- Difficult to run servers at home – requires explicit “port-forwarding” rules

- Additional issues when there are no connections (UDP apps)
	- Often solved with regular “keep-alive” messages to keep table entries

- Breaks apps that unwisely represent their IP addresses as ASCII within packet data (e.g., FTP)

# NAT Upsides
- Relieves much IP address scarcity pressure
	- Many (most) home hosts behind NATs

- Easy to deploy
	- Rapidly, and by you alone
	- Very flexible in terms of address space

- Useful functionality
	- Firewall
	- Hides internal network structure and configuration (enhances privacy)

- Kinks will get worked out eventually
	- “NAT Traversal” for incoming traffic