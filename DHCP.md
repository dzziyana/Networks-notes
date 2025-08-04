# Dynamic Host Configuration Protocol
protocol for automatically configuring addresses

> [!Tip] Functionality
> - leases IP addresses to nodes
> - provides parameters, such as
> 	- Network prefix, 
> 	- address of local router = ***default gateway***
> 	- DNS server, time server, etc.
### Bootstrap
![[Pasted image 20250327180752.png]]

![[Pasted image 20250327180920.png]]
To renew an existing lease, an abbreviated sequence is used:

• REQUEST , followed by ACK
Protocol also supports replicated servers for reliability

## ... is on top of [[UDP]]
